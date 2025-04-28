# Configuring Command+R for FZF Reverse Search in iTerm2

This guide explains how to configure Command+R (⌘+R) in iTerm2 to trigger fuzzy history search using FZF.

## Prerequisites

- [iTerm2](https://iterm2.com/) installed
- [fzf](https://github.com/junegunn/fzf) installed
  - Install with Homebrew: `brew install fzf`
  - Run the installer: `$(brew --prefix)/opt/fzf/install`

## Configuration Steps

1. **Open iTerm2 Preferences**
   - Press `⌘,` or go to iTerm2 → Preferences

2. **Navigate to Keys Section**
   - Select the "Keys" tab
   - Click on "Key Bindings"

3. **Add a New Keyboard Shortcut**
   - Click the "+" button to add a new key binding
   - Set:
     - Keyboard Shortcut: Press `⌘R`
     - Action: Select "Send Text"
     - Value: `\C-r` (Control+R)

4. **Enhance FZF Configuration (Optional)**

   Add the following to your `~/.zshrc` for improved FZF history search:

   ```bash
   # FZF history search configuration
   export FZF_DEFAULT_OPTS="--height 40% --layout=reverse --border"

   # CTRL-R - Paste the selected command from history into the command line
   bindkey '^R' fzf-history-widget

   # Configure FZF history search
   export FZF_CTRL_R_OPTS="
     --preview 'echo {}'
     --preview-window up:3:hidden:wrap
     --bind 'ctrl-/:toggle-preview'
     --bind 'ctrl-y:execute-silent(echo -n {2..} | pbcopy)+abort'
     --color header:italic
     --header 'Press CTRL-Y to copy command to clipboard'"
   ```

5. **Source Your Updated Configuration**
   ```bash
   source ~/.zshrc
   ```

## Usage

- Press `⌘R` in iTerm2 to activate fuzzy history search
- Type part of a command to filter your command history
- Navigate with arrow keys and press Enter to execute the selected command
- Press Esc to cancel the search

## Troubleshooting

- If `⌘R` doesn't work, ensure no other application or system shortcut is intercepting it
- Verify that fzf is properly installed by running `which fzf`
- If you see an error like `No such widget 'fzf-history-widget'`, run the fzf installer to set up zsh integration:
  ```bash
  $(brew --prefix)/opt/fzf/install
  ```
- If the binding doesn't work, try restarting iTerm2 after configuration

## Additional Resources

- [FZF Documentation](https://github.com/junegunn/fzf)
- [iTerm2 Documentation](https://iterm2.com/documentation.html)
