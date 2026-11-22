# minecraft hosting notes

A small starter for running a Java server behind a proxy on a cloud VM. The systemd unit is an example: review paths, Java version, resource limits and your server software before enabling it.

## start

1. Create a dedicated unprivileged service user and a server directory owned by it.
2. Install a compatible Java runtime and place your server jar and configuration in that directory.
3. Copy `systemd/minecraft.service.example` to `/etc/systemd/system/minecraft.service`, edit its user, paths and memory settings, then run `sudo systemctl daemon-reload` and `sudo systemctl enable --now minecraft`.
4. Check `systemctl status minecraft` and `journalctl -u minecraft` for startup errors.

## network

Open only the ports needed for your setup in both your cloud firewall and host firewall. Players connect to the proxy’s public listener; allow the backend listener only from trusted proxy IPs or a private network. Set up the forwarding secret and backend authentication according to your proxy and Paper documentation. A proxy alone does not verify cracked account ownership.

Keep SSH restricted, use individual SSH keys and protect backups. Measure latency and resource usage before adding extra proxies: routing through a distant proxy can increase latency. A proxy cannot reliably identify all cheating clients from a client hash.

This is a community example. It has no production addresses, credentials or server data. Adapt it to your provider and software versions.
