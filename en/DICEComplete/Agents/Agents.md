# Agents

DICE Complete provides an agent driven experience for Microsoft Windows, Linux and Apple MacOS.  

The agent must be installed to take advantage of these features and consists of a non-interactive agent (DICE Complete) and a KVM agent (DICE Complete KVM Agent).  The non-interactive agent is installed by default and the KVM agent must be installed separately.

## DICE Complete Agent (Windows)
The DICE Complete agent can be installed via GPO, script, command line, Microsoft MEMCM (ConfigMgr) or Microsoft Intune.

### Installation 
Agent download: [Windows Agent MSI](https://github.com/Now-Micro/DICE-Docs/raw/main/en/DICEComplete/Agents/4.1/NowMicro.Dice.Agent.Installer.msi)

#### MSI command line options
For a silent installation, the following command can be used.  Substitute <APIKEY> with your 
API key from: [Organization](https://diceapp.nowmicro.com/Organization) | Organization Management | Api Key

```cmd
	msiexec /i "NowMicro.Dice.Agent.Installer.msi" /qn PSK=<APIKEY>
```

### Microsoft Intune Installation
See the image below for a basic MSI based installation performed by Microsoft Intune.

![image](https://github.com/Now-Micro/DICE-Docs/raw/main/en/DICEComplete/Agents/4.1/MicrosoftIntunePackageSetup.png)

## DICE Complete Agent (Windows) Troubleshooting
Log files for the DICE Agent are available at: C:\ProgramData\Now Micro\Logs.  These logs can be provided to support to troubleshoot individual agent issues.


## Apple MacOS and Linux agents
Please [contact support](https://nowmicro.com/contact) for the newest agent download.

## DICE Complete KVM Agent Installation

**Please contact support for the KVM agent installation package.**

**Installation**
```powershell
.\dicecompletekvm64.exe -fullinstall
```

**Verification**
```powershell
Get-Service DICECompleteKVMAgentService
(Get-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Open Source\DICECompleteKVMAgentService" -Name NodeId).NodeId
```

**Uninstallation**
```powershell
.\dicecompletekvm64.exe -fulluninstall
```

## KVM Agent TroubleShooting
```powershell
# Verify the service is running
$serviceStatus = (Get-Service DICECompleteKVMAgentService).Status

# Get the Agent Values
$primaryRegistryPath = "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Open Source\DICECompleteKVMAgentService"
$secondaryRegistryPath = "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Open Source\DICEComplete"

if (Test-Path $primaryRegistryPath) {
    $registryPath = $primaryRegistryPath
}
elseif (Test-Path $secondaryRegistryPath) {
    $registryPath = $secondaryRegistryPath
}
else {
    Throw "Neither registry key was found: `n  $primaryRegistryPath`n  $secondaryRegistryPath"
}

$agentValues = Get-ItemProperty -Path $registryPath
$meshId        = $agentValues.MeshId
$nodeId        = $agentValues.NodeId
$meshServerId  = $agentValues.MeshServerId
$meshServerUrl = $agentValues.MeshServerUrl

$alternateRegistryPath = "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Open Source\MeshAgent2"
Set-ItemProperty -Path $alternateRegistryPath -Name MeshId -Value $meshId
Set-ItemProperty -Path $alternateRegistryPath -Name NodeId -Value $nodeId
Set-ItemProperty -Path $alternateRegistryPath -Name MeshServerId -Value $meshServerId
Set-ItemProperty -Path $alternateRegistryPath -Name MeshServerUrl -Value $meshServerUrl

# Restart the KVM service
Restart-Service DICECompleteKVMAgentService -Force

# Restart the non-interactive agent service
Restart-Service NowMicroDICE -Force
```
