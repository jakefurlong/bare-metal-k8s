# bare-metal-k8s
A bare metal Kubernetes cluster implemented at home

<img src="images/jake-with-k8s.jpg" alt="Jake with K8s Cluster" width="540" height="700">


## Background

I moved into a new house and have to set up my homelab. Rather than standup my usual Proxmox cluster, I decided to go a different direction and build out a bare metal Kubernetes (K8s) cluster instead. My goal is to pass the CKA and CKAD certification exams and learn more about K8s so I figure this is a great place to start.

My original goal was to build a micro cluster using RaspberryPis but they became so hard to find and so dang expensive that I was better off just buying cheap refurbished PCs when they were on sale. I picked up these computers for about $80 a piece. I'm going to call them servers because they are acting in a server capacity but I understand that they aren't high-end server quality.

## Approach

I'll probably work on this on the weekends and inbetween running dunegons for the new World of Warcraft expansion, The War Within. Work, work, work... (dun, dun, duuuuuuuun) queue's up! Additionally, I am only going to use ChatGPT4 and the [Kubernetes Documentation.](https://kubernetes.io/docs/home/)

## Hardware Specs

HP EliteDesk 800 G2 SFF
- CPU: Intel i5 6500
- RAM: 8GB
- Storage: 256 SSD

HP ProDesk 600 G2 SFF
- CPU: Intel i5 6500 
- RAM: 8GB
- Storage: 256 GB SSD

HP EliteDesk 800 G2 Desktop Mini
- CPU: Intel i5 6500
- RAM: 16 GB DDR4
- Storage: 512 GB SSD

## Getting Started

There are a few things I learned from the K8s documentation so far:
- You have to use Linux.
- For a cluster you're managing yourself, the officially supported tool for deploying K8s is kubeadm.
- The K8s documentation doesn't assume you're a try-hard setting up bare metal on budget PCs

That's where ChatGPT comes in...

My question: What are the steps for setting up kubernetes on bare metal?

Response (I removed all of the details after each section for brevity in this README):

Setting up Kubernetes on bare metal involves several steps. Here’s a high-level overview to guide you through the process:

1. Prepare Your Environment
2. Install Required Software
3. Set Up the Control Plane
4. Set Up Networking
5. Join Worker Nodes
6. Verify the Cluster
7. Install Additional Components
8. Configure Storage and Resources
9. Secure Your Cluster
10. Monitor and Maintain

This is a broad outline; each step might have specific commands and configurations depending on your exact setup and requirements.

Alrighty!

Now that we have a rouch guideline, let's step through this process and see how far we get.

## Prepare Environment

Let's check the K8s documentation to check the hardware requirements. Well... I didn't find anything concrete but after reading a ton of K8s community forum posts and asking CHatGpt, the answer is "it depends." Given what I'm trying to do, I should have *plenty* of resources. And it doesn't seem to matter what architecture the CPU is or anything that low level. It may matter when it comes to isntalling software, but it doesn't matter for just using K8s to begin with. I'm going to call this one complete.

Next, we need to isntall Linux on each node. In this environment, each PC is a  K8s "node" so I'll stop calling them servers from here on out. So the question is, what flavor of Linux? I prefer something that has a lot of community support behind it so without ever looking at the Internet, I'm thinking I go with Ubuntu. I feel I'll be much more likely to find people with similar issues when I run into problems and need guidance. Most people are probably using 20.04 or 22.04 but 24.04 is out so that's what I'm gonna roll with. OS decision, done!

Last step, I need a static network. I'll set this up after I install Ubuntu. This will likely require that I do some network magic with my router and I just got a new router so nothing has been customized. I'll include all of those details. Network should be pretty basic.

Next up, do the thing!

**Install Ubuntu Server 24.04 and configure a static network.**

