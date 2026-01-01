# PCem Flatpak

Flatpak packaging for [PCem](https://github.com/sarah-walker-pcem/pcem), a PC emulator for classic IBM PC compatibles and clones.

## Features

- Accurate cycle-by-cycle CPU emulation from 8088 to Pentium
- Wide range of graphics cards from CGA to 3D accelerators
- Sound Blaster, Gravis Ultrasound, and other sound cards
- Bundled ROMs for various machines

## Installation

### From Repository

Add the Flatpak repository:

```bash
flatpak remote-add --if-not-exists pcem-flatpak https://jokujossai.github.io/pcem-flatpak/pcem-flatpak.flatpakrepo
```

Install PCem:

```bash
flatpak install pcem-flatpak io.github.jokujossai.pcem
```

### Building from Source

Requirements:
- flatpak-builder
- org.freedesktop.Sdk//25.08
- org.freedesktop.Sdk.Extension.llvm20//25.08

Build and install:

```bash
cd base/io.github.jokujossai.pcem
flatpak-builder --user --install build --force-clean io.github.jokujossai.pcem.yml
```

## Running

```bash
flatpak run io.github.jokujossai.pcem
```

## Configuration

PCem stores its configuration in `~/.var/app/io.github.jokujossai.pcem/`.

ROMs are pre-installed at `/app/share/pcem/roms/` inside the Flatpak.

## License

This Flatpak packaging is licensed under the MIT License. See [LICENSE](LICENSE) for details.

**Note:** PCem itself is licensed under GPL-2.0. wxWidgets is licensed under the wxWindows Library Licence.

## Links

- [PCem Source Code](https://github.com/sarah-walker-pcem/pcem)
- [PCem Website](https://pcem-emulator.co.uk/)
