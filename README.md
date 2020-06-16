# chromebookDevSetup

* The **first thing** you will probably want to do with your Chromebook is **enable developer mode**. Since this will wipe your Chromebook, if you do it later you will lose all your configuration and have to start over, so best to do it first as explained at the top here:
https://9to5google.com/2018/09/20/how-to-install-android-studio-on-chrome-os/

* There are two options for Android Studio; download and install the Linux version as describe above, or download the new Chrome OS version and install that as described here:
https://developer.android.com/studio/install and here: https://www.aboutchromebooks.com/news/android-studio-chrome-os-chromebook-recommendation-google-io-2019/
The user interface to install a Linux file has changed; you have to click it in files, Open With, then Install with Linux option appears

* Create ssh keys
https://www.ssh.com/ssh/keygen/#creating-an-ssh-key-pair-for-user-authentication

* Add squashfs compatibility
The version of Linux used in the container is quite old and doesn't come with SquashFS integrated, so to run software that requires it (suck as snap) you must download, build and install squashfuse:
https://github.com/vasi/squashfuse

* Install snap
https://snapcraft.io/docs/installing-snap-on-debian

* Fix directory permissions
As per here, root directory has bad permissions and SNAP detects is
https://askubuntu.com/questions/1114511/snap-installation-wont-start

* Install sdk SDKMAN
For managing Java versions
https://sdkman.io/















**Container manipulation**
*This is an advanced process that we don’t recommend for new Linux users.*
* You can customize and configure your Linux containers for an ideal set-up. Below are some examples of container manipulation you may want to try. Check out the documentation on running custom containers in Chrome OS for more details.

**Manually starting the container**
* From a Chrome shell (Ctrl-Alt-T), stop and restart the penguin container:

vmc stop termina
vmc start termina
exit
vmc container termina penguin

**GPU acceleration (alpha)**
* Want to try (alpha) GPU acceleration? Restart the container with the --enable-gpu flag:

vmc stop termina
vmc start --enable-gpu termina
exit
vmc container termina penguin

* Then, install updated mesa drivers inside the container:

sudo apt update
sudo apt install -y cros-gpu-alpha mesa-utils
sudo apt update
sudo apt dist-upgrade

* Now, your apps and games should run with GPU acceleration. Give it a shot with Tux Racer:

sudo apt install -y extremetuxracer
/usr/games/etr
