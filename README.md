# Sheldon fixes for MSYS2

Small fixes for [Sheldon](https://github.com/rossmacarthur/sheldon) 0.8.5 to improve compatibility with MSYS2 UCRT64 and Zsh on Windows.

This is an unofficial, locally tested modification. It is not an official Sheldon release.

## Changes

- **Windows configuration locking:** Use a dedicated `.sheldon.lock` file instead of locking the configuration directory itself.
- **Plugin paths in MSYS2:** Convert Windows paths to POSIX-style paths using `cygpath -u` when running under an MSYS2 environment (`MSYSTEM` is set).

These changes are intended to make `sheldon source` work more reliably with Zsh plugins under MSYS2.

## Modified files

- `src/main.rs`
- `src/lock/script.rs`

## Tested environment

- Sheldon 0.8.5
- MSYS2 UCRT64
- Zsh
- Rust release build

The modified binary was tested locally. Plugin loading, `fzf` integration, and the `Ctrl-R` history search were also checked.

Other Windows environments and configurations have not been fully tested. These changes may be incomplete.

## How to apply

1. Obtain the Sheldon 0.8.5 source code.
2. Replace `src/main.rs` and `src/lock/script.rs` with the modified files in this repository.
3. Build Sheldon from the source directory:

   ```sh
   cargo fmt
   cargo build --release
   ```

4. Use the resulting binary in your MSYS2 environment.

Keep a backup of the original files before replacing them.

## License

Sheldon is dual-licensed under either:

- Apache License 2.0 (`LICENSE-APACHE`)
- MIT License (`LICENSE-MIT`)

These license files are included with this repository. See the respective files for the license terms.

## Disclaimer

This is an unofficial modification for personal use and experimentation. It is not affiliated with or endorsed by the original Sheldon project.
