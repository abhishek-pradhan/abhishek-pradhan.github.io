---
title: Host blog on GitHub Pages with custom domain
date: 2022-01-01 18:10
categories: [Blog, GitHub, AWS]
tags: [blog, github, git, aws]
render_with_liquid: false
pin: true
---

This tutorial will help you to host a blog on GitHub (via GitHub Pages using Jekyll theme chirpy) for free with a custom domain

##  Create new site

Create a new repository in GitHub & give username as abhishek-pradhan.github.io (abhishek-pradhan is my github username)

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

  Ensure your user name & email id is set
  ```bash
	git config --list
	
	git config --global user.name "FirstName LastName"
	
	git config --global user.email "myusername@provider.com"
  ```
  Commit to remote
  ```bash
	git push
  ```
  and you will get a prompt if this is the first time you are using GitHub. Either login or generate classic token from Settings -> Developer token and then copy & paste the token in dialog
 
That's all folks! Open browser & goto your new site! <https://abhishek-pradhan.github.io>

##  Configure custom domain

### Set Custom domain
- Github -> Settings -> Pages: blog.abhishekpradhan.com

### AWS Route 53
- Go inside existing Public Hosted zone: abhishekpradhan.com
- Add CNAME record with: blog.abhishekpradhan.com points to  abhishek-pradhan.github.io

> Note: It takes time for github to verify DNS check & there after some time to Enforce https
{: .prompt-info }

### Github site settings
![image](/assets/img/posts/2022-01-01-host-blog-on-github-pages/github-site-settings.png)
_Github site settings_

### AWS Route53 site settings
![image](/assets/img/posts/2022-01-01-host-blog-on-github-pages/aws-route53-site-settings.png)
_AWS Route53 site settings_

> Note: I have removed my other site records from here, for clarity
{: .prompt-info }

##  Setup Jekyll for its themes
- <https://jekyllrb.com/>

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
However, since I don't see the UI, I will be setting up Jekyll on my Windows 10 machine (see below).
{: .prompt-info }

> Update: Cloud9 supports app preview on localhost, with only condition of:
You aren't required to run your application using HTTP over port 8080, 8081, or 8082 with the IP address of 127.0.0.1, localhost, or 0.0.0.0. However, if you don't do so, you can't preview your running application from within the IDE.

from <https://docs.aws.amazon.com/cloud9/latest/user-guide/app-preview.html> 

```bash
jekyll serve --port 8080 --host 127.0.0.1
```
{: .prompt-tip }

## Setup Jekyll for its themes - Chirpy:
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

- After that, ensure to goto Settings -> Pages -> Build and Deployment -> Source = GitHub Actions & clicked Configure button which created jekyll.yml file having CI/CD details. Commit this file to the repo. This file is used by GitHub Actions to build & deploy the site.

- Once deploy is successful, navigate to blog.abhishekpradhan.com
### GitHub Pages Actions
![image](/assets/img/posts/2022-01-01-host-blog-on-github-pages/github-pages-actions.png)
_GitHub Pages Actions_

## Writing new blog post
- Create a new file named YYYY-MM-DD-TITLE.md and put it in the _posts of the root directory. For instance: 2020-01-26-containerize-aspnetcore-web-app.md

