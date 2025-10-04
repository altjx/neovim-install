# Neovim Configuration Installer

One-line installer for [altjx/nvim-configs](https://github.com/altjx/nvim-configs) - a comprehensive Neovim setup based on NvChad.

## Quick Install

```bash
curl -fsSL https://alton.sh/install.sh | bash
```

## What It Does

1. **Checks & Installs Neovim** (≥ 0.10.0)
   - Adds neovim-ppa/stable repository
   - Installs or upgrades Neovim to latest stable

2. **Backs Up Existing Configs**
   - `~/.config/nvim` → `~/.config/nvim.backup_TIMESTAMP`
   - `~/.local/share/nvim` → `~/.local/share/nvim.backup_TIMESTAMP`
   - `~/.local/state/nvim` → `~/.local/state/nvim.backup_TIMESTAMP`
   - Cleans `~/.cache/nvim`

3. **Installs Prerequisites**
   - git
   - fd-find
   - ripgrep
   - Node.js (LTS)
   - build-essential

4. **Clones Configuration**
   - Clones [altjx/nvim-configs](https://github.com/altjx/nvim-configs)
   - Removes .git directory for clean independent setup

5. **Optional Ruby Tools** (if Ruby detected)
   - ruby-lsp
   - rubocop

## Requirements

- **OS:** Ubuntu or Debian-based Linux
- **Permissions:** Non-root user with sudo access
- **Internet:** For downloading packages and repositories

## Manual Installation

If you prefer to review the script first:

```bash
# Download and review
curl -fsSL https://alton.sh/nvim -o install.sh
less install.sh

# Make executable and run
chmod +x install.sh
./install.sh
```

## After Installation

1. Launch Neovim:
   ```bash
   nvim
   ```

2. Lazy.nvim will automatically install all plugins (wait for completion)

3. Restart Neovim after plugins finish installing

4. Install a [Nerd Font](https://www.nerdfonts.com/) for proper icon display

## Hosting This Script

### GitHub Pages (Recommended)

1. Enable GitHub Pages in repository settings
2. Set source to `main` branch, root directory
3. Add custom domain `alton.sh` in settings
4. Configure DNS:
   ```
   Type: CNAME
   Name: alton.sh (or @)
   Value: <username>.github.io
   ```

### Raw GitHub URL

Direct link to raw file:
```bash
curl -fsSL https://raw.githubusercontent.com/altjx/neovim-install/main/install.sh | bash
```

### Cloudflare Pages

1. Connect GitHub repo to Cloudflare Pages
2. Set custom domain to `alton.sh`
3. Auto-deploys on every push

## Troubleshooting

**Script fails with permission errors:**
- Don't run as root - run as normal user with sudo access

**Old Neovim version persists:**
- Run `sudo apt-get update && sudo apt-get upgrade neovim`
- Verify with `nvim --version`

**Plugins won't install:**
- Check Node.js is installed: `node --version`
- Check git is working: `git --version`
- Try `:Lazy sync` inside Neovim

**Icons not displaying:**
- Install a [Nerd Font](https://www.nerdfonts.com/)
- Set your terminal to use the Nerd Font

**Restore old configuration:**
```bash
# Find your backup
ls ~/.config/nvim.backup_*

# Restore it
rm -rf ~/.config/nvim
mv ~/.config/nvim.backup_TIMESTAMP ~/.config/nvim

# Restore data directory
rm -rf ~/.local/share/nvim
mv ~/.local/share/nvim.backup_TIMESTAMP ~/.local/share/nvim
```

## Development

Edit the script and test locally:

```bash
# Test without running
bash -n install.sh

# Test in a container
docker run -it ubuntu:latest bash
# Then paste the curl command
```

## License

MIT License - See [nvim-configs LICENSE](https://github.com/altjx/nvim-configs/blob/main/LICENSE)
