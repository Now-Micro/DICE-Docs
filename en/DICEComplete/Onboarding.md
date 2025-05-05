# Onboarding DICE Complete

Onboarding DICE Complete can be simplified by deploying the agent to devices to populate a wide swath of information without having to upload existing records.

1. Deploy Agents via GPO, Microsoft Intune or Microsoft MEMCM.  See [Agents](../../Agents/Agent.md)
1. Upload end user information (optional).  End user information can be utilized in the Assets section to assign assets to users.  This is optional, as the agent will populate current logged in username via the DICE Complete agent.
1. Upload asset information (optional).  Assets will be populated by agent check ins.  Location and other metadata can be amended via the UI or bulk import.  See [Importing Assets](../AssetManagement/ImportingAssets.md) for more information.
1. Invite tool users to DICE with initial roles

## Advanced
Since DICE is an API driven platform, data can be imported via APIs in addition to the UI driven upload interfaces. API information and example data structures are available in [DICE Swagger](https://diceapp.nowmicro.com/swagger).
Please contact support if you need additional assistance, including example scripts.
