---
title: "How we build and host Operational Dev"
date: 2018-05-13T16:00:17+02:00
draft: false
---

I figured the best topic to start with would be how we automatically build and deploy the Operationaldev.com blog. As the blog is all automation, surely we don't build it using handraulics.

To build our blog, we use the following components:

- vim - editing content (Ed: If you saw bob use vim, you would recommend he does not use vim)
- Hugo - framework for building websites
- AWS - our hosting provider
- Terraform - automate the build of all the components used to host this site
- Travis CI - CI tool we use to automatically push changes
- Github - source control

Over the next four posts we will cover in detail how we use each of these tools to bring you this blog.
