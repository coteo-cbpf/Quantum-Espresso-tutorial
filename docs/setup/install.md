---
title: Working environment setup
sidebar_label: Installation
keywords: ["Quantum ESPRESSO installation", "Installing Quantum Espresso", "PWTK"]
---

# Working environment setup

## Google Colab

Google Colab is a free cloud-based Jupyter notebook environment that allows you to write and execute Python code directly in your browser. Think of it as a remote machine (on the cloud) with everything pre-setup for you to run python code. There, we are going to prepare jupyter notebooks that run python code to prepare, launch, and post-process Quantum ESPRESSO calculations.  Thus, using Google Colab, it is not required local installation or computational resources.

Access Google Colab here: [colab.research.google.com](colab.research.google.com)
Sign in with your personal Google account.

## Quantum ESPRESSO installation

Google Colab does not contain Quantum ESPRESSO by default, so we need to install it.

Perhaps the easiest way to install Quantum Espresso is from the package manager
of respective Linux distribution. This is the recommended option.

First make sure your system is up-to-date.

```bash
sudo apt update && sudo apt upgrade
```

Install Quantum ESPRESSO from APT repository:
```bash
sudo apt install --no-install-recommends \
    libfftw3-dev \
    quantum-espresso
```

## Clone the tutorial repository

The quantum espresso input files, jupyter notebooks (containing python code for
visualizations), and other source files related to this tutorial can be found on
GitHub: [coteo-cbpf/Quantum-Espresso-tutorial](https://github.dev/coteo-cbpf/Quantum-Espresso-tutorial/).


You may clone the repository to your local machine by typing in the terminal:

```bash
git clone https://github.com/coteo-cbpf/Quantum-Espresso-tutorial.git
```

Or, if you do not have git installed, download zipped copy of the repository
[here](https://github.com/coteo-cbpf/Quantum-Espresso-tutorial/archive/refs/heads/main.zip).

## Installing PWTK
We will install a very hand scripting package PWscf Toolkit (PWTK). First we
need to install following dependencies:

```bash
sudo apt install tcl tcllib
```

Download the file from - http://pwtk.ijs.si/download/pwtk-2.0.tar.gz

```bash
wget "http://pwtk.ijs.si/download/pwtk-2.0.tar.gz"
```

Above command will download and save the file to your current directory. Next we
need to just un-tar (no need to compile):

```bash
tar -zxvf pwtk-2.0.tar.gz
```

Add the path (modify below as appropriate) to `.bashrc`:

```bash
echo 'export PATH="/root/pwtk-2.0:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

