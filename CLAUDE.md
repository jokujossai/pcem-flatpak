# PCem Flatpak

Flatpak packaging for PCem, a PC emulator for classic IBM PC compatibles.

## Project Structure

```
pcem/
├── .claude/
│   └── settings.json
├── .github/
│   └── workflows/
│       └── flatpak-build.yaml    # CI/CD workflow
├── base/
│   └── io.github.jokujossai.pcem/
│       ├── io.github.jokujossai.pcem.yml         # Main Flatpak manifest
│       ├── io.github.jokujossai.pcem.desktop     # Desktop entry
│       ├── io.github.jokujossai.pcem.metainfo.xml
│       └── io.github.jokujossai.pcem.svg         # App icon
├── CLAUDE.md
├── LICENSE
├── README.md
└── repo.gpg                      # GPG public key for signing
```

## Build Dependencies

PCem requires:
- CMake + Ninja
- Clang (via org.freedesktop.Sdk.Extension.llvm20)
- SDL2 (provided by Freedesktop Platform)
- wxWidgets 3.x (built as module)
- OpenAL (provided by Freedesktop Platform)

## Building Locally

```bash
cd base/io.github.jokujossai.pcem
flatpak-builder --user --install build --force-clean io.github.jokujossai.pcem.yml
```

## CI/CD

GitHub Actions workflow:
- Builds on push to main and tags
- Publishes Flatpak repository to GitHub Pages
- Creates releases with .flatpak bundles on tags

Required secrets:
- `GPG_PRIVATE_KEY` - GPG private key for signing
- `GPG_PASSPHRASE` - GPG key passphrase

Required variables:
- `GPG_KEY_ID` - GPG key ID
- `GPG_KEY_GREP` - GPG keygrip for preset passphrase

## Licenses

- **Flatpak packaging**: MIT
- **PCem**: GPL-2.0 (https://github.com/sarah-walker-pcem/pcem)
- **wxWidgets**: wxWindows Library Licence

## Notes

- PCem uses the `dev` branch (CMake-based build)
- ROMs are sourced from mirror.linjama.com with archive.org fallback
- Runtime: org.freedesktop.Platform 25.08
- Requires LLVM 20 SDK extension for Clang compiler
