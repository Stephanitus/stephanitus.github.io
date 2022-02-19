---
layout: post
title: Quick and Easy Ghidra Setup
date: 2022-02-19 17:00:00
categories: [Reverse Engineering, Dev Tools]
---

## TLDR

Run [this](https://github.com/stephanitus/mre-toolchain-setup/blob/main/ghidraSetup.ps1) powershell script to have a nicely configured Ghidra installation, accessible by entering `ghidraRun` into any command line.

## What is Ghidra?

Ghidra is a tool created by the NSA that allows threat hunters to deconstruct executable files and determine the malicious capabilities of these files. The installation is relatively simple, as well as getting started with the tool.

![Ghidra Logo](/assets/img/ghidra_logo.png)

## Quick Installation

I've put together a Powershell script that downloads the necessary files, unzips them to a preconfigured path, and adds the program's path to the environment variables for easy launching. The installation also switches Ghidra to dark mode using a complementary tool for Ghidra. **I encourage you to review the contents of the script  before you decide to run it.**

> [Github Repo Link](https://github.com/stephanitus/mre-toolchain-setup/blob/main/ghidraSetup.ps1)

## Step-by-Step Installation

1. Download Ghidra from its [Github releases page](https://github.com/NationalSecurityAgency/ghidra/releases/)
2. Download a copy of the [ghidra-dark-theme](https://github.com/zackelia/ghidra-dark) installer
3. Ensure you have a working installation of a JDK (11+) and Python3
4. Unzip Ghidra and dark theme installer
5. Run `python install.py --path {Your_Ghidra_Path}` inside of your ghidra-dark-theme directory 

## Getting Started with Ghidra

Upon launching Ghidra for the first time, you will be met with a workspace selection menu, where you can upload the files you'd like to reverse engineer. Simply enter **CTRL + N** and designate a new project folder, then drag and drop your files into the newly created project folder shown on the ghidra workspace manager.

After this you can double click on the file you'd like to start working on and explore some of the code browser's functionality.

### To be continued...