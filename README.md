# Prompt Engineering Course Setup Guide

<br>

![Download from Resources tab](images/course-setup-link.png)

<br>

## Local Setup Is Optional

You don't need to install anything or get an API key to take this course. Watching the lectures is enough to learn how to write effective prompts — you'll see the code, outputs, and explanations on screen either way.

<br>

## Which Path Is Right For You?

- **🎥 Watch only** — Skip this guide entirely. No setup, no API key required.

- **🟣 Watch + run in the Udemy In-Course Labs** (Personal Plan, Udemy Business, or Udemy Business Pro) — The notebooks are included as in-course labs — a browser-based environment that opens during each video. No local install needed.

- **💻 Watch + run locally (this guide)** — 3 videos, about an hour:
  1. Course Setup Guide (this document)
  2. M01A: Setup Test
  3. M01B: OpenAI Setup

  Set aside about an hour, more if you're new to Python or JupyterLab.

<br>

## Change Your Mind Later?

Setup can happen whenever you want. If you start by watching and later decide you want to run the code, come back to this guide at any point — the rest of the course will work from there.

<br>

## What We're Setting Up

Before we start, here's what we'll install:

- **Conda**: Manages Python and course tools
- **JupyterLab**: Where you'll write and run AI code (opens in your web browser)
- **OpenAI Python library**: For API calls
  
<br>

## System Requirements

- 🍎 **macOS**: 12.1+ for Apple Silicon; Intel Macs can use the last available Intel installer
- 🪟 **Windows**: 10 version 1809+ (October 2018 Update) or later
- 🐧 **Linux**: Ubuntu 20.04+, Red Hat/AlmaLinux/Rocky Linux 8+, or equivalent
- **Disk Space**: 2GB free
- **Internet**: Required for downloads

<br>

## Before You Begin

**Important**: Follow these steps in order! Each step depends on the previous one.

<br>

## Step 1: Open Your Terminal

**🍎 macOS - Terminal**:

1. Press `Cmd + Space` to open Spotlight search
2. Type "Terminal"
3. Press Enter

**🪟 Windows - PowerShell**:

1. Press the `Windows key` on your keyboard
2. Type "PowerShell"
3. Press Enter

**🐧 Linux - Terminal**:

1. Press `Ctrl + Alt + T` (most distributions)
2. Or search for "Terminal" in your application menu

<br>

## Step 2: Download Course Materials

Download `prompt-eng.zip` from the Resources tab:

![Download from Resources tab](images/download-resources-pe.png)

<br>

Run the commands below to create a `courses` folder and extract the course files into this folder:

![Terminal commands to unzip files](images/dir_path.png)

<br>

**🍎 macOS & 🐧 Linux**:
```bash
mkdir -p ~/courses

cd ~/courses

unzip ~/Downloads/prompt-eng.zip

cd prompt-eng
```

**🪟 Windows**:
```powershell
cd "$env:USERPROFILE"

mkdir -Force courses

cd courses

Expand-Archive -Path "$env:USERPROFILE\Downloads\prompt-eng.zip" -DestinationPath . -Force

cd prompt-eng
```

<br>

![Directory Path](images/dir_path2.png)

<br>

**Your folder structure should look like this**:

![Folder structure](images/folder-structure.png)

<br>

## Step 3: Install Conda

Conda installs Python and manages all the libraries we'll need for the course.

**Check if Conda is already installed (all platforms)**:
```bash
conda --version
```

✅ **If you see something like `conda 23.1.0`, skip to Step 4!**


### If Conda is NOT Installed:

**🍎 macOS**:

1. Go to the <a href="https://docs.conda.io/en/latest/miniconda.html" target="_blank">Miniconda download page</a>
2. **Apple Silicon (M1/M2/M3/M4)**: Download "Miniconda3 macOS Apple M1 64-bit pkg"
3. **Intel Macs**: The Intel installer is no longer listed on the main page — use this direct installer link: <a href="https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg" target="_blank">Miniconda3-latest-MacOSX-x86_64.pkg</a>
4. Double-click downloaded file, follow installation steps
5. Close Terminal completely and reopen it

**🪟 Windows**:

