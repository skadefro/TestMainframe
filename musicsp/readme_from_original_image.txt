
Sim390 MUSIC/SP Demo System                             Jun 23, 2006
===========================

                         Demo 1-volume MUSIC/SP system:  version "B"

                         MUSIC/SP version:  6.2 (ESA/390)


(c) Copyright Dave Edwards, 2001-2006. All rights reserved.

1. Overview
2. Conditions of Use
3. Distribution files
4. How to install and run Sim390 and MUSIC/SP under Windows
5. General notes and usage
6. Technical notes
7. Where to get more information

** Note: Check the Sim390 web site http://musicm.mcgill.ca/sim390
         for the latest version of the Sim390 mainframe emulator and
         updates to the MUSIC/SP Demo system.  There is also an
         alternate (backup) web site at http://www.geocities.com/sim390


Overview
--------

Sim390 is a Windows application that emulates an ESA/390 mainframe
computer.  This distribution musdemo_b.zip contains a one-volume demo
MUSIC/SP system that you can IPL under the emulator.  MUSIC/SP stands
for "Multi-User System for Interactive Computing / System Product" -
it is a mainframe operating system, similar in flavor to Unix but more
oriented towards 3270-type terminals.  It was developed at McGill
University in Montreal.  Sim390 contains a tn3270 (telnet for IBM
3270-type terminals) server that lets you connect to MUSIC/SP via
tcp/ip as an emulated 3270, using any of several available tn3270
clients.  It also provides local 3270 sessions, with various screen
sizes (24x80, 32x80, 43x80, 27x132), in which the 3270 emulation is
done by Sim390 itself.

You can also run the MUSIC/SP Demo system under the Hercules mainframe
emulator, but in that case none of the tcp/ip applications in MUSIC/SP
can be used, such as FTP, FTPD, HTTPD, socket programming, etc.

The MUSIC/SP Demo system in this distribution is version 6 release 2
(6.2).  It is equivalent to the previous 6.1 Demo system, with the
following changes:
 - All of the 6.1 update files have been applied:
   help.arc, man.arc, admin.arc, misc1.arc, fix_http1.arc, misc2.arc,
   misc3.arc, conf.arc, misc4.arc, misc5.arc, pl1fbas.arc, musbasic.arc,
   misc6.arc, misc7.arc, watc.arc, misc8.arc, misc9.arc, misc10.arc,
   misc11.arc.  See directory mus61 of the FTP site
   ftp://musicm.mcgill.ca/sim390 for more info about these updates.
 - The MUSICX volume (musicxd.vol) is now 150 MB (was 92 MB).
 - The system Load Library has been expanded.
 - The system Save Library has been enlarged, and now has about 50 MB
   of free space.
 - The version number in the MUSIC/SP nucleus has been changed from
   6.1 to 6.2.
 - More explanatory comments have been added to the default Sim390
   configuration file musicxdm.cfg.

MUSIC running under Sim390 supports most of the features of the
mainframe version of MUSIC (MUSIC/SP or MUSIC/ESA), except those
related to VM (e.g. spool files and external email) and mainframe
tapes.  (Tapes can be used in MUSIC/SP under Hercules.)  It is a true
multi-tasking operating system, with preemptive task scheduling, good
security, and high reliability.  It takes advantage of many of the
advanced features of Windows.  It supports TCP/IP, including an FTP
client, an FTP server (FTPD), a Web server (HTTPD), and a Telnet 3270
(TN3270) server for logging in to MUSIC over the network from a remote
workstation.  A tn5250 server is being developed, which will let
Sim390 accept connections from a tn5250 client emulating an IBM
5250-type terminal.

Some reasons why you may want to run MUSIC/SP under Sim390:

- Your real mainframe MUSIC system no longer exists, but you still
  want to be able to run your personal MUSIC programs.
- You want to learn more about how a mainframe operates.  The Sim390
  control window has tracing and debugging features, as does MUSIC itself.
  Perhaps you want to write your own mainframe operating system and
  run it under Sim390.
- Your MUSIC TCP/IP program is not working correctly, and you want to
  trace all its socket calls. (Hint: In the CPU / Debug and tracing menu,
  set ui.traceio to hex 1000. You may also try setting ui.debug to 1 or 2.)
- You want an easy FTP server or Web server for your PC.  Setting up a
  Web page is as simple as creating an HTML file in MUSIC.  You can use
  MUSIC's Rexx language processor to write HTML forms processors and
  CGI programs.
- MUSIC's server programs (FTPD and HTTPD), because of their relative
  simplicity and their isolation from Windows, are not subject to the
  usual viruses and security holes that plague the "mainstream" Windows
  and Unix server programs.  MUSIC is secure and reliable.
- You can write applications in Assembler, Rexx, PL/1 F, MUSIC Basic,
  WATFIV Fortran, and Waterloo C.  Applications can use tcp/ip sockets
  and VSAM.
- It's easy and fun.


Conditions of Use
-----------------

This software, including the Sim390 mainframe emulator, the MUSIC/SP
Demo system, and third-party software provided with the MUSIC/SP
Demo system, is provided on an "as-is" basis, and is intended only
for demonstration and evaluation purposes.  Use it at your own risk.
The author is not responsible for any damages or losses that may
occur from your use of this software, and no support or warranty is
provided.  This software must not be used, sold, or distributed for
profit, without the written permission of the author.  It is
provided only for personal use by individuals.  Use in a production
or commercial or institutional environment is prohibited, unless
specific written permission is obtained from the author.

Sim390 is (c) Copyright by Dave Edwards, 2001-2006.
All rights reserved.

The MUSIC/SP operating system is (c) Copyright by McGill University,
1989-2000.  Additions and modifications to MUSIC/SP and its
components made 2001 and later, as distributed with the MUSIC/SP
Demo system, are (c) Copyright by Dave Edwards, 2001-2006.

The Waterloo C compiler and library is (c) Copyright by the
University of Waterloo, 1989.  The Waterloo C compiler and library
distributed with the MUSIC/SP Demo system is provided without
support, warranty, or source code.  It is to be run only on the
MUSIC/SP Demo system running under Sim390, Hercules, or a similar
mainframe emulator.  It must not be repackaged or redistributed for
use under any other system.


Distribution files contained in musdemo_b.zip
----------------------------------------------

   musicxd.vol - This 150 MByte binary file contains the FBA disk volume
        MUSICX for the MUSIC/SP demo system.  Sim390 uses this file to
        emulate a mainframe FBA disk volume.  Note: In order to save
        space, some of the standard files normally present on a MUSIC
        system are not on this system's Save Library.
        NOTE: To run under Hercules, you would define this volume file
        as device type 3370 in the Hercules config file.

   musicxdm.cfg - Configuration file for Sim390.  This is an editable
        text file.  It assumes that the distribution files are
        restored to the directory c:\sim390dm.  If you used a
        different location, you should change any config statements
        that refer to that directory.  You can make changes to the
        config file, for example, to increase the memory size or
        change the tn3270 listening port number.  See the comments in
        the file.

   printout.txt - This is a text file that is used by the emulator for
        printer output.  The emulator assumes this file exists, and
        appends any printer output to it.  You can use Notepad to view
        this file while the emulator is running, to see the output of
        MUSIC batch jobs.  The emulator does not actually print anything.

   readme.txt - This file.

The Sim390 emulator itself (sim390.exe) should be downloaded
separately from the anonymous FTP site ftp://musicm.mcgill.ca/sim390 .
The Sim390 home page http://musicm.mcgill.ca/sim390 contains
additional info and files, including a detailed description of the
config statements (file config.txt on the Tech Info page) and other
useful documentation.

NOTE: Only those updates (xxx.arc files) designated for MUSIC/SP 6.2
should be applied to this Demo system.  Such updates, if any, are
in directory mus62 of the FTP site.  Previous updates (in directory
mus61) are already part of this Demo system, and must not be applied,
since they would possibly down-date some files and components.


How to install and run Sim390 and MUSIC/SP under Windows
--------------------------------------------------------

1. Create a directory called c:\sim390dm.
   (If you want to use a different directory, you must change the
   file names in the configuration file musicxdm.cfg.)

2. Use WinZip (or equivalent) to restore the files from the
   distribution musdemo_b.zip file to the directory c:\sim390dm.

3. Copy the latest sim390.exe file to directory c:\sim390dm.
   You can download it from ftp://musicm.mcgill.ca/sim390 . The
   download file is usually named sim390_nn.exe, where nn is a version
   number (for example 15 means version 1.5).  After download, rename
   it to sim390.exe.  If you need to run the emulator on Windows 95,
   which has only Winsock 1.1, download sim390_nn_w95.exe instead.
   The emulator has been tested successfully on Windows 95 (see the
   note above), 98, NT, 2000, and XP.  To get a reasonable execution
   speed, a PC with a speed of 200 MHz or more is recommended,
   although it will run on slower machines.  Multiple copies of Sim390
   can be run simultaneously under Windows, but then each should
   normally have its own volume (*.vol) files.

4. Review the config file musicxdm.cfg and make any changes you need.

5. Start the emulator by the following command:

      c:\sim390dm\sim390.exe c:\sim390dm\musicxdm.cfg

   This command can be entered via Start / Run, or in a Command window.
   You can also create a desktop shortcut, with the command as the
   target.  Or you can create a .bat file containing the command.

6. The above command opens 2 windows:

   (1) The Sim390 control window, which is a small window with a
       beige background.

   (2) An operator messages (console) window, which is an output-only
       window for messages from the emulator and MUSIC/SP.  To enter an
       operator command to MUSIC/SP (for example, the command "stop" to
       shut down MUSIC/SP), enter it via the Input menu item on the
       Sim390 control window.

   In the messages window, you should see the startup messages for
   Sim390, indicating that the configuration file has been read and an
   ESA/390 system reset has been done.  At this point, the ESA/390 CPU
   is in stopped state.  (An optional autoipl statement in the config
   file can be used to automatically IPL from the MUSIC/SP volume, in
   which case the next step is already done and should be skipped.)

   Abbreviations:   CPU = Central Processing Unit
                    IPL = Initial Program Load

7. Use the CPU menu to IPL from device 201, specifying the option
   "Supply blank record for first console read".  This IPLs the
   MUSIC system from volume MUSICX.  Messages showing the progress
   of the IPL will appear in the operator messages window.
   When IPL is finished, the control window will indicate "CPU running"
   and "Wait state".  Some error messages relating to terminal devices
   are normal during MUSIC IPL.  (You can modify the Sim390 config
   file to automatically do the IPL operation when Sim390 starts.)

8. To sign on to MUSIC, select "Add local 3270 session" from the File
   menu, to open a 3270 window.  In the 3270 window, press Enter to
   get the MUSIC sign-on screen.  Enter $000 as the userid and music
   as the password.  You can now enter MUSIC commands, such as edit,
   view, library, sysdate, etc.  When finished, use the off command
   to sign off MUSIC.  You can add more local 3270 sessions, up to the
   number defined in the configuration file.  When you add a local 3270
   session, you choose the screen size (24x80, 32x80, 43x80, or 27x132).
   You can also sign on to MUSIC remotely, using a Telnet (TN3270)
   client, such as Hummingbird's HostExplorer (HostExplorer 4.0 is known
   to work).  The TCP port number to connect to is as defined by the
   "remote3270port" statement in the Sim390 config file; you can
   change the port number if you want.  ("3270" is a type of mainframe
   terminal or workstation. A TN3270 client, running on a PC, emulates
   a "real" 3270 terminal, and allows for remote connection to a
   mainframe system. Several free TN3270 clients are available.)

   ---> You should change the password of the MUSIC userid $000, for
        security reasons, if your PC is connected to the Internet.
        This can be done, after sign-on, by the commands:
           /vip on
           newpw
        (Or just use item 7 from the main menu of the Admin Facility.)

   While signed on, the 3270 screen is in one of several modes.
   The $000 userid starts in "full-screen" mode, with the Admin Facility
   main menu; the command input area is near the top of the screen.
   You can press F3 to exit Admin, which puts you into *Go mode, which
   is a line-by-line mode with the command input area near the bottom
   of the screen and a larger output area in the top part of the screen.
   To re-enter Admin, type the command admin in the *Go command area.

9. While MUSIC is running, you can enter operator console commands via
   the Input menu of the Sim390 control window.  You can also enter
   operator console commands by running the CONSOLE program while
   signed on to MUSIC.  To start it, type console in the command area
   of the MUSIC screen.

   NOTE: If you inadvertently use the mouse to highlight text in the
   console messages window, MUSIC/SP may appear to freeze, since it
   cannot write messages to the console, and it waits for the writes
   to complete. To clear this freeze condition, simply press the Esc
   key while the console is the current window.  Also, be careful not
   to close the console window, since that shuts down Sim390.

10. To shut down MUSIC, enter the operator command stop from the
   Input menu.  This closes all 3270 terminal sessions and stops the
   MUSIC/SP system (disabled wait state in Sim390).  At this point you
   can re-IPL MUSIC or shut down Sim390 itself.


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

- The MUSIC system included with this demo is a stripped-down system,
  intended for demonstration purposes only, and many of the normal
  MUSIC Save Library files are not present.  It is at level MUSIC/SP 6.2
  (MUSIC/ESA).  However, most of the basic MUSIC utilities (including
  an FTP client) are there, and files can be added to it from MUSIC
  archive (.arc) files.  The MUSICX volume could be enlarged, and other
  disk volumes could be added.  Manuals (slightly out of date) for
  MUSIC are available from http://musicm.mcgill.ca in PDF form.
  Be careful when copying nucleus or system utility files from an
  earlier MUSIC version (e.g. 5.1 or 5.3) to MUSIC/ESA (6.x), since
  MUSIC/ESA uses ESA/390 mode, as required by the Sim390 emulator,
  while earlier MUSICs use 370 mode; the mainframe input/output model
  is different, as well as some CPU instructions.  This warning applies
  especially to nucleus modules and system utilities.

- VM is not present, therefore MUSIC operations that depend on VM
  (such as spool file i/o) do not work.  This means that MUSIC's MAIL
  and RDMAILER programs cannot be used to send or receive external
  email (but local email within MUSIC still works).  However, a MUSIC
  SMTP is being developed, and it is possible to use Sim390's TCP/IP
  support to send email from MUSIC to an external SMTP server for
  delivery, although the programs to do so are not included with the
  demo system.

- There is no support in Sim390 for mainframe tapes.  However, in many
  cases, a MUSIC UDS file can be used instead of a tape.  The best way
  to import or export data to or from MUSIC is to use FTP (File Transfer
  Protocol).  MUSIC has an FTP client and server.  Note that FTP can be
  used to rapidly transfer files between MUSIC and Windows on the same
  machine; use the ftp.exe client in Windows, and the FTPD server in MUSIC.
  For details on MUSIC FTP, see file ftphelp.txt.

- To submit a MUSIC batch job: see sample MUSIC file ccde:batch.job .

- To have MUSIC read a PC file as a batch job from the card reader
  (device number 00C): use the "Reader file" dialog from the File menu
  of the Sim390 control window.

- In a MUSIC batch job, you can specify ROUTE(MUSIC) to direct the
  printed output to the MUSIC Output Queue, rather than to the
  printer (device number 00E).  To view the output, use the OUTPUT
  command of MUSIC.


Technical notes
---------------

- The following configuration settings are easy to change:
   - The memory size available to MUSIC: change the memory statement
     in the Sim390 config file.  To avoid excessive swapping and paging
     at the Windows level, the size should be considerably less than
     the real PC memory size.  Typical MUSIC memory sizes are 6M or 8M
     (small), 16M (medium), 32M (large).
   - To have MUSIC automatically started when Sim390 starts: uncomment the
     autoipl statement in the Sim390 config file.
   - The TCP port number for the built-in Telnet TN3270 server: change the
     remote3270port statement in the Sim390 config file.
   - The TCP port numbers for MUSIC's FTPD and HTTPD servers: change
     MUSIC file $tcp:inetd.ports and restart Sim390.
   - Other MUSIC TCP/IP settings: edit the MUSIC file $tcp:tcpip.config.
     File $tcp:tcpip.config contains the time zone settings, IP addresses
     of your DNS server(s), and various setting for HTTPD (Web server).

- The nucleus modules of MUSIC under Sim390 were assembled in
  "McGill mode" rather than the normal "MUSIC mode": &OPSYS in the
  macro SYSTEM.M was set to 'MCGILL' rather than 'MUSIC'.
  CALL SYSENV(1,N) returns N=1, not 0.  This means that MUSIC BTRMs
  (background tasks, such as SYSLG, AUTOSUB, and INETD) are set up
  using userid CFMN instead of $MON.

- Sim390 uses emulated FBA (Fixed Block Architecture) disk devices
  for its disk volumes.  The FBA block size is 512 bytes.  Each FBA
  device is represented by a binary PC file, which is logically a
  sequence of 512-byte blocks numbered 0, 1, 2,...  Block 0 is at
  displacement 0 in the PC file.  Block 1 is at displacement 512 in
  the PC file, etc.  Each volume is represented by an iodevice
  statement in the Sim390 config file.  The MUSIC nucleus (see file
  $gen:nucgen.job) allows for ESA/390 FBA device numbers 201 thru 206
  and 301 thru 306.  By using the provided 1-volume MUSICX as a base,
  you can create a larger MUSIC system by increasing the size of the
  musicxd.vol PC file, by adding additional FBA volumes, by increasing
  the sizes of the various MUSIC system data sets (scratch, swap, page,
  acct), and by adding more Save Library data sets.

- MUSIC has BTRMs (background tasks) set up for SYSLG, AUTOSUB, and
  INETD, on userids CFMN001, CFMN002, and CFMN003.  You can configure
  the system log server SYSLG by editing file $pgm:syslg.define. By
  default, most log records are discarded.  You can configure AUTOSUB,
  for example to schedule MUSIC jobs to run automatically at various
  times, by editing file cfmn:auto.data1.  Since VM is not present in
  Sim390, the BTRMs VMREADX, RDMAILER, and AUTOPR should not be set up.


Where to get more info
----------------------

For more info or to report problems or make suggestions:

   Dave Edwards

   Web page:  http://musicm.mcgill.ca/sim390

   Alternate web page:  http://www.geocities.com/sim390

   Anonymous FTP site:  ftp://musicm.mcgill.ca  (directory: sim390)

   To contact me:  Use the "Send a message" form on the web site.

The Web site and its anonymous FTP site musicm.mcgill.ca have
general MUSIC documentation and downloads, including most manuals
(slightly out of date).  Several current and former MUSIC/SP
customer sites, including McGill University, have staff who are
familiar with the usage, configuration, and internals of MUSIC.

For ESA/390 mainframe architecture: See online manuals on www.ibm.com.

