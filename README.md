# DVWA Vagrant Deployment on Kali Linux

This project sets up the Damn Vulnerable Web Application (DVWA) (https://github.com/digininja/DVWA) on a Kali Linux virtual machine using Vagrant and VirtualBox.

The purpose is to provide a quick, repeatable lab environment for web application security testing.

## Purpose

Perform testing on DVWA without needing to download any ISO files. Using vagrant allows us to easily spin up and down VMs in Virtualbox on demand without downloading ISOs.
The Vagrantfile will pull a Kali Linux box, and the post-install script will configure DVWA.

---

## Getting Started

### Prerequisites

Make sure you have the following installed:

[VirtualBox](https://www.virtualbox.org/)
[Vagrant](https://developer.hashicorp.com/vagrant/install)
[Git Bash for Windows](https://gitforwindows.org/) (if you do not have git installed, also if on Windows)

---

### Clone the Repo and run vagrant

git clone https://github.com/Gleezy96/dvwa-vagrant-deploy.git
cd dvwa-vagrant-deploy
vagrant up

---

### Done

After the shell script configures the system, visit http://127.0.0.1/dvwa/setup.php
Then click "Create / Reset Database" to begin.

Login is vagrant:vagrant

Vagrant boot should appear similar to this:
![image](https://github.com/user-attachments/assets/810263f6-983e-4c3d-9944-69b1bfdbe0fc)

