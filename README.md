# FFmpeg-Subprocess-Fix

## Overview
This document details the solution for the FFmpeg subprocess issue encountered when executing `ffmpeg` using Python's `subprocess` module. The error typically indicates that `ffmpeg` is either not installed or not accessible via the system's PATH.

## Table of Contents
- [Issue Overview](#issue-overview)
- [Root Cause](#root-cause)
- [Solution](#solution)
- [Usage Instructions](#usage-instructions)
- [Code Example](#code-example)
- [Summary](#summary)

## Issue Overview
When attempting to run `ffmpeg` with the `subprocess` module, errors such as the following may appear:

FileNotFoundError: [WinError 2] The system cannot find the file specified

or

OSError: [Errno 2] No such file or directory: 'ffmpeg'


These errors occur because the system cannot locate the `ffmpeg` executable.

## Root Cause
- **Installation Issue**: `ffmpeg` is not installed.
- **PATH Issue**: `ffmpeg` is not added to the system's PATH.
- **Incorrect Command**: The command or its path is not correctly specified in the script.

## Solution
1. **Install `ffmpeg`**:  
   - Download it from the [official FFmpeg website](https://ffmpeg.org/download.html).
   - Follow the installation instructions provided for your operating system.

2. **Update the System PATH**:  
   - **Windows**: Add the path to the `ffmpeg/bin` directory to the environment variable `Path`.
   - **Linux/Mac**: Append the following line to your shell configuration file (e.g., `.bashrc` or `.zshrc`):
     ```bash
     export PATH=$PATH:/path/to/ffmpeg/bin
     ```

3. **Use the Absolute Path in Your Script**:  
   - If you cannot update the PATH, modify your script to use the full path to the `ffmpeg` executable.

## Usage Instructions
- **Verify Installation**: Run `ffmpeg -version` in your terminal or command prompt to confirm `ffmpeg` is installed.
- **Test in Python**:  
  - Use the `shutil.which` method to check if `ffmpeg` is available:
    ```python
    import shutil
    if shutil.which("ffmpeg") is None:
        print("ffmpeg is not installed or not in PATH")
    else:
        print("ffmpeg found, proceeding...")
    ```
- **Modify Your Script**:  
  - Either rely on the system PATH or use the absolute path to call `ffmpeg` via `subprocess`.

## Code Example
```python
import subprocess

# Option 1: Using the system PATH
result = subprocess.run(["ffmpeg", "-version"], capture_output=True, text=True)
if result.returncode == 0:
    print("FFmpeg is working correctly:")
    print(result.stdout)
else:
    print("Error running FFmpeg:")
    print(result.stderr)

# Option 2: Using an absolute path to the ffmpeg executable
ffmpeg_path = "C:\\path\\to\\ffmpeg.exe"
result = subprocess.run([ffmpeg_path, "-version"], capture_output=True, text=True)
if result.returncode == 0:
    print("FFmpeg is working correctly:")
    print(result.stdout)
else:
    print("Error running FFmpeg:")
    print(result.stderr)
```
## Repository structure
``` bash
FFmpeg-Subprocess-Fix/
│── README.md               # Main documentation file
│── solution.ipynb          # Jupyter Notebook containing the solution and test examples
│── solution.md             # Detailed explanation of the solution(Contained pictures)
│── tests/
│   ├── test_ffmpeg.py      # Python test script for validation
│   ├── test_ffmpeg.ipynb   # Jupyter Notebook for testing FFmpeg integration
```
