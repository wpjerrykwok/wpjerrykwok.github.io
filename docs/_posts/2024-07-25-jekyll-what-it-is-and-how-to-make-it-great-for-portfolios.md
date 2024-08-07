---
title: Jekyll... What It Is and How to make it Great for Portfolios
tags: [Portfolio, Jekyll, Beginner Guide]
style: fill
color: primary
description: Learn to create a website using Jekyll on GitHub Pages.
asset_path: /assets/images/blog/2024-07-25/
---
When I started my portfolio project, I wanted a simple yet powerful way to create and manage my content. That's when I discovered Jekyll.

In this post, I will share with you how I use Jekyll to enhance the look and feel of my portfolio.

- [What is Jekyll?](#what-is-jekyll)
- [Set up GitHub Pages with Jekyll](#set-up-github-pages-with-jekyll)
  - [Install Git](#install-git)
  - [Install VS Code (Optional if you have your own code editor)](#install-vs-code-optional-if-you-have-your-own-code-editor)
  - [Install Jekyll](#install-jekyll)
  - [Ready to Set up](#ready-to-set-up)
- [Jekyll Basics](#jekyll-basics)
- [Creating and Organizing Content](#creating-and-organizing-content)
- [Building and Testing Locally](#building-and-testing-locally)
- [Deploying to GitHub Pages](#deploying-to-github-pages)
- [Conclusion and Next Steps](#conclusion-and-next-steps)

![Two cute claymation monsters on a gradient background working together - Image created with Microsoft Designer]({{ page.asset_path }}my_image.jpeg)

## What is Jekyll?

Jekyll is a static site generator that turns plain text into beautiful websites. What made Jekyll even more appealing was its seamless integration with GitHub Pages. This combination offers several benefits:

- Free hosting on GitHub

- Version control for your website

- Easy collaboration with others

- :bulb: Automatic builds and deployments

- :bulb: Ready-to-use themes

---

## Set up GitHub Pages with Jekyll

To set up GitHub Pages with Jekyll, we need to do some preparation first. This preparation would be helpful for testing changes before pushing them live.

---

### Install Git

Follow [Set up Git](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git) to install Git on your computer locally.

---

### Install VS Code (Optional if you have your own code editor)

Follow [Download Visual Studio Code](https://code.visualstudio.com/Download) to install VS Code on your computer.

---

### Install Jekyll

Follow [Installation](https://jekyllrb.com/docs/installation/) to install Ruby, Jekyll and Bundler on your system.

---

### Ready to Set up

From [my previous blog post](./getting-started-to-set-up-github-pages-for-portfolio), we created a repository `analystjoey.github.io` remotely in GitHub and commited an `index.html` as the portfolio first page.

Let's continue!

1. Open **VS Code**.

2. Click **File**, then **Open Folder...** and open a location where you want to store the portfolio site's source file. For example, I put them under `Documents/github`.
   ![folder]({{ page.asset_path }}folder.png)

3. Click **Terminal**, then **New Terminal**. You should have Git Bash open. (If it is not bash, click the **+** to change to Git Bash).
   ![bash]({{ page.asset_path }}bash.png)

4. In Git Bash, initialize a local Git repository

   ```bash
   git init analystjoey.github.io
   ```

5. Change to the repository directory.

   ```bash
   cd analystjoey.github.io
   ```

6. Create a folder called `docs` and change directories to it.

    ```bash
    mkdir docs
    cd docs
    ```

7. Create and checkout a new branch `gh-pages`. This would be the branch to be used later to publish the portfolio.

    ```bash
    git checkout --orphan gh-pages
    ```

8. Create a new Jekyll site. Ensure you have the `.` at the end.

    ```bash
    jekyll new --skip-bundle .
    ```

9. Open and edit the `Gemfile`.
   ![gemfile]({{ page.asset_path }}gemfile.png)

10. Locate the line starting with `gem "jekyll"` (line 10) and the line starting with `# gem "github-pages"` (line 15).
   ![changecode1]({{ page.asset_path }}changecode1.png)

11. Add `#` to comment out line 10.

12. Note the Dependency Version of **github-pages** from [GitHub Pages Dependency Version](https://pages.github.com/versions/).
   ![version]({{ page.asset_path }}version.png)

13. Remove `#` in line 15 and edit this line as below, where `GITHUB-PAGES-VERSION` is 231 in this example.

      ```bash
      gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
      ```

14. The updated file should be like this.
   ![changecode2]({{ page.asset_path }}changecode2.png)

15. Save and close the `Gemfile`.

16. In Git Bash, run:

      ```bash
      bundle install
      ```

17. Open `.gitignore` and add this line `Gemfile.lock`. The file should look like this. Save and close this file.
   ![ignore]({{ page.asset_path }}ignore.png)

Congratulations! :tada: You have just set up Jekyll with your GitHub Pages.

---

## Jekyll Basics

To manage the content in our portfolio effectively, we should first understand Jekyll's file structure. Here's a simple breakdown:

- _posts: to put our blog posts

- _config.yml: Site configuration

- 404.html: the **not found** page; we can customize

- about.markdown: the **about** page; we can customize

- Gemfile: Jekyll configuration

- index.markdown: the **index** page; we can customize

Jekyll has a powerful feature called **front matter**. It's a section at the top of files where you can set variables for your content. For example:

```yaml
---
layout: post
title: "My First Blog Post"
date: 2024-08-01
---
```

We may explore more about customization later. Let's try to create some content.

---

## Creating and Organizing Content

To write content like this blog post, we can rely on using **Markdown**. Markdown is easy to use and therefore we can focus on the words without worrying much about complex formatting. Jekyll automatically converts these to HTML pages.

1. Create a new file in the `_posts` folder with names `2024-08-01-my-first-post.md`.

2. The `2024-08-01` will appear as the blog date when we publish the post.

3. Let's put a simple message in this post. Close and save the file.

   ```markdown
      ---
      layout: post
      title:  "Hello World!"
      ---
      Hello World!
   ```

Now that we have created our first blog post. Let's build and test it!

---

## Building and Testing Locally

Before pushing changes to GitHub, I always tested my site locally to catch and fix any issues before they went live. Here is how to do it.

1. In Git Bash, run

   ```bash
   bundle exec jekyll serve
   ```

2. If the server is running successfully, you should have output similar to this.

   ```bash
   >  Server address: http://127.0.0.1:4000/
   >  Server running... press ctrl-c to stop.
   ```

3. If you do not receive this output, check if some files are missing. For example, a common issue is:

   ```bash
   :37:in `require': cannot load such file -- webrick (LoadError)
   ```

4. You may find how to solve issues by researching. For example, the above webrick issue is [discussed and solved](https://github.com/jekyll/jekyll/issues/8523) by running:

   ```bash
   bundle add webrick
   ```

5. Now run again

   ```bash
   bundle exec jekyll serve
   ```

6. Open a browser and go to `http://127.0.0.1:4000/`. You should see your website now. Enjoy how minimal it is and see if your **Hello World!** post is there.
   ![site]({{ page.asset_path }}site.png)

You may create more posts with the same `YYYY-MM-DD-post-name.md` naming convention and have some more fun with Markdown.

---

## Deploying to GitHub Pages

Deploying the Jekyll site to GitHub Pages was surprisingly easy. 

1. Commit the changes

   ```bash
   git add .
   git commit -m 'Initial GitHub pages site with Jekyll'
   ```

2. Add your remote repository; USER is the username and REPOSITORY is the name of the repository

   ```bash
   git remote add origin https://github.com/USER/REPOSITORY.git
   ```

   For example,

   ```bash
   git remote add origin https://github.com/analystjoey/analystjoey.github.io.git
   ```

3. Push to the **gh-pages** branch on GitHub

   ```bash
   git push -u origin gh-pages
   ```

4. Ensure the **publishing source** is using the **gh-pages** branch.

   - Go to the analystjoey.github.io repository on GitHub
   - Click **Settings** tab
   - Click **Pages** on the left
   - Under **Build and deployment**, check that the **Branch** is **gh-pages** and **docs**
      ![branch]({{ page.asset_path }}branch.png)

5. Click the **Actions** tab and wait for a success green tick for deployment.

6. Check your live site at analystjoey.github.io.

Congratulations! :tada: GitHub Pages has automatically built and deployed the site. Within minutes, our changes were live!

---

## Conclusion and Next Steps

Setting up a website with Jekyll and GitHub Pages has been a rewarding experience. It's given me a powerful platform to share my thoughts and projects with the world. (and YOU!)

For topic coming I will cover:

- how to customize the portfolio with a theme
- how to customize within a theme
- some markdown tips

If you're interested in trying this yourself, don't worry and try it. Remember, the key to success is patience and persistence. Happy coding!
