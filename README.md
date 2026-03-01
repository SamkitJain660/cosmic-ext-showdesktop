# cosmic-applet-toggle-minimize-all

A small COSMIC panel applet that toggles all tracked windows between:
- **Minimize all windows**
- **Restore previously minimized windows**

It remembers each window's state (normal/maximized), workspace, and active window status so restore behavior is predictable.

## What it offers

- One-click **minimize all** for regular app windows
- One-click **restore** of the same window set
- Restores windows in an order that preserves the previously active window
- Preserves maximize state on restore
- Uses COSMIC Wayland toplevel management APIs

## Requirements

- Linux with **COSMIC desktop** (Wayland session)
- Rust toolchain (stable)
- `cargo`

## Build

```bash
cargo build --release
```

Binary output:

```text
target/release/cosmic-applet-toggle-minimize-all
```

## Run for testing

```bash
cargo run --release
```

Note: This project is a COSMIC applet, so it is intended to be launched by the desktop environment/panel integration.

## Install (manual)

1. Copy the binary:

```bash
install -Dm755 target/release/cosmic-applet-toggle-minimize-all \
  ~/.local/bin/cosmic-applet-toggle-minimize-all
```

2. Install the desktop entry:

```bash
install -Dm644 data/com.example.CosmicToggleMinimizeAll.desktop \
  ~/.local/share/applications/com.example.CosmicToggleMinimizeAll.desktop
```

3. Ensure the `Exec=` line in the desktop entry points to your binary path (default in this repo uses `~/.local/bin/cosmic-applet-toggle-minimize-all`).

## Project structure

- `src/main.rs` - applet UI/button and application wiring
- `src/wm.rs` - Wayland/COSMIC window management logic
- `data/com.example.CosmicToggleMinimizeAll.desktop` - desktop/applet entry metadata

## Notes

- This applet targets COSMIC-specific protocols and is not expected to work on non-COSMIC desktops.
