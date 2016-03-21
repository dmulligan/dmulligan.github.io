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

    18:40:18 T:1868559424   DEBUG: CecLogMessage - >> 01:8a:91                                                
    18:40:18 T:1868559424   DEBUG: CecLogMessage - >> TV (0) -> Recorder 1 (1): vendor remote button down (8A)
    18:40:18 T:1868559424   DEBUG: CecLogMessage - key pressed: return (Samsung) (91)                         
    18:40:18 T:1868559424   DEBUG: PushCecKeypress - received key e5 duration 500                             
    18:40:18 T:1969861152   DEBUG: OnKey: 229 (0xe5) pressed, action is Title                                  
    18:40:18 T:1969861152   DEBUG: CGUIWindowManager::PreviousWindow: Deactivate               


From the above you can see that key code 229 was pressed, which is currently mapped to Title. However I wish to remap this key to Back using the following
keymap XML

    <?xml version="1.0" encoding="UTF-8"?>
    <keymap>
      <global>
        <remote>
          <red>back</red>
        </remote>
        <keyboard>
          <key id="229">back</key>
        </keyboard>
      </global>
    </keymap>


You can find more information about keymapping on [kodi.wiki](http://kodi.wiki/view/keymap)

