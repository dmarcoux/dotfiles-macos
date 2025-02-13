# <a href="https://github.com/dmarcoux/dotfiles-macos">dmarcoux/dotfiles-macos</a>

My MacOS configuration files.

## Setup

1. Install _Xcode command line tools_ and [homebrew](https://brew.sh/).

   ```bash
   xcode-select --install &&
      /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. Install all packages from [Brewfile](Brewfile).

   ```bash
   curl -o ~/Brewfile https://raw.githubusercontent.com/dmarcoux/dotfiles-macos/refs/heads/main/Brewfile &&
     brew bundle &&
     rm ~/Brewfile
   ```

3. Setup 1Password GUI/CLI and browser extensions.

   1. Enable [1Password SSH agent](https://developer.1password.com/docs/ssh/get-started/#step-3-turn-on-the-1password-ssh-agent).

   2. [Sign Git commits with my SSH key](https://developer.1password.com/docs/ssh/git-commit-signing/).

   3. Configure the 1Password GUI and browser extensions to match the settings stored in my 1Password notes.

4. Setup my dotfiles with [chezmoi](https://www.chezmoi.io/).

   _[Brewfile](Brewfile) is symlinked to my home directory in order to be able
   to run `brew bundle` from everywhere._

   ```bash
   chezmoi init git@github.com:dmarcoux/dotfiles-macos.git &&
     ln --symbolic "$(dirname "$(chezmoi source-path)")/Brewfile" ~/Brewfile &&
     brew bundle &&
     chezmoi apply
   ```
