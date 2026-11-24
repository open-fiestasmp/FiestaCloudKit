# operating the server

Use a dedicated unprivileged account for each service. Check your service's working directory and Java version before enabling it. A systemd example is in `systemd/minecraft.service.example`.

Keep a tested, access-controlled backup of worlds, plugin data and configuration. Store credentials separately from public templates. For a restore, stop the affected services, restore into a separate location first, check ownership and permissions, then bring services back up and check logs.

For a move between hosts, test the proxy, authentication, queue, backups and firewall rules on a separate address before switching public DNS. Record the previous configuration so you can reverse the change.

## Remote cold storage

[FiestaWorldTier](https://github.com/open-fiestasmp/FiestaWorldTier) is experimental code for storing complete, cold Minecraft region bundles on another host. It is separate from backups; keep a tested, restorable backup of the world.

Its `remote.max_bytes` cap counts published objects and staging data. `remote.minimum_free_bytes` sets a filesystem free-space floor used by planning and checked before each publish. For example:

```json
{
  "max_bytes": 50000000000,
  "minimum_free_bytes": 40000000000
}
```

These are example decimal-byte values, not requirements. Adjust them for the remote filesystem and its other users. The application checks are not an OS-enforced quota, and unrelated processes can consume space during a transfer. Use a provider-enforced quota where available. Keep automatic eviction disabled until outage, interrupted-transfer, restart-recovery and connected-player cold-load behavior have been tested on disposable data.
