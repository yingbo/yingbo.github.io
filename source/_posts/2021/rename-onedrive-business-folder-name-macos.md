---
title: Rename OneDrive Business Folder Name on MacOS
date: 2021-06-20
categories: 
 - Mac
tags: 
 - mac
---

Onedrive for bussiness forces adding the business name suffix in the sync folder. For example, if your business is "Foo", the sync folder under your home directory will be like `OneDrive - Foo`. It will be more anonying if your business name is long and have spaces. The setting from the client doesn't have an option for renaming the folder. There are "user feedback" to Mircosoft (https://onedrive.uservoice.com/forums/913522-onedrive-on-windows/suggestions/8729746-allow-onedrive-for-business-folder-to-be-renamed) for years but as you seen nothing happened yet.

Here is a "hacking" way. Please use it carefully. No garantee it won't harm your computers, but at least below are what I do on my Mac and works well.

1. Quit OneDrive client. 
2. First locate the setting folder. It should be under `$HOME/Containers/com.microsoft.OneDrive-mac/Data/Library/Application Support/OneDrive/settings/Business1/`. 
3. Looking for a `.ini` file in the folder. It's name is a UUID. For example, it looks like `a27edc43-553b-4447-82af-857f36d750ef.ini`. In the first line you can see your sync folder name there. Change it to any name you'd like. I simply rename it to "OneDrive". Note just using OneDrive might have a problem if you are using a personal account on this computer too, but it's not my casse.
4. For safty, run `find . -type f|xargs grep Foo` (replace Foo by your businese name) to find out any other files haveing the old folder name. Change them too.
5. Dont' forget change the folder name in your home directory. 

