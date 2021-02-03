---
title: Kodu Game Lab
subtitle: Community Notes
layout: page
show_sidebar: false
hero_height: is-small
hide_footer: true
---

## Classic Community
The classic community is built from the [KoduCloudService](https://github.com/KoduGameLab/KoduCloudService) project using VS 2019.

### Notes:
- The file Web.config should **not** be checked in.  Instead, if changes are needed, update Web.config.zip and check that in.  Keep in sync via email about this.

### To Debug Locally
Build and run debug version.  This will open a browser page with localhost:port as the address.  In Kodu, set this port for the CommunityUrl in CommunityRequest.cs.  Then you can debug both sides.  The community will still talk to the SQL database so everything should work. 
 
 ### To Deploy
 In the Solution Explorer right click on **Azure->Prod->KoduCloudServiceProd** and select **Publish**.
- **Sign in**
  - Sign in if needed.
  - Subscription should be **Kodu Production**
- **Settings**
  - Common Settings 
    - Cloud Service: **kodu community (North Central US)**
    - Environment: **Staging** (can swap once deployed)
    - Build configuration: **Release**
    - Service configuration: **Cloud**
    - Nothing checked.
  - Advanced Settings
    - Deployment label: **KoduCloudServiceProd**
    - Check Append current date and time
    - Storage account: **kodu (NorthCentrral US)**
    - Only check **Deployment update**
- **Diagnostics**
  - Uncheck **Send diagnostics data to Application Insights**

Finally, click publish.  Takes about 5 minutes to fully deploy.  You can watch the progress in the **Microsoft Azure Activity Log** window.  Expand current deployment to watch individual steps.  

## New Community