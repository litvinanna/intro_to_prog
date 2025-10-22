# Install the Programs Required for the Course

Before you start programming in Python, you need to install a few tools that will let you write, run, and share code easily.  
Follow the steps below carefully — everything will work the same on any computer if you do.

---

## Step 1. Install Git

Git is a tool that enables programmatic interaction with GitHub. It allows users to clone repositories and install packages.

- **Windows:**  
  Go to [https://gitforwindows.org](https://gitforwindows.org) and download the installer.  
  During installation, keep all default settings (just click “Next” on each step).

- **MacOS and Linux:**  
  Follow the official instructions here:  
  [https://git-scm.com/install](https://git-scm.com/install)  
  (Click your operating system’s tab on that page.)

---

## Step 2. Install Conda and JupyterLab

- **Conda** is a package manager — it installs Python and other tools into isolated environments so that everything works without conflicts.
- **JupyterLab** is an interactive environment where you’ll write and run Python code in the browser. We’ll use it throughout the course.

1. Go to [https://www.anaconda.com/download/success](https://www.anaconda.com/download/success).  
2. Scroll to the bottom of the page and find the **Miniconda** section (right column).  
3. Download the installer for your operating system.

> [!CAUTION]
> Important note for Windows users: when installing Miniconda, **do not install it into a folder that contains spaces or Cyrillic characters** in its path. Bad examples: `C:\Program Files (x86)\miniconda3`, `C:\Users\Киса\miniconda3`. Good example: `C:\Programs\miniconda3`. 

If your Windows username contains Cyrillic letters, create a new folder (for example, `C:\Programs`) and install Miniconda there.

---

## Step 3. Set Up Your Conda Environment

After installation:

- **Windows:** open *Anaconda Prompt* (search for it in the Start menu).  
- **Mac/Linux:** open the *Terminal* application.

Now, create a new Conda environment for the course (this is like a separate workspace for your Python setup):

```
conda create -n itp python=3.10 pip jupyterlab -y
```

This will:

- Create an environment named *itp*
- Install Python version 3.10, pip (another python packages manager), and JupyterLab (environment for interactive Python coding)

When installation finishes, activate your environment:

```
conda activate itp
```

Now install the package we’ll use for automatic task checking during the course:

```
pip install git+https://github.com/kluwik/checkmagic.git
```

## Step 4. Run JupyterLab

After everything is installed, launch JupyterLab:

```
jupyter lab
```

Your web browser will open JupyterLab. This is where you’ll write and run your Python code during the course.

When you’re done coding, you can close JupyterLab by pressing Ctrl+C in the terminal and confirming with y or just closing the terminal window.
