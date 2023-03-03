# Agent Information

DICE Complete provides an agent driven experience for Microsoft Windows, Linux and Apple MacOS.  
The agent must be installed to take advantage of these features.

Current Agent (4.1)

## Windows 
The agent can be installed via GPO, script, command line, Microsoft MEMCM (ConfigMgr) or Microsoft Intune.

### Download
[Windows](/Agents/4.1/NowMicro.Dice.Agent.Installer.msi)

### Windows command line options
For a silent installation, the following command can be used.  Substitute <APIKEY> with your 
API key from Organization | Organations Management | Api Key

```csharp
	msiexec /i "NowMicro.Dice.Agent.Installer.msi" /qn PSK=<APIKEY>
```

