# Process Optimizer - Windows Installer

A native **.NET 8** Windows desktop application for inspecting and tuning running processes: a tabbed UI (optimizer / settings / diagnostics / about), a tray icon, live process data, per-process priority and affinity control, a boost loop, diagnostics export, and English, Arabic, German, Spanish, French, Russian and Chinese UI.

Two build layouts are published here.

| File | Size | SHA-256 |
|---|---|---|
| `ProcessOptimizer.msi` (1.0.0, 2026-05-01) | 1,482,752 bytes | `859975C574459A9A4BFA8EC610696F2A8CFAA5D47BCFD4102779C8F7A7F38D95` |
| `ProcessOptimizer-1.0.0-portable-fd.zip` (2026-04-23) | 1,131,798 bytes | `8AD31EBDDBBB336398550A89BFB31ABF2CBC9E5E7B15123558A16DFA8E9DCCE2` |

## Requirements

- Windows 10 or Windows 11, x64
- **.NET 8 Desktop Runtime** (both packages are framework-dependent): https://dotnet.microsoft.com/download/dotnet/8.0
- Administrator rights - the app requests elevation because process priority and affinity changes need it

## Install with the MSI

1. Download `ProcessOptimizer.msi`.
2. Double-click it. Windows SmartScreen shows "Windows protected your PC" because the build is not Authenticode-signed - choose **More info -> Run anyway**.
3. Accept the UAC prompt, then finish the wizard.
4. Start **Process Optimizer** from the Start Menu.

Optional flag:

```
msiexec /i ProcessOptimizer.msi INSTALLDESKTOPSHORTCUT=0
```

That installs without a desktop shortcut.

## Run the portable build

1. Download `ProcessOptimizer-1.0.0-portable-fd.zip` and extract it to any folder.
2. Double-click `ProcessOptimizer.Desktop.exe`.
3. Accept the UAC prompt.

Nothing is written to Program Files; settings and logs live under `%LocalAppData%\ProcessOptimizer`.

## Verify a download

```powershell
Get-FileHash .\ProcessOptimizer.msi -Algorithm SHA256
Get-FileHash .\ProcessOptimizer-1.0.0-portable-fd.zip -Algorithm SHA256
```

Compare against the table above.

## Notes

- The MSI is a WiX 6 package with a Start Menu shortcut, an optional desktop shortcut and Add/Remove Programs metadata.
- Neither artifact is Authenticode-signed, so SmartScreen warns on first run. The hash table above is the integrity check.
- The portable ZIP is an older 1.0.0 publish (2026-04-23) and ships the Desktop host only; the MSI is the newer build (2026-05-01) and also includes the bootstrap launcher.

## Source

The application source is not published in this repository. This repository carries the installers only.

## License

All rights reserved. This is **not** an MIT-licensed project and no open-source license is granted for the application, the MSI or the portable build. You may download and install them for personal use. Redistribution, modification or republishing is not permitted.