---

title: BDB XML container and query tutorial
date: '2012-06-01'
description: Create a BDB XML database file from yahoo-example.xml
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - bdb
    - xml
    - index

layout: post

---

Create a BDB XML database
----------------

### Prerequisites

Have installed Xubuntu 12.04 in a Virtual Machine along the lines of [this guide](http://dpollini.ruhoh.com/installation/guided-installation-of-a-xubuntu-virtual-machine-for-developers/) (up until the Install Mercurial and Meld step).

First create a folder where your database files will live. Execute

	mkdir -p ~/dbxmldev

And nagivate into that directory:

	cd ~/dbxmldev

Start up dbxml. Execute

	dbxml

### Database creation

Create a new database container. At the prompt, execute

	dbxml> createContainer example.dbxml

Add an XML document:

	dbxml> putDocument example /path/to/example.xml f

Add an index corresponding to the deal level:

	dbxml> addIndex "" dealLevel node-element-equality-double

Now we can query our database, by for instance, finding all deal levels above a certain threshold. Let's find all deal levels above 620:

	dbxml> query 'collection("example.dbxml")/quoteEvents/quoteEvent[dealLevel > 620]'
	dbxml> print
