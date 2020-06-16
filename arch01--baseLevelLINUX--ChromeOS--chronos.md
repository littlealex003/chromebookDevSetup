# Chromium (ChromeOS)

## Chromebook Root Level OS -- ChromeOS

https://www.chromium.org/chromium-os

### The Chromebook is running a root level protected Linux Kernel

#### Accessing the root level OS:

##### Open the Developer Console (VT02)

###### Clicking < Ctrl > - < Alt > - < -> > (right navigation key) will open the Developer Console. Here you can login as root or chronos (the developer user)

##### Via crosh (chrome shell)

1. Click < Ctrl > - < Alt > - t to open a crosh tab 
1. Type "shell" to open a shell logged into the root OS
1. You are now logged in as chronos

#### What to do with the root level os

##### Launch VMs with vmc and connect to them with vsh

* You can launch crosh and use the vmc command to create new VMs manually. It will only run Termina at this point in time. You can then use vsh to connect to a VM instance and use LXC to run arbitrary containers.

* Connect to default container

`crosh> vmc container termina penguin`

* Connect to the the default VM

`crosh> vsh termina`

* Start default VM

`crosh> vmc start termina`

Audio is an experimental feature in R79+ images. You need to enable audio capture (without permission model) from crosh.

`crosh> vmc start termina --enable-audio-capture`

* Stop default VM

`crosh> vmc stop termina`

##### Play with crosvm kvm monitor


## Chromium Components

* **crosvm**

**crosvm** is a custom virtual machine monitor that takes care of managing KVM, the guest VM, and facilitating the low-level (virtio-based) communication.

* **Concierge**

**Concierge** is a daemon that runs in **Chrome OS** which handles lifecycle management of VMs and containers and uses gRPC over vsock to communicate with Maitred (running in the Termina VM).

* **Cicerone**

**Cicerone** is a daemon that runs in **Chrome OS** which handles all communication directly with the VM and container once the container starts running. Specifically, it communicates with Tremplin (which runs inside of the VM), and Garcon (which runs in a container inside the VM).

* **Seneschal**

**Seneschal** is a daemon that runs in **Chrome OS** that handles lifecycle management of 9P servers. When Concierge starts a VM, it sends a message to Seneschal to also start a 9s instance for that VM. Then, while configuring the VM, Concierge sends a message to Maitred instructing it to connect to the 9s instance and mount it inside the VM.

* **9s**

**9s** is a server for the 9P file system protocol. There is one instance of 9s for each VM and it provides that VM with access to the user's data stored outside the VM. This includes things like the Downloads folder, Google Drive, and removable media. The lifecycle of each 9s instance is managed by Seneschal. Each 9s instance starts with no access to any files. Access to specific paths is granted by sending a message to Seneschal, which makes the requested path available to the specified 9s instance. Requests to share paths can only be triggered by some user action.

