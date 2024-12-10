---
title: 💻 How to use manim on an HPC using containers
summary: Just some pieces of code on how to run manim on HPC
date: 2024-12-09
authors:
  - admin
tags:
  - Code
  - Python
  - Manim
  - HPC
image:
  caption: ''
---


## Example Output

Below is an example of a Fourier Square Wave animation created using Manim:

![Fourier Square Wave Animation](FourierSquareWave.gif)

This animation demonstrates how a square wave can be approximated by summing the first few terms of its Fourier series. The visualization helps in understanding the concept of Fourier series and how complex waveforms can be constructed from simpler sine and cosine waves.

<details>
  <summary>Click to expand the code</summary>

  ```python
  from manim import *

class FourierSquareWave(Scene):
    def construct(self):
        # Intro slide
        intro_text = Text(
            "This video was made using \nManim's Apptainer \non Unity HPC System",
            font_size=30,
            t2c={"Unity HPC System": YELLOW, "Apptainer": BLUE}
        )
        intro_text.to_edge(ORIGIN)
        self.play(Write(intro_text))
        self.wait(2)
        self.play(FadeOut(intro_text))
        # Title
        title = Text("Fourier Series Approximation of a Square Wave", font_size=36)
        title.to_edge(UP)
        self.play(Write(title))

        # Axes for the graph
        axes = Axes(
            x_range=[0, 2 * PI, PI / 4],  # X-axis range
            y_range=[-1.5, 1.5, 0.5],    # Y-axis range
            x_length=10,                 # Length of X-axis
            y_length=6,                  # Length of Y-axis
            axis_config={"color": WHITE},
        )
        labels = axes.get_axis_labels(x_label="x", y_label="y")
        self.play(Create(axes), Write(labels))

        # Fourier series terms
        def fourier_series(x, n):
            result = 0
            for k in range(1, n + 1, 2):  # Only odd terms
                result += (4 / (PI * k)) * np.sin(k * x)
            return result

        # Add graphs incrementally to show the Fourier approximation
        graphs = []
        colors = [BLUE, GREEN, YELLOW, ORANGE, RED]
        for i, n in enumerate(range(1, 10, 2)):
            graph = axes.plot(lambda x: fourier_series(x, n), color=colors[i % len(colors)], stroke_width=2)
            graphs.append(graph)

        # Create square wave for comparison
        square_wave = axes.plot(
            lambda x: 1 if (x % (2 * PI)) < PI else -1,
            color=WHITE,
            stroke_width=3,
        )

        # Animation of Fourier approximation
        self.play(Create(graphs[0]), run_time=2)
        self.wait(1)
        for i in range(1, len(graphs)):
            self.play(Transform(graphs[i - 1], graphs[i]), run_time=2)
            self.wait(0.5)

        # Final comparison with square wave
        self.play(Transform(graphs[-1], square_wave))
        self.wait(2)

        # Closing
        closing_text = Text("Fourier Series converges to the square wave!", font_size=30)
        closing_text.to_edge(DOWN)
        self.play(Write(closing_text))
        self.wait(2)
        # Save the final render to a custom path and name as a GIF
        self.renderer.file_writer.finish()
        self.renderer.file_writer.write_to_movie("../FourierSquareWave.gif")

  ```

</details>

## What is Manim

Manim (Mathematical Animation Engine) is an open-source Python library used to create precise and visually appealing animations for educational and illustrative purposes, especially in mathematics, physics, and engineering. It allows users to create mathematical visualizations, plots, and interactive 3D models that can be used in videos or presentations. Manim provides a wide range of tools for rendering equations, graphs, and geometric shapes, along with support for animations like transformations, rotations, and scaling. The library is widely used by educators, YouTubers, and researchers to explain complex concepts clearly and engagingly.

## What is HPC

