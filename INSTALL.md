# Jeeves Chat installation

## For players — compiled DLL

Once you have a compiled `JeevesChat.dll`:

1. Fully close Guild Wars and GWToolbox++.
2. Find your GWToolbox++ per-computer plugin folder:

   ```text
   GWToolboxpp\<ComputerName>\plugins\
   
   Example
   C:\Users\USERNAME\Documents\GWToolboxpp\COMPUTERNAME\plugins
   ```

3. Copy `JeevesChat.dll` into that folder.
4. Start Guild Wars and GWToolbox++.
5. Open **Toolbox → Settings → Plugins**.
6. Enable **JeevesChat.dll**, then open its settings panel.
7. Leave **Enable Jeeves Chat** enabled. Enable **Color linked alliance overhead tags** if you want opposite-faction native `[TAG]` coloring.

To update, fully close Guild Wars first and replace the existing DLL with the new one.

## For developers — build from source

Current GWToolbox++ source builds require a supported Visual Studio C++ toolchain, Windows SDK, CMake, vcpkg and Git. Follow the current GWToolbox++ source-build requirements if your environment is not already configured.

### 1. Apply the Jeeves Chat source

From PowerShell:

```powershell
powershell -ExecutionPolicy Bypass -File `
  ".\update-existing.ps1" `
  -ToolboxRoot "C:\path\to\GWToolboxpp"
```

The script:

- backs up an existing `plugins\JeevesChat` source folder;
- copies the public source into `plugins\JeevesChat`;
- adds `add_tb_plugin(JeevesChat)` to the Toolbox plugin CMake configuration only if no existing JeevesChat target is found.

### 2. Configure/reconfigure CMake

```powershell
cd "C:\path\to\GWToolboxpp"
cmake --preset=vcpkg
```

### 3. Build the plugin

```powershell
cmake --build build --config RelWithDebInfo --target JeevesChat
```

Expected DLL:

```text
bin\RelWithDebInfo\JeevesChat.dll
```

### 4. Test locally

Fully close your test Guild Wars client, then copy the DLL into its Toolbox plugin folder. Example:

```powershell
Copy-Item `
  ".\bin\RelWithDebInfo\JeevesChat.dll" `
  "$env:USERPROFILE\Documents\GWToolboxpp\<ComputerName>\plugins\JeevesChat.dll" `
  -Force
```

Start Guild Wars and test chat, overhead `[TAG]` coloring, normal native hiding/stacking, and UI occlusion.

## Creating the public end-user ZIP

After the DLL has passed testing, run:

```powershell
powershell -ExecutionPolicy Bypass -File `
  ".\make-public-bundle.ps1" `
  -ToolboxRoot "C:\path\to\GWToolboxpp"
```

This creates a small public ZIP containing the compiled DLL plus the player installation guide and prints its SHA-256 hash.
