# dotfiles

## Initial setup

- Update OS

## Configure MacOS
```
# System Preferences > General > Appearance
defaults write -globalDomain AppleInterfaceStyleSwitchesAutomatically -bool true

# System Preferences > General > Click in the scrollbar to: Jump to the spot that's clicked
defaults write -globalDomain AppleScrollerPagingBehavior -bool true

# System Preferences > General > Sidebar icon size: Medium
defaults write -globalDomain NSTableViewDefaultSizeMode -int 2

# System Preferences > Desktop & Screen Saver > Start after: Never
defaults -currentHost write com.apple.screensaver idleTime -int 0

# System Preferences > Dock > Size:
defaults write com.apple.dock tilesize -int 36

# System Preferences > Dock > Magnification:
defaults write com.apple.dock magnification -bool false

# System Preferences > Dock > Minimize windows into application icon
defaults write com.apple.dock minimize-to-application -bool true

# System Preferences > Mission Controll > Automatically rearrange Spaces based on most recent use
defaults write com.apple.dock mru-spaces -bool false

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

# System Preferences > Keyboard >
defaults write NSGlobalDomain KeyRepeat -int 2

# System Preferences > Keyboard >
defaults write NSGlobalDomain InitialKeyRepeat -int 25

# System Preferences > Trackpad > Tap to click
# Trackpad: enable tap to click for this user and for the login screen
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true
defaults -currentHost write NSGlobalDomain com.apple.mouse.tapBehavior -int 1
defaults write NSGlobalDomain com.apple.mouse.tapBehavior -int 1

# Trackpad: map bottom right corner to right-click
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadCornerSecondaryClick -int 2
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadRightClick -bool true
defaults -currentHost write NSGlobalDomain com.apple.trackpad.trackpadCornerClickBehavior -int 1
defaults -currentHost write NSGlobalDomain com.apple.trackpad.enableSecondaryClick -bool true

# Increase sound quality for Bluetooth headphones/headsets
### NEEDS TESTING? defaults write com.apple.BluetoothAudioAgent "Apple Bitpool Min (editable)" -int 40

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

# Finder: show hidden files by default
defaults write com.apple.finder AppleShowAllFiles -bool true

# Finder > Preferences > Show all filename extensions
defaults write NSGlobalDomain AppleShowAllExtensions -bool true

# Finder > View > As List
defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"

# Finder > View > Show Path Bar
defaults write com.apple.finder ShowPathbar -bool true

# Finder: show status bar
defaults write com.apple.finder ShowStatusBar -bool true

# Display full POSIX path as Finder window title
defaults write com.apple.finder _FXShowPosixPathInTitle -bool true

# Keep folders on top when sorting by name
defaults write com.apple.finder _FXSortFoldersFirst -bool true

# When performing a search, search the current folder by default
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"

# Disable the warning when changing a file extension
defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false

# Enable spring loading for directories
defaults write NSGlobalDomain com.apple.springing.enabled -bool true

# Remove the spring loading delay for directories
defaults write NSGlobalDomain com.apple.springing.delay -float 0

# Avoid creating .DS_Store files on network or USB volumes
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true

# Enable AirDrop over Ethernet and on unsupported Macs running Lion
defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true

# Show the ~/Library folder
chflags nohidden ~/Library && xattr -d com.apple.FinderInfo ~/Library

# Show the /Volumes folder
sudo chflags nohidden /Volumes

# Expand the following File Info panes:
# “General”, “Open with”, and “Sharing & Permissions”
defaults write com.apple.finder FXInfoPanesExpanded -dict \
	General -bool true \
	OpenWith -bool true \
	Privileges -bool true
 
# Speed up Mission Control animations
defaults write com.apple.dock expose-animation-duration -float 0.1 

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

# Set language and text formats
defaults write NSGlobalDomain AppleLanguages -array "en" "it"
defaults write NSGlobalDomain AppleLocale -string "en_GB@currency=GBP"
defaults write NSGlobalDomain AppleMeasurementUnits -string "Centimeters"
defaults write NSGlobalDomain AppleMetricUnits -bool true

# Show language menu in the top right corner of the boot screen
sudo defaults write /Library/Preferences/com.apple.loginwindow showInputMenu -bool true

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

# Require password immediately after sleep or screen saver begins
defaults write com.apple.screensaver askForPassword -int 1
defaults write com.apple.screensaver askForPasswordDelay -int 0

# Enable subpixel font rendering on non-Apple LCDs
# Reference: https://github.com/kevinSuttle/macOS-Defaults/issues/17#issuecomment-266633501
# ??? defaults write NSGlobalDomain AppleFontSmoothing -int 1

# Enable HiDPI display modes (requires restart)
# ??? sudo defaults write /Library/Preferences/com.apple.windowserver DisplayResolutionEnabled -bool true


```

## Steps

```bash
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install cli tools
brew install \
 git \
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
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src # before `source "$ZSH/oh-my-zsh.sh"`
ZSH_THEME="powerlevel10k/powerlevel10k"
COMPLETION_WAITING_DOTS="true"
plugins=(<existing...> zsh-autosuggestions zsh-syntax-highlighting)
eval "$(fnm env --use-on-cd)"

export EDITOR='micro' # set micro as default text editor
alias ll="exa -la --git --icons --colour-scale"
alias l="exa -la --git --icons --colour-scale --no-user --no-time --no-permissions
```

# Configure iTerm2

- Blinking Cursor: Settings -> Profiles -> Text -> Blinking cursor
- Colors: Settings -> Profiles -> Colors -> Color Preset -> Tango Dark
- Keyboard (Micro editor): Settings -> Profiles -> Keys -> General -> Left Option Key -> Esc+
- Keyboard (Word jump delete with Option key): Settings → Profiles → Keys → Key mappings → Presets... → Natural Text Editing

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
- Agenda
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

````

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

# Adjust MacOS settings
```bash
defaults write com.apple.Finder AppleShowAllFiles true
````

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
