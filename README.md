# Django REST API

##### Technologies Used:
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)
![Vagrant](https://img.shields.io/badge/vagrant-%231563FF.svg?style=for-the-badge&logo=vagrant&logoColor=white)<img src="https://img.shields.io/badge/virtualbox-%23183A61.svg?&style=for-the-badge&logo=virtualbox&logoColor=white" />
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

### 12 Step Plan:
1. Setting up dev environment
2. Setting up project folders/structure
3. Create dev server
4. Create Django App
5. Setup the database
6. Setup Django Admin
7. APIView
8. Viewsets
9. Create Profiles API
10. Create login API
11. Create profile feed API
12. Deploy API to server on AWS

#### Docker VS. Vagrant

Both use virtualization technolgoy to isolate app from machine, but do it in different ways.

**What is Docker?**
- [x] Open source containerization tool
- [x] Run app in light-weight image

Creates a Dockerfile that contains all the steps required to build the image. An image is a lightweight version of Linux OS. Once we have the image, we can run on our local machine or deploy it to a server.

Limitations of Docker:

- [x] Because Dockers is designed to run in PRODUCTION, it has a steeper learning curve compared to Vagrant.
- [x] Limited versions for Windows Home

**What is Vagrant?**
- [x] Manage virtual development environments
- [x] No "out-of-the-box" virtualization technology

Vagrant uses a Hypervisor (i.e. Virtualbox) to create a Vagrantfile. Vagrant uses the Hypervisor to create and configure the server on our machine.

Benefits of Vagrant:

- [x] Streamlined but complete version of Linux OS
- [x] Because Vagrant is not designed to run in production, it has an easier learning curve compared to Docker
- [x] Wider range of support
- [x] Runs on any machine that supports Virtualbox

Basically, we would use Docker if we are looking to streamline our workflow and ALL developers use supported OS. Vagrant is preferred if we're just getting started or if we need support on a wider range of OS.

### Installing Virtualbox, Vagrant, and ModHeader for MAC OS
1. Install GIT for your terminal. Check with git --version
2. [Install VirtualBox for your OS/Chipset](https://www.virtualbox.org/wiki/Downloads) Check by opening up VirtualBox with Spotlight. We should see the app open up.
3. [Install Vagrant](https://developer.hashicorp.com/vagrant/downloads) Test in terminal with vagrant --version
4. Install VSCode (or your preferred IDE).
5. Install ModHeader Chrome Extension (used to test API as we build it) [ModHeader Chrome Extension](https://chrome.google.com/webstore/detail/modheader-modify-http-hea/idgpnmonknjnojddfkpgkljpfnnfcklj) Check the ModHeader Chrome Browser extension after installing. Pin it.

### Setting Up Project
1. Add template .gitignore files for standard Python Vagrant project [.gitignore template](https://www.toptal.com/developers/gitignore/api/python,vagrant)
2. Create a LICENSE file in root directory of project
```console
touch LICENSE
```
Paste the contents of [MIT LICENSE TEMPLATE](https://choosealicense.com/licenses/mit/) and change year and name appropriately.

### Creating a Development Server
1. Create a template Vagrantfile

In our profiles-rest-api folder directory inside terminal:
```console
vagrant init ubuntu/bionic64
```

2. Configure Vagrant box
Inside Vagrantfile, create a customized Vagrantfile by replacing ALL of the template Vagrantfile settings.
```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
 # The most common configuration options are documented and commented below.
 # For a complete reference, please see the online documentation at
 # https://docs.vagrantup.com.

 # Every Vagrant development environment requires a box. You can search for
 # boxes at https://vagrantcloud.com/search.
 config.vm.box = "ubuntu/bionic64"
 config.vm.box_version = "~> 20200304.0.0"

 config.vm.network "forwarded_port", guest: 8000, host: 8000

 config.vm.provision "shell", inline: <<-SHELL
   systemctl disable apt-daily.service
   systemctl disable apt-daily.timer
 
   sudo apt-get update
   sudo apt-get install -y python3-venv zip

   touch /home/vagrant/.bash_aliases
   if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
     echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
     echo "alias python='python3'" >> /home/vagrant/.bash_aliases
   fi
 SHELL
end
```

### Running and Connecting to Our Dev Server

