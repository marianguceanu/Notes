# GNU Stow

## What is GNU Stow?

- **symlink farm manager**
- automates the creation of symbolic links -> 
    - manage software packages or configuration files in a clean, modular way.

Originally designed for managing local software installations in `/usr/local/stow`, it is now widely used for managing **dotfiles**.

---

## Key Concept

Stow uses a **directory structure** like this:

```fish
~/dotfiles/
├── bash/
│   └── .bashrc
├── git/
│   └── .gitconfig
└── nvim/
    └── .config/
        └── nvim/init.vim
```

---

Or like this:
```fish
~/dotfiles/
├── .config
│   ├── alacritty
│   │   ├── ...
│   ├── awesome
│   │   ├── ... 
│   ├── hypr
│   │   ├── ...
│   ├── nvim
│   │   └── ...
│   ├── qtile
│   │   ├── ... 
│   └── waybar
│       ├── ... 
├── .gitignore
├── README.md
├── .tmux.conf
└── .wezterm.lua
```

---

Running:

_For the first example_
```fish
stow -t ~ bash git nvim
```
_For the second one_
```fish
stow .
```
Will create symlinks in your home directory:

- **~/.bashrc** → ~/dotfiles/bash/.bashrc
- **~/.gitconfig** → ~/dotfiles/git/.gitconfig
- **~/.config/nvim/init.vim** → ~/dotfiles/nvim/.config/nvim/init.vim

Each subdirectory (bash, git, nvim) is treated as a package.

---
# Why Use Stow?
- Dotfile Management
    - Organize your dotfiles in version-controlled, modular directories.
    - Easily symlink them to ~ with a single command.
    - Clean removal of dotfiles with stow -D.

- Software Deployment
    - Use for locally compiled packages in /usr/local/stow/.
    - Avoid conflicts between software.
    - Quickly uninstall packages by removing their symlinks.

---
# Notes and Gotchas
- Stow **will not overwrite** existing non-symlink files — move or remove them first.
- Symlinks are relative by default, improving portability.
- Always run stow from the parent directory of the package folders.
