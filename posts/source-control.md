---

title: Installing Version Control Software
date: '2012-06-04'
description: Installing Mercurial, Git, and Meld for Xubuntu 12.04
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - mercurial
    - git
    - meld

layout: post

---
Installing Version Control Software
----------------------------------

### Prerequisites

Have installed Xubuntu 12.04 in a Virtual Machine along the lines of [this guide](http://dpollini.ruhoh.com/installation/guided-installation-of-a-xubuntu-virtual-machine-for-developers/) (up until the Install Mercurial and Meld step).

We use source control as explained [here](http://praxis.rocketknowledge.com/2011/11/source-control-with-mercurial-and.html).

### Mercurial and Git

We're going to use two version control software packages, Mercurial and Git. Differences between the two can be found [here](http://stackoverflow.com/questions/35837/what-is-the-difference-between-mercurial-and-git).

### Mercurial

Install mercurial:

	sudo apt-get install mercurial

### Git
Install git

	sudo apt-get install git-core

### File Structure

Create a file structure to store your repositories:

	mkdir -p ~/hgdev/com.bitbucket/asmith
	mkdir -p ~/gitdev/com.github/asmith

### Git SSH key

Git requires you to use an SSH key. If you haven't already, link your SSH key to your Dropbox config folder.

	ln -s ~/Dropbox/config/ssh/.ssh ~

### Meld
A good diff viewer is [meld](http://meldmerge.org/)

	sudo apt-get install meld
