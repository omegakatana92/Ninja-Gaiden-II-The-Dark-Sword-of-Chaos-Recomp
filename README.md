# Ninja Gaiden II: The Dark Sword of Chaos — NESRecomp (Windows x64)

A cycle-accurate native recompilation of the NES game **Ninja Gaiden II: The
Dark Sword of Chaos (USA)**, built with mstan's
[NESRecomp](https://github.com/mstan/nesrecomp) framework.

The 6502 CPU is statically recompiled to native x64 code; the PPU, MMC3
mapper, APU, and input are the framework's cycle-accurate implementations.

> No ROM is included. This project ships only redistributable code and build
> configuration. Supply your own legally obtained Ninja Gaiden II cartridge
> image (.nes) at first launch.

## Supported cartridge

| Property | Value |
| --- | --- |
| Title | Ninja Gaiden II - The Dark Sword of Chaos (USA) |
| PRG-ROM | 128 KB |
| CHR-ROM | 128 KB |
| Mapper | 4 (MMC3) |
| Mirroring | horizontal |
| Verified SHA-256 (after iNES header) | `21c51dc47a458a7de66544533d56eb9a69de0190d012b1645699e816d2cb5008` |

## Building from source

Requires: Visual Studio 2022 or 2026 with the MSVC x64 toolset (or another C11
C/C++ compiler), CMake 3.20+, Python 3.11+, and SDL2.

```powershell
# 1. Fetch the NESRecomp framework (this project assumes it sits at ../nesrecomp)
git clone --depth 1 https://github.com/mstan/nesrecomp.git ../nesrecomp
cd ../nesrecomp
git submodule update --init --recursive
git submodule add https://github.com/mstan/recomp-ui.git recomp-ui

# 2. Copy the recomp-ui submodule into the game project
cp -r ../nesrecomp/recomp-ui ./recomp-ui

# 3. Configure and build
cmake -S . -B build -G "Visual Studio 17 2022" -A x64
cmake --build build --config Release --parallel 4
```

The executable is `build/Release/NinjaGaidenIIRecomp.exe`.

## Running

```powershell
# With a verified ROM path:
.\build\Release\NinjaGaidenIIRecomp.exe "C:\path\to\Ninja Gaiden II - The Dark Sword of Chaos (USA).nes"

# Or without arguments: the launcher opens and asks for a ROM.
```

## Controls

| Action | Keyboard | Gamepad |
| --- | --- | --- |
| D-pad | Arrow keys | D-pad |
| A (Dragon Sword) | Z | A |
| B (Jump) | X | B |
| Start | Enter | Start |
| Select | Backslash | Select |
| Menu | Escape | — |
| Fast-forward | hold Tab | — |
| Save state | F8 | — |
| Load state | F9 | — |

## License

- NESRecomp: [LICENSE](../nesrecomp/LICENSE) — `licenses/NESRecomp-LICENSE.txt`
- SDL2: `licenses/SDL2-COPYING.txt`
- Dear ImGui: `licenses/Imgui-LICENSE.txt`

This project contains no copyrighted ROM data and no extracted proprietary
game assets.