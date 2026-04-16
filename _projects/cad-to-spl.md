---
name: Drylab CAD2SPL
tools: [GPT-5, AutoCAD, Python]
image: /assets/images/angel.jpg
description: Inputs CAD files and determines what changes you should make to them to flatten the SPL. This is the first project I've made that was completely agentic-driven. 
---

# The Movies Project

Inputs CAD files and determines what changes you should make to them to flatten the SPL. This is the first project I've made that was completely agentic-driven. 

## Usage

The user enters his CAD files and gets (1) the predicted SPL chart out (2) areas in the CAD files to modify to flatten the SPL.

## GPT-5 API 

On the backend, uses Python to query GPT-5-nano to generate the x,y data that will be used to construct the SPL plot. 

<p class="text-center">
{% include elements/button.html link="https://github.com/yousinix/portfolYOU" text="Learn More" %}
</p>