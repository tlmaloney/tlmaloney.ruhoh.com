---

title: Setting up the Reuters project
date: '2012-05-31'
description: Connecting to Reuters
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - blackbox
    - reuters
    - jython

layout: post

---

Guide to setting up Reuters Dev Project
---------------------------------------
### Audience

Autonomy Capital staff

### Install maven2

Execute

	sudo apt-get install maven2

### Install Java

Download [Java SE 6 Update 32](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (choose the file named jdk-6u32-linux-x64.bin). Afterwords, a file named jdk-6u32-linux-x64.bin should be in ~/Downloads.

Execute the following (disregarding any prompts for registration)

	cd ~
	chmod +x ~/Downloads/jdk-6u32-linux-x64.bin
	./Downloads/jdk-6u32-linux-x64.bin
	sudo mv jdk1.6.0_32/ /usr/lib/jvm
	sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0_32/bin/java" 1
	sudo update-alternatives --config java

Choose the number corresponding to "/usr/lib/jvm/jdk1.6.0_32/bin/java".

Confirm that you're using the correct JVM:

	java -version
	
This should output:
	
	java version "1.6.0_32"
	Java(TM) SE Runtime Environment (build 1.6.0_32-b05)
	Java HotSpot(TM) 64-Bit Server VM (build 20.7-b02, mixed mode)

### Install Jython

Execute:

	sudo apt-get install jython

### Install RFAj-7.2.0.E3

Download [RFAj](https://aim.autonomycapital.com/@api/deki/files/2172/=rfaj7.2.0.E3.all.zip) (you'll need  your Autonomy login/passowrd) to ~/Downloads.

Unzip *twice*:

	unzip ~/Downloads/rfaj7.2.0.E3.all.zip
	unzip ~/Downloads/setup/rfaj7.2.0.E3.all.zip

Create a directory /opt/rfaj/:

	cd /opt
	sudo mkdir rfaj
	cd rfaj/

Create a symlink:

	sudo ln -s ~/Downloads/setup/rfaj7.2.0.E3.all current

### Install ksh

Execute:

	sudo apt-get install ksh

### Fork and clone
Fork the repository located at https://bitbucket.org/cuddihyd/reut into your own bitbucket account, and then clone the fork onto your machine in ~/hgdev/org.bitbucket/asmith.

### Test the project

Navigate into the root directory of the project

	cd ~/hgdev/org.bitbucket/asmith/reut

Make the RFA jar visible to Maven2:

	make install-rfa-jar

### Import Chicago server

Execute

	cd /opt/rfaj/current/Tools
	./config_editor.ksh

An RFA Configuration Editor window will pop up. Go to File > Import > File. Then navigate to ~/vedev/vereut/reut/etc/rfaj-config and select reut-chicago.xml.


Next, build and launch the Jython shell:

	make jython

Then pull 20 Eurodollar front contract events:

	>>> dump_events()

If you get no errors, we have success.