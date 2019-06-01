# Upgrade from v1.1 to v1.2

This version contains many changes in favor of stability and performance. In this guide we list all breaking changes and how to migrate to the latest implementations.

## Migration

### Events

All events received an overhaul and now follow the [standard .NET event pattern](https://docs.microsoft.com/en-us/dotnet/csharp/event-pattern). The event-signature now contains the sender of that event and the arguments as the second parameter.

#### Changes

Before:
```cs
public async Task OnPlayerReady(IPlayer player) 
{
    player.OutputChatBox("Hey!");
}
```

After:
```cs
public async Task OnPlayerReady(object sender, PlayerEventArgs eventArgs)
{
    IPlayer player = eventArgs.Player;

    player.OutputChatBox("Hey!");
}
```

### Properties

We replaced all properties with getter and setter methods to streamline synchronous and asynchronous methods. This way is much cleaner in regards of exception handling and simplicity in combination with asynchronous methods.

#### Changes

Before
```cs
Vector3 position = player.Position;

player.Position += new Vector3(0, 1, 0);
```

After
```cs
Vector3 position = player.GetPosition();

player.SetPosition(position + new Vector3(0, 1, 0));
```

### Utility API

In order to clean up the `MP` class we moved all methods into a special utility class, accessible from `MP.Utility`.

[See IUtility interface documentation](~/api/AlternateLife.RageMP.Net.Interfaces.IUtility.yml)

#### Changes

Before
```cs
MP.Joaat("name");

MP.Schedule(() => {
    // Calls
});
```

After
```cs
MP.Utility.Joaat("name");

MP.Utility.Schedule(() => {
    // Calls
});
```