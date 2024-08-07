---
title: Getting Started to Set Up GitHub Pages for Portfolio
tags: [Portfolio, GitHub Pages, Beginner Guide]
style: fill
color: secondary
description: what I did to create a free portfolio website using GitHub Pages
asset_path: /assets/images/blog/2024-07-01/
---
Welcome to my first step in creating the online portfolio using GitHub Pages. In this post, I will share with you how to set up a professional website to showcase our work and skills.

- [What is GitHub Pages and Why Use It?](#what-is-github-pages-and-why-use-it)
- [Create a GitHub account](#create-a-github-account)
- [Make a new repository](#make-a-new-repository)
- [Add Content and Make Your First Commit](#add-content-and-make-your-first-commit)
- [Conclusion and Next Steps](#conclusion-and-next-steps)

By the end, we would have the basic structure for a portfolio website.

Let's begin.

![A cute claymation monster on a gradient background who is a bit confused but have a thinking face - Image created with Microsoft Designer]({{ page.asset_path }}my_image.jpeg)

## What is GitHub Pages and Why Use It?

GitHub Pages is a free service that turns GitHub repositories into websites. It's an excellent tool for creating a portfolio website because:

- :dancers: It's **Free**: There is no need to pay for hosting.
  
- :star: It's **Simple**: If you can use GitHub, you can use GitHub Pages.
  
- :hushed: It Has **Version Control**: easily track changes to the website.
  
- :eyes: It Works Well with **Jekyll**: create a dynamic-looking site without managing a database.
  
- :flags: It **Connects to My Code**: easily link to my other GitHub projects.

By using GitHub Pages, I created a portfolio that effectively presents my work to potential employers or clients.

---

## Create a GitHub account

Before using **GitHub Pages**, we need to have a **GitHub** account. If you already have one, go ahead to [make a new repository](#make-a-new-repository). If not, follow these steps to create an account:

1. Go to [GitHub](https://github.com) website.

2. Click **Sign Up** and enter your email address to continue.
   ![sign up button]({{ page.asset_path }}sign-up.png)

3. Create a strong password for your account.
   ![email & password]({{ page.asset_path }}email.png)

4. Choose a username for your GitHub account. :bulb: **Tips:** This will be visible to others and will be part of your GitHub Pages URL, so **choose wisely**.

5. Follow the prompts to verify your account.

6. For **Choose a plan**, the free plan is good enough for creating a portfolio with GitHub Pages. Select **Free Plan**.

7. Follow the prompts to customize or skip it for now.

8. Check your email inbox for a verification message from GitHub. Follow the prompts to **verify your account**.

9. For added security, set up **two-factor authentication**.

Now that you have a GitHub account, you're ready to create a repository for your portfolio website. In the next section, I'll cover how to do this and start setting up GitHub Pages.

---

## Make a new repository

With a GitHub account, the next step is to create a new repository for the portfolio website. This repository will hold all the files for the site.

1. Log in to [GitHub](https://github.com).

2. Click the **+** icon in the top right corner of the page. Select **New repository** from the dropdown menu to create a new repository.
   ![plus]({{ page.asset_path }}plus.png)

3. Name the repository in this format: **username.github.io**, where username is the GitHub username. :bulb: For example, if your username is **analystjoey**, your repository should be named **analystjoey.github.io**.
   ![reponame]({{ page.asset_path }}reponame.png)

4. Choose **Public**.
   ![public]({{ page.asset_path }}public.png)

5. Check **Add a README file** to initialize the repository with a README.md file.
   ![readme]({{ page.asset_path }}readme.png)

6. Click the **Create repository** button at the bottom of the page.
   ![create]({{ page.asset_path }}create.png)

7. You'll be taken to your new repository's page. You should see a README.md file listed.
   ![landing]({{ page.asset_path }}landing.png)

8. :bulb: **Enable GitHub Pages**
    - Go to the **Settings** tab of your repository.
    ![settings]({{ page.asset_path }}settings.png)
    - Click on **Pages** on the left.
    ![pages]({{ page.asset_path }}pages.png)
    - Under **Build and deployment**, click **None** and select **main**.
    ![build]({{ page.asset_path }}build.png)
    - Click **Save**.
    ![save]({{ page.asset_path }}save.png)

Congratulations! :tada: You've now created a repository for your GitHub Pages site. GitHub will provide you with a URL where your site will be published (:bulb: usually https://username.github.io).

In the next section, we'll cover how to add content to the site and make your first commit.

---

## Add Content and Make Your First Commit

Now that you have created your repository, it's time to add some content to your site and make your first commit. We'll start with a simple `index.html` file.

1. Go to your repository page on GitHub.
   ![landing]({{ page.asset_path }}landing.png)

2. Click the **+** button, then select **Create new file**.
   ![newfile]({{ page.asset_path }}newfile.png)

3. In the **Name your file...** field at the top, type `index.html`. This will be the homepage of your site.
   ![nameyrfile]({{ page.asset_path }}nameyrfile.png)

4. In the **edit** area, add some basic HTML.
   - Here's a simple example:
  
      ```html
      <!DOCTYPE html>
      <html lang="en">
      <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>My Portfolio</title>
      </head>
      <body>
         <h1>Welcome to My Portfolio</h1>
         <p>This is my GitHub Pages website. More content coming soon!</p>
      </body>
      </html>
      ```

   ![code]({{ page.asset_path }}code.png)

5. :bulb: Commit the new file:
    - Click "Commit changes...".
        ![commit1]({{ page.asset_path }}commit1.png)
    - A commit message like **Create index.html** is automatically filled in.
    - Leave the "Commit directly to the main branch" option selected.
    - Click "Commit changes".
        ![commit2]({{ page.asset_path }}commit2.png)

6. After committing, you'll be taken back to your repository's main page. An `index.html` file is listed in your repository files.
   ![commit3]({{ page.asset_path }}commit3.png)

7. Click **Actions** tab. Wait for the **workflow** to be success (a green tick).
   ![workflow]({{ page.asset_path }}workflow.png)

8. Open a new tab in your browser and go to https://username.github.io (replace 'username' with your GitHub username). You should see your new webpage live!

:sunglasses: Congratulations! :tada: You've just created and published your first page on GitHub Pages. This is the foundation of your portfolio website.

---

## Conclusion and Next Steps

You've successfully set up your basic portfolio website using GitHub Pages. Let's recap what we've accomplished:

1. Created a GitHub account

2. Set up a new repository specifically for GitHub Pages

3. Added a simple index.html file as the foundation of your site

4. Made your first commit and published your site

Your portfolio is now live and accessible to anyone on the internet. While this is a great start, a basic HTML site might feel a bit limited for a full portfolio :bear:.

:raising_hand: This is where **Jekyll** comes in. Jekyll is a static site generator that works seamlessly with GitHub Pages, allowing you to create more complex and feature-rich websites without the need for server-side programming or databases.

In my next blog post, I will explore:

- What Jekyll is and why it's beneficial for portfolio sites

- How to set up Jekyll with your existing GitHub Pages repository

- Creating and organizing content using Jekyll's powerful features

- Customizing your site's appearance with Jekyll themes

Stay tuned to take your GitHub Pages portfolio to the next level with Jekyll!
