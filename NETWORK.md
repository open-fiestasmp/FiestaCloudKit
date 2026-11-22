# proxy and firewall notes

Players need to reach your proxy's public game port. Your game server and queue should only accept backend connections from your own proxies over a private network or an authenticated tunnel. Apply restrictions at both the cloud firewall and host firewall.

Configure modern forwarding on the proxy and backend using your software's own documentation. Generate your own forwarding secret and keep it outside public repos. Verify the backend rejects direct connections before opening your proxy to players.

If using Bedrock support, follow the Geyser and Floodgate instructions for your installed version and open only the transport and ports you actually use. Keep their generated keys private. Offline accounts need their own authentication; a proxy by itself doesn't prove who owns an account.

A proxy in another country can improve routing for some players and worsen it for others. Measure the full round trip to the actual game server before promising lower ping.
