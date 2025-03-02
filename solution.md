# FFmpeg Installation & Fix Guide

## **Step 1: Download FFmpeg**  
1. Open the [official FFmpeg website](https://ffmpeg.org/download.html).  
2. Choose **Windows**, **Linux**, or **macOS**, based on your OS.  
3. Download the precompiled version.

![image](https://github.com/user-attachments/assets/bf34bcf6-2bd6-4b95-977a-22d876152795)


---

## **Step 2: Extract the Files**  
1. Once the `ffmpeg.zip` file is downloaded, extract it.
![image](https://github.com/user-attachments/assets/d749cd3b-6fc2-4a2e-8529-cf72a8a2e0be)
3. You will see a folder named `bin` containing FFmpeg executable files (`ffmpeg.exe`).
![image](https://github.com/user-attachments/assets/73efb660-b333-401b-adfc-56c87bc6b73b) 
5. Move to `bin` folder and copy path of this folder
![image](https://github.com/user-attachments/assets/a8e95cef-9c02-4f28-b7c9-c5ea7363e47d)

---

## **Step 3: Add FFmpeg to the System PATH**  
### **For Windows:**  
1. Open the Search Bar by pressing Win + S, then type "Edit the system environment variables".
![image](https://github.com/user-attachments/assets/7ca611b9-5ded-4040-9b98-ab39375dfd60)
2. Click on the result that appears.
3. In the System Properties window, click on Environment Variables.
![image](https://github.com/user-attachments/assets/25193003-2a0a-4404-8fb1-dc092af639f7)
4. Under System Variables, find Path and click Edit.
![image](https://github.com/user-attachments/assets/8dfd3e79-a985-49f4-be69-41bf581d799c)
![image](https://github.com/user-attachments/assets/bf83323e-90c1-49e3-a22a-d75876160084)

5. Click New and add the path of FFmpeg that you copied.
![image](https://github.com/user-attachments/assets/e3b869d6-7f60-40bf-b199-1de32910b734)

6. Click OK to save the changes.  
![image](https://github.com/user-attachments/assets/9049c226-1ea6-4a54-925f-17fae693c47d)

### **For Linux/macOS:**  
Open the **Terminal** and manually add the path to `.bashrc` or `.zshrc`:  
```bash
export PATH=$PATH:/path/to/ffmpeg/bin
```

## Alternative Method:
Use the Full Path Instead of Modifying System PATH.
If you don't want to modify your system's environment variables, you can use the full path to `ffmpeg.exe` directly in your code. You can find `ffmpeg.exe` file in `bin` folder

---

## Step 4: Verify the Installation
After adding the path, check if FFmpeg is working by running:
```bash
ffmpeg -version
```
If the version information appears, FFmpeg is correctly installed!
