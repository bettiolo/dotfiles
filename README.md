# dotfiles

## Initial setup

- Update OS
- Install Xcode
- Run Xcode and accept T&C
- Install latest Command Line Tools from https://developer.apple.com/download/all/?q=command%20line%20tools
- Enable latest Command Line Tools
  ```bash
  sudo xcode-select -switch /Library/Developer/CommandLineTools
  ```
- Install `brew`
  ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
- Configure `ssh`
  ```bash
  ssh-keygen -t ed25519 -C "marco@bettiolo.it"
  eval "$(ssh-agent -s)"
  ssh-add --apple-use-keychain ~/.ssh/id_ed25519
  pbcopy < ~/.ssh/id_ed25519.pub
  ```
- Add ssh key to GitHub: https://github.com/settings/ssh/new
- Edit `~/.ssh/config`
  ```
  Host *.github.com
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/id_ed25519
  ```
- Install `git` and clone this repo
  ```bash
  brew install git &&
  mkdir -p ~/Code/bettiolo &&
  cd ~/Code/bettiolo &&
  git clone git@github.com:bettiolo/dotfiles.git &&
  cd dotfiles
  ```

## Configure MacOS

Run [`setup-macos.sh`](./setup-macos.sh)

## Configure Finder

- View > Show View Options > Configure settings and click "Use as Defaults"
- Settings > Sidebar > Enable / Disable shortcuts

## Configure Safari

- View > Show Status Bar
- Settings > General > Safari opens with: All windows from last session
- Settings > Tabs > Tab layout: Compact
- Settings > Tabs > X Always show website title in tabs
- Settings > Advanced > Smart Search Field: X Show full website address
- Settings > Advanced > X Show Develop menu in menu bar

## Steps

Add Accounts: System Settins -> Internet Accounts

```bash
open -b com.apple.systempreferences /System/Library/PreferencePanes/InternetAccounts.prefPane
```

```bash

# Install cli tools
brew install \
 micro `# command line text editor`  \
 fnm `# fast node version manager` \
 htop `# fancy top` \
 glances `# fancy system monitor` \
 exa `# replacement for ls` \
 httpie `# better ux than curl` \
 dog `# better ux than dig` \
 dust `# replacement for du` \
 duf `# replacement for df` \
 lazygit `# command line git ui` \
 fd `# simple find` \
 gping `# ping with a graph` \
 figlet `# generates big console text` \

# Install apps
brew install \
 iterm2 \
 smartgit \
 google-chrome \
 visual-studio-code \
 webstorm \
 discord
```

# Install shell customisations

```bash
# Install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install powerlevel10k theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# Install zsh plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
# TODO: review zsh-completions
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
```

# Configure `.zshrc`

```
export ZSH="$HOME/.oh-my-zsh"
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src # before `source "$ZSH/oh-my-zsh.sh"`
ZSH_THEME="powerlevel10k/powerlevel10k"
COMPLETION_WAITING_DOTS="true"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

source $ZSH/oh-my-zsh.sh
eval "$(fnm env --use-on-cd)"

export EDITOR='micro' # set micro as default text editor
alias ll="exa -la --git --icons --colour-scale"
alias l="exa -la --git --icons --colour-scale --no-user --no-time --no-permissions
```

# Configure iTerm2

- Blinking Cursor: Settings -> Profiles -> Text -> X Blinking cursor
- Colors: Settings -> Profiles -> Colors -> Color Preset -> Tango Dark
- Keyboard (Micro editor): Settings -> Profiles -> Keys -> General -> Left Option Key -> Esc+
- Keyboard (Word jump delete with Option key): Settings → Profiles → Keys → Key mappings → Presets... → Natural Text Editing

# Configure MacOS

- Settings > Apple ID > iCloud > Private Relay > Enable
- Settings > Apple ID > iCloud > iCloud Drive > Apps Syncing to iCloud Drive > X Desktop & Documents Folders
- Settings > Displays > Night Shift > Schedule: Sunset to Sunrise
- Settings > Displays > Night Shift > Color temperature: Few clicks to the left
- Settings > Displays > More Space
- Settings > Battery > Low power mode: Only on Battery
- Settings > Lock Screen > Turn display off on battery: 10 minutes
- Settings > Lock Screen > Turn display off on power: 1 hour
- Settings > Lock Screen > Require password after: 5 seconds
- Settings > Keyboard > Keyboard navigation: Enabled
- Settings > Keyboard > Turn Keyboard backlight off after inactivity: After 5 minutes
- Settings > Keyboard > Keyboard Shortcuts... > Function Keys > Use F1, F2, etc. keys as standard function keys: Enabled
- Settings > Keyboard > Text input > Edit ... > Correct spelling automatically: Disabled
- Settings > Keyboard > Text input > Edit ... > Capitalise words automatically: Disabled
- Settings > Trackpad > Tracking Speed: 1 notch from the right
- Settings > Trackpad > Force Click: Disable
- Settings > Trackpad > Look up: Disable
- Settings > Trackpad > Tap to click: Enable
- Settings > Trackpad > Click: Light
- Settings > Trackpad > More Gestures > App Expose: Swipe Down with Three Fingers
- Settings > Trackpad > More Gestures > Launchpad: Disable
- Settings > Notifications > Disable all "Allow notification when ..."

# App Store

- Maccy
- Hand Mirror
- OTP Auth
- Magnet

- Messenger
- Telegram
- WhatsApp
- Slack

- Next Meeting
- Agenda?
- Structured?

- Adguard
- HushNagBlocker
- Super Agent

# Pick one

- iStatsMenu (App Store)
- MenuBar Stats (App Store)
- `stats`

# DB Tools

- `tableplus`
- `sequel-pro`
- `studio-3t`

# Docker tools

- `ctop` like `top` for containers

# Configure `micro`

TODO: Enable editorconfig or `"tabstospaces": true` ?

# Install VS Code extensions:

- Error Lens
- Gitlens
- Todo Highlight
- Prettier
- VSCode icons
- ESLint
- EditorConfig

# Confgiure VS Code

Edit `settings.json`

```bash
"editor.fontFamily": "MesloLGS NF",
"editor.defaultFormatter": "esbenp.prettier-vscode",
"editor.formatOnSave": true,
```

# TODO

- ? `direnv` to have per folder `.envrc`
- ? `zoxide` a smarter `cd`
- ? `z` cli tool for frequently used folders
- ? `autojump` db of used folder
- ? `fzf` a command line fuzzy finder
- ? `broot` command line `tree` navigator
- ? `diff-so-fancy` better readabilty for diff
- ? `bat` replacement for cat with color syntax
- ? `lazydocker` docker info dashboard
- ? `chezmoi` manage your dotfiles across multiple diverse machines
- ? `flameshot` screenshot software
- ? `ranger` filemanager for console
- ? `shellcheck` linter for shell scripts
- ? `tig` commandline ui for git
- ? `youtube-dl`
- ? `fig` augments cli
- ? `jq,jo` json cli
- ? `gifsicle` gif command line editor
- ? `mas` command line interface for the Mac App Store
- ? `hub` extension to command-line git for github
- ? `clog` changelog for the rest of us
- Look into `brewfile`

# Examples / Inspiration

- https://github.com/betarelease/dotfiles
- https://pwal.ch/posts/2021-12-27-dev-env-dotfiles/
- https://github.com/pwalch/dotfiles
- https://www.youtube.com/watch?v=AuoYzuQ1yes
- https://gitlab.com/dnsmichi/dotfiles/-/tree/main/
- https://github.com/mathiasbynens/dotfiles/blob/master/.macos
  - https://git.herrbischoff.com/awesome-macos-command-line/about/
- https://git.herrbischoff.com/awesome-command-line-apps/about/
- TODO: https://github.com/mathiasbynens/dotfiles/tree/main
