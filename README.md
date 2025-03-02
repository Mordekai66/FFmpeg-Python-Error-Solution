# FFmpeg-Python-Error-Solution

This document details the solution for the FFmpeg subprocess issue that occurs when executing `ffmpeg` using Python's `subprocess` library. The error typically indicates that `ffmpeg` is either not installed or not accessible on the system's PATH.

## Table of Contents
- [Issue Overview](#issue-overview)
- [Main Cause](#possible-cause)
- [Solution](#solution)
- [Installation and Configuration](#installation-and-configuration)
- [Repository structure](#repository-structure)

## Issue Overview
When trying to run `ffmpeg` with the `subprocess` library, There are errors such as the following may appear:

`FileNotFoundError: [WinError 2] The system cannot find the file specified`

or

`OSError: [Errno 2] No such file or directory: 'ffmpeg'`


These errors occur because the system failed to find and locate the `ffmpeg` EXE file.

## Possible Cause
- **Installation Issue**: `ffmpeg` is not installed.
- **PATH Issue**: `ffmpeg` is not added to the system's PATH environment.
- **Incorrect Command**: The command or it's path is not correctly specified in the script.

## Solution
1. **Install `ffmpeg`**:  
   - Download it from the [official FFmpeg website](https://ffmpeg.org/download.html).
   - Follow the installation instructions provided for your operating system.

2. **Update the System PATH(Recommended)**:  
   - **Windows**: Add the path to the `ffmpeg/bin` directory to the environment variable `Path`.
   - **Linux/Mac**: Append the following line to your shell configuration file (e.g., `.bashrc` or `.zshrc`):
     ```bash
     export PATH=$PATH:/path/to/ffmpeg/bin
     ```

3. **Use the Absolute Path in Your code**:  
   - If you cannot update the PATH, you can use the full path to the `ffmpeg` EXE file.

## Installation And Configuration
For a complete step-by-step guide with images on installation, adding FFmpeg to PATH, and testing with Python, check **[solution.md](solution.md)** now! 🚀

## Repository structure
``` bash
FFmpeg-Python-Error-Solution/
│── README.md               # Main documentation file
│── solution.ipynb          # Jupyter Notebook containing the solution and test examples
│── solution.md             # Detailed explanation of the solution(Contained pictures)
│── tests/
│   ├── test_ffmpeg.py      # Python test script for validation
│   ├── test_ffmpeg.ipynb   # Jupyter Notebook for testing FFmpeg integration
```
