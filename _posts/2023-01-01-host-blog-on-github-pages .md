---
title: Host blog on GitHub Pages with custom domain
date: 2023-01-01 18:10
categories: [Blog, GitHub, AWS]
tags: [blog, github, git, aws]
render_with_liquid: false
pin: true
---

This tutorial will help you to create a new blog/website and host it on GitHub (via GitHub Pages using Jekyll) for free with a custom domain (optional).
- <https://pages.github.com/>
- Architecture diagram captures end-state of our Blog &amp; tools/shared services used:
  ### Blog Architecture diagram
  ![image](/assets/img/posts/2023-01-01-host-blog-on-github-pages/blog-architecture.drawio.png)
  _Blog Architecture diagram_

##  Create new website

Create a new repo &amp; use your username 'abhishek-pradhan.github.io' in Repository name &amp; for rest of the options, use the default settings (abhishek-pradhan is my github username)

### Create a new repository
![image](/assets/img/posts/2023-01-01-host-blog-on-github-pages/create-new-repo.png)
_Create a new repository_

  ```bash
  git clone https://github.com/abhishek-pradhan/abhishek-pradhan.github.io.git
  ```

  Create a new page 'index.html'
  ```bash
  cd abhishek-pradhan.github.io
  echo "Hello World" > index.html
  ```

  Commit index.html to remote
  ```bash
	git add .
	git status
	git commit -m "initial commit"
  ```

  If it's a new repo
  ```bash
	git remote add origin https://github.com/abhishek-pradhan/abhishek-pradhan.github.io.git
  ```
  OR an existing git repo
  ```bash  
  git remote set-url origin https://github.com/abhishek-pradhan/abhishek-pradhan.github.io.git
  ```

  Check remote origin, just to be sure
  ```bash
	git remote -v
  ```

  Ensure your user name &amp; email id is set
  ```bash
	git config --list
	
	git config --global user.name "FirstName LastName"
	
	git config --global user.email "myusername@provider.com"
  ```
  Commit to remote
  ```bash
	git push
  ```
  and you will get a prompt if this is the first time you are using GitHub. Either login or generate classic token from Settings -> Developer token and then copy &amp; paste the token in dialog
 
That's all folks! Open browser &amp; goto your new site! <https://abhishek-pradhan.github.io>

##  Configure custom domain

### Set Custom domain
- Github -> Settings -> Pages: blog.abhishekpradhan.com

### AWS Route 53
- Go inside existing Public Hosted zone: abhishekpradhan.com
- Add CNAME record with: blog.abhishekpradhan.com points to  abhishek-pradhan.github.io

> Note: It takes time for github to verify DNS check &amp; there after some time to Enforce https
{: .prompt-info }

### Github site settings
![image](/assets/img/posts/2023-01-01-host-blog-on-github-pages/github-site-settings.png)
_Github site settings_

### AWS Route53 site settings
![image](/assets/img/posts/2023-01-01-host-blog-on-github-pages/aws-route53-site-settings.png)
_AWS Route53 site settings_

> Note: I have removed my other site records from here, for clarity
{: .prompt-info }

##  Setup Jekyll
- Transform your plain text into static websites and blogs: <https://jekyllrb.com/>
- I will be using AWS Cloud9 IDE, since it has developer tools installed out of the box, like git, ruby, gems: https://aws.amazon.com/cloud9/ 

> Warning: AWS Cloud9 IDE will incur you charges, ensure to delete Cloud9 once you are done with it.
{: .prompt-warning }

### Pre-requisites when using AWS Cloud 9 IDE
```bash
gem update --system
```

### Quick-start Instructions
```bash
gem install bundler jekyll  
jekyll new my-awesome-site
cd my-awesome-site
bundle exec jekyll serve
```

Now browse to <http://127.0.0.1:4000/>

> Note: Since we are on Linux terminal, I did curl http://127.0.0.1:4000/
However, since I don't see the UI, I tried setting up Jekyll on my Windows 10 machine - this approach didn't work - check below update.
{: .prompt-info }

