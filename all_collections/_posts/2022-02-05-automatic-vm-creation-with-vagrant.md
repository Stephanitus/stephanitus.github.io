---
layout: post
title: Automatic VM Creation with Vagrant
date: 2022-02-05 20:00:00
categories: [Vagrant, Dev Tools]
---

## What is Vagrant?

> *Vagrant is a tool for building and managing virtual machine environments in a single workflow. - [Vagrant](https://www.vagrantup.com/intro)*

Nearly every developer has to set up various virtual machines in order to test out and develop programs in different environments without paying for cloud VMs. It is also no surprise that this process can be painful on its own. The process of creating virtual machines changes from host to host which creates the need for a tool like Vagrant.

## Why use Vagrant?

I personally recommend getting familiar with Vagrant and adding it to your arsenal. It makes VM creation so easy and painless and why wouldn't anyone want that? There's a large amount of options you can customize to make it suit any need that might arise.

## Making your first Vagrantfile

A Vagrantfile allows you to share setup configurations so that your peers can obtain an identical environment. It also allows you to keep track of and change certain configuration options for future VM cloning.

---

After installing Vagrant and Virtualbox, navigate to a new directory in powershell in order to store your Vagrantfile in

```
mkdir UbuntuSetup; cd UbuntuSetup
vagrant init hashicorp/bionic64
```

You can choose any box you'd like from the cloud box catalogue. Boxes will have different operating systems and preinstalled software.

After this directory is setup, download, create, and start the VM using this command:

```
vagrant up
```

Once this command finishes running, you will be able to `ssh` into the VM using:

```
vagrant ssh
```

If you're all done with a certain VM, deleting it is as simple as using:

```
vagrant destroy
```

You just need to remember to delete the box file that Vagrant used to setup the VM

```
// View downloaded boxes with
vagrant box list

// Delete any box with
vagrant box remove hashicorp/bionic64
```
