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
4. Install VSCode or Atom.
5. Install ModHeader Chrome Extension (used to test API as we build it) [ModHeader Chrome Extension](https://chrome.google.com/webstore/detail/modheader-modify-http-hea/idgpnmonknjnojddfkpgkljpfnnfcklj) Check the ModHeader Chrome Browser extension after installing. Pin it.

### Setting Up Project
1. Add template .gitignore files for standard Python Vagrant project [.gitignore template](https://www.toptal.com/developers/gitignore/api/python,vagrant)