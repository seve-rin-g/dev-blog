---
title: Host Saleor on AWS
tags: [Software Development, e-Commerce, Saleor, GraphQL, Next.js, AWS]
date: 2026-04-04 15:58 -0700
style: fill
layout: post
color: info
description: Deploying Saleor backend and frontend on AWS

---
Continuing on with the first [Saleor project](2026-03-26-saleor-first-pass) I started last week, I'm now going to deploy this on AWS.

I'm starting off with [this tutorial](https://medium.com/@hey.godson/deploying-saleor-api-in-aws-elastic-bean-stalk-5fd4e360b2a6) on Saleor x AWS elastic beanstalk... however this implementation didn't work and since doing the tutorial, I learned EBS is a bit outdated. Moving to just containerizing a Docker image via ECS.    