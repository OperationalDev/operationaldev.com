---
title: "Hosting Operational Dev.com - Part 1"
date: 2018-05-18T09:00:17+02:00
tags: ["hosting","hugo","hugoio"]
draft: false
---

Right before we setup any hosting, we actually need something to host right? Previously I had used wordpress, but it's a bit complex and has way more functionality than I need. Enter [Hugo](https://gohugo.io/). Hugo is a open source framework for generating websites. It's really easy to use and it makes the automation part of building and deploying a blog really easy. 

There are a few different options for installing (see <https://gohugo.io/getting-started/installing/>), but on Mac, I recommend homebrew.


To install Hugo:
```bash
brew install hugo
```

To verify that it has installed correctly:
```bash
hugo version
```

Pretty easy, you are now ready to go ahead and start creating your site.

To create a site:
```bash
mdkir blog
cd blog
hugo new site mywebsite
```

This will make a folder with a skeleton structure of your website.

Next you will need a theme. To checkout all the themes available, go to <https://themes.gohugo.io/>

Once you have found a theme you like, add your theme to your site using the following:
```bash
git init

git submodule add <git url> themes/<theme name>;

echo 'theme = "<theme>"' >>  config.toml
```

For example, for Operational Dev we used Beautiful Hugo:

```bash
git init

git submodule add https://github.com/halogenica/beautifulhugo.git themes/beautifulhugo;

echo 'theme = "beautifulhugo"' >> config.toml
```

And that is it. You're now ready to go. To checkout your new site run:
```bash
hugo server
```

And now browse to the location it gives you (should be <http://localhost:1313>)

To generate some content you can use the built the Hugo command line:
```bash
hugo new post/mypost.md
```

You can now edit mypost.md with the text editor of your choice.


In the next post, we'll look at how we deploy our site. 
