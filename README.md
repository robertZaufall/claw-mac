# claw-mac

Installations steps

## Basic
- [Chrome](https://www.google.com/chrome) + [AdGuard extension](https://chromewebstore.google.com/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg)  
- [XCode](https://apps.apple.com/de/app/xcode/id497799835?l=en-GB&mt=12) (App Store)
- [Tailscale](https://apps.apple.com/de/app/tailscale/id1475387142?l=en-GB&mt=12) (App Store)
- [Telegram](https://apps.apple.com/de/app/telegram/id747648890?l=en-GB&mt=12) (AppStore)
- [WhatsApp](https://apps.apple.com/de/app/whatsapp-messenger/id310633997?l=en-GB) (AppStore)  
- [Coca](https://apps.apple.com/de/app/coca/id1000808993?l=en-GB&mt=12) (App Store)
- [Windows App (App Store)](https://apps.apple.com/de/app/windows-app/id1295203466?l=en-GB&mt=12) - Remote Desktop  
- Office + OneDrive Business (App Store)

- [VSCode](https://code.visualstudio.com)  
- [Obisdian](https://obsidian.md)  
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
- [OpenClaw MacOS-App](https://github.com/openclaw/openclaw/releases) (ARM64 dmg)
- HomeBrew tap for Peter Steinberger Cli Tools
```
brew tap steipete/tap
```

### Gmail (gws-cli or gog-cli) -> Google Cloud Account + project needed!  
  
- GCP (Google Cloud Platform) setup  
Go to [GCP Console](https://console.cloud.google.com/auth/clients)  
Click "Create Client"  
Application type: "Desktop app"  
Download the JSON file (usually named client_secret_....apps.googleusercontent.com.json)  
  
- Recommended: gws (Google)  
```
brew install googleworkspace-cli
gws auth setup     # walks you through Google Cloud project config
gws auth login     # subsequent OAuth login
```
  
- Alternative: gog (Peter Steinberger)  
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
Set system permissions (System Settings -> Privacy & Security -> Screen & System Recording
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

