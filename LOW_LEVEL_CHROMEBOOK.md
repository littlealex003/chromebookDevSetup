**Access Root OS** (*requires Developer Mode to be enabled???*)

Press Ctrl + Alt + T to bring up a terminal window tab.

Type shell and press Enter.




* To see the Vital Product Data, or configuration information such as time zone, UUID, IMEI, model, region, language, keyboard layout and serial number: sudo dump_vpd_log --full --stdout
* To see the bios of your Chromebook, open up a command prompt (Control-Alt-T) and use the following command: sudo /usr/sbin/chromeos-firmwareupdate -V
