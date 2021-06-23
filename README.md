# The NO Edge Project
The Project Helps you to remove build-in Edge Browser from Windows and replacing another Browser instead of Edge

# Installation
### 1. Remove Microsof Edge
Before Doing anything you need to uninstall Microsoft Edge form your System.

1. Goto Start and Search for ``cmd.exe`` and Run Command Prompt as Adminstrator
2. In Command Prompt Window type ``cd %PROGRAMFILES(X86)%\Microsoft\Edge\Application\<Version>*\Installer``
  Note: Replace <Version> of the Edge version, Example your Edge version is 91.0.864.37 then type 91 in the <version> field
3. Now use ``setup --uninstall --force-uninstall --system-level`` to uninstall Edge
  
 The Microsoft Edge will uninstall automatically
  
 Although, Edge will keep some files to keep alive Windows, we just gonna delete some files from them to stop Edge from doing Our Operation.
 
### 2. Removing Edge Leftover Files from Windows Folder
Now Don't close the Command Prompt, cuz We need it.

1. Type ``cd %windir%\SystemApps``

There's you will found 2 folder ``Microsoft.MicrosoftEdge_8wekyb3d8bbwe`` and ``Microsoft.MicrosoftEdgeDevToolsClient_8wekyb3d8bbwe``. Now we will take Adminstrator Permission of these 2 folders So that we can remove it.

2. Use ``takeown /f Microsoft.MicrosoftEdge_8wekyb3d8bbwe /a /r`` to change owner to Adminstrator
3. Now Use ``icacls Microsoft.MicrosoftEdge_8wekyb3d8bbwe /grant Everyone:f /t`` to give remove permission to all child files and folders
4. ``rd /s /f Microsoft.MicrosoftEdge_8wekyb3d8bbwe`` to remove the folder completly
  
  Use the same method to the second folder to remove it.

### 3. Changing Edge Opening links

Edge uses ``microsoft-edge:`` to open links into edge So we need to change the value of ``microsoft-edge:`` value under the registry.

1. Open Registry Editor (Press Win+R into Keyboard and then type regedit and hit enter)
2. Goto the hive ``Computer\HKEY_CLASSES_ROOT\microsoft-edge`` and create a New Key Named ``Shell`` (If any key already exist with the name then Delete it)
3. Under Shell Again Create a new key name it ``MSEDGE``
4. Create a new key name ``Command`` under ``MSEDGE``
5. Into ``Command`` you will find a key name ``(Default)`` which value data is empty, just change the Value Data to ``C:\ProgramData\MSEDGE\edge.exe %1 %2 %3``

  Now all done, All ``microsoft-edge:`` opening links is port to ``C:\ProgramData\MSEDGE\edge.exe``  
  The ``C:\ProgramData\MSEDGE\edge.exe`` is modified version of Edge Browser. It's a Portable Program which open given links into those browser whose are set as default browser.
  
  You can download the modified Web browser from [here](https://github.com/BiltuDas1/no-edge/tree/main/EDGE)
  NOTE: SOME AV MAY DETECT THE FILE AS A VIRUS BUT IT'S FALSE POSITIVE.
