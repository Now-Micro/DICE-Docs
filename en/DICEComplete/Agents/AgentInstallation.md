# Agent Installation

DICE Complete provides an agent driven experience for Microsoft Windows, Linux and Apple MacOS.  
The agent must be installed to take advantage of these features.

## Windows 
The agent can be installed via GPO, script, command line, Microsoft MEMCM (ConfigMgr) or Microsoft Intune.

Current Agent (4.1)

**Please contact support for an additional installation piece required to enable KVM functionality.**

### MSI Installation
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

## Apple MacOS and Linux agents
Please [contact support](https://nowmicro.com/contact) for the newest agent download.
