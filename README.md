# chromebookDevSetup

1 The first thing you will probably want to do with your Chromebook is enable developer mode. Since this will wipe your Chromebook, if you do it later you will lose all your configuration and have to start over, so best to do it first as explained at the top here:
https://9to5google.com/2018/09/20/how-to-install-android-studio-on-chrome-os/

2 There are two options for Android Studio; download and install the Linux version as describe above, or download the new Chrome OS version and install that as described here:
https://developer.android.com/studio/install and here: https://www.aboutchromebooks.com/news/android-studio-chrome-os-chromebook-recommendation-google-io-2019/
The user interface to install a Linux file has changed; you have to click it in files, Open With, then Install with Linux option appears

3 Create ssh keys
https://www.ssh.com/ssh/keygen/#creating-an-ssh-key-pair-for-user-authentication

4 Add squashfs compatibility
The version of Linux used in the container is quite old and doesn't come with SquashFS integrated, so to run software that requires it (suck as snap) you must download, build and install squashfuse:
https://github.com/vasi/squashfuse

5 Install snap
https://snapcraft.io/docs/installing-snap-on-debian

6 Fix directory permissions
As per here, root directory has bad permissions and SNAP detects is
https://askubuntu.com/questions/1114511/snap-installation-wont-start
