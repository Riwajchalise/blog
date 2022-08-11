---
layout: post
title: How to use your custom domain in Github pages
author: riwaj
categories: [tech]
tags: [github, gh pages, Cloudflare, jekyll]
image: assets/images/cloudflare-github-pages.png
# description: "."
featured: false
hidden: false
---
Github page is an awesome tool to host your static website. In this post, we will see how we can deploy our static HTML site into our Github pages. This article assumes that the site is already pushed into your public GitHub repository.

We will be using the following tools:-
- Github
- Cloudflare

Make sure the repo where you are pushing your code is public. If not **go to your repository > click settings > scroll down to danger section > click the change repository visiblity button > click make public.**

![github repo image]({{ site.baseurl }}/assets/images/github.png)


Now that our repo is ready let's follow the following steps to publish the site on Github pages
- **Step 1** Go to repo **settings**.
- **Step 2** Go to **Pages**.
- **Step 3** In the Branch section click the dropdown and select the branch that you want to deploy.
- **Step 4** Click **Save**.
- **Step 5** Enter your domain in the custom domain field and click **save**.

![github pages]({{ site.baseurl }}/assets/images/github_page_section.png)

Now We have to Point our domain into Github's IP address and we will be using cloud flare as our DNS

- Go to https://www.cloudflare.com/ and signup.
- On the website section click **add site** button.
- Write the name of your domain (For example test.com) 
- Click the free (0$) option. 
- You will see two NS records remove the already existing records and change the name server (ns1 and ns2) in your domain name provider's console.
- Now click the **Add record** button.
- Select **A** record type, **@** in Name section, **192.30.252.153** as ipv4 address of github. 
- Select **A** record type, **@** in Name section, **192.30.252.154** as ipv4 address of github. 

![Dns record]({{ site.baseurl }}/assets/images/dns-record.png)

Please note that the site will not be published until your domain has a green checkmark. Github pages can be used to deploy static site, jekyll site and other static contents.

![Web pages]({{ site.baseurl }}/assets/images/final-site.png)
