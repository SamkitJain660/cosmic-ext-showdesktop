# cosmic-ext-showdesktop

A small COSMIC DE [Wayland session] panel applet that toggles all tracked windows between:
- **Minimize all windows**
- **Restore previously minimized windows**

## Functions

- One-click **minimize all** for regular app windows
- One-click **restore** of the same window set
- Restores windows in an order that preserves the previously active window
- Preserves maximize state on restore

## Build

```bash
cargo build --release
```

Binary output:

```text
target/release/cosmic-ext-showdesktop
```

## Run for testing

```bash
cargo run --release
```

## Install (manual)

1. Copy the binary:

```bash
install -Dm755 target/release/cosmic-ext-showdesktop \
  ~/.local/bin/cosmic-ext-showdesktop
```

2. Install the desktop entry:

```bash
install -Dm644 data/com.example.CosmicShowDesktop.desktop \
  ~/.local/share/applications/com.example.CosmicShowDesktop.desktop
```

3. Ensure the `Exec=` line in the desktop entry points to your binary path (default in this repo uses `~/.local/bin/cosmic-ext-showdesktop`).


thnk u codex ❤️❤️❤️
