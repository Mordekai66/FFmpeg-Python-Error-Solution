# FFmpeg-Subprocess-Fix

This document details the solution for the FFmpeg subprocess issue occurs when executing `ffmpeg` using Python's `subprocess` library. The error typically indicates that `ffmpeg` is either not installed or not accessible on the system's PATH.

## Table of Contents
- [Issue Overview](#issue-overview)
- [Main Cause](#main-cause)
- [Solution](#solution)
- [Usage Instructions](#usage-instructions)
- [Code Example](#code-example)
- [Repository structure](#repository-structure)

## Issue Overview
When trying to run `ffmpeg` with the `subprocess` library, There are errors such as the following may appear:

`FileNotFoundError: [WinError 2] The system cannot find the file specified`

or

`OSError: [Errno 2] No such file or directory: 'ffmpeg'`


These errors occur because the system cannot find and locate the `ffmpeg` EXE file.

## Main Cause
- **Installation Issue**: `ffmpeg` is not installed.
- **PATH Issue**: `ffmpeg` is not added to the system's PATH environment.
- **Incorrect Command**: The command or it's path is not correctly specified in the script.

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

3. **Use the Absolute Path in Your code**:  
   - If you cannot update the PATH, you can use the full path to the `ffmpeg` EXE file.

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
- **Modify Your Code**:  
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
