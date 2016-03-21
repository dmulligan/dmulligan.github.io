---
layout: post
title: Kodi - Custom Keymaps
---

Some TVs do not have the back button correctly mapped by default in Kodi (via CEC over HDMI), this makes navigation of the
menu structure very difficult. However, a fall back can be created by mapping 'Back' within Kodi to another button that is
not used as often on the TV remote. I selected the Red button for this task.

To do this, SSH into Kodi using the user root (default password 'openelec') and create a file named '~/.kodi/userdata/keymaps/samsung.xml' with the content

    <?xml version="1.0" encoding="UTF-8"?>
    <keymap>
      <global>
        <remote>
          <red>back</red>
        </remote>
      </global>
    </keymap>


If you wish to correctly map the back button for your TV, you will need to first discover the correct code that is
assigned for your TV. This code can be found by enabling the debug mode with the settings menu of Kodi, and then
monitoring Kodi's log file.

    tail -f ~/.kodi/temp/kodi.log

For each button that is pressed on the remote, a log entry will be outputted with the matching key code. 



Once the correct key code is found (in my case, 229), it can be added to the keymap XML file as follows

    <?xml version="1.0" encoding="UTF-8"?>
    <keymap>
      <global>
        <remote>
          <red>back</red>
        </remote>
        <keyboard>
          <!--key id="216">back</key-->
          <key id="229">back</key>
        </keyboard>
      </global>
    </keymap>

You can find more information about keymapping with Kodi as http://kodi.wiki/view/keymap

