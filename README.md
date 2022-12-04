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
plugins=(<existing...> zsh-autosuggestions zsh-syntax-highlighting)
eval "$(fnm env --use-on-cd)"
```

# Configure iTerm2
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
TODO: Set as default editor
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

# TODO
- ? `direnv` to have per folder `.envrc`
- ? `zoxide` a smarter `cd`
- ? `fzf` a command line fuzzy finder
- ? `fd` simple `find`
- ? `broot` command line `tree` navigator
- ? `diff-so-fancy` better readabilty for diffs
- ? `lazygit` command line git diff ui
- ? `bat` replacement for cat with color syntax
- ? `lazydocker` docker info dashboard
- ? `chezmoi` manage your dotfiles across multiple diverse machines
- ? `flameshot` screenshot software
- ? `ranger` filemanager for console
- ? `shellcheck` linter for shell scripts
- ? `tig` commandline ui for git
- ? `youtube-dl`
- ? `z` cli tool for frequently used folders
- ? `fig` augments cli

# Examples
- https://github.com/betarelease/dotfiles
- https://pwal.ch/posts/2021-12-27-dev-env-dotfiles/
- https://github.com/pwalch/dotfiles
- https://www.youtube.com/watch?v=AuoYzuQ1yes