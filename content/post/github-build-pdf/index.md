---
title: Github Action to Build PDF using pdflatex
summary: A piece of YAML code when used with Github actions will compile PDF on git push.
date: 2025-02-07
authors:
  - admin
tags:
  - Github
  - Code

---

```yaml
name: Build PDF and Push to Orphan Branch

on:
  push:
    branches:
      - main         # Trigger on pushes to main
  pull_request:
    branches:
      - main         # Trigger on pull requests to main

jobs:
  build-pdf:
    runs-on: ubuntu-latest

    steps:
      # 0. Cache APT packages for faster dependency installation
      - name: Cache APT packages
        uses: actions/cache@v3
        with:
          path: |
            /var/cache/apt
            /var/lib/apt/lists
          key: ${{ runner.os }}-apt-cache

      # 1. Check out the repository
      - name: Check out repository
        uses: actions/checkout@v3

      # 2. Set up LaTeX environment (full TeXLive is installed by default)
      - name: Set up LaTeX environment
        uses: xu-cheng/latex-action@v2
        with:
          root_file: "paper.tex"

      # 3. Compile PDF using Makefile
      - name: Compile PDF using Makefile
        run: make

      # 4. Upload the compiled PDF as an artifact
      - name: Upload PDF artifact
        uses: actions/upload-artifact@v4
        with:
          name: compiled-pdf
          path: paper.pdf

      # 5. Commit the PDF to an orphan branch named 'pdflatex'
      - name: Commit PDF to orphan branch
        run: |
          # Configure git user details
          git config --global user.name "GitHub Action"
          git config --global user.email "action@github.com"
          # Create an orphan branch named pdflatex (this leaves all files in place)
          git checkout --orphan pdflatex
          # Remove all tracked files from the index (this doesn't remove untracked files)
          git rm -rf .
          # Since paper.pdf is already present in the working directory,
          # we don't need to copy it.
          git add paper.pdf
          git commit -m "Built PDF"
      # 6. Push the orphan branch to GitHub
      - name: Push orphan branch
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: pdflatex
          force: true
```
