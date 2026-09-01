# ANV15-51 Audio TUI

A tiny terminal interface for switching between the built-in speakers and wired
headphones on the Acer Nitro V 15 ANV15-51 running Omarchy.

On this laptop, ALSA UCM exposes the speakers and headphones as mutually
exclusive card profiles. With headphones plugged in, the speaker sink disappears,
so a normal PipeWire output selector cannot switch to it. This utility changes the
card profile, waits for the new sink, makes it the default, and moves active audio
streams through Omarchy's existing audio helper.

![Shell](https://img.shields.io/badge/shell-bash-4EAA25)
![Platform](https://img.shields.io/badge/laptop-ANV15--51-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## Requirements

- Acer Nitro V 15 ANV15-51
- Omarchy with PipeWire/WirePlumber
- `bash`, `pactl`, `jq`, and [`gum`](https://github.com/charmbracelet/gum)
- `omarchy-audio-output-set-default` (included with Omarchy)

## Install

```bash
git clone https://github.com/muralibaburaj/anv15-51-audio-tui.git
cd anv15-51-audio-tui
install -Dm755 audio-output-tui ~/.local/bin/audio-output-tui
```

Ensure `~/.local/bin` is on your `PATH`.

## Use

```bash
audio-output-tui
```

Use the arrow keys to select **Laptop speakers** or **Wired headphones**, then
press Enter. The active profile is marked with a dot. Escape or Ctrl+C exits
without changing anything.

## Uninstall

```bash
rm ~/.local/bin/audio-output-tui
```

## Scope

This utility deliberately checks the computer model and exits on anything other
than an ANV15-51. Its profile discovery is dynamic, but it has only been designed
and tested for this laptop's UCM configuration on Omarchy.

## License

[MIT](LICENSE)
