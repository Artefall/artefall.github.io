---
layout: post
title:  "DevOps tools for everyone! Basic DevOps tools"
date:   2021-05-31 12:00:00 +0200
---

![welcome](images/2021/devops-tools-for-everyone/welcome.jpeg)

In this article I want to explain first priority DevOps tools, every IT-specialist, like programmer, system administrator, tester, DevOps engineer should know.

In my humble opinion, not only DevOps engineers should know CI/CD tools, how to deploy, but EVERY IT-specialist. It’s horrible to hear from programmer or tester: “DevOps? CI/CD tools? No, this is not in the scope of my specialty!”
It’s very sad, because this can be said only by person, who doesn’t want to
improve themself.

In my humble opinion, it’s very oddly, when team member can’t describe the production process of software he works with. The purpose of this article is to improve such ignorance and describe must know DevOps tools for every IT-specialist.

## Linux

Everything works on Linux and Unix-based systems now: Developers, network devices, Applications in containers, etc. Linux provides powerful tool, such as shell — one of the best things linux can offer to you. Linux is light-weight, unlike windows, open-source, modifiable and various. Most part of developer and operation tools are available only on Linux, or much fit, when you use Linux, instead other platforms. Linux is your platform №1, so you should learn Linux at first. It would be unfamiliar first time, but soon you will appreciate Linux with all your heart.
Programming languages

![linux](images/2021/devops-tools-for-everyone/linux.png)

## Programming languages.

Programming languages will help you to automate most part of processes. I want to recommend you languages, that fit most for automation, tools and DevOps theme at all.

- **Python** — one of the most popular programming languages. Python has plain syntax, lots of libraries, what makes it great language for automation tools. There are lots of guides and books, dedicated to python.

![python](images/2021/devops-tools-for-everyone/python.png)

- **Go** — Goland is a popular language, when we talk about famous DevOps tools like Docker, Kubernetes and Terraform. It is quite famous and easy to learn.

![go](images/2021/devops-tools-for-everyone/go.jpeg)

- **Bash** — script language for most Linux distros. It’s powerful and provides you a great set of different commands with which you can flexibly control the system.

![bash](images/2021/devops-tools-for-everyone/bash.png)

- **PowerShell** — PS is a script language for Windows systems. Great replacement for CMD. PowerShell is bit familiar to Bash, so it won’t be a problem to learn them together or switch from first language to second.

![powershell](images/2021/devops-tools-for-everyone/powershell.jpeg)

## CI/CD systems

By CI/CD systems I mean systems, which helps you to automate testing, build and deploy, by describing pipelines with configuration or script languages such as YAML or groovy. Among a bunch of CI/CD systems, I want to highlight Jenkins and GitHub actions. Jenkins provides you infrastructure to create your own automation server, when GitHub actions works with GitHub repositories and executes all workflows on GitHub servers. As for me, CI/CD systems are one of most useful positions in this list.

![Jenkins](images/2021/devops-tools-for-everyone/jenkins.png)

![Github actions](images/2021/devops-tools-for-everyone/actions.png)

## Git

Git represents version control system or VCS. VCS let you efficiently work with files, that changes regular and this changes must be recorded. There are lots of VCSs, but de facto git is a standard for IT-world. Mercurial and Subversion VCS…have died. VCS saves you from confusion in code versions, conflicts, etc.

![git](images/2021/devops-tools-for-everyone/git.png)

## App Deployment

Tests have passed successfully? App have successfully built? Great! Now you need to deploy your app. Let’s consider useful for deploying and technologies:

## Docker

Docker is an OS-level virtualization technology, that provides the ability to use mini-virtual machines, called “containers” in terms of docker. Such virtual machines have many advantages, such as application isolation and ease of software delivery. But that’s not all advantages. Docker is just a step for something more grandiose, when we talk about app deployment (check below).

![docker](images/2021/devops-tools-for-everyone/docker.png)

## Kubernetes

Kubernetes is a system for container orchestration. Container orchestration allow deploying and managing pool of containers, configure network access, balancing using brand-new Kubernetes abstractions as Pod, services, ingress etc. Kubernetes based on containers. Yep, you can use something except docker, but other container technologies is not such popular as docker. That is where containers show their best: fast start, build, termination, isolation promote to the rapid deployment and operation of the application

![kubernetes](images/2021/devops-tools-for-everyone/kubernetes.png)

## Clouds

Cloud technologies are getting more and more involved in IT-world because of scalability, variety of services, pricing policy, outdated format of local capacities etc.

Imagine clouds as a set of services, that provides digital resources, computing power, data. The cloud provides an unlimited number of digital capacities that a user can rent for money. If earlier developers had to work with local capacities, now everything is moving to the clouds. All the dirty work of connecting the Internet, security, purchasing and installing hardware is undertaken by the cloud provider.

Сlouds are quite a lucrative business, so there is fierce competition in the market between several cloud providers such as Microsoft Azure, Amazon Web Services, Google Cloud Platform. Basically, they differ in prices and implementation of digital services. Knowledge of at least one cloud provider can make a numerous boost for you, as for engineer.

![clouds](images/2021/devops-tools-for-everyone/clouds.png)

In my opinion, basic knowledge of this technologies will make you better as a an IT-specialist and give you basic DevOps foundation.


{% include farewell.md conclusion="We have found out most popular devops tools for developer" %}