---
layout: post
title: Moving to a new computer
---

Moving to a new computer can have both its pros and cons. From one side, its (hopefully) a cool new computer but it also means you have to move all of you existing data across, that's if you don't want to start afresh. With the advert of the cloud, things have become a lot simpler. Developer's lives also have become simpler when moving code / workspaces if Git is used. Here's a list of notes that I created when moving to a new laptop recently.


Firefox
-------
After installing Firefox on your new computer, just copy the following directory from your old comptuer to your new and open Firefox. Ensure to close the browser on both computers first!

Windows XP:
		C:\Documents and Settings\<WINDOWS_USERNAME>\Application Data\Mozilla\

Windows Vista / 7 / 8:
		C:\Users\<WINDOWS_USERNAME>\AppData\Roaming\Mozilla

or using the following Environment Variable:
		%APPDATA%\Mozilla

It maybe necessary, the first time, to open Firefox on your new computer using the -p option. This will display the Firefox profile selector, allowing you to set the default profile to use when Firefox starts.

1. Press the Windows Key and the letter 'R'  on your keyboard at the same time.
2. Type 'C:\Program Files (x86)\Mozilla Firefox\firefox.exe -p' and click 'OK'.



Skype
-----
Moving to a new computer is as simple as copying across the Skype configuration directory from the old computer to the new. Again ensure Skype is closed on both computers before starting, then copy the old Skype direction which, depending on the version of Windows installed, will be found in one of the following locations:

Windows XP:
		C:\Documents and Settings\<WINDOWS_USERNAME>\Application Data\Skype\

Windows Vista / 7 / 8:
		C:\Users\<WINDOWS_USERNAME>\AppData\Roaming\Skype

or using the following Environment Variable:
		%APPDATA%\Skype

Once you have copied the directory to the new computer, you can open Skype and login.



Putty
-----
Export you saved sessions using:

1. Open the Registry Editor by pressing the Windows Key and the letter 'R', type 'regedit' and click 'OK'.
2. Once the Registry Editor has opened, press Ctrl-F and search for 'SimonTatham'.
3. When the folder has been located in the left tree, right click on it and select 'Export'. Now you can enter the name of the file you wish to export the settings to.

Import those saved sessions back into your new computer by:

1. Copy the file to your new computer.
2. Right click on the file and select 'Merge'. 

Now all of your Putty session settings are on your new computer.



Fonts
-----
Adding my prefered open source fonts, I had to download, extract, select, right click, install each of the following:

- [Android Droid](https://github.com/android/platform_frameworks_base/tree/master/data/fonts)
- [Android Roboto](https://github.com/android/platform_frameworks_base/tree/master/data/fonts)
- [Ubuntu](http://font.ubuntu.com/)
- [Adobe Source Code Pro](https://github.com/adobe/source-code-pro)
- [Eco Sans](http://www.ecofont.com/en/products/green/font/download-the-ink-saving-font.html)



Command Prompt
--------------
I prefer to change the default font used by Command Prompt to a the Droid Monospace font. To do this, I first had to setup the font as an option to be selected in the Preferences of Command Prompt. This requires a little messing around inside the Registery Editor.

1. Open the Registry Editor: Window key + R, type 'regedit' and click 'OK'.
2. Navigate to HLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Console\TrueTypeFont
3. Add a new String Value with the name set to x '0's and the value of the front name. (x is one more zero than already displayed)

		0	REG_ZS	Lucida Console
		00	REG_ZS	Consolas
		000	REG_ZS	Droid Sans Mono



Sublime Text 2
--------------
Add Explorer Context Menu. If you are missing an Windows Explorer context menu option to open files in Sublime Text (or any other editors for that matter), you can add the option using the following:

1 Create a new empty text file with a '.reg' extension. 
2 Add the below content (you may need to alter the path to the '.exe' file).
3 Right click on the file in Explorer and select 'Merge'

		Windows Registry Editor Version 5.00

		[HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2]
		@="Open with S&ublime Text 2"

		[HKEY_CLASSES_ROOT\*\shell\Open with Sublime Text 2\command]
		@="C:\\Program Files\\Sublime Text 2\\sublime_text.exe \"%1\""



I also setup the following tools, but all of their data is stored in the cloud, leaving me the only tasks of download, install and login.

- Dropbox
- Evernote
- AeroFS

Notes still to complete:

- Git
- Chrome
- GitHub
