---
title: Clone a WordPress site to Pantheon using Duplicator plugin
description: Learn to copy a WordPress site to Pantheon using the Duplicator plugin.
category:
  - WordPress
  - getting-started
  - developing
keywords: wordpress, pantheon, duplicator, clone, new site
---
### Install [Duplicator](https://wordpress.org/plugins/duplicator/) on your Existing WordPress Site

### Archive Your Site's Code/Files/Database

Within your WordPress site, go to the Duplicator plugin page and create a new package. Using the default settings, click **Next** and then **Build**. When complete, click **Archive** to download the .zip file.

## 3. Create A New Pantheon Site/Import Your Archive

1. On your Dashboard, click **Create A New Site**.
2. Name your new site, and select **Import site** from the "Choose your Start State" options.
3. Select **Import Archive**.
4. Select the **File** option, and upload the .zip file.
5. Click **Import Site**.
6. The import process will create and deploy a new site based on the file you uploaded. If there are issues, please refer to our [migration](/docs/articles/sites/migrate) document for possible solutions or open a support ticket from your Dashboard. Be sure to include any error messages or relevant information.
