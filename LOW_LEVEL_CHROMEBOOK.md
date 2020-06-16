**Access Root OS** (*requires Developer Mode to be enabled???*)

Press Ctrl + Alt + T to bring up a terminal window tab.

Type shell and press Enter.




* To see the Vital Product Data, or configuration information such as time zone, UUID, IMEI, model, region, language, keyboard layout and serial number: sudo dump_vpd_log --full --stdout
* To see the bios of your Chromebook, open up a command prompt (Control-Alt-T) and use the following command: sudo /usr/sbin/chromeos-firmwareupdate -V


**By default, the Chromium OS rootfs is read-only. If you boot the system in developer mode, you will be able to disable rootfs verification and modify existing files or write new files into the file system.** Before you do this, note that your file system will no longer be verifiable (won’t checksum properly) and you’ll end up needing to restore a recovery image in order to get back to normal mode. So this might be a bit dangerous if you’re not using the device for something like regression analysis (why I needed to do this).
* To make the file system writeable, first fire up a command prompt via crosh, by using Control-Alt-T and then running the shell command at the shell prompt: shell
* Then run the following shell script to remote rootfs verification and make the file system writeable: sudo /usr/share/vboot/bin/make_dev_ssd.sh --remove_rootfs_verification
* Then reboot and do whatever it is you need to do. For example, install a vine server and run automation scripts to do regression testing. Enjoy.