High-Performance Computing (HPC) refers to the use of powerful computing resources, such as supercomputers or clusters, to solve complex and computationally intensive problems at high speeds. HPC systems typically feature multi-core processors, large amounts of memory, and parallel processing capabilities, which allow them to perform calculations and simulations that would be too slow or infeasible for standard computers. HPC is applied in various fields, including scientific research, climate modeling, aerospace, genomics, and financial modeling, where massive datasets and intricate calculations are common.

## What are containers (apptainer, singularity, docker)

Containers are lightweight, portable environments that encapsulate applications and their dependencies, allowing them to run consistently across different systems. Containers ensure that software runs in the same way regardless of the underlying hardware or operating system.

- **Docker**: A widely-used container platform that enables developers to package applications and their dependencies into containers. Docker simplifies the process of creating, testing, and deploying applications, offering tools like Docker Hub for sharing containers and Docker Compose for managing multi-container applications.
  
- **Singularity**: A container platform designed for high-performance computing (HPC) environments, offering similar features to Docker but with additional focus on providing seamless integration with supercomputing resources. It allows users to run containers on HPC clusters and enables reproducible scientific workflows.
  
- **Apptainer**: A continuation of Singularity, Apptainer is an open-source containerization platform that focuses on providing secure, reproducible, and scalable containers for scientific computing. Apptainer emphasizes a simplified user experience and integration with the HPC ecosystem, facilitating the deployment of complex applications in research environments.

Each of these tools provides a way to ensure that applications run consistently across different systems while minimizing compatibility issues and improving deployment speed.


## Running Manim on HPC using Apptainer

To run Manim on an HPC system using Apptainer, follow these steps:

1. **Load the module Apptainer**:
  ```bash
  module load apptainer/latest
  ```

2. **Pull the Docker Image for Manim**:
  Manim provides an official Docker image. Use the following command to pull the Docker image and convert it to an Apptainer SIF (Singularity Image Format) file:
  ```bash
 apptainer build manim.sif docker://manimcommunity/manim

  ```
Note: If you want to use your own docker container file, you can do so by:
  - ** Create a Dockerfile for Manim: **
    ```dockerfile
    FROM manimcommunity/manim:latest

    # Update Cairo and Pango
    # This is to ensure you are at the latest installation of cairo and pango
    RUN apt-get update && apt-get install -y libcairo2-dev libpango1.0-dev

    # Ensure pycairo is compatible
    RUN pip install --upgrade pycairo
    ```
  - **Build the Docker Image**
    ```bash
    docker build -t manim-updated .
    ```
  - **Build and Convert the Container**
    ```bash
    docker build -t custom-manim .
    apptainer build manim-custom.sif docker://custom-manim
    ```


3. **Run the Manim Container**:
  ```bash
  apptainer exec manim.sif manim --version
  ```

4. **Use manim for rendering**:
  ```bash
  apptainer exec --bind $(pwd):/workspace /path/to/manim.sif manim -pql example.py SceneName
  ```

Here’s what happens:

- `--bind $(pwd):/workspace`: Mounts your current directory into the container at `/workspace`.
- `/path/to/manim.sif`: Specifies the Apptainer image. Put proper path here
- `manim -pql example.py SceneName`: Runs Manim with the specified script (example.py) and scene (SceneName).

Replace `example.py` with your Manim script and SceneName with desired name for scene. This setup ensures that Manim runs consistently on the HPC system using the Apptainer container.


## References

1. [Manim](https://www.manim.community/): An open-source Python library for creating mathematical animations.
2. [3Blue1Brown](https://www.3blue1brown.com/): A YouTube channel that uses Manim to explain complex mathematical concepts.
3. [Docker](https://www.docker.com/): A platform for developing, shipping, and running applications in containers.
4. [Singularity](https://sylabs.io/singularity/): A container platform designed for high-performance computing environments.
5. [Apptainer](https://apptainer.org/): An open-source containerization platform for scientific computing, formerly known as Singularity.
6. [Unity](https://docs.unity.rc.umass.edu/about//): Unity is a collaborative research computing platform with a variety of member institutions.

## Did you find this page helpful? Consider sharing it 🙌

