# operating the server

Use a dedicated unprivileged account for each service. Check your service's working directory and Java version before enabling it. A systemd example is in `systemd/minecraft.service.example`.

Keep a tested, access-controlled backup of worlds, plugin data and configuration. Store credentials separately from public templates. For a restore, stop the affected services, restore into a separate location first, check ownership and permissions, then bring services back up and check logs.

For a move between hosts, test the proxy, authentication, queue, backups and firewall rules on a separate address before switching public DNS. Record the previous configuration so you can reverse the change.
