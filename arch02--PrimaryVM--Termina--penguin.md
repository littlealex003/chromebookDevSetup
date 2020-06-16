# Termina

## VM running on Chromium (ChromeOS) via crosvm

* Termina is a VM image with a stripped-down Chrome OS linux kernel and userland tools. 
* Its only goal is to boot up as quickly as possible and start running containers. 
* Many of the programs/tools are custom here. 
* In hindsight, we might not have named it one letter off from “Terminal”, but so it goes.

When you run the Terminal, the Termina VM will be started automatically, and the default Crostini container will be started in that. You can now connect to the container via SSH or SFTP (via the Files app).


## Termina Components

* Maitred is our init and service/container manager inside of the **VM**, and is responsible for communicating with Concierge (which runs in the Chromium Root OS outside of the VM). Concierge sends it requests and Maitred is responsible for carrying those out.

* Tremplin is a daemon that runs in the VM to provide a gRPC wrapper for LXD. This includes basic functionality such as creating and starting containers, but also provides other Crostini-specific integration such as setting up a container's primary user, and setting up apt repositories in the guest to match the Chrome OS milestone.

