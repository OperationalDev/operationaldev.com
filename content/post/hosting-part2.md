---
title: "Hosting a site with Hugo and Aws - Part 2"
date: 2018-06-10T16:00:17+02:00
draft: true
---

In part 1, we built a simple static site which is now ready to be hosted. While there are many good options for this, I've opted to go with AWS as I have a bunch of stuff hosted there already. However if you'd rather not use AWS, I strongly recommend <a href="https://www.netlify.com/">netlify</a>

For hosting, we will be using the following AWS components:

- S3 Bucket for storing our content
- S3 Bucket for logs
- Cloudfront as our CDN
- Route53 for DNS hosting
- ACM for a SSL certificate
- Terraform for automating the setup of the above components

Why Terraform? Well who wants to go and fiddle around in the AWS console with settings to try and setup their static site. And in 6 months time, you'll have no clue how you did it. Trust me. Also lots of people use terraform with AWS so we can mostly just copy/pasta.

Update: I've written a terraform module that does builds the full static site with DNS and SSL <a href="https://github.com/OperationalDev/aws_static_website">aws_static_website</a>. I will unpack this module in a future post.

<h3>prerequisites</h3>

- AWS account
- domain name
- route 53 setup as the authorative name server for this

<h3>Deployment Plan</h3>

To get started, create a deployment folder with a terraform file (.tf) that has the following:
<pre><code>
provider "aws" {
  region     = "us-east-1"
}

module "operationaldev_website" {
  source = "git::https://github.com/OperationalDev/aws_static_website.git"

  website_name = "operationaldev"
  website_url = "operationaldev.com"
  website_root_domain = "operationaldev.com"
}
</code></pre>

You should now be ready to build your hosting platform.

<h3>Deployment Build</h3>
To run your terraform code, you will need to do the following:

Export your AWS access and secret key:
<pre><code>
export hahahaha
</code></pre>

To initialize your terraform project run:
<pre><code>
terraform init

terraform get
</code></pre>
This will download the necessary providers as well as download the module.
Note that there are other ways to do this, this is just one way.

To check to see if everything is in order:
<pre><code>
terraform plan
</code></pre>

<pre><code>
terraform apply -auto-approve
</code></pre>

And magic, your site hosting will begin building. The plan should take about
2 minutes to run, depending on how AWS ACM feels that day.

Note: It does take about 15 minutes for cloudfront to be deployed to all regions, so be patient.

Now all you need to do is upload your code to your website which I will cover in the next post.
