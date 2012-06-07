---

title: Installing BDB XML in Ubuntu
date: '2012-06-01'
description: Installing BDB XML in Ubuntu
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - bdb
    - xml
    - rlwrap

layout: post

---

Installing BDB XML in Ubuntu
---------------------------

### Prerequisites

Have installed Xubuntu 12.04 in a Virtual Machine along the lines of [this guide](http://dpollini.ruhoh.com/installation/guided-installation-of-a-xubuntu-virtual-machine-for-developers/) (up until the Install Mercurial and Meld step).

### Introduction

Read [this](http://zeth.net/post/350/) for a little introduction to BDB XML.

### Download and install

Download BDB XML from [Oracle's web site](http://www.oracle.com/technetwork/products/berkeleydb/downloads/index.html). You'll need to create a login (free) if you don't have one already.

Decompress the downloaded file:

	cd ~/Downloads
	tar xvfz dbxml-2.5.16.tar.gz

Before building the source, modify one of the files:

	~/Downloads/dbxml-2.5.16/xqilla/include/xqilla/framework/XPath2MemoryManager.hpp

In the file, after line 26 add a line with

	#include <cstddef>

After which you can now build:

	cd dbxml-2.5.16/
	sh buildall.sh

More build options can be [found here](http://docs.oracle.com/cd/E17276_01/html/ref_xml/xml_unix/intro.html).

Once compilation is complete, the dbxml binary is located in

	~/Downloads/dbxml-2.5.16/install/bin/

I suggest either moving the binary, or making a symlink:

	ln -s ~/Downloads/dbxml-2.5.16/install/bin/dbxml ~/bin/dbxml

### Rlwrap

I recommend using rlwrap to add input history and command completion.

Install rlwrap

	sudo apt-get install rlwrap

Create a script in ~/bin called "start_dbxml.sh" to start dbxml:

	#!/usr/bin/env bash
	
	mkdir -p $HOME/.rlwrap/dbxml/"`date +%Y%m%d`"
	
	rlwrap -rcl $HOME/.rlwrap/dbxml/`date +%Y%m%d`/`date +%H%M%S-%N`.log dbxml