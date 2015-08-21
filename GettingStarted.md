# Introduction #

This is a basic guide to installing and using the chatpad super driver.  For now, this is an alpha release so the install and uninstall process are rough.  Do not try the driver right now unless you are comfortable testing alpha software.  :)

Does it work on your system?  Please email me (**gtschemer at gmail dot com**) and tell me which OS, and whether it's 32-bit or 64-bit, and whether you have a "Made for Windows" controller or not!  I'm trying to get a feel for whether it is working for most people, only a few, and so on.

Does it NOT work on your system?  Post on the forum and wait for a mod to approve your post (http://www.mp3car.com/vbulletin/hardware-development/140189-contest-xbox-chatpad-driver-challenge.html), or email me.  Please tell me OS version information, the command line printout information if you have it, any special information you noticed, and if you happened to get a crash, the crash codes.  Event Viewer might be helpful to recover those codes if needed.
<br />

# Disclaimer #

This software is provided with no guarantees.  See the [License](License.md) wiki page for license information.<br />

  * This software is open-source, but I have not yet finished uploading everything to this project page.  If you are uncomfortable installing software without source, please wait until I upload the files.

  * This software currently only works with **WIRED** 360 controllers.  It may only currently work with the "Made for Windows" variant but that should change soon to support normal XBox 360 console controllers as well.

  * This software currently contains unsigned kernel drivers.  You must enable the use of unsigned drivers if you are using 64-bit Windows Vista or Windows 7.

  * This software is used at your own risk if you play games protected by the VAC (Valve anti-cheat) system.  This software does not mess with anything in Steam folders, does not replace DLLs, does not hook calls to DLLs, and does not communicate with games at all except by providing keyboard and mouse virtual HID devices to the operating system.  It is my belief that this should be safe, and the VAC FAQ (https://support.steampowered.com/kb_article.php?ref=7849-Radz-6869) mentions that system drivers should not trigger a VAC ban.  I am using the software myself as a gesture of good faith, and I play VAC-protected games.  Nevertheless, Valve provides no way to verify whether particular software is safe, so do not use the software if you are worried about this.  As long as the control utility is not running, the virtual keyboard and mouse devices should not even generate events.
<br />

# Install Process #

**WARNING!!!  THIS IS ALPHA SOFTWARE!  IF YOU ARE UNCOMFORTABLE WITH MESSING WITH DEVICE MANAGER OR DRIVERS, WAIT FOR A LATER RELEASE!**<br />

  * If you have used Driver Verifier on your system before, you will need to disable it until some things are fixed with the driver.  You can disable it by doing Start->Run, running "verifier.exe", selecting "Delete existing settings", and restarting your computer after clicking the Finish button and closing any other dialog/message boxes that appear.  If you don't know what Driver Verifier is, you probably do not need to worry about disabling it.

  * If you are using Windows Vista 64-bit or Windows 7 64-bit versions, you will need to first restart your system and press F8 right after the BIOS information goes away to get a boot menu.  Choose the option shown here:
![http://www.abload.de/img/boot_optionsqx8l.png](http://www.abload.de/img/boot_optionsqx8l.png)

You will need to choose that option with each boot for 64-bit systems, until we potentially get a kernel signing certificate.

  * Once Windows boots, connect your wired XBox 360 Controller.

  * Download the install package zip file that matches your OS:
    * **Windows XP:** http://code.google.com/p/chatpad-super-driver/downloads/detail?name=chatpad_0_0_3a_winxp.zip&can=2&q=
    * **Windows Vista:** http://code.google.com/p/chatpad-super-driver/downloads/detail?name=chatpad_0_0_3a_winvista.zip&can=2&q=
    * **Windows 7:** http://code.google.com/p/chatpad-super-driver/downloads/detail?name=chatpad_0_0_3a_win7.zip&can=2&q=

  * Extract the install package zip file to a directory.

  * IMPORTANT NOTE:  Go read Troubleshooting below, in case the next step causes a blue screen or crash!  It really shouldn't, but be prepared!

  * Launch the installer that matches your system.  Run chatpad\_installer\_amd64.exe for 64-bit systems and chatpad\_installer\_i386 for 32-bit systems.  It may ask for administrator privileges if you are on Windows Vista or Windows 7.  Do not run the ia64 binary unless you are sure your system needs it.

  * If it does not run at all, go check the Troubleshooting section for information about the Visual C++ 2010 redistributable.

  * A series of message boxes should appear describing the install process.  Some devices will get added in device manager, and you should see two or three dialog boxes (one for the chatpad driver, one for the virtual keyboard driver, and one for the virtual mouse driver) asking you whether you want to install an unsigned driver.  You will need to allow this to happen to install the drivers in their current state.<br />  **Note:  This step may take MINUTES.  Please give Windows time to install the drivers, parse INF files, and create restore points as appropriate.  Do not try to rerun the installer!  Check task manager if you are unsure if the installer is still running.**

  * If none of the message boxes mention an error, go to "Using the Drivers" below.  If an error occurs, go to Troubleshooting.  If it fails, do not try to immediately run the installation again since it probably won't work the second time either!
<br />

# Using the Drivers #

  * Launch the control utility that matches your system.  Run chatpad\_control\_amd64.exe for 64-bit systems, or chatpad\_control\_i386 for 32-bit systems.  It may ask for administrator privileges if you are on Windows Vista or Windows 7.  Do not run the ia64 binary unless you are sure your system needs it.

  * A command prompt window should open and stay visible.  If it closes instantly, you can try opening an adminstrator command prompt yourself (Start Menu, Programs, Accessories, right click Command Prompt, Run as administrator) and run the control utility again to see what output you get.  Only do this if you are comfortable with the command line and want to help me with debug output, though!

  * If everything goes well, the command prompt window will print some stuff and stay visible.  If you were watching your 360 controller, you might have noticed the light blinking.  Try pressing some chatpad keys!  They should type stuff.  :)  You can try using mouse control by pressing the "people" button to toggle double thumbstick mouse control.  You can use the left and right top triggers as mouse buttons.  Or, try A/B for buttons and X/Y for scrolling (holding X/Y down for repeated scrolling does not currently work)

  * Bring the control utito the foreground and press Control-C on the normal Windows keyboard to kill it, when you are finished with the chatpad.

  * If you got this far and everything is working, then you are welcome to modify chatpad\_config.txt (make a backup if you want, first) and change the bindings to suit your own taste.  See the comments in chatpad\_config.txt, and the strings in README.TXT, for information about how to set up key bindings.  Note that my documentation is in an early state, so please forgive TODO comments and debug output for now.  **Special note for key configuration:**  If you use an international key mapping, such as the German one, you will need to try to use mappings that match from a US keyboard to a German keyboard.  There is a German keyboard config file in the downloads section of this website right now.  Also note that you can use the KEYBOARD\_KEY\_RIGHT\_ALT modifier, or the SPECIAL\_ACTION\_RIGHT\_ALT binding, if you want to use the AltGr key.

  * If you want to copy the control utility to another directory, the only files that should be required are the control utility that matches your system (such as chatpad\_control\_amd64.exe) and the configuration file, chatpad\_config.txt.

  * If you tried the driver, thank you very much.  There are many improvements to be made to the install and driver process, but I wanted to get an alpha version out so that people could at least try it.  :)  Thank you for your patience, and I apologize in advance for any bugs you may find.
<br />

# Troubleshooting #

  * If the installer does not run at all, try getting the Visual C++ 2010 redistributable:  http://www.microsoft.com/downloads/en/details.aspx?FamilyID=a7b7a05e-6de6-4d3a-a423-37bf0912db84 or http://www.microsoft.com/downloads/en/details.aspx?FamilyID=bd512d9e-43c8-4655-81bf-9350143d5867 for 32-bit or 64-bit.

  * I haven't had problems with crashes lately and I really hope you won't either.  However, if you do encounter a blue screen or crash, don't panic!  First, unplug the 360 controller.  Then, wait for the system to reboot (or reboot it manually if necessary).  Then, run the uninstaller utility that matches your system (chatpad\_uninstaller\_amd64.exe for 64-bit systems or chatpad\_uninstaller\_i386.exe for 32-bit systems), approve administrator access if needed, wait for the uninstaller to indicate that it has finished, and plug the controller back in.  Open device manager, and notice that the 360 controller should now be indicating an error.  Right click it, and use Update Driver Software to go back to the normal Microsoft controller driver.

  * The uninstall process does not currently delete the virtual keyboard and mouse devices.  I need to add this code, but it's not in yet.  To manually remove the devices, first right click the "HID Keyboard Device" and "HID-compliant mouse" devices in Device Manager, under the **Keyboards** category and **Mice and other pointing devices** category, and choose the Uninstall option

> If you are not sure which devices belong with the chatpad, right click one and choose Properties.  Go to the Details tab, and you should see a Device Instance Id containing "CHATPADKBD" or "CHATPADMOUSE" if it is a device that belongs with the chatpad.

> Once all of the above devices are removed, right click the "XBox 360 Controller HID Keyboard for Chatpad" and "XBox 360 Controller HID Mouse for Chatpad" entries under the **Human Interface Devices** category and choose Uninstall on them as well, clicking the "Delete the driver software for this device" options.

  * If you get a "This program failed to install correctly" error for the installer or the uninstaller, just click the button to indicate that it worked, instead of trying to reinstall.

  * If your question is not answered above, check the Issues section (https://code.google.com/p/chatpad-super-driver/issues/list?can=1) and see if it is a problem that is already known and may already have a known fix.  Feel free to email me (gtschemer at gmail dot com) and let me know you are having the problem too, so I can get additional information or increase the priority of certain fixes.