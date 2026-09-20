# global-fullscreen

Hyprland helper that expands the active window across the combined monitor
area, temporarily hides Waybar, and restores Waybar after the fullscreen window
is gone.

## Build and install

```bash
nix build github:RevolunixOS/pkg-global-fullscreen
nix profile install github:RevolunixOS/pkg-global-fullscreen
```

Run `global-fullscreen` from a Hyprland key binding while the target window is
active.

## How it works

The script reads monitor geometry from `hyprctl`, toggles the active window to
floating mode, resizes it to the aggregate display area, kills Waybar, and
polls Hyprland clients until the matching floating window disappears.

## Limitations

- Designed specifically for Hyprland; `hyprctl` must already be in `PATH`.
- Geometry parsing assumes a simple monitor layout and may be wrong for
  vertically stacked, scaled, transformed, or mixed-resolution outputs.
- `pkill -f waybar` terminates every matching Waybar process.
- There is no state restoration if the script exits unexpectedly.
- The package metadata currently contains an unrelated backup-tool
  description.

Test with your monitor layout before assigning it to a frequently used key.

## License

See [`LICENSE`](LICENSE).
