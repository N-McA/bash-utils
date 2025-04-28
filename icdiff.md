# icdiff Installation Guide

icdiff is a terminal-based tool that provides side-by-side, colored diff output.

## Installation

### macOS
```bash
brew install icdiff
```

### pip (Python package manager)
```bash
pip install icdiff
```

### From source
```bash
git clone https://github.com/jeffkaufman/icdiff.git
cd icdiff
sudo python setup.py install
```

## Future Integration with Repository Scripts

While the scripts in this repository currently use the standard git diff, icdiff can be leveraged for improved diff visualization in the future.

## Usage with Git Alias

You can also add icdiff as a git alias:

```bash
git config --global icdiff.options '--line-numbers'
git config --global alias.dff 'icdiff'
```

Now you can use `git dff` instead of `git diff` for side-by-side colored diffs.

## Removing icdiff as Default Diff Tool

If you previously set icdiff as your default diff tool and need to undo it:

```bash
git config --global --unset diff.external
```