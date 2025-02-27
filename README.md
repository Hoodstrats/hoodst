# COMPILING
- When compiling make all your changes in the config.def.h file and not just the config.h file (which is generated when you first use the build command)
    - sudo make clean install 
---
## PATCHING
- When applying patches or trying to use this command: patch -p1 < /path/to/file.diff 
    - this command will create a .rej file if there are any conflicts while merging the files 
    you can then open the .rej file and the .c or .h file it was trying to patch and make the changes yourself 
        - you can also use this command: patch --merge -i /path/to/file.diff 
            - this will give you GIT like merge conflict notes inside the files themselves indicated by

            ```C
            <<<<<<<
                Old code here 
            =====
                Changes here
            >>>>>>>
            ```
        - so far I've liked the patch -p1 command with the .rej files because I just open them side by side 
        and pull in what I want (easier to read for me)

---
## NOTES
- "Mod1Mask" is the alt key and "ShiftMask" is the Shift key. 
    - in the config.h file there are references to Mod1Mask >>>> can use this in place of ctrl or shift
---
## PATCHES I MADE SO FAR TO ST
- Added: Themes folder with gruvbox.h 
    - the header file contains the entire theme patch, removed stock colors in default config.h 
    - just added #include "./themes/gruvbox.h" in place of stock theme lines 
- Changed: Font to ComicShannsMono Nerd Font (might have to change this if this font isn't installed)
- Changed: Font size to 18 
- Changed: Border to 0 since i3 will take care of that for us 
- Added: Delete key patch (makes backspace and delete work appropiately...not sure why this isn't a thing by default)
---
#### Suggestions
##### Making ST selectable as the default terminal emulator in UBUNTU
- sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/local/bin/st 50
    - the 50 gives it priority above the other terminals in the list
    - then run and choose st from list: 
        - sudo update-alternatives --config x-terminal-emulator
---
# Original README
st - simple terminal
--------------------
st is a simple terminal emulator for X which sucks less.


Requirements
------------
In order to build st you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (st is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install st (if
necessary as root):

    make clean install


Running st
----------
If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

    tic -sx st.info

See the man page for additional details.

Credits
-------
Based on Aurélien APTEL <aurelien dot aptel at gmail dot com> bt source code.

