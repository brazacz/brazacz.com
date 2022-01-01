---
title: How to stop automatic updates of Windows 10
subtitle:
date: 2021-07-17 20:00 +0200
last_modified_at:
tags: [windows]
---

> There is no easy way to stop Windows forcing us new fixes and updates of Windows 10. Many PC users has experienced the situation that their computer started updating at the wrong time (e.g. during presentation) or lost their unfinished work due to automatic updates of the system.

If you have admin rights to your PC, there is a way to fix this. Following steps allow you to permanently stop automatic updates of Windows 10:

1. Open **Local Group Policy Editor** by clicking on **START** and by searching `gpedit.msc`
2. On the left side navigate to the following path:  
    `Computer Configuration > Administrative Templates > Windows Components > Windows Update`
3. In navigation menu click on **Windows Update**
4. On the right side double-click on **Configure Automatic Updates**
5. Check the **Disabled** option to turn off automatic updates permanently on Windows 10
6. Click **Apply** and then **OK**

The ability to manually check for updates remains available via `Settings > Update & Security > Windows Update > Check for updates`