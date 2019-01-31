# Visual Studio Code Remote File System Setup for CS1550
---
This is a guide to set up an sftp extension to allow files hosted on Pitt's thoth
server to be edited using Microsoft's Visual Studio Code.

**NOTE: This is a guide made by a student and not Professor Khattab nor a cs1550 TA,
therefore this guide may be prone to errors.**

This guide assumes that you are connected to pitt's network via some VPN. For
instructions on how to do so, look here:
https://www.technology.pitt.edu/help-desk/how-to-documents/pitt-vpn-pulse-secure-connect-pulse-secure-client

1. Create some local folder on your machine to open in VSCode to work in. Then open VScode.
2. Open the created folder, then click the extensions tab on the left-hand side of the window
3. Search for remote-fs from liximomo. Here is a link to the vscode page if there is any difficulty finding it: https://marketplace.visualstudio.com/items?itemName=liximomo.remotefs
4. Click 'install'. Once the extension is finished downloading, click 'reload'.
5. Open the command pallet (Crtl+Shift+P), type 'Open Settings', and click on
   'Preferences: Open Settings(JSON)'
6. settings.json will open. Add the following to your settings:
    
```json
  "remotefs.remote": {
    "pitt-thoth":{
      "scheme": "sftp",
      "host": "thoth.cs.pitt.edu",
      "port": 22,
      "username": "[YOUR USERNAME]",
      //"password": "[YOUR PASSWORD]", optional
      "interactiveAuth": true, //may switch this out with password
      "rootPath": "/afs/pitt.edu/home/[first character of your username]/[second char of your username]/YOURUSERNAME", 
    }
  },
```

**note: The path depends on your username [I believe]. Since my username is bim7, my path ends with /b/i/bim7**
 
**note: You may wish to substitute the given path for '/u/OSLab/[YOURUSERNAME]/linux-2.6.23.1' if working on project1**

7. You should now be able to run the 'Remote FS: Add Folder to Workspace' command
   from the command pallet (agin, Crtl+Shift+P). A selection of 'pitt-thoth' shows
   up. Click it.
8. If you have interactiveAuth set to true, you may be prompted to enter your
   password. Otherwise, you will be able to edit and navigate your remote repository
   as if it were local!

You may consider installing git for windows. You can set the accompanying bash
terminal to your integrated terminal in VScode, so you can ssh directly into thoth
from VScode and execute command-line commands!