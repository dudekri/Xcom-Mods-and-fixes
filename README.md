# Xcom-Mods-and-fixes

## Installation

For **XCOM 2: War of the Chosen on Windows**, using the Alternative Mod Launcher (AML).

1. **Close XCOM 2.**
2. Download and extract the release ZIP.
3. Copy the included **`XCom2-WarOfTheChosen`** folder into your XCOM 2 installation directory, usually:
   ```text
   ...\Steam\steamapps\common\XCOM 2\
   ```
4. Merge the folders when prompted. The installed files should be at:
   ```text
   XCOM 2\XCom2-WarOfTheChosen\Binaries\Win64\dinput8.dll
   XCOM 2\XCom2-WarOfTheChosen\XComGame\Mods\WotCNativeCrashFix\WotCNativeCrashFix.XComMod
   ```
5. Open or restart AML and enable **WotC Native Crash Fix**.
6. Launch War of the Chosen normally. On first enabled use, acknowledge the restart prompt, then launch the game again with the mod enabled.

**Already have a `dinput8.dll` in that location?** Replace it only if it belongs to an earlier version of this fix. Do not overwrite a DLL supplied by another mod; DLL chaining is not supported.

### Mod not appearing in AML?

Ensure AML’s mod directories include:
```text
...\XCOM 2\XCom2-WarOfTheChosen\XComGame\Mods
```
Then refresh the mod list or restart AML.

### How it works

The DLL applies the HQ buffer-overflow repair and the candidate Avenger-return crash repair automatically in memory. **No replacement `XCom2.exe` is included or required, and this package does not rewrite the executable on disk.**

The fixes remain active for the entire game session, including save loading and returning to the Avenger.

### Disable or uninstall

To disable, uncheck **WotC Native Crash Fix** in AML and restart XCOM.

To uninstall, close XCOM and remove:

- The `WotCNativeCrashFix` folder from `XComGame\Mods`.
- This package’s `dinput8.dll` from `Binaries\Win64`.

If you previously installed an executable patch, uninstalling this DLL does not undo that older disk modification.

### Testing status

**Experimental release.** The original executable-based overflow fix successfully restored loading of an affected save in testing. This DLL-based package and the Avenger-return repair still require in-game validation. Other executable builds may be rejected by the loader’s compatibility checks.
