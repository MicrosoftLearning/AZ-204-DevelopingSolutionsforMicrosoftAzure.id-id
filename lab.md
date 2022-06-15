---
ms.openlocfilehash: 57e7101c824903545932fce809cd5661f95cd3dd
ms.sourcegitcommit: d2d374fffa4fcbf92b9c4bdc9c9ecc470152e033
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 11/16/2021
ms.locfileid: "145196327"
---
# <a name="lab-virtual-machine-setup"></a>Penyiapan Mesin Virtual Lab

## <a name="installed-software"></a>Perangkat Lunak yang Diinstal

| Perangkat lunak | Link |
| --- | --- |
| Windows 10 (Build 2004) | <https://www.microsoft.com/software-download/windows10> |
| Visual Studio Code | <https://code.visualstudio.com> |
| Ekstensi Visual Studio Code Akun Azure | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account> |
| Ekstensi Visual Studio Code Azure Functions | <https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions> |
| Ekstensi Alat Visual Studio Code Azure Resource Manager | <https://marketplace.visualstudio.com/items?itemName=msazurermtools.azurerm-vscode-tools> |
| Ekstensi Alat Azure CLI Visual Studio Code | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.azurecli> |
| Ekstensi PowerShell Visual Studio Code | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell> |
| Ekstensi C# Visual Studio Code | <https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp> |
| PowerShell 7 | <https://github.com/PowerShell/PowerShell/releases/tag/v7.0.3> |
| SDK .NET Core 3.1 | <https://dotnet.microsoft.com/download/dotnet-core/3.1> |
| Azure PowerShell | <https://docs.microsoft.com/powershell/azure/install-az-ps> |
| Azure CLI | <https://docs.microsoft.com/cli/azure/install-azure-cli> |
| Azure Storage Explorer | <https://azure.microsoft.com/features/storage-explorer> |
| Alat .NET - HttpRepl | <https://github.com/dotnet/HttpRepl> |
| Azure Functions Core Tools | <https://docs.microsoft.com/azure/azure-functions/functions-run-local#v3> |
| Windows Terminal | <https://aka.ms/terminal> |
| Azure Stack Edge (chromium) | <https://www.microsoft.com/edge> |

## <a name="additional-configuration"></a>Konfigurasi Tambahan

- Aktifkan ClearType
  
- Konfigurasikan Microsoft Edge sebagai browser default

- Perbarui konfigurasi VSCode

  ```json
  {
    "editor.fontFamily": "'Cascadia Code', Consolas, 'Courier New', monospace",
    "update.enableWindowsBackgroundUpdates": false,
    "update.mode": "manual",
    "terminal.integrated.shell.windows": "C:\\Program Files\\PowerShell\\7\\pwsh.exe",
    "workbench.startupEditor": "none",
    "terminal.integrated.rendererType": "dom",
    "csharp.suppressDotnetInstallWarning": true,
    "csharp.suppressDotnetRestoreNotification": true,
    "csharp.supressBuildAssetsNotification": true,
    "azureFunctions.showProjectWarning": false
  }
  ```

- Perbarui konfigurasi Terminal Windows

  ```json
  {
    "$schema": "https://aka.ms/terminal-profiles-schema",
    "defaultProfile": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
    "profiles": [
      {
        "guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
        "useAcrylic": true,
        "acrylicOpacity": 0.85,
        "colorScheme": "Campbell",
        "fontFace": "Cascadia Code",
        "hidden": false,
        "name": "PowerShell",
        "source": "Windows.Terminal.PowershellCore"
      },
      {
        "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
        "hidden": false,
        "name": "Azure Cloud Shell",
        "source": "Windows.Terminal.Azure"
      }
    ],
    "schemes": [],
    "keybindings": []
  }
  ```

- Konfigurasikan Start Menu & Taskbar untuk menyertakan ikon berikut saja:
  - File Explorer
  - Azure Stack Edge
  - Windows Terminal
  - Visual Studio Code
  - Azure Storage Explorer

- Nonaktifkan pemberitahuan pembaruan PowerShell 7

  1. [Buat variabel lingkungan](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7) bernama ``POWERSHELL_UPDATECHECK``
  
  1. Atur nilai variabel lingkungan ke ``Off`` (peka huruf besar-kecil)

- Jalankan Azure Functions Core Tools setidaknya sekali untuk mengonfigurasi Windows Firewall

  ```bash
  func init test --worker-runtime dotnet
  cd test
  func new --template 'HTTP trigger' --name web
  func start --build
  ```
