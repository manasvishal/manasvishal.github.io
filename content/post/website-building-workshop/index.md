---
title: 🌐 Personal Portfolio Website Workshop!
summary: Use popular tools such as Hugo, HTML, Jekyll
date: 2024-11-15
authors:
  - admin
tags:
  - Hugo
  - Jekyll
  - PhD
  - Code
  - HTML
image:
  caption: 'Image credit: [**ChatGPT**](https://chatgpt.com)'
---

# Welcome to the Personal Portfolio Website Workshop! 👋

Hello, fellow PhD students! 🎓

This repository is here to help you build your personal academic portfolio website. By the end of this guide, you’ll have a beautiful, professional webpage to showcase your research, publications, and achievements. We’ll use **HTML5 UP templates**, **Jekyll**, or **Hugo** to create a static website and deploy it to **GitHub Pages** for free hosting.

> 💡 *Feel free to choose the tools that best suit your skills and style. Each option has its own setup instructions.*

---
Tip: My [webpage](https://manasvishal.github.io/) uses [Hugo Academic CV Template](https://github.com/HugoBlox/theme-academic-cv) 

### Table of Contents

1. [Prerequisites](#prerequisites)
2. [Step 1: Fork and Clone the Repository](#step-1-fork-and-clone-the-repository)
3. [Step 2: Choose a Website Template](#step-2-choose-a-website-template)
4. [Step 3: Set Up Your Website with HTML5 UP, Jekyll, or Hugo](#step-3-set-up-your-website-with-html5-up-jekyll-or-hugo)
5. [Step 4: Customize Your Website](#step-4-customize-your-website)
6. [Step 5: Deploy to GitHub Pages](#step-5-deploy-to-github-pages)
7. [Resources & Tips](#resources--tips)

---

### Prerequisites

Before we start, here are a few things you’ll need:

- **GitHub Account:** Sign up if you haven’t already [here](https://github.com/).
- **Git**: [Download Git](https://git-scm.com/) to version control your website.
- **Code Editor**: Use a code editor like [VS Code](https://code.visualstudio.com/) or Atom.

> *Optional but helpful*: Familiarity with basic HTML, Markdown, or command line usage.

---

### Step 1: Fork and Clone the Repository

1. **Fork this repository** to create a copy under your GitHub account.
2. **Clone the repository** to your local machine. Open a terminal and run:

   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

   Now you’ll be able to work on your website locally!

---

### Step 2: Choose a Website Template

You have three main options for building your portfolio. Choose the one that best fits your needs:

1. **HTML5 UP Templates**: These are simple, beautiful HTML templates. Good for custom HTML/CSS.
2. **Jekyll**: A popular static site generator that works well with Markdown and GitHub Pages.
3. **Hugo**: Another static site generator that’s fast and flexible, especially for complex sites.

> **Note**: HTML5 UP templates provide raw HTML/CSS files, while Jekyll and Hugo generate static pages using Markdown and themes.

---

### Step 3: Set Up Your Website with HTML5 UP, Jekyll, or Hugo


#### Option A: Wordpress

1. Go to UMassD's word press [server](https://sites.umassd.edu/)
2. Login with your UMassD's credentials.
3. Choose a theme, add content and deploy the website.


#### Option B: HTML5 UP Templates

1. Go to [HTML5 UP](https://html5up.net/) and browse the templates. My [website](https://manasvishal.github.io/) uses [Editorial theme](https://html5up.net/editorial) 
2. Download the template you like, unzip it, and move its contents to your cloned repository.
3. Customize the HTML and CSS to reflect your personal information.

More resources:
- Standalone picocss templates : https://picocss.com/examples
- 100 templates : https://technext.github.io/100-template-bundle/


#### Option C: Jekyll

1. Install Jekyll by following [these instructions](https://jekyllrb.com/docs/installation/).
2. Create a new Jekyll site:

   ```bash
   jekyll new my-portfolio
   ```

3. Move your Jekyll site files into your cloned repository folder.
4. Start a local server to preview:

   ```bash
   bundle exec jekyll serve
   ```

5. Access the site at `http://localhost:4000` to see your progress.

More resources: 
- A comprehensive guide:  https://blog.christianposta.com/theme-setup/
- Another one:  https://www.pwills.com/posts/2017/12/20/website.html
- https://jamstackthemes.dev/theme/jekyll-professional-resume/
- https://jekyll-theme-minimal-resume.netlify.app/ https://github.com/murraco/jekyll-theme-minimal-resume
- https://jamstackthemes.dev/theme/jekyll-online-cv/
- https://ddbullfrog.github.io/resumecard/

#### Option D: Hugo

1. Install Hugo by following [these instructions](https://gohugo.io/getting-started/installing/).
2. Create a new Hugo site:

   ```bash
   hugo new site my-portfolio
   ```

3. Choose a theme from [Hugo Themes](https://themes.gohugo.io/) and install it.
4. Move your Hugo site files into your cloned repository folder.
5. Start a local server to preview:

   ```bash
   hugo server -D
   ```

6. Visit `http://localhost:1313` to view your website locally.

---

### Step 4: Customize Your Website

Now it’s time to make the website yours! Here are a few things you’ll want to update:

- **Personal Information**: Update your name, photo, bio, and contact information.
- **Research & Publications**: Add sections for your academic work, projects, and publications.
- **Social Media Links**: Add links to your LinkedIn, Twitter, or Google Scholar profiles.

If you're using HTML5 UP, edit the HTML files directly. For Jekyll and Hugo, you’ll generally edit Markdown files in the `content` or `_posts` folders.

---

### Step 5: Deploy to GitHub Pages

Once you’re happy with your website, it’s time to deploy!

1. Commit and push your changes to your GitHub repository:

   ```bash
   git add .
   git commit -m "Initial website setup"
   git push origin main
   ```

2. **Enable GitHub Pages** in your repository settings:
   - Go to your repository on GitHub.
   - Click on **Settings** > **Pages**.
   - Under **Source**, choose the `main` branch and save.

3. After a few minutes, your site will be live at `https://yourusername.github.io/your-repo-name`.

More resources:
- https://www.arnoudplantinga.nl/post/getting-started/
- https://matteocourthoud.github.io/post/website/
- https://lakemper.eu/blog/getting-started-with-hugo-academic-and-github-pages/

> **Note**: If using Jekyll or Hugo, make sure your `_config.yml` or `config.toml` file is configured correctly for GitHub Pages.

---

### Resources & Tips

- **HTML5 UP Documentation**: [HTML5 UP](https://html5up.net/)
- **Jekyll Documentation**: [Jekyll Docs](https://jekyllrb.com/docs/)
- **Hugo Documentation**: [Hugo Docs](https://gohugo.io/documentation/)

For help, reach out in the Slack channel or DM.

---

### Final Words

Congratulations on setting up your academic portfolio website! 🎉 This website will help showcase your work to the world, so feel free to iterate and improve it over time.

Happy coding, and best of luck with your research!


## Did you find this page helpful? Consider sharing it 🙌
