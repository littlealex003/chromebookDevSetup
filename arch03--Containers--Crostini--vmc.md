# Running Containers

* You can launch crosh and use the vmc command to create new VMs manually. It will only run Termina at this point in time. You can then use vsh to connect to a VM instance and use LXC to run arbitrary containers.

* The default container launched via Terminal is Debian with custom packages. See cros-container-guest-tools for more details.

* In this flow, the VM is named termina and the container is penguin.




By virtue of having things installed, nothing starts running right away. In that regard, when you log out, everything is shut down and killed, and when you log in, nothing is automatically restarted.

When you run the Terminal, the Termina VM will be started automatically, and the default Crostini container will be started in that. You can now connect to the container via SSH or SFTP (via the Files app).

Similarly, if you run a Linux application directly (e.g. pinned to your shelf or via the launcher), the Termina VM will be started automatically, and the container that application belongs to will be launched. There's no need to run Terminal manually in these situations.

When you close all visible applications, the VM/containers are not shut down. If you want to manually stop them, you can do so via crosh and the vmc command.

Similarly, if you want to spawn independent VMs, or more containers, you can do so via crosh and the vmc and vsh commands.

Persistence
All the VMs and containers created, and the data within those containers, will persist across user sessions (logout/login). They are kept in the same per-user encrypted storage as the rest of the browser's data.

If a VM or container are stopped or killed ungracefully (e.g. powerloss), then data might be lost and need recovery like anything else in the system.