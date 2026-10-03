# claw-mac

A starter guide for setting up a new Mac for development, productivity, AI tools,
and remote workflows. Complete the base setup, then install the applications and
integrations needed for the device's role.

Commands assume an Apple Silicon Mac using zsh. Replace placeholders before
running them, and review existing shell and SSH configuration before adding lines.
Keep credentials, SSH keys, host addresses, OAuth files, browser profiles, personal
data, and diagnostic logs outside this repository.

## Before you start

- Complete macOS setup and install available system updates.
- Choose the local account that will own development files and run tools.
- Set a recognizable computer name and connect to the intended network.
- Decide whether the Mac will be an interactive workstation, an always-on host,
  or both; use that choice when configuring remote access and power settings.

## Homebrew and shell setup

Install the Xcode Command Line Tools if they are missing, and wait for the
installation dialog to finish:

```sh
xcode-select --install
```

If full Xcode is needed, install it from the App Store and complete its first-run
setup. Check which developer directory is active:

```sh
xcode-select -p
```

The result should point to the Command Line Tools or the intended Xcode
installation before you continue.

Install Homebrew and initialize it in the login shell:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv zsh)"
```

Add the `brew shellenv` line only once. Open a fresh terminal and confirm
`brew --version` works. If you will use the automation tools below, add Peter
Steinberger's tap:

```sh
brew tap steipete/tap
```

## Applications

Choose the apps needed for this device; this list is a menu, not a requirement to
install everything. Sign in and open each selected app once to complete setup.

### Browser, productivity, and communication

- [Chrome](https://www.google.com/chrome) with the [AdGuard extension](https://chromewebstore.google.com/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg)
- Google Drive, Google Docs, Google Sheets, and Google Slides
- Office and OneDrive Business (App Store)
- [Obsidian](https://obsidian.md)
- [Telegram](https://apps.apple.com/de/app/telegram/id747648890?l=en-GB&mt=12) (App Store)
- [WhatsApp](https://apps.apple.com/de/app/whatsapp-messenger/id310633997?l=en-GB) (App Store)

### Development and AI

- [Xcode](https://apps.apple.com/de/app/xcode/id497799835?l=en-GB&mt=12) (App Store)
- [VS Code](https://code.visualstudio.com)
- [cmux](https://github.com/manaflow-ai/cmux/releases/latest/download/cmux-macos.dmg), a Ghostty-based terminal
- Antigravity
- ChatGPT and [Codex Desktop](https://openai.com/codex)
- [Claude Desktop and Cowork](https://claude.com/product/overview)
- Grok Bot
- [LM Studio](https://lmstudio.ai); choose local models to fit the device's memory and intended tasks
- [Blender](https://www.blender.org)

### Remote access and utilities

- [Tailscale](https://apps.apple.com/de/app/tailscale/id1475387142?l=en-GB&mt=12) (App Store)
- [Windows App](https://apps.apple.com/de/app/windows-app/id1295203466?l=en-GB&mt=12) for Remote Desktop (App Store)
- NVIDIA Sync
- [Coca](https://apps.apple.com/de/app/coca/id1000808993?l=en-GB&mt=12) (App Store)
- [DaisyDisk](https://daisydiskapp.com) or [Disk Inventory X](https://www.derlien.com)
- Blackmagic Disk Speed Test
- [OnyX](https://www.titanium-software.fr/en/onyx.html); see [power and desktop settings](#power-and-desktop-settings) for App Nap

## Development tools

### Node and Python

```sh
brew install node python uv
```

Use each project's runtime requirements when choosing Node and Python versions.
Keep Python dependencies in a project environment rather than installing them
into the system interpreter.

If a project uses pyenv, install it and complete its shell initialization before
selecting a version:

```sh
brew install pyenv
pyenv install "<python-version>"
# Run inside the project directory:
pyenv local "<python-version>"
```

Verify `node --version`, `npm --version`, `python3 --version`, and `uv --version`.
For pyenv projects, also check `pyenv version` and `command -v python` in a fresh
shell. Homebrew Python and pyenv are separate installations.

### Git and GitHub

```sh
brew install git-lfs gh gitleaks
git lfs install
git config --global user.name "<NAME>"
git config --global user.email "<EMAIL>"
mkdir -p ~/git
gh auth login
gh auth setup-git
```

This sets up Git LFS filters and the GitHub credential helper. Authenticate
separately on each new Mac, then use `gh auth status` and clone a repository to
verify access. Keep authentication files out of Git.

### Azure

```sh
brew install azure-cli
az login
```

### AI command-line tools

```sh
npm install -g @openai/codex
npm install -g @google/gemini-cli
npm install -g @anthropic-ai/claude-code
```

Install only the CLI tools you intend to use, complete their sign-in flows, and
verify their version commands in a fresh terminal.

If using Grok CLI, follow its installer first. For an installation under
`$HOME/.grok` that provides zsh completions, add the following to `~/.zshrc` once:

```sh
export PATH="$HOME/.grok/bin:$PATH"
fpath=(~/.grok/completions/zsh $fpath)
autoload -Uz compinit && compinit -C
```

### VS Code extensions

Install extensions for the workflows needed on the machine:

- Remote SSH, Remote Explorer, Remote Tunnels, WSL, and Dev Containers.
- Python, Pylance, Python environments, debugging, isort, Jupyter, and Data Wrangler.
- C# / .NET, C/C++, Go, Java / Maven / Gradle, Swift, PowerShell, and AppleScript / JXA.
- Azure resources, CLI, Functions, App Service, Storage, Cosmos DB, virtual machines,
  Static Web Apps, Azure MCP, Terraform, Azure Pipelines, Docker, and Kubernetes.
- GitHub Copilot Chat, GitHub Actions, Codex, Claude Code, and the Gemini CLI companion.
- ESLint, Prettier, Oxc, Angular, YAML, XML, JSON, Markdown, CSV, Parquet, SQLite,
  SQL Server, Git History, Live Share, Live Server, Repomix, and VS Code icons.

For migration from another computer, export its active extension list with
`code --list-extensions` and review it against the new device's workflows. Install
the `code` command in PATH from VS Code's Command Palette before using CLI checks.

## Account logins

Sign in on each machine as needed:

- [Azure](https://portal.azure.com)
- [Office 365](https://portal.office.com/account)
- [Google Cloud](https://console.cloud.google.com)
- [GitHub](https://github.com)
- [X / xAI](https://x.com)
- [OpenAI](https://chatgpt.com)
- [Anthropic](https://claude.ai) (optional)

## OpenClaw and automation tools

### OpenClaw

Follow the [OpenClaw CLI setup](https://docs.openclaw.ai/start/getting-started):

```sh
curl -fsSL https://openclaw.ai/install.sh | bash
```

The [OpenClaw macOS app](https://github.com/openclaw/openclaw/releases) is optional
(ARM64 DMG). Complete the tool's onboarding on this device and verify a small
workflow before relying on it for automation.

### Gmail and Calendar

A Google Cloud account and project are required. In the
[GCP Console](https://console.cloud.google.com/auth/clients), choose **Create
Client**, select **Desktop app**, and download the OAuth client JSON locally.

```sh
brew install steipete/tap/gogcli
gog auth credentials ~/Downloads/client_secret_....json
gog auth add you@gmail.com
gog calendar list
```

### Peekaboo

```sh
brew install steipete/tap/peekaboo
```

In **System Settings → Privacy & Security → Screen & System Recording**, configure
permissions for `/opt/homebrew/bin/peekaboo` and the terminal used to run it.

### WhatsApp CLI

```sh
brew install steipete/tap/wacli
wacli
```

Log in using the QR code; see the [wacli instructions](https://github.com/steipete/wacli).

### Summarize, MCP, and Oracle

```sh
brew install steipete/tap/summarize
brew install steipete/tap/mcporter
brew install steipete/tap/oracle
```

## Remote access

### SSH

1. On each destination Mac, enable **System Settings → General → Sharing → Remote
   Login** and allow only the intended local account. Enable **Allow full disk
   access for remote users** if the intended workflows require it.
2. Give each source computer its own SSH key pair. Keep private keys on their
   originating computers and append only public keys to the destination account's
   `~/.ssh/authorized_keys`, preserving existing entries.
3. Set permissions to `700` for `~/.ssh` and `600` for private keys and
   `authorized_keys`. Back up existing SSH configuration before editing it.
4. Define a destination alias in the source computer's `~/.ssh/config`:

   ```sshconfig
   Host destination
       HostName <LAN-address>
       User <short-username>
       IdentityFile ~/.ssh/<private-key-file>
       IdentitiesOnly yes
       StrictHostKeyChecking yes
       ForwardAgent no
   ```

5. Verify the destination's server host key through an independent trusted
   connection before adding it to the source computer's `~/.ssh/known_hosts`.
6. Test key-based access without allowing a password fallback:

   ```sh
   ssh -o BatchMode=yes -o PasswordAuthentication=no \
       -o KbdInteractiveAuthentication=no destination 'hostname; whoami'
   ```

For access between several computers, repeat the public-key authorization and
host-key verification for each required direction. Access from one computer to
another does not automatically grant access in reverse. Verify each direction
from its actual source computer.

Use consistent aliases across machines, for example:

```sh
ssh mac-studio
ssh mac-mini
ssh dgx-spark
ssh giga
```

A dedicated key such as `~/.ssh/id_ed25519_interconnect` can separate this access
from other SSH uses. To keep peer host keys in a separate file, configure
`UserKnownHostsFile ~/.ssh/known_hosts_interconnect` for those aliases. Keep
addresses, account details, key material, and backups outside this repository.

### Screen Sharing and Remote Management

Configure desktop access under **System Settings → General → Sharing** and
restrict it to the intended local accounts. If **Remote Management** controls
Screen Sharing, grant **Observe** and **Control** to accounts that need to view
and operate the desktop; leave other management privileges off unless needed.

If the service is reachable but login fails, check the allowed accounts and their
permissions as well as the credentials. Verify access with a real Screen Sharing
login and desktop interaction; a listening VNC port alone does not prove that
remote desktop access works. Verify SSH separately.

### Screen Sharing watchdog (optional)

For a Mac that relies on remote desktop access, `scsh-watchdog` can recover from
persistent dead desktop-agent errors
or repeated local VNC greeting failures. It restarts affected Screen Sharing
services, disconnecting active sharing sessions without rebooting or logging
users out.

| Component | Location or behavior |
| --- | --- |
| LaunchDaemon | `/Library/LaunchDaemons/local.scsh-watchdog.plist` |
| Schedule | At boot and every 60 seconds |
| Interpreter | `/usr/bin/python3 -I` |
| Installed program | `/Library/PrivilegedHelperTools/scsh-watchdog/watchdog.py` |
| Log | `/var/log/scsh-watchdog.log` |
| Private state | `/var/db/scsh-watchdog/` |

Install or update through the project's reviewed installer after Screen Sharing
works. The root job must execute an installed, root-owned copy, not a
user-writable checkout. Verify the installed job and its recent log locally;
keep incident logs private.

## Power and desktop settings

Configure these for the device's role rather than copying another Mac's values:

- For an always-on host, prevent automatic system sleep while connected to power
  and enable wake for network access where supported.
- Choose a display sleep timeout independently of system sleep; remote work does
  not require leaving a physical display lit.
- Decide whether automatic restart after a power failure is appropriate for the
  host, and plan how it will become accessible again after restarting.
- Review energy-saving options for an interactive or portable Mac according to
  how it will be used.
- If a particular background workflow requires App Nap to be disabled, configure
  it deliberately using the appropriate tool, such as OnyX.
- Enable **Show all filename extensions** in Finder for development work.

Inspect the resulting power configuration with:

```sh
pmset -g custom
```

## Verify the new device

- Open a fresh terminal and check Homebrew, Git, and the selected runtime tools.
- Clone a real project into `~/git`, install its dependencies, and run its normal
  build or checks.
- Complete the selected apps' sign-ins and verify one small workflow in each.
- Test SSH from every computer that needs access, and test a real remote desktop
  session if Screen Sharing is enabled.
- For browser or desktop automation, grant the required permissions to the actual
  executable and test from the context that will run it. SSH and a logged-in GUI
  session can have different access.
- Configure a backup destination and verify that a sample file can be restored.
- Before relying on unattended operation, perform a planned restart and verify
  that the required access and applications can be restored.

Document reusable setup improvements here. Keep device-specific configuration,
private authentication, and workload deployment instructions with their own
local configuration or project documentation.