> Update: AWS Cloud9 IDE supports app preview on localhost, with only condition of:
You aren't required to run your application using HTTP over port 8080, 8081, or 8082 with the IP address of 127.0.0.1, localhost, or 0.0.0.0. However, if you don't do so, you can't preview your running application from within the IDE: from <https://docs.aws.amazon.com/cloud9/latest/user-guide/app-preview.html> 

```bash
jekyll serve --port 8080 --host 127.0.0.1
```
{: .prompt-tip }

## Configure Jekyll theme - Chirpy:
- <https://chirpy.cotes.page/posts/getting-started/>

```bash
git clone https://github.com/cotes2020/jekyll-theme-chirpy.git
```

Installing Dependencies by navigating to root directory of blog:
```bash
bundle
```
```bash
jekyll serve --port 8080 --host 127.0.0.1
```
That's all folks! Now go build!

> Tip: Check out Usage section for configuration: <https://chirpy.cotes.page/posts/getting-started/#usage>
{: .prompt-tip }

- For now, all I did was update _config.yml file with my details

- After that, ensure to goto Settings -> Pages -> Build and Deployment -> Source = GitHub Actions &amp; clicked Configure button which created jekyll.yml file having CI/CD details. Commit this file to the repo. This file is used by GitHub Actions to build &amp; deploy the site.

- Once deploy is successful, navigate to blog.abhishekpradhan.com
### GitHub Pages Actions
![image](/assets/img/posts/2023-01-01-host-blog-on-github-pages/github-pages-actions.png)
_GitHub Pages Actions_

## Write a new blog post
- Create a new file named YYYY-MM-DD-blog-title.md and put it in the _posts of the root directory. For instance: 2020-01-26-containerize-aspnetcore-web-app.md
- Add Jekyll Front Matter at the top of the blog page, to configure per blog post basis settings:

  ```md
  ---
  title: Host blog on GitHub Pages with custom domain
  date: 2023-01-01 18:10
  categories: [Blog, GitHub, AWS]
  tags: [blog, github, git, aws]
  render_with_liquid: false
  ---
  
  Now add blog's actual markdown like this
  ## Hello world
  This tutorial will help you to create a new blog/website and host it on GitHub...
  ```
  {: file='2020-01-26-containerize-aspnetcore-web-app.md'}

- Commit &amp; push changes to GitHub. Since we have configured GitHub Actions, any changes made to site are automatically deployed!
- Visit your site on internet

## Add Disqus comments to blog post
- Ensure you first register your newly created blog on <https://disqus.com> and you note down shortname
- Open _config.yml and set up disqus comments at 2 places:

  ```yaml
  comments:
    active: 'disqus'      # The global switch for posts comments. Keep it empty means disabled
    disqus:
      shortname: 'blog-myshortname-fromdisqus-com'   # fill with the Disqus shortname
  defaults:
    - scope:
        path: ''          # An empty string here means all files in the project
        type: posts
      values:
        comments: true    # Enable comments in posts.
  ```
  {: file='_config.yml'}

## Add Google Analytics
- Please Refer <https://chirpy.cotes.page/posts/enable-google-pv/>

## Setup CDN for images
Let's use AWS S3 bucket as our CDN to serve images for this blog. We will be using S3 bucket to store images, instead of storing them as part of site at assets/img/ folder
- First create a AWS S3 bucket (for example: cdn.blog.yourblogname.com) and enable public access &amp; S3 bucket policy with public access
- Ensure you follow the same paths &amp; create similar folder structure in S3
- Upload your images to appropriate folders
- Enable image cdn in _config.yml file &amp; more importantly read the notice of paths starting with '/':
  ```yaml
  # The CDN endpoint for images.
  # Notice that once it is assigned, the CDN url
  # will be added to all image (site avatar &amp; posts' images) paths starting with '/'
  #
  # e.g. 'https://cdn.com'
  # img_cdn: 'https://cdn.com'
  img_cdn: 'https://s3.ap-south-1.amazonaws.com/cdn.blog.yourblogname.com'
  ```
  {: file='_config.yml'}

