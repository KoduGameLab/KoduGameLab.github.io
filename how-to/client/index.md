---
title: Kodu Game Lab
subtitle: Client Notes
layout: page
show_sidebar: false
hero_height: is-small
hide_footer: true
---

## Dev Environment
The Kodu client still builds with Visual Studio 2010 due to the dependency on XNA.  You can get VS 2010 [here](https://download.cnet.com/Microsoft-Visual-Studio-2010-Ultimate/3000-2383_4-75450998.html).
### Prerequisites
[XNA 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=23714) -- Graphics, sound, input, etc.

[WiX 3.10.4](https://github.com/wixtoolset/wix3/releases/tag/wix3104rtm) -- Used for building the release installer.

---
## Branches
Currently we have two active branches, **Main** and **V2**.  The **Main** branch contains the current release build of Kodu.  This branch is primarily used for fixing bugs in the release.  The **V2** branch is a working branch where currently the underlying UI system is being rewritten/replaced.  The **V2** branch builds but is not yet fully functional.

---
<a name="build"></a>
## Building Kodu
In the solution there are several build options.  The three that matter are **Debug**, **Release**, and **Installer**.  The **Debug** and **Release** builds are for building and running Kodu from within VS and work just like you'd expect them to.  The **Installer** build creates the .MSI and .EXE installation packages.  For this, select **Installer** and then build as usual.  At the end of the build process a Windows Explorer instance will be opened to the folder containing the build results.  
### Notes:
- The **Installer** build will automatically increment the version number which touches 3 files (which need to be checked in in their new state).

---
## Deploy a New Desktop Build
Currently, the builds are being hosted on Azure blob storage at  **<https://kodugamelab.blob.core.windows.net/blob/Builds/>**.  

- Rename the .msi build to match the naming of the .exe.  The current naming format is KoduSetup_1.5.53.0.exe and KoduSetup_1.5.53.0.msi.  (version numbers changed, of course)
- Upload the builds to Azure.
- Edit the downloads page **KoduGameLab.github.io\downloads\index.md** markdown file to point to the new builds.
- Commit and push the changes.
- [Update the Version Server.](https://KoduGameLab.github.io/how-to/website#version)
- [Post a new blog detailing the changes.](https://KoduGameLab.github.io/how-to/website#blog)
- [Create a new news feed item to notify users.](https://KoduGameLab.github.io/how-to/website#newsfeed)

---
## Building for the Microsoft Store
The Microsoft Store build uses the results of a normal build.

### Requirements
> - [MSIX Packaging Tool](https://www.microsoft.com/store/productId/9N5LW3JBCXKF) (Microsoft Store download)
> - Hyper-V must be activated on your machine.

### Steps for creating build

> - [Build the installer as normal.](#build)  In the target folder, rename the MSI to include the version number.
> - Run Hyper-V manager.
> - Run the MSIX Packaging Tool.
> - In the MSIX Packing Tool select "Application package".
> - Select "Create package on local virtual machine".
> - In the dropdown select "MSIX Packaging Tool Environment".
> - Enter local username and password for virtual environment.  (scoy, ERT4me!)
> - Click Next.  Dismiss Windows Security dialog.  Doesn't seem to work.
> - Check box to deactivate Windows Search, click Disable Selected, Click Next.
> - Browse to the MSI.  No args.  Choose "Do not sign package".  Click Next.
> - **Package information**
>> Package name = **9673InfiniteInstant.KoduGameLab_jhcksg2e634ay**<br>
>> *NOTE This name is no longer accepted by the MSIX packaging tool so use **9673InfiniteInstant.KoduGameLab** BUT this will fail validation when uploaded to the Store Dashboard.  Apparently if you just hit Save in the dashboard anyway it will work.*<br>
>> Package display name = **Kodu_Game_Lab** _(note the underscores)_<br>
>> Publisher name = **CN=92DF2F3C-F659-4DB2-9E93-41141C78BA29**<br>
>> Publisher display name = **InfiniteInstant**<br>
>> enter current version<br>
>> Package Description **Kodu Game Lab**<br>
>> Installation location = _leave blank_<br>
> - In Hyper-V manager, connect to MSIX Packaging Tool Environment.
> - Click Next to start installation.  When installer pauses, run XNA installer, click Refresh, click through and finish installation.  **DO NOT RUN KODU!**  Running Kodu at this point will create the SiteOptions file.  This will then be used by every single instance of Kodu instead of being unique to each machine.
> - In the MSIX Packaging Tool:  No restart needed, click Next.
> - Do not run any "first launch tasks".  Click Next, "Yes, move on".. 
> - No Services, click Next.
> - Save location = **C:\GitHub\store builds**
> - Click "Create".
> - In Hyper-V, right click on "Fresh Slate" checkpoint and apply.  This resets the virtual machine to pre-install state for next time.  Right click on VM and turn off.

### Steps for uploading to Partner Center
> - [In Partner Center](<https://partner.microsoft.com/en-us/dashboard/windows/overview>) click on Kodu project. 
> - At Game overview select Update for the current submission.
> - Click on Packages.
> - Drag/drop new msix package into box on web page.  After the upload, a quick validity check will be done.  This will find errors in PackageName or PublisherName etc. 
> - Decide whether to force this update or roll it out slowly and hit Save.
> - Once saved the final step is to Submit to Microsoft Store.
















