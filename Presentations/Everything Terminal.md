# Everything terminal (and some more)
## Hello everyone!
## This presentation will focus on some nice terminal (and not only) tools that I use daily
- Without anything else left to discuss, I think we can move forward.
---
# Kicking it off, my terminal emulator of choice: Alacritty
- Fast, GPU-accelerated terminal emulator known for its simplicity and performance.
- Written in Rust and uses OpenGL for rendering -> faster than many traditional terminal emulators.

## Why use it?
- Cross-platform (Linux, Windows, MacOS).
- Highly & easily configurable - uses TOML (Tom's Obvious Minimal Language), so it is begginner friendly.
- Good font & ligature support -> no funky characthers on the screen.
### Let's take a look at the config shall we?

[Official website](https://alacritty.org/)
---
# Tmux

- Tmux (**Terminal Multiplexer**): command-line tool that allows you to **manage multiple terminal sessions** within a single window. 
- Particularly useful for: developers, system administrators, anyone who works extensively (or likes to work) in the command line.

## Key Features of Tmux:
1. **Multiple Panes & Windows**: You can split a terminal window into multiple panes and switch between them easily.
2. **Session Persistence**: If your SSH connection drops, your tmux session remains active, allowing you to reconnect and resume work.
3. **Detach & Reattach Sessions**: You can start a session, detach from it, and reattach later from a different location.
4. **Customization**: Tmux supports extensive configuration via the `~/.tmux.conf` file.

### Let's take a look at my tmux config

[GitHub link](https://github.com/tmux/tmux)
---
# Slides.md: presentations in the terminal
- Written in Golang -> pretty fast
- It renders markdown in the terminal as nice slides
- Has (almost) all the features of markdown
- Bonus point: it looks hacky

[GitHub link](https://github.com/maaslalani/slides)
---
# The text editor: neovim (nvim)
- Vim successor
## Aims to improve Vim by:
- **Better Plugin System**: Uses Lua for configuration and plugins, making it faster and more flexible.
- **Asynchronous Execution**: Runs tasks in the background without blocking the editor.
- **Modern UI Features**: Supports floating windows, true color, and popup menus.
- **Reverse compatibility**: can run most Vim scripts/plugins

### Let's look into the configuration 
[Official website](https://neovim.io/)
[GitHub link](https://github.com/neovim/neovim)
---
# Windowing system: Qtile
- Dynamic tiling window manager written in Python.
- Highly customizable
- Lightweight
- Designed for both beginners and power users

## Why use it?
- **Python-Based**: Configure and extend it using Python scripts.
- **Tiling & Floating Windows**: Automatically arranges windows efficiently.
- **Keyboard-Driven Workflow**: Minimal need for a mouse.
- **Extensible**: Supports widgets, bars, and custom layouts.

### Let's take a look at the configuration

[Official website](https://qtile.org/)
[GitHub link](https://github.com/qtile/qtile)
