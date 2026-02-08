Edit as planned (loopback → lan):


{
"gateway": {
"mode": "local",
"auth": {
"mode": "token"
},
"port": 18789,
"bind": "lan",  // ← Critical change for stable local binding
"tailscale": {
"mode": "off"
}
},
// ... unchanged (keep xAI/Telegram)
}

1. Foreground Start (Reveals Crash)

Apply
docker compose down  # Clean
docker compose up openclaw-gateway  # FOREGROUND: Logs stream live!
Hits error? Ctrl+C, share full output (e.g., "Model fetch fail", "Bind error").


Success: "Gateway ready", hit Ctrl+C, then docker compose up -d openclaw-gateway.


5. Nuclear: Re-Run Setup (5 Mins, Fresh xAI)

Apply
docker compose down -v
rm -rf ~/.openclaw docker-compose.extra.yml  # Reset config/mounts
export OPENCLAW_EXTRA_MOUNTS="$HOME/clawdpal-data-exchange:/home/node/clawdpal-data-exchange:rw"
$(brew --prefix)/bin/bash ./docker-setup.sh  # Re-wizard xAI
In wizard: xAI key → "lan" bind explicitly.



0.2s

wanghui@WANGs-MBA-2023 openclaw % docker compose up openclaw-gateway 

WARN[0000] The "CLAUDE_AI_SESSION_KEY" variable is not set. Defaulting to a blank string. 

WARN[0000] The "CLAUDE_WEB_SESSION_KEY" variable is not set. Defaulting to a blank string. 

WARN[0000] The "CLAUDE_WEB_COOKIE" variable is not set. Defaulting to a blank string. 

WARN[0000] The "CLAUDE_AI_SESSION_KEY" variable is not set. Defaulting to a blank string. 

WARN[0000] The "CLAUDE_WEB_SESSION_KEY" variable is not set. Defaulting to a blank string. 

WARN[0000] The "CLAUDE_WEB_COOKIE" variable is not set. Defaulting to a blank string. 

[+] up 2/2

✔ Network openclaw_default              Created                                                         0.0s

✔ Container openclaw-openclaw-gateway-1 Created                                                         0.1s

Attaching to openclaw-gateway-1

openclaw-gateway-1  | 2026-02-08T10:54:46.077Z [canvas] host mounted at http://0.0.0.0:18789/__openclaw__/canvas/ (root /home/node/.openclaw/canvas)

openclaw-gateway-1  | 2026-02-08T10:54:46.179Z [heartbeat] started

openclaw-gateway-1  | 2026-02-08T10:54:46.183Z [gateway] agent model: xai/grok-4-1-fast

openclaw-gateway-1  | 2026-02-08T10:54:46.184Z [gateway] listening on ws://0.0.0.0:18789 (PID 7)

openclaw-gateway-1  | 2026-02-08T10:54:46.185Z [gateway] log file: /tmp/openclaw/openclaw-2026-02-08.log

openclaw-gateway-1  | 2026-02-08T10:54:46.203Z [browser/service] Browser control service ready (profiles=2)

openclaw-gateway-1  | 2026-02-08T10:54:48.087Z [telegram] [default] starting provider (@MyClawdpalBot)

openclaw-gateway-1  | 2026-02-08T10:54:48.105Z [telegram] autoSelectFamily=false (default-node22)

openclaw-gateway-1  | 2026-02-08T10:54:53.365Z [ws] unauthorized conn=bcec4a6a-bc16-4eef-95bb-4510c525cca4 remote=149.154.166.110 client=openclaw-control-ui webchat vdev reason=token_mismatch

openclaw-gateway-1  | 2026-02-08T10:54:53.373Z [ws] closed before connect conn=bcec4a6a-bc16-4eef-95bb-4510c525cca4 remote=149.154.166.110 fwd=n/a origin=http://localhost:18789 host=localhost:18789 ua=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/144.0.0.0 Safari/537.36 Edg/144.0.0.0 code=4008 reason=connect failed

openclaw-gateway-1  | 2026-02-08T10:55:08.396Z [ws] unauthorized conn=11207f08-0bab-4ebd-96da-928a130421d7 remote=149.154.166.110 client=openclaw-control-ui webchat vdev reason=token_mismatch

openclaw-gateway-1  | 2026-02-08T10:55:08.399Z [ws] closed before connect conn=11207f08-0bab-4ebd-96da-928a130421d7 remote=149.154.166.110 fwd=n/a origin=http://localhost:18789 host=localhost:18789 ua=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/144.0.0.0 Safari/537.36 Edg/144.0.0.0 code=1008 reason=unauthorized: gateway token mismatch (open the dashboard URL and paste the token in Control UI settings)

openclaw-gateway-1  | 2026-02-08T10:55:23.438Z [ws] unauthorized conn=7a3af368-022b-4435-91e2-a467a5f1dbf0 remote=149.154.166.110 client=openclaw-control-ui webchat vdev reason=token_mismatch

openclaw-gateway-1  | 2026-02-08T10:55:23.458Z [ws] closed before connect conn=7a3af368-022b-4435-91e2-a467a5f1dbf0 remote=149.154.166.110 fwd=n/a origin=http://localhost:18789 host=localhost:18789 ua=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/144.0.0.0 Safari/537.36 Edg/144.0.0.0 code=1008 reason=unauthorized: gateway token mismatch (open the dashboard URL and paste the token in Control UI settings)

openclaw-gateway-1  | 2026-02-08T10:55:38.551Z [ws] unauthorized conn=a9ccfd46-fc71-47f9-836f-b7b084d98ec5 remote=149.154.166.110 client=openclaw-control-ui webchat vdev reason=token_mismatch

openclaw-gateway-1  | 2026-02-08T10:55:38.559Z [ws] closed before connect conn=a9ccfd46-fc71-47f9-836f-b7b084d98ec5 remote=149.154.166.110 fwd=n/a origin=http://localhost:18789 host=localhost:18789 ua=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/144.0.0.0 Safari/537.36 Edg/144.0.0.0 code=1008 reason=unauthorized: gateway token mismatch (open the dashboard URL and paste the token in Control UI settings)

openclaw-gateway-1  | 2026-02-08T10:55:53.607Z [ws] unauthorized conn=dae99a5e-40ba-49a0-8e0c-1ba377343d7a remote=149.154.166.110 client=openclaw-control-ui webchat vdev reason=token_mismatch

openclaw-gateway-1  | 2026-02-08T10:55:53.610Z [ws] closed before connect conn=dae99a5e-40ba-49a0-8e0c-1ba377343d7a remote=149.154.166.110 fwd=n/a origin=http://localhost:18789 host=localhost:18789 ua=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/144.0.0.0 Safari/537.36 Edg/144.0.0.0 code=1008 reason=unauthorized: gateway token mismatch (open the dashboard URL and paste the token in Control UI settings)


Get Fresh Token:

Potentially dangerous command
Run
docker compose run --rm openclaw-cli dashboard --no-open
Output: "Dashboard URL: http://localhost:18789/?token=abc123def..." (copy FULL URL/token).
```output
                                                        0.0s
wanghui@WANGs-MBA-2023 openclaw % docker compose run --rm openclaw-cli dashboard --no-open
WARN[0000] The "CLAUDE_AI_SESSION_KEY" variable is not set. Defaulting to a blank string. 
WARN[0000] The "CLAUDE_WEB_SESSION_KEY" variable is not set. Defaulting to a blank string. 
WARN[0000] The "CLAUDE_WEB_COOKIE" variable is not set. Defaulting to a blank string. 
WARN[0000] The "CLAUDE_WEB_SESSION_KEY" variable is not set. Defaulting to a blank string. 
WARN[0000] The "CLAUDE_WEB_COOKIE" variable is not set. Defaulting to a blank string. 
WARN[0000] The "CLAUDE_AI_SESSION_KEY" variable is not set. Defaulting to a blank string. 
Container openclaw-openclaw-cli-run-616905ded6d2 Creating 
Container openclaw-openclaw-cli-run-616905ded6d2 Created 

🦞 OpenClaw 2026.2.6-3 (unknown) — WhatsApp automation without the "please accept our new privacy policy".

Dashboard URL: http://172.18.0.3:18789/#token=fd08927d43baebccc24dd7ff588e494cce4275de82514dfa
Copy to clipboard unavailable.
No GUI detected. Open from your computer:
ssh -N -L 18789:127.0.0.1:18789 user@<host>
Then open:
http://localhost:18789/
http://localhost:18789/#token=fd08927d43baebccc24dd7ff588e494cce4275de82514dfa
Docs:
https://docs.openclaw.ai/gateway/remote
https://docs.openclaw.ai/web/control-ui
wanghui@WANGs-MBA-2023 openclaw % 

```

Dashboard URL: http://172.18.0.3:18789/#token=xxxx
Copy to clipboard unavailable.
No GUI detected. Open from your computer:
ssh -N -L 18789:127.0.0.1:18789 user@<host>
Then open:
http://localhost:18789/
http://localhost:18789/#token=xxxx
Docs:
https://docs.openclaw.ai/gateway/remote
https://docs.openclaw.ai/web/control-ui



when @MyClawdpalBot -> start, got message:

OpenClaw: access not configured.

Your Telegram user id: 1151855936

Pairing code: X9R7EQRR

Ask the bot owner to approve with:
openclaw pairing approve telegram <code>

cd ~/openclaw-docker/openclaw
docker compose run --rm openclaw-cli pairing approve telegram X9R7EQRR


docker ps | grep openclaw
4df4d51c2114   openclaw:local                           "docker-entrypoint.s…"   39 minutes ago   Up 35 minutes   0.0.0.0:18789-18790->18789-18790/tcp, [::]:18789-18790->18789-18790/tcp   openclaw-openclaw-gateway-1

docker exec -it openclaw-openclaw-gateway-1 openclaw status 
docker exec -it openclaw-openclaw-gateway-1 openclaw gateway status 
docker exec -it openclaw-openclaw-gateway-1 openclaw config get   
docker exec -it openclaw-openclaw-gateway-1 openclaw config schema
docker exec -it openclaw-openclaw-gateway-1 openclaw token        



1. Install OpenClaw CLI on Host (Recommended—proxies to Docker gateway)

Bash
curl -sSf https://get.openclaw.ai | bash  # Installs ~/.openclaw/bin/openclaw
export PATH=$PATH:~/.openclaw/bin         # Or add to ~/.bashrc
openclaw status                           # Now works! Proxies to Docker gateway
openclaw gateway status
openclaw config get
openclaw token                            # Fresh UI token

• Host CLI auto-detects Docker gateway. Magic.


nslookup get.openclaw.ai 8.8.8.8
curl --dns-servers 8.8.8.8 -sSf https://get.openclaw.ai | bash
