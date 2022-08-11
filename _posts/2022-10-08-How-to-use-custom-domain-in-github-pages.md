---
layout: post
title: How to use your coustom domain in github pages using Cloud flare
author: riwaj
categories: [tech]
tags: [github, gh pages, cloudflare, jekyll]
image: assets/images/cloudflare-github-pages.png
# description: "."
featured: true
hidden: false
---

Github pages is an awesome tool to host your static website. In this post we are going to see how we can deploy our static html site into our github pages. This article assumes that the site is alredy pushed into you public gihub repositary.

We will be using following tools:-
- Github
- Cloudflare

Make sure the repo where you are pushing your code is a public. If not **go to your repositary > click settings > scroll buttom to danger section > click the change repository visiblity buttom > click make public.**

{% include image.html img="assets/images/github.png" alt="github repo image" %}

Now that our repo is ready lets follow the following steps to publish the site into github pages
- **Step 1** Go to repo **settings**.
- **Step 2** Go to **Pages**.
- **Step 3** In the Branch section click the dropdown and select the branch that you want to deploy.
{% include image.html img="assets/images/github_page_section" alt="github repo image" %}
- **Step 4** Click **Save**

A link 




