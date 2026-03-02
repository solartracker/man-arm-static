# man-arm-static

**Portable `man` program for ARMv7 Linux devices**

`man-arm-static` is a portable implementation of the classic `man` program, bundled with manpages. It is designed for ARMv7 Linux devices, especially those with read-only firmware. You can store manpages on external storage and run the program without modifying the system installation.

## Features

- Fully **portable**: can be unpacked anywhere on the filesystem.
- **Bundled manpages**: stored outside read-only firmware.
- **Self-contained environment**: `install.sh` sets up a symbolic link to an isolated sysroot and updates your `PATH`.
- **ARMv7 Linux compatible**: built statically with musl libc for minimal dependencies.

## Installation

### Build the Package

First, clone the repository and build the install package:

```bash
git clone https://github.com/solartracker/man-arm-static
cd man-arm-static
./man-arm-musl.sh
```

This will compile the program and produce a tarball, e.g.:  

```bash
man_2.13.1-1_armv7_musl.tar.gz
```

### Deploy to Target Device

1. Copy the tarball to your ARMv7 Linux device.  
2. Unpack it anywhere you like:  

```bash
tar -xzf man_2.13.1-1_armv7_musl.tar.gz
```

3. Source the `install.sh` script in your shell before using `man`:  

```bash
source ./install.sh
```

> ⚠️ **Important:** The `install.sh` script **must be sourced**, not executed, to correctly configure your environment.

4. You can now use the portable `man` program:

```bash
man ls
```

## Notes

- The program is **fully self-contained** and does not require root privileges.  
- Multiple devices or users can share the same external storage setup.  
- Designed for ARMv7; other architectures are **not supported**.

## License

This project is licensed under the **GPLv3**.



