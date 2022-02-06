---
layout: post
title: Better Command Lines
date: 2022-02-05 23:00:00
categories: [Windows, Dev Tools]
---

One of the first things I do when I set up a new computer is customize my terminal. As a developer, you use your terminal constantly and it is insanely helpful to have one that is visually pleasing and displays various information about git branch status, time, battery life, etcetera.

Here's an example of my current terminal

![Terminal](/assets/img/terminal.png)

## How to customize your terminal

First off, you're going to want to download "Windows Terminal Preview," which is available through the "Microsoft Store" app which ships with the Windows 10/11 operating system.

![Microsoft Store](/assets/img/storepage.png)

## Downloading a new font

Once you've started the download, it's now time to choose a font for your new terminal. You will want to check out [NerdFonts](https://www.nerdfonts.com/font-downloads) since most of their fonts will have all the necessary symbols to work with the next step of the process.

You're going to need to install the font which is done simply by going into your Windows font settings. After Windows recognizes your new font, set that font in Windows Terminal Preview.

I'd highly recommend taking a minute to look around Windows Terminal Preview if you haven't used it before. There are lots of useful and interesting features baked into the app that are handy to know about.

You'll need to set the default command line tool to Powershell within the app settings. Once you have Powershell open, run these commands.

```
Install-Module oh-my-posh -Scope CurrentUser -AllowPrerelease
Get-PoshThemes
```

Choose a theme from [here](https://ohmyposh.dev/docs/themes).

Open your Powershell config using `notepad $PROFILE` and add these lines to it, replacing "YourTheme" with the name of the theme you've chosen.

```
Import-Module oh-my-posh
Set-PoshPrompt -Theme YourTheme
```