1. Go to the <a href="https://www.anaconda.com/docs/getting-started/miniconda/install/windows-gui-install" target="_blank">Miniconda Windows installer page</a> and follow the instructions there to download the **Windows 64-Bit Graphical Installer**
2. Run installer, accept defaults until "Advanced Installation Options"
3. **Important**: Check both boxes:
   - ☑️ "Add Miniconda3 to my PATH environment variable" **(We're checking this box so `conda` works directly in PowerShell throughout the course — the installer labels this "not recommended," but we are doing it on purpose for a simpler workflow.)**
   - ☑️ "Register Miniconda3 as my default Python 3.x"
4. Complete installation, close PowerShell completely and reopen it

**🐧 Linux**:

1. Download installer:
```bash
   wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
2. Run installer:
```bash
   bash Miniconda3-latest-Linux-x86_64.sh
```
3. Accept license, choose install location (default is fine)
4. When asked "Do you wish the installer to initialize Miniconda3?", type `yes`
5. Close terminal and reopen it


### ✅ Verify Installation (Everyone)

Before proceeding, close your terminal/PowerShell, reopen it, and run:
```bash
conda --version
```

If you see a version number (e.g., `conda 24.1.2`), you are ready for Step 4!

<br>

## Step 4: Create Your Course Environment

**Navigate to course folder**:

**🍎 macOS & 🐧 Linux**:
```bash
cd ~/courses/prompt-eng
```

**🪟 Windows**:
```powershell
cd "$env:USERPROFILE\courses\prompt-eng"
```

<br>

**Create environment (5-15 minutes depending on internet speed)**:
```bash
conda env create -f environment.yml
```

*This installs Python 3.11 and all AI tools. Go grab a coffee!*

**What's being installed?**

- Python 3.11
- JupyterLab
- OpenAI Python SDK
- python-dotenv (for API keys)
- tiktoken (token counting)
- requests (API calls)

**If this fails**: Try `conda clean --all` then run the command again.

<br>

**Activate your environment**:
```bash
conda activate prompt-eng
```

**Verify it worked**:
```bash
conda env list
```

✅ You should see `prompt-eng` marked with an asterisk (*). Example output (paths vary by OS):
```
base                     /home/user/miniconda3
prompt-eng            *  /home/user/miniconda3/envs/prompt-eng
```

**Your terminal prompt should now show `(prompt-eng)` at the beginning.**

<br>

## Step 5: Launch JupyterLab

**Start JupyterLab (all platforms)**:
```bash
jupyter lab
```

### What Should Happen:

- Your web browser should automatically open
- You should see the JupyterLab interface
- If it doesn't open automatically, look for a link like `http://localhost:8888/lab` in the terminal and **click the link**, or **copy and paste** it into your browser.

<br>

## 📍 What's Next

In the next two videos, you'll:

1. **M01A**: Verify your Python environment and packages
2. **M01B**: Create your OpenAI API key and `.env` file ($5 minimum — more than enough for this course)

<br>

## 🔧 Troubleshooting

### "Command not found" / "not recognized" errors

- Make sure you've activated your environment: `conda activate prompt-eng`
- Close terminal/PowerShell completely and reopen it
- Restart your computer

### Environment creation failed

- Run: `conda clean --all` then try again
- Check disk space (2GB+) and internet connection
- **🪟 Windows**: Disable antivirus temporarily if installation hangs

### Conda activate doesn't work

- Close terminal and reopen it
- Run `conda init zsh` (macOS) or `conda init bash` (Linux) or `conda init powershell` (Windows)
- Close and reopen terminal again, then retry `conda activate prompt-eng`

### JupyterLab won't start

- Ensure environment is active (you should see `(prompt-eng)` in your prompt)
- Check no other Jupyter instances are running
- **Port busy?** Try running: `jupyter lab --port=8889`

### Wrong kernel in JupyterLab

- In JupyterLab: "Kernel" → "Change Kernel" → "Python 3 (ipykernel)"

### Import errors for libraries

- Ensure environment is activated: `conda activate prompt-eng`
- Restart Jupyter: Close browser, `Ctrl + C` in terminal, then `jupyter lab` again

### Platform-Specific Issues

**🪟 Windows**:

- **Permission errors**: Try running PowerShell as Administrator
- **Path issues**: Your files are in `C:\Users\YourName\courses\prompt-eng`

**🐧 Linux**:

- **Permission errors**: Avoid using `sudo` with conda commands
- **Missing packages**: Install build tools: `sudo apt install build-essential` (Ubuntu)

**🍎 macOS**:

- **Xcode issues**: Run `xcode-select --install` if you get compiler errors
- **Chip confusion**: Use Activity Monitor to check if you have Intel or Apple Silicon

### Still stuck?

Don't worry! Programming setup can be tricky. Common fixes:

1. Restart your computer
2. Make sure you followed each step in order
3. Copy the error message and paste it into ChatGPT or Claude—they're great at debugging setup issues

<br>
<br>
