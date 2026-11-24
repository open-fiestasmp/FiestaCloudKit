# fiesta cloud kit

Notes and starter files for running a Minecraft server and proxy on cloud hosts. Review them for your own operating system, provider and software versions before putting them live.

- [Network and proxy notes](NETWORK.md)
- [Operations and backups](operations.md)
- [Example systemd service](systemd/minecraft.service.example)
- [Velocity proxy service](systemd/velocity.service.example)
- [Queue Paper service](systemd/queue-paper.service.example)
- [Fiesta plugin inventory](https://github.com/open-fiestasmp/FiestaServerKit/blob/main/PLUGINS.md)

Create a separate service user and working directory for each process. Install the Java version each server needs, then edit the unit's user, path, heap and jar name. Check a unit with `systemd-analyze verify` before copying it to `/etc/systemd/system/`; after starting it, check the journal. These units limit writable paths and Linux capabilities. They do not set up your firewall or proxy.

This repo is a community example with no production configs or credentials. It's not an official Minecraft or cloud provider project.
