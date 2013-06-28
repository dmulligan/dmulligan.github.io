---
layout: post
title: Moving to a new computer
---

Firefox: History
----------------
Install Firefox and ensure that you have fully closed the browser. Once complete, copy the following directory from your old comptuer to your new and open Firefox.

Windows XP
		C:\Documents and Settings\<WINDOWS_USERNAME>\Application Data\Mozilla\

Windows Vista / 7 / 8
		C:\Users\<WINDOWS_USERNAME>\AppData\Roaming\Mozilla

or using the following Environment Variable
		%APPDATA%\Mozilla

It maybe necessary to open Firefox using the -p option, which will display the Firefox profile selector, allowing you to set the default profile to use.

1 Press the Windows Key and the letter 'R'  on your keyboard at the same time.
2 Type 'C:\Program Files (x86)\Mozilla Firefox\firefox.exe -p' and click 'OK'.



Skype: History
--------------
Moving to a new computer is as simple as copying across the Skype configuration directory from the old computer to the new. First ensure that Skype is closed on both computers, then copy the old Skype direction which will be found in one of the following locations, depending on the version of Windows you have installed:

Windows XP:
		C:\Documents and Settings\<WINDOWS_USERNAME>\Application Data\Skype\

Windows Vista / 7 / 8:
		C:\Users\<WINDOWS_USERNAME>\AppData\Roaming\Skype

or using the following Environment Variable
		%APPDATA%\Skype

Once you have copied the directory to the new computer, you can open Skype and login.



Putty: Settings
---------------
Export:
1. Open the Registry Editor by pressing the Windows Key and the letter 'R', type 'regedit' and click 'OK'.
2. Once the Registry Editor has opened, press Ctrl-F and search for 'SimonTatham'.
3. When the folder has been located in the left tree, right click on it and select 'Export'. Now you can enter the name of the file you wish to export the settings to.

Import:
1. Copy the file to your new computer, right click on the file and select 'Merge'. This will add Putty's settings to your new computers registory.



Fonts: Install
--------------
Download, extract, select, right click, install each of the following
- [Android Droid](https://github.com/android/platform_frameworks_base/tree/master/data/fonts)
- [Android Roboto](https://github.com/android/platform_frameworks_base/tree/master/data/fonts)
- [Ubuntu](http://font.ubuntu.com/)
- [Adobe Source Code Pro](https://github.com/adobe/source-code-pro)
- [Eco Sans](http://www.ecofont.com/en/products/green/font/download-the-ink-saving-font.html)



Command Prompt: Setup
---------------------
I like to change the default font used by Command Prompt to a Droid Monospace font. To do this, I must first setup the font as an option to be selected in the Preferences of Command Prompt. Again, this will require a little messing around inside the Registery Editor.

1. Open the Registry Editor: Window key + R, type 'regedit' and click 'OK'.
2. Navigate to 


Sublime Text 2: Install
-----------------------
Add Explorer Context Menu. If you are missing an Windows Explorer context menu option to open files in Sublime Text (or any other editors for that matter), you can add the option using the following:

1 Create a new empty text file with a '.reg' extension. 
2 Add the below content (you may need to alter the path to the '.exe' file).
3 Right click on the file in Explorer and select 'Merge'

		Windows Registry Editor Version 5.00

		[HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2]
		@="Open with S&ublime Text 2"

		[HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2\command]
		@="C:\\Program Files\\Sublime Text 2\\sublime_text.exe \"%1\""



I also setup the following projects, but all of their data is in the cloud, so you only need to install and login.
- Dropbox
- Evernote
- AeroFS

Notes still to be complete:
- Git: Install
- Chrome: History
- GitHub: Setup
