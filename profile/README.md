# FocusRGB

**Lighting that follows what you're doing.** FocusRGB is an open-source desktop RGB controller.
It switches lighting profiles automatically depending on the app or game in focus, and it is
built around plugins.

> 🚧 **Early development.** No release is published yet. Follow the [roadmap](https://github.com/orgs/FocusRGB/projects/1)
> for progress.

## Repositories

| Repository | What it is |
|---|---|
| [**FocusRGB**](https://github.com/FocusRGB/FocusRGB) | The desktop app (.NET 10 and Avalonia), the portable core, the plugin host and the protocol spec |
| [**FocusRGB-Plugin-SDK**](https://github.com/FocusRGB/FocusRGB-Plugin-SDK) | Official plugin SDKs: .NET (`FocusRgb.PluginSdk` on nuget.org), with Node and Python planned |
| [**FocusRGB-Plugin-SignalRGB**](https://github.com/FocusRGB/FocusRGB-Plugin-SignalRGB) | Official plugin that lets SignalRGB render FocusRGB profiles |
| [**FocusRGB-Plugin-Steam**](https://github.com/FocusRGB/FocusRGB-Plugin-Steam) | Official discovery plugin that scans installed Steam games and launch executables |

## How it works

- **Profiles:** each profile has one effect and one layout. The app chooses a profile manually,
  or automatically from an ordered list of application groups. The top matching rule wins.
- **Plugins:** output and integrations run as separate processes that talk to the app over a
  versioned JSON-RPC protocol on stdio. Remove a plugin and the app keeps working.
- **Game frames:** game integration plugins read game data and emit direct RGB frames; the host
  accepts those frames only while the bound game profile is active, routing them to output.
- **Windows first:** the core is portable, so other platforms can follow.

```mermaid
flowchart TD
    subgraph Host["FocusRGB Desktop Host"]
        App["Focused App or Game"] --> Rules["Ordered Rules\n(Manual override wins)"]
        Rules --> Active["Active Profile"]
        Gate{"Game Profile Active?"}
        Frames["Plugin RGB Frames"] --> Gate
        Active --> OutputRouter["Output Routing"]
        Gate -- Yes --> OutputRouter
        Gate -- No --> Discard["Discarded"]
    end

    subgraph Plugins["Process Plugins (stdio JSON-RPC)"]
        GamePlugin["Game Integration Plugin\n(e.g., Telemetry to RGB)"] --> Frames
        OutputRouter --> RenderPlugin["Rendering Plugin\n(SignalRGB today, native planned)"]
    end

    RenderPlugin --> Devices["RGB Devices & Hardware"]
```

### Protocol and SDKs

Protocol changes are defined and tagged in the main repository before reaching SDKs and plugins.

```mermaid
flowchart LR
    Spec["FocusRGB\nsdk/spec/"] --> Tag["Tagged Spec Release\nspec-vX.Y.Z"]
    Tag --> SDKs["Official SDKs\n(.NET on nuget.org; Node & Python planned)"]
    SDKs --> Plugins["FocusRGB Plugins"]
```

## Contributing

- **Bugs and ideas:** open an issue in the [main repository](https://github.com/FocusRGB/FocusRGB/issues).
- **Writing a plugin:** plugins communicate with the host over versioned stdio JSON-RPC. The protocol contract is normatively documented in [`sdk/spec/`](https://github.com/FocusRGB/FocusRGB/tree/spec-v1.2.0/sdk/spec) and can be implemented in any language. .NET developers can use [`FocusRgb.PluginSdk`](https://www.nuget.org/packages/FocusRgb.PluginSdk) on nuget.org; official Node and Python SDKs are planned.
- **Official plugins** are repositories in this organization that carry the
  `focusrgb-plugin` topic.

FocusRGB is developed and maintained by **Devantix**.
Licensed under MIT.
