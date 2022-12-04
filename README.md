# dotfiles

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

# Confgiure VS Code
Edit `settings.json` and set the Meslo font from Powerline10k

```bash
"editor.fontFamily": "MesloLGS NF",
```

# Install VS Code extensions:
- Error Lens
- Gitlens
- Todo Highlight
- ? VSCode icons
- ? ESLint
- ? EditorConfig

# Adjust MacOS settings
```bash
defaults write com.apple.Finder AppleShowAllFiles true
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