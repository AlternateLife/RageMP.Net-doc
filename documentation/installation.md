# **Installation**

Before you can start using AlternateLife.RageMP.Net, you need to check following requirements:

## Downloads

- Latest [.NET Core 2.2 SDK](https://www.microsoft.com/net/download/dotnet-core/2.2) *(Last tested: 2.2.5)*
- Latest RAGE Multiplayer serverfiles [(Download Launcher)](https://www.rage.mp)    
   - *The server files are contained in the RAGE Multiplayer installation.*
- Latest [AlternateLife.RageMP.Net ZIP](https://github.com/AlternateLife/RageMP.Net/releases/latest)

## Step 1

Uninstall the pre-installed GTA-Network bridge from the default RAGE Multiplayer server installation:

- Delete plugin-file `<server-files>/plugins/bridge.dll`.
- Delete folder `<server-files>/bridge/`.

## Step 2

Extract the AlternateLife.RageMP.Net ZIP file (see [downloads](#downloads)) that contains following folders: `dotnet` and `plugins` and paste it into your root server folder.

The RAGE Multiplayer server folder should look like this now:

```text
├── client_packages/
├── dotnet/
|   ├── plugins/
|   |   └── ...
|   ├── resources/
|   |   └── example/
|   ├── runtime/
|   |   └── ...
|   └── NLog.config
├── maps/
├── packages/
├── plugins/
|   └── dotnet-wrapper.dll
├── bt.dat
├── conf.json
├── node.dll
└── server.exe
```

*If you want to install your own gamemode, you can delete the `example` folder under `<server-folder>/dotnet/resources`*

## Step 3

Create your first serverside resource by implementing the interface `IResource`.