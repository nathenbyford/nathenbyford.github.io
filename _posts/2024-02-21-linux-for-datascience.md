---
layout: post
title: "Setting up Linux for Statistics and Data Science"
date: 2023-02-21
tags: [linux, Data Science, R]
author: Nathen Byford
excerpt: "Quick start for how to setup Linux for data science and statistical work."
---

# Linux Setup for Data Science and Statistics

This guide will walk you through how to setup a workstation for statistics and data science on linux. The key parts of the guide will go over how to install the most recent version of R and some of the dependecies needed to install commonly used packages like the tidyverse. This guide will also continue to be updated as I think of things that need to be added for future reference.

## Operating system

The first step to setup a workstation for statistics and data science in linux is to decide which operating sustem to choose. You might be thinking, but I thought linux was the operatigns system? If you don't know, there are over 600 different linux "distributions" being actively maintained. These distributions are all linux operating systems, but each is a bit different in how they install programs and operate. Some are based off of others and some are alone , to learn more about linux distributions check out the wikipedia article [here](https://en.wikipedia.org/wiki/List_of_Linux_distributions).

With many linux distributions available, deciding what operating system to choose is a big task. Essentially there are 3 linux distributions that all others are based on, there are of course exceptions. These 3 that most are based on are Debian, Red Hat, and Arch. It all boils down to what package manager the distributions uses and the updating structure of the system. 

I've opted to use Ubuntu or Ubuntu based distributions for my systems. I have also used fedora before with no issues, both are great choices with large user bases and great communities. Ubuntu has a LTS(long term support) release cycles that is updated once a year in April and is supported for 4 years. This means that the system will continue to get updates for 4 years before you need to upgade to the new version.

## Post install

There are many guides that show the process of installing linux on your pc, so I will not go over that on here. But once you have Ubuntu LTS installed, the following steps can be used to setup various software that we use for statistics or data science.

### R and tidyverse install

Since Ubuntu doesn't have the most up to date version of R, we need to add the key to the package manager so we can get the newest versions directly from cran.  

To do this copy and past the following code into the terminal as a user with sudo access.
```bash
wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/r-project.gpg
```

Next we add the R sources to the sources that apt will look through by running the following in the terminal.

```bash
echo "deb [signed-by=/usr/share/keyrings/r-project.gpg] https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" | sudo tee -a /etc/apt/sources.list.d/r-project.list
```

Now that we have added cran to apt as a source we want to update the source list in apt using apt update.

```bash
sudo apt update
```

Then finally installing R we can simply run the following in the terminal to install the latest version of R.

```bash
sudo apt install r-base
```

Now the most recent version of R should be install this can be checked by running `R` in your terminal or by typing `R --version` in the terminal.

### Tidyverse and dependencies

Before installing the tidyverse package in R we need to install some dependencies on the operating system. To do this run the following in the terminal.

```bash
sudo apt install r-base-dev libcurl4-openssl-dev libssl-dev libxml2-dev libfontconfig1-dev libharfbuzz-dev libfribidi-dev libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev libcairo2-dev
```

After the dependencies are installed using R and `install.packages()` we can install the tidyverse and any other packages you need.

### Bayesian mcmc samplers

To install `JAGS` for use with `rjags` the following command can be ran.

```bash
sudo apt-get update && sudo apt-get install jags
```


### Additional R packages

Aside from the tidyverse here are some other helpful R packages that I like to use.

- `quarto`: For report and presentation creation.
- `gt`: For making high quality tables for reports.
- `gtsummary`: Extending `gt` with more table options.
- `readxl`: For reading in Microsoft Excel data.
- `latex2exp`: To label plots from `ggplot2` with TeX formating, especialy helpful for math symbols in axes.
- `rjags` or `rstan`: Bayesian modeling in R.

## Other lanuages

- Python 3 is already installed on linux, I don't use it much, but when I need it I Google how to install what I need on Ubuntu. `pip` can be installed as follows.
```bash
# install pip
sudo apt install python3-pip
```

- Julia can be installed in the software center if you search for it.

- Latex can be installed through texlive, to do this copy the following in to bash. There are many LaTeX editors available on linux through the software center. I prefer to just use visual studio code with the LaTeX workshop extension as my TeX editor.
```bash
# install texlive full
sudo apt install texlive-full
```

## Software and IDEs

In terms of installing applications for coding like Rstudio, these can be installed from their website. Just find the download for Ubuntu 22 and then open the installer and it will install through the software center.  Many other popular apps that are a part of everyday life can also be installed similarly, some are even in the software center and only a search away. Some examples are: 

- Visual Studio Code
- TeXstudio/TeXworks
- Zotero
- Zoom
- Slack
- Todoist

## Cloud Storage

Some cloud storage solutions offer native linux clients like dropbox, but for most of us using Microsoft's OneDrive, Google Drive or Box are not so fortunate. There is an open source program that can be used to sync the system with cloud storage solutions.

The software I use for this is called `rclone`, it can be installed using the terminal command

```bash
sudo apt install rclone -y
```

Then run 

```bash
rcone config
```

And follow the directions to setup a new remote for your cloud storage.

Once the remote is setup you can create an empty directory to link the remote to. I like to set it up to be a directory in the root directory to keep it easy to find. Then the following code with your remote name and directory name will setup the remote at the new directory location.

```bash
rclone --vfs-cache-mode writes mount [remote_name]: ~/[directory] &
```