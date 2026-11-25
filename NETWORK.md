# proxy and firewall notes

Players need to reach the proxy's public game port. Bind Paper and queue backends to `127.0.0.1` when they share the host. Across hosts, use a private network or authenticated tunnel and allow backend traffic only from your proxy at both the cloud and host firewalls.

Configure modern forwarding on the proxy and backend using your software's own documentation. Generate your own forwarding secret and keep it outside public repos. Verify the backend rejects direct connections before opening your proxy to players.

If using Bedrock support, follow the Geyser and Floodgate instructions for your installed version and open only the transport and ports you actually use. With Geyser's `both` transport, built-in signaling, `port: 19132` and `webrtc-port: 19133`, allow TCP 19132 for signaling, UDP 19132 for RakNet, and UDP 19133 for NetherNet. Apply the rules at both the cloud firewall and the host firewall. Other transport and HTTPS-proxy setups use different port roles; follow the matching [Geyser port-forwarding](https://geysermc.org/wiki/geyser/port-forwarding/) and [HTTPS for NetherNet](https://geysermc.org/wiki/geyser/nethernet-https/) guides. Keep generated keys private. Offline accounts need their own authentication; a proxy by itself doesn't prove who owns an account.

A proxy in another country can improve routing for some players and worsen it for others. Measure the full round trip to the actual game server before promising lower ping.

Keep one active server process responsible for each world. A second regional proxy can shorten a player's route to that proxy, but it adds the proxy-to-game-server trip. Do not run two Paper servers against the same world files.
