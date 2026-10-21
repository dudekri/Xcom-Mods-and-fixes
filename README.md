# Xcom-Mods-and-fixes

## Installation

For **XCOM 2: War of the Chosen on Windows**, using the Alternative Mod Launcher (AML).

1. **Close XCOM 2.**
2. Download and **extract the entire release ZIP**. Do not run the installer inside the ZIP.
3. Double-click **`INSTALL.cmd`**.
4. The installer finds the game through Steam, including additional Steam libraries. If it cannot find it, or finds multiple installations, paste your XCOM 2 installation folder when prompted, usually:
   ```
   C:\Program Files (x86)\Steam\steamapps\common\XCOM 2
   ```
5. Wait for **Installed and verified** (or **All 3.1 files are already installed**).
6. Open or restart AML and enable **WotC Native Crash Fix**. Launch normally. If first-use setup requests a restart, acknowledge it and launch again with the mod enabled.

**Upgrading?** Use the same installer. It upgrades the recognized 3.0 release or completes an existing 3.1 installation, backs up replaced files under `XCom2-WarOfTheChosen\NativeCrashFix-Backups`, and verifies the installed files. No SDK compilation is needed.

**Access denied?** Right-click `INSTALL.cmd` and choose **Run as administrator**.

**Already have a `dinput8.dll`?** The installer only replaces the recognized 3.0 or 3.1 DLL from this project. It refuses unknown DLLs, including those supplied by another mod. DLL chaining is not supported.

### Manual installation (optional)

Copy the included **`XCom2-WarOfTheChosen`** folder into your XCOM 2 installation directory and merge folders. Replace an existing DLL only if it belongs to this fix. The installed files should be at:

```
XCOM 2\XCom2-WarOfTheChosen\Binaries\Win64\dinput8.dll
XCOM 2\XCom2-WarOfTheChosen\XComGame\Mods\WotCNativeCrashFix\WotCNativeCrashFix.XComMod
```

Then enable the mod in AML and launch normally.

### Mod not appearing in AML?

Ensure AML's mod directories include:

```
...\XCOM 2\XCom2-WarOfTheChosen\XComGame\Mods
```

Then refresh the mod list or restart AML.

### How it works

The DLL applies the HQ buffer-overflow repair, the candidate Avenger-return crash repair, and the **3.1 large-save buffer repair** automatically in memory. **No replacement `XCom2.exe` is included or required, and this package does not rewrite the executable on disk.**

The large-save repair addresses an overflow when the game's temporary duplication buffer crosses 2 GiB during loading. It supports buffers up to approximately 4 GiB; it does not reduce save sizes or memory use, and it cannot fix every cause of a save-loading crash.

The fixes remain active for the entire game session, including save loading and returning to the Avenger.

### Disable or uninstall

To disable, uncheck **WotC Native Crash Fix** in AML and restart XCOM.

To roll back an installer upgrade, close XCOM and copy the backed-up files from that installation's dated `NativeCrashFix-Backups` folder back into `XCom2-WarOfTheChosen`, preserving their folder paths.

To uninstall, close XCOM and remove:

- The `WotCNativeCrashFix` folder from `XComGame\Mods`.
- This package's `dinput8.dll` from `Binaries\Win64`.

If you previously installed an executable patch, uninstalling this DLL does not undo that older disk modification. The separate object-table reserve patch is not included in this package.

### Testing status

**Experimental release.** The 3.1 large-save fix successfully loaded the affected save in user testing. This complete package contains that same DLL unchanged. The installer has been checked in a simulated filesystem, but has not been run on Windows here. Fresh-install compatibility and the Avenger-return repair still require further in-game validation. Other executable builds may be rejected by the loader's compatibility checks.

Source, validation reports and additional technical details are included in the release ZIP.
