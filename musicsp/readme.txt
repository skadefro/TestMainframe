
Alternative readme.txt to get thing going in a hurry


1. Install Hercules.  I used the spinhawk version from https://github.com/Open3270/spinhawk


2. Unzip the .VOL file ane Run Hercules using the musicxd_for_hercules.cng configuration file

./unzip_volume
hercules -f musicxd_for_hercules.cng

3. Initialise the mainframe.  Follow this carefully, it's a little odd

[from command line:]  telnet localhost 3270
[from hercules prompt:] ipl 201
[from telnet command line:]  <press enter>

** Leave everything open.  You can ignore the errors if you're just testing, for more information read the full readme.txt

4. Connect to the TN3270 session by running your favourite terminal emulator and connecting to port 3270

5. Login using userid : $000 and password 'music'

6. Use the MUSIC/SP system

7. To quit, press F3 until you leave the menu system and type OFF <enter> to quit the 3270 session. Then type 'quit' on the Hercules window



General notes and usage
-----------------------

- Local 3270 keyboard assignments:
    Clear: Ctrl+Z
    PA1: - on numeric keypad
    PA2: + on numeric keypad
    PA3: / on numeric keypad
    Newline: * on numeric keypad, or Ctrl+Enter
    Reset: Esc
    PF1 to PF12: F1 to F12
    PF13 to PF24: Shift+F1 to Shift+F12
    PF7: PageUp
    PF8: PageDown
    PF23: Ctrl+PageUp
    PF11: Ctrl+PageDown
    Erase EOF: Ctrl+End
    Erase Input: Ctrl+Home
    Sys-Request: Ctrl+K

- 3270 Clipboard operations in a local 3270 window:
    Use the left mouse button to select a block of text.
    Ctrl+C: Copy selected text to Clipboard.
    Ctrl+X: Cut: copy to Clipboard and erase the block.
    Ctrl+E: Erase (without copy to Clipboard).
    Ctrl+V: Paste from Clipboard to 3270 cursor location; the cursor
            should be in a modifiable field.  To get a large area to
            paste into, run the PASTE program or use Input Mode of
            the MUSIC Editor.
    To unselect the block, left-click the mouse.

