Ninja Gaiden II: The Dark Sword of Chaos — NES Recomp
An unofficial native Windows x64 recompilation project for Ninja Gaiden II: The Dark Sword of Chaos (NES), using mstan's NESRecomp framework.

NESRecomp translates NES 6502 machine code into generated C source, which can be compiled and integrated with its native runner. This repository is intended to provide a Windows port that uses a compatible, user-supplied ROM.
Status: Experimental / in development. A successful source-generation or library build does not by itself establish a playable game. Confirm the executable, launcher, and gameplay tests before marking a release stable.

Planned features
- Native Windows x64 executable (NinjaGaidenIIRecomp.exe)
- ROM-selection launcher and compatibility validation
- Keyboard and SDL-compatible controller input
- Windowed and fullscreen display
- Original gameplay, cinematics, graphics, and audio sourced from the user's compatible ROM
Availability of these features depends on the specific release and its testing status.
Requirements
- Windows 10 or 11, 64-bit (target platform)
- A compatible, legally obtained Ninja Gaiden II: The Dark Sword of Chaos (USA) .nes ROM
- Any runtime dependencies listed with the particular release
No game ROM is provided here.
Running a verified Windows release
1. Download the Windows x64 ZIP from Releases, if one is available.
2. Extract the ZIP to a folder.
3. Launch NinjaGaidenIIRecomp.exe if it is included in that release.
4. Select your compatible NES ROM through the launcher, if supported by that build.
5. Start the game.
Check each release's notes for verified features and known issues. Do not assume the steps above work until the corresponding build has been tested.
Building from source
NESRecomp Windows CLI: Releases

Example source-generation command in PowerShell:
$root = 'C:\Users\omega\Documents\tools\nesrecomp-cli-windows-x86_64'
& "$root\nesrecomp.exe" build `
  --rom "$root\game\Ninja Gaiden II - The Dark Sword of Chaos (USA).nes" `
  --output "$root\NinjaGaidenIIRecomp"
From the generated project folder, run build.ps1 to check that the generated static library compiles. This does not produce a playable executable on its own. A full game port also requires game-specific configuration and integration with the NESRecomp runner and SDL2. Consult the upstream documentation and the source in this repository for the actual executable build process.
Controls
NESRecomp supports configurable keyboard and SDL-compatible gamepad mappings via keybinds.ini where the native runner is integrated. See the release notes for supported controls and shortcuts.
Compatibility and known issues
- ROM variant: USA version intended; verify the actual ROM header and hash against the build's supported version.
- Gameplay: Not yet independently verified in this README.
- Audio, cinematics, saves, and later stages: Verify against the specific release before claiming full support.
Please report reproducible issues with the ROM variant/hash, build version, steps to reproduce, and relevant logs. Do not attach copyrighted ROMs.
Legal and credits
- Original game: Tecmo
- NESRecomp framework: mstan/nesrecomp
- Target platform: Windows x64
This is an unofficial fan project, not affiliated with or endorsed by Nintendo, Tecmo, or Koei Tecmo. Original game rights remain with their respective owners.

A ROM-free launcher does not automatically mean generated source or binaries are free of copyrighted game data. Audit all distributed artifacts and comply with applicable licenses before publication.
