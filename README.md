# dotfiles

## Steps
```bash
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install cli tools
brew install \
 git \
 micro `# command line text editor`  \ 
 fnm `# node version manager` \ 
 htop \ 
 exa `# replacement for ls` \ 
 httpie `# better ux than curl` \
 dog `# better ux than dig`

# Install apps
brew install \
 iterm2 \
 smartgit \
 google-chrome \
 visual-studio-code \
 webstorm \
 discord
```

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
TODO: Set default editor, confgiure iTerm to handle well option as ESC+, `"tabstospaces": true`

# Configure `fnm`
TODO: setup ZSH to use the `fnm env` with `cd` and clear the binary cache of ZSH to switch to the new `node`

# TODO
- ? `direnv` to have per folder `.envrc`
- ? `zoxide` a smarter `cd`
- ? `fzf` a command line fuzzy finder
- ? `fd` simple `find`
- ? `broot` command line `tree` navigator
- ? `dust` replacement for `du`
- ? `duf` replacement for `df`
- ? `glances` command line system monitor
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


# Examples
- https://github.com/betarelease/dotfiles
- TODO: Read https://pwal.ch/posts/2021-12-27-dev-env-dotfiles/
- https://github.com/pwalch/dotfiles
- https://www.youtube.com/watch?v=AuoYzuQ1yes