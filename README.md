# Zsh Setup Guide for Debian

Complete setup for Zsh with autocompletion, history, autosuggestions, and syntax highlighting.

## 1. Install Zsh

```bash
sudo apt update
sudo apt install zsh git curl -y
```

## 2. Set Zsh as Default Shell

```bash
chsh -s $(which zsh)
```

Log out and log back in for the change to take effect.

## 3. Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 4. Install Essential Plugins

### zsh-autosuggestions
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### zsh-syntax-highlighting
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

## 5. Configure ~/.zshrc

Edit your `~/.zshrc` file:

```bash
nano ~/.zshrc
```

Find the line with `plugins=` and replace it with:

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

Save and exit (Ctrl+O, Enter, Ctrl+X).

## 6. Reload Configuration

```bash
source ~/.zshrc
```

## 7. Test Features

- **TAB completion**: Type `cd /e` then press TAB
- **History**: Press ↑ arrow to browse previous commands
- **Autosuggestions**: Start typing a previous command, you'll see a gray suggestion (press → to accept)
- **Syntax highlighting**: Valid commands appear green, invalid ones red

## 8. Troubleshooting TAB Completion

If TAB completion doesn't work:

```bash
rm -f ~/.zcompdump*
autoload -Uz compinit && compinit
```

## 9. Optional: Install fzf (Fuzzy Finder)

```bash
sudo apt install fzf -y
```

Add to `~/.zshrc`:

```bash
# fzf fuzzy search
source /usr/share/doc/fzf/examples/key-bindings.zsh
source /usr/share/doc/fzf/examples/completion.zsh
```

Then reload:

```bash
source ~/.zshrc
```

Use `Ctrl+R` for fuzzy history search.

---

**Done!** Your Zsh is now fully configured with all essential features.
