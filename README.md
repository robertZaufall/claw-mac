# claw-mac

Installations steps

## Basic
- Chrome
- AdGuard
- XCode (App Store)
- Tailscale (App Store)
- Coca (App Store)
- Office + OneDrive (App Store)

- VSCode (https://code.visualstudio.com)  
- DaisyDisk (https://daisydiskapp.com) or Disk Inventory X (https://www.derlien.com)    
- Onyx (https://www.titanium-software.fr/en/onyx.html) (switch on "don't use app nap")  
- Blender (https://www.blender.org)  

## Homebrew (app repository)
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo >> /Users/master/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> /Users/master/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv zsh)"
```

## Logins (Browser)  
- Azure (https://portal.azure.com)
- Office365 (https://portal.office.com/account)  
- Google Cloud
- Amazon Shop
- GitHub
- X / xAI
- OpenAI
- Anthropic (optional)  

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
- Codex-Desktop (https://openai.com/codex)  
- Codex-Cli `npm install -g @openai/codex`  
- Gemini-Cli `npm install -g @google/gemini-cli`  
- Claude-Cli `npm install -g @anthropic-ai/claude-code`  
- Claude-Desktop + Cowork (https://claude.com/product/overview)   

## OpenClaw
- OpenClaw Cli (https://docs.openclaw.ai/start/getting-started)  
```
curl -fsSL https://openclaw.ai/install.sh | bash
```
- OpenClaw MacOS-App from https://github.com/openclaw/openclaw/releases (ARM64 dmg)
- HomeBrew tap for Peter Steinberger Cli Tools
```
brew tap steipete/tap
```

### Gmail (gog-cli or gws-cli) - Google Cloud Account needed 
- Installation on GCP (Google Cloud Platform)
Go to https://console.cloud.google.com/auth/clients  
Click "Create Client"  
Application type: "Desktop app"  
Download the JSON file (usually named client_secret_....apps.googleusercontent.com.json)  

- gog (Peter Steinberger)  
```
brew install steipete/tap/gogcli
gog auth credentials ~/Downloads/client_secret_....json
gog auth add you@gmail.com
gog calendar list
```
- gws (Google)  
```
brew install googleworkspace-cli
gws auth setup     # walks you through Google Cloud project config
gws auth login     # subsequent OAuth login
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
Login using 

### Other tools (Summarize, MCP-Cli, Oracle for OpenAI Pro Model)
```
brew install steipete/tap/summarize
brew install steipete/tap/mcporter
brew install steipete/tap/oracle
```

