---
title: "Hosting a site with Hugo and Aws - Part 1"
date: 2018-06-09T16:00:17+02:00
draft: true
---

I figured what better topic to start off with on operationaldev.com than how the site is built and automatically deployed.

<h2>CMS/Framework</h2>

Previously, I had setup a site using wordpress. And while wordpress is an awesome product, I found it to be overkill and have a lot more options and features than I needed. Especially for a small blog or static website, it just seemed a little bloated (ED: Wordpress is pretty awesome as a genral CMS). When looking for something easy and simple, I stumbled apon <a href="https://hugoio.io/">Hugo</a>. With Hugo there is no need for complex web server configurations (php etc) or database (mysql/mariadb) setups. For a bigger, more complex site, wordpress would probably be a better choice but for a site as simple as this, Hugo is perfect.

<h3>Getting started with Hugo</h3>

There are a few different options for installing (see https://gohugo.io/getting-started/installing/), but on Mac, I recommend homebrew.


To install:
<pre><code>brew install hugo
</code></pre>

To verify that it has installed correctly:
<pre><code>hugo version
</code></pre>

You are now ready to go ahead and create your site.

To create a site:
<pre><code>hugo new site mywebsite
</code></pre>

This will make a folder with a skeleton structure of your website.

Next you will need a theme. To checkout all the themes available, go to https://themes.gohugo.io/

Once you have a theme that you like, add your theme using the following:
<pre><code>git init

git submodule add https://github.com/halogenica/beautifulhugo.git themes/beautifulhugo;

echo 'theme = "beautifulhugo"' >> config.toml
</code></pre>

And you're ready to go. To checkout your new site run:
<pre><code>hugo server</code></pre>

and browse to the location it gives you (should be http://localhost:1313)

My editor of choice thus far has been vim (ED: vim for life) which I've used to build all of the current content.

In the next post, we'll look at how we deploy our site. 
