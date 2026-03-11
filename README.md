# claw-mac

Installations steps

## Basic
Chrome, AdGuard
XCode
Tailscale

Blender  
VSCode  

DaisyDisk  
Onyx (switch on "don't use app nap")  
Coca  

## Logins
- Azure + Office365
- Google Cloud
- Amazon Shop
- GitHub
- OpenAI
- Anthropic
- xAI

## Homebrew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo >> /Users/master/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> /Users/master/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv zsh)"
```
Azure  
```
brew install azure-cli
az login
```

## Node + Python
```
brew install node
brew install python
brew install pyenv
pyenv install 3.12
pyenv global 3.12
brew install uv
```

## Git
```
brew install git-lfs
git lfs install
git config --global user.name Rob
git config --global user.email "mail@zaufall.de"
mkdir git
```

## MS + Office
https://portal.azure.com  
https://portal.office.com/account  
Office  

## AI
Codex-Desktop  
Codex-Cli  
```
npm install -g @openai/codex
```

Claude-Desktop  
Claude-Cli  
```
npm install -g @anthropic-ai/claude-code
```

Gemini-Cli
```
npm install -g @google/gemini-cli
```

## OpenClaw
```
brew tap steipete/tap
```
```
brew install steipete/tap/gogcli
```
Go to https://console.cloud.google.com/auth/clients  
Click "Create Client"  
Application type: "Desktop app"  
Download the JSON file (usually named client_secret_....apps.googleusercontent.com.json)  
```
gog auth credentials ~/Downloads/client_secret_....json
gog auth add you@gmail.com
gog calendar list
```
```
brew install steipete/tap/peekaboo  
/opt/homebrew/bin/peekaboo + terminal.app
```
```
brew install steipete/tap/wacli
wacli
```
```
brew install steipete/tap/summarize
brew install steipete/tap/mcporter
brew install steipete/tap/oracle
```
