# fiesta cloud kit

Notes and starter files for running a Minecraft server and proxy on cloud hosts. Review them for your own operating system, provider and software versions before putting them live.

- [Network and proxy notes](NETWORK.md)
- [Operations and backups](operations.md)
- [Example systemd service](systemd/minecraft.service.example)
- [Fiesta plugin inventory](https://github.com/open-fiestasmp/FiestaServerKit/blob/main/PLUGINS.md)

Create a dedicated service user, install the Java version your server needs, and edit the example service's paths and memory settings. Copy it to `/etc/systemd/system/`, reload systemd and check the journal after starting. The example does not set up your firewall or proxy for you.

This repo is a community example with no production configs or credentials. It's not an official Minecraft or cloud provider project.
