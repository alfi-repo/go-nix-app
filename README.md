# Nix-Go

## Test Bed

- Windows 10 22H2
- WSL 2.2.4.0
- Ubuntu 24.04 (noble)
- Nix 2.22

## Prepare WSL (Optional)

- Enable WSL.
- Install Ubuntu 24.04.
- Get into Ubuntu shell.
- Install Fish Shell.

```shell
# Install.
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt update
sudo apt install fish

# Verify.
fish --version

# Set as default shell.
chsh -s $(which fish)
```

- Install starship

```shell
# Install.
curl -sS https://starship.rs/install.sh | sh

# Add the following to the end of ~/.config/fish/config.fish:
starship init fish | source
```

## Prerequisites

- Install Nix package manager.

```shell
# Requires POSIX-compliance shell. i.e. bash.
sh <(curl -L https://nixos.org/nix/install) --daemon
```

- Enable Nix flakes experimental features.

```shell
# Add the following line to ~/.config/nix/nix.conf
# Create one if the file doesn't exist yet.
experimental-features = nix-command flakes
```

- Install direnv

```shell
# Install package.
sudo apt install direnv

# Verify
# Make sure version > 2.34
direnv --version

# Setup hook into shell.
# https://direnv.net/docs/hook.html
# i.e. Fish
# Add following line to the end of the ~/.config/fish/config.fish
# direnv hook fish | source
```

- Restart WSL. Close console, wait a minute, and open again.

- Install Nix direnv

```shell
# Install
nix profile install nixpkgs#nix-direnv

# Register.
# Requires POSIX-compliance shell. i.e. bash.
source $HOME/.nix-profile/share/nix-direnv/direnvrc
```

## Usage

```shell
direnv allow
```

## Update Flake

```shell
# Should update automatically.
# Just in case, manually update flake.lock.
nix flake update
```

## IDE Integrations

- vscode: https://marketplace.visualstudio.com/items?itemName=mkhl.direnv
- jetbrains: https://plugins.jetbrains.com/plugin/15285-direnv-integration

Note: Restart IDE after installing plugins.