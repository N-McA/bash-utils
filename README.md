# Bash Utils

A collection of zsh utilities for Git workflows, notebook creation, and development tasks.

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/nmca/nmca-bash-utils.git
   ```

2. Add the directory to your PATH and set default directories in your `~/.zshrc` file:
   ```bash
   UTIL_PATH="/path/to/nmca-bash-utils"
   export PATH="$PATH:$UTIL_PATH"

   # Default directories for notebooks and notes
   export NOTEBOOK_DIR="$HOME/notebooks"
   export NOTES_DIR="$HOME/notes"

   # Optional: customize notebook template location
   export NOTEBOOK_TEMPLATE="/path/to/nmca-bash-utils/templates/notebook.py"

   source "$UTIL_PATH/alias.zsh"
   ```

3. Reload your shell:
   ```bash
   source ~/.zshrc
   ```

## Dependencies

These scripts require the following dependencies:

- **Zsh**: The default shell on macOS. All scripts use Zsh.
- **Git**: Required for all Git-related commands.
- **fzf**: Required for the `git-branch-restore` and fuzzy selection.
  - Install with Homebrew: `brew install fzf`
- **GitHub CLI** (optional): Used by `open-pr-on-github` for better PR detection.
  - Install with Homebrew: `brew install gh`
- **uv**: Used for Python script dependencies management.
  - Install with: `curl -sSf https://astral.sh/uv/install.sh | bash`
- **Python 3.9+**: Required for the notebook scripts.

## Available Commands

### Git Commands

- `git mm`: Fetch master from remote and merge it into the current branch.
- `git nb <branch-name>`: Fetch master from remote and create a new branch from it.
- `git gb <branch-name>`: Fetch a branch from remote and checkout as `$USER/branch-name`.
- `gd`: Show diff between current branch and master.
- `gdf`: Show filenames that differ from master.
- `gbh`: List recently checked out local branches.
- `gbr <branch-name>`: Restore selected files from a branch.
- `sb <search-term>`: Search for term in diffs of local branches.
- `pr`: Open the PR for the current branch in browser.

### Notebook Commands

- `nb [name]`: Create a new Python notebook from template in `$NOTEBOOK_DIR`.
- `nt [name]`: Create a new markdown notes file in `$NOTES_DIR`.

## Usage Examples

```bash
# Merge remote master into current branch
git mm

# Create a new branch from up-to-date master
git nb feature-branch

# Fetch remote branch and create your own version
git gb feature-branch  # Creates $USER/feature-branch

# Search for a term in branch diffs
sb "search term"

# Create a new notebook
nb data-analysis  # Creates in $NOTEBOOK_DIR with name YYYY-MM-DD-data-analysis.py

# Create a new notes file
nt meeting  # Creates in $NOTES_DIR with name YYYY-MM-DD-meeting.md
```

## Python Notebooks

Python notebooks use `uv` for dependency management. The template includes commonly used data science packages.

To modify default dependencies, edit the template at `templates/notebook.py`.

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `NOTEBOOK_DIR` | Directory where new notebooks are created | `$HOME/notebooks` |
| `NOTES_DIR` | Directory where new notes are created | `$HOME/notes` |
| `NOTEBOOK_TEMPLATE` | Path to the notebook template file | `<script_dir>/templates/notebook.py` |

## Script Behavior

All scripts in this repository:

1. Fail immediately on any error (`set -e`)
2. Return meaningful exit codes
3. Print error messages to stderr

This makes them safe to use in automated workflows and pipelines.
