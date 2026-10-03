# claw-mac

Installation steps

## Basic
- [Chrome](https://www.google.com/chrome) + [AdGuard extension](https://chromewebstore.google.com/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg)  
- [XCode](https://apps.apple.com/de/app/xcode/id497799835?l=en-GB&mt=12) (App Store)
- [cmux](https://github.com/manaflow-ai/cmux/releases/latest/download/cmux-macos.dmg) (Download dmg) - Ghostty-based Terminal
- [Tailscale](https://apps.apple.com/de/app/tailscale/id1475387142?l=en-GB&mt=12) (App Store)
- [Telegram](https://apps.apple.com/de/app/telegram/id747648890?l=en-GB&mt=12) (AppStore)
- [WhatsApp](https://apps.apple.com/de/app/whatsapp-messenger/id310633997?l=en-GB) (AppStore)  
- [Coca](https://apps.apple.com/de/app/coca/id1000808993?l=en-GB&mt=12) (App Store)
- [Windows App (App Store)](https://apps.apple.com/de/app/windows-app/id1295203466?l=en-GB&mt=12) - Remote Desktop  
- Office + OneDrive Business (App Store)

- [VSCode](https://code.visualstudio.com)  
- [Obsidian](https://obsidian.md)
- [LMStudio](https://lmstudio.ai) + `Supergemma4 26B Uncensored v2` model (14.23 GB)
- [DaisyDisk](https://daisydiskapp.com) or [Disk Inventory X](https://www.derlien.com)    
- [Onyx](https://www.titanium-software.fr/en/onyx.html) (switch on: "don't use app nap")  
- [Blender](https://www.blender.org)  

## Homebrew (app repository)
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo >> /Users/master/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> /Users/master/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv zsh)"
```

## Logins (Browser)  
- [Azure](https://portal.azure.com)
- [Office365](https://portal.office.com/account)  
- [Google Cloud](https://console.cloud.google.com)
- [GitHub](https://github.com)
- [X / xAI](https://x.com)
- [OpenAI](https://chatgpt.com)
- [Anthropic](https://claude.ai) (optional)  

## Cli + Dev apps
### Azure  
```
brew install azure-cli
az login
```

### Node + Python
```
brew install node
brew install python
brew install pyenv
pyenv install 3.12
pyenv global 3.12
brew install uv
```

### Git
```
brew install git-lfs
git lfs install
git config --global user.name <NAME>
git config --global user.email <EMAIL>
mkdir git
```

### AI
- [Codex-Desktop](https://openai.com/codex)  
- Codex-Cli `npm install -g @openai/codex`  
- Gemini-Cli `npm install -g @google/gemini-cli`  
- Claude-Cli `npm install -g @anthropic-ai/claude-code`  
- [Claude-Desktop + Cowork](https://claude.com/product/overview)   

## OpenClaw
- [OpenClaw Cli](https://docs.openclaw.ai/start/getting-started)  
```
curl -fsSL https://openclaw.ai/install.sh | bash
```

- HomeBrew tap for Peter Steinberger Cli Tools
```
brew tap steipete/tap
```

Optional:  
- [OpenClaw MacOS-App](https://github.com/openclaw/openclaw/releases) (ARM64 dmg)

### Gmail (Google Cloud account + project needed)
  
- GCP (Google Cloud Platform) setup  
Go to [GCP Console](https://console.cloud.google.com/auth/clients)  
Click "Create Client"  
Application type: "Desktop app"  
Download the JSON file (usually named client_secret_....apps.googleusercontent.com.json)  
  
- gog-cli (Peter Steinberger)  
```
brew install steipete/tap/gogcli
gog auth credentials ~/Downloads/client_secret_....json
gog auth add you@gmail.com
gog calendar list
```
  
### peekaboo (Screenshotter)
```
brew install steipete/tap/peekaboo  
```
Set system permissions (System Settings -> Privacy & Security -> Screen & System Recording)
- /opt/homebrew/bin/peekaboo
- terminal.app
  
### WhatsApp
```
brew install steipete/tap/wacli
wacli
```
Login using QR code (more on https://github.com/steipete/wacli)

### Other tools (Summarize, MCP-Cli, Oracle for OpenAI Pro Model)
```
brew install steipete/tap/summarize
brew install steipete/tap/mcporter
brew install steipete/tap/oracle
```


## Additional Mac Mini setup (checked 2026-10-04)

This section records a read-only inspection of the existing Mac Mini. It is an
installation reference, not a full backup or a claim that every item above is
installed. Account identities, host addresses, SSH keys, tokens, OAuth files,
browser profiles, private data, and diagnostic logs are intentionally omitted.
Use placeholders below for machine-specific values and keep credentials outside
this repository.

### Additional applications

The following applications were present in `/Applications` in addition to the
items already listed above:

- Antigravity
- Blackmagic Disk Speed Test
- ChatGPT
- Google Drive, Google Docs, Google Sheets, and Google Slides
- Grok Bot
- NVIDIA Sync

The inspected system was Apple Silicon, running macOS 27.0.1. Xcode was present,
but the active developer directory was `/Library/Developer/CommandLineTools`.
Check `xcode-select -p` before assuming full Xcode is selected.

### Additional command-line tools and runtime details

```sh
brew install gh gitleaks
```

- `gh` is configured as the Git credential helper for GitHub and Gist. Authenticate
  separately on a new machine with `gh auth login`, then use `gh auth setup-git`.
  Do not copy authentication files into this repository.
- Git LFS filters are configured globally, in addition to the Git author settings.
- Homebrew Node was **v25.8.0**, and Homebrew Python was **3.14.3**.
- pyenv's selected Python was **3.12.13**. This is separate from Homebrew Python;
  a selected pyenv version does not prove every shell uses its shims.
- The scheduled exporters use **Node v25.2.1** at
  `$HOME/.nvm/versions/node/v25.2.1/bin/node`. The directory exists, but
  `$HOME/.nvm/nvm.sh` was absent. Do not assume a complete nvm installation or
  replace the job interpreter with Homebrew Node without checking compatibility.
- The Homebrew npm prefix contained `@openai/codex` **0.156.0** and
  `@google/gemini-cli` **0.33.0**. It also contained the package `i` **0.3.7**;
  its purpose was not established, so it is not an installation requirement.
- Grok has a separate executable at `$HOME/.grok/bin/grok`. The zsh setup adds
  `$HOME/.grok/bin` to `PATH`, adds `$HOME/.grok/completions/zsh` to `fpath`,
  and runs `autoload -Uz compinit && compinit -C`.
- `.zprofile` initializes Homebrew with `brew shellenv`.
- A `collectors` command exists in `$HOME/.local/bin` for Collector Control.
- No Homebrew services were listed. Scheduled exporter jobs use launchd instead.

The Homebrew inventory included `azure-cli`, `gh`, `git-lfs`, `gitleaks`,
`gogcli`, `node`, `pyenv`, `python@3.14`, `summarize`, `uv`, and `wacli`, with
`steipete/tap` configured. The earlier OpenClaw section remains setup guidance:
no `$HOME/.openclaw/openclaw.json` was found in this inspection.

### VS Code extensions

The extension directory contained tooling for:

- Remote SSH, Remote Explorer, Remote Tunnels, WSL, and Dev Containers.
- Python, Pylance, Python environments, debugging, isort, Jupyter, and Data Wrangler.
- C# / .NET, C/C++, Go, Java / Maven / Gradle, Swift, PowerShell, and AppleScript / JXA.
- Azure resources, CLI, Functions, App Service, Storage, Cosmos DB, virtual machines,
  Static Web Apps, Azure MCP, Terraform, Azure Pipelines, Docker, and Kubernetes.
- GitHub Copilot Chat, GitHub Actions, Codex, Claude Code, and the Gemini CLI companion.
- ESLint, Prettier, Oxc, Angular, YAML, XML, JSON, Markdown, CSV, Parquet, SQLite,
  SQL Server, Git History, Live Share, Live Server, Repomix, and VS Code icons.

Some extension directories contain multiple versions; their presence does not
prove which version is active. For a deliberate migration, export the active
list with `code --list-extensions` and review it before installing on the new Mac.

### Background exporter schedules

Seven user LaunchAgents were installed and loaded in the logged-in user's GUI
session. All had a last recorded exit code of `0` when inspected. This confirms
job completion status, not freshness or correctness of their remote outputs.

| Exporter | Schedule | Run when loaded |
| --- | --- | --- |
| aport | Every 3,600 seconds | Yes |
| gport | Every 900 seconds | Yes |
| hport | Every 900 seconds | Yes |
| lport | Every 900 seconds | Yes |
| wport | Every 3,600 seconds | No |
| xport | Every 900 seconds | Yes |
| yport | 06:20 and 18:20 in the host's local timezone | Yes |

The plists live in `~/Library/LaunchAgents`; working directories are under
`~/git/<exporter>`, with stdout and stderr logs under `~/Library/Logs`.
They use the explicit Node v25.2.1 path above. On another machine, regenerate
plists for the destination account and install each exporter's dependencies and
private configuration separately. Do not start duplicate production schedules
as part of initial machine setup.

These jobs run briefly and normally show `not running` between scheduled runs.
Inspect the specific job with:

```sh
launchctl print "gui/$(id -u)/<job-label>"
```

Browser- or Keychain-dependent jobs need verification in their actual GUI
LaunchAgent context; an SSH session can have different access. Grant only the
permissions required by each tool to its actual executable. Do not put cookies,
Keychain exports, or personal result files into Git.

### Remote access and Screen Sharing recovery

Remote Login (`com.openssh.sshd`) and Screen Sharing
(`com.apple.screensharing`) were loaded, and SSH access was verified. The macOS
application firewall was enabled.

A separate `scsh-watchdog` installation monitors Screen Sharing:

- LaunchDaemon: `/Library/LaunchDaemons/local.scsh-watchdog.plist`.
- Runs at boot and every 60 seconds through `/usr/bin/python3 -I`.
- Installed program:
  `/Library/PrivilegedHelperTools/scsh-watchdog/watchdog.py`.
- Logs: `/var/log/scsh-watchdog.log`; private state: `/var/db/scsh-watchdog/`.
- Detects persistent dead desktop-agent errors or repeated local VNC greeting
  failures, then restarts affected Screen Sharing services. Recovery disconnects
  active Screen Sharing sessions; it does not reboot or log users out.
- The job was loaded with last exit code `0`. No recovery was triggered for this
  inspection, and a full remote desktop session was not tested.

Install or update it using its own reviewed installer; the root job runs an
installed, root-owned copy, not the user-writable checkout. Keep its incident
logs private.

### Power and desktop settings

Observed AC power settings suitable for an always-on host:

| Setting | Observed value |
| --- | --- |
| System sleep | Disabled (`sleep 0`) |
| Display sleep | Disabled (`displaysleep 0`) |
| Disk sleep | 10 minutes |
| Standby | Disabled |
| Wake on network access | Enabled (`womp 1`) |
| Power Nap | Enabled |
| TCP keepalive | Enabled |
| Keep awake for active terminal sessions | Enabled (`ttyskeepawake 1`) |
| Low Power Mode | Disabled |
| Automatic restart after power failure (`autorestart`) | Disabled |

These are observed settings, not a blanket instruction to apply every value.
`NSAppSleepDisabled` was enabled, matching the App Nap note above. Finder was
configured to show all filename extensions.

### SSH setup for another Mac

1. On the destination, enable **System Settings → General → Sharing → Remote
   Login** and allow the intended local account.
2. Keep the source private key on the source computer. Add only its public key
   to the destination account's `~/.ssh/authorized_keys`; preserve existing keys.
3. Use permissions `700` for `~/.ssh` and `600` for `authorized_keys`.
4. Put the destination's private address and username in the source computer's
   `~/.ssh/config`, outside this repository:

   ```sshconfig
   Host mac-studio
       HostName <LAN-address>
       User <short-username>
       IdentityFile ~/.ssh/<private-key-file>
       IdentitiesOnly yes
   ```

5. Verify the destination host key and test unattended access:

   ```sh
   ssh -o BatchMode=yes mac-studio 'sw_vers; uname -m'
   ```

Never copy private SSH keys, passwords, or host-specific access inventories into
this document. SSH setup alone does not migrate applications or production jobs.

### Mac Studio access setup (checked 2026-10-04)

- Remote Management is restricted to the intended local account, with **Observe**
  and **Control** enabled and other management privileges disabled. A real Screen
  Sharing reconnection succeeded after correcting those permissions. A listening
  VNC port alone had not established that the account could authenticate.
- Remote Login is enabled for the intended account only. **Allow full disk access
  for remote users** is enabled at the user's request. The source computer's
  public key was added while preserving existing authorized keys; directory/file
  permissions are `700` / `600`.
- The source computer has a local `mac-studio` SSH alias. The server's ED25519
  host key was verified against the independently connected Studio session before
  saving local host trust. `ssh -o BatchMode=yes mac-studio` succeeded.
- Machine addresses, host-key material, account passwords, and SSH configuration
  remain outside this repository.

### SSH between the four hosts (checked 2026-10-04)

The Mac Studio, Mac Mini, DGX Spark, and Gigabyte AI TOP ATOM can each SSH to
the other three using the existing local account and public-key authentication.
All **12 directed connections** were verified with `BatchMode=yes` and password
and keyboard-interactive authentication disabled.

Use the destination alias from any of the other three hosts:

```sh
ssh mac-studio
ssh mac-mini
ssh dgx-spark
ssh giga
```

- Each host has its own `~/.ssh/id_ed25519_interconnect` key pair. Private keys
  stay on their originating hosts; only public keys were distributed.
- LAN destinations and account details live in each host's private SSH config.
  Existing configuration and authorized keys were preserved, with local backups.
- Server public keys were collected through existing trusted connections and
  pinned in `~/.ssh/known_hosts_interconnect`; strict host-key checking is enabled.
- Agent forwarding is disabled for these aliases. Existing passwords were not
  changed or saved by this setup. No password is needed for these connections.
