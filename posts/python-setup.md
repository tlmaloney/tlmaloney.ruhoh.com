---

title: Python packages installation for Developers
date: '2012-06-04'
description: Installing packages for Python, Xubuntu 12.04
categories: sysadmin
tags: 
    - ubuntu
    - precise
    - python
    - pip
    - virtualenv
    - virtualenvwrapper
    - numpy
    - scipy
    - pandas
    - matplotlib

layout: post

---
### Prerequisites

Have installed Xubuntu 12.04 in a Virtual Machine along the lines of [this guide](http://dpollini.ruhoh.com/installation/guided-installation-of-a-xubuntu-virtual-machine-for-developers/) (up until the Install Mercurial and Meld step).

### Pip

According to [Dru Pollini](http://dpollini.ruhoh.com/installation/guided-installation-of-a-xubuntu-virtual-machine-for-developers/): "Pip is an installer tailored specifically to Python packages. It will install the most recent version of the package, which is important for satisfying certain dependencies." Read more [here](http://pypi.python.org/pypi/pip).

	sudo apt-get install python-pip python-dev build-essential

### Virtualenv

Read about virtualenv [here](http://pypi.python.org/pypi/virtualenv) and about virtualenvwrapper [here](http://www.doughellmann.com/projects/virtualenvwrapper/).

	sudo pip install --upgrade pip virtualenv virtualenvwrapper

For how to setup and work in a virtual environment, refer to the mint example [here](http://dpollini.ruhoh.com/installation/guided-installation-of-a-xubuntu-virtual-machine-for-developers/).

### Numerical Packages (numpy, scipy, pandas, matplotlib)

Install dependencies

	sudo apt-get install libamd2.2.0 libblas3gf libc6 libgcc1 libgfortran3 liblapack3gf libumfpack5.4.0 libstdc++6 gfortran python-all-dev libatlas-base-dev libfreetype6-dev libpng12-dev

It is recommended to install these in a virtual environment

	sudo pip install numpy scipy pandas matplotlib