# claw-mac

Installations steps

## Basic
Chrome
XCode

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
