# FocusRGB

**Lighting that follows what you're doing.** FocusRGB is an open-source desktop RGB controller.
It switches lighting profiles automatically depending on the app or game in focus, and it is
built around plugins.

> 🚧 **Early development.** No release is published yet. Follow the [roadmap](https://github.com/orgs/FocusRGB/projects/1)
> for progress.

## Repositories

| Repository | What it is |
|---|---|
| [**FocusRGB**](https://github.com/FocusRGB/FocusRGB) | The desktop app (.NET 10 and Avalonia), the portable core, the plugin host, and `FocusRgb.PluginSdk` |
| [**FocusRGB-Plugin-SignalRGB**](https://github.com/FocusRGB/FocusRGB-Plugin-SignalRGB) | Official plugin that lets SignalRGB render FocusRGB profiles |

## How it works

- **Profiles:** each profile has one effect and one layout. The app chooses a profile manually,
  or automatically from an ordered list of application groups. The top matching rule wins.
- **Plugins:** output and integrations run as separate processes that talk to the app over a
  small JSON-RPC protocol on stdio. Remove a plugin and the app keeps working.
- **Windows first:** the core is portable, so other platforms can follow.

## Contributing

- **Bugs and ideas:** open an issue in the [main repository](https://github.com/FocusRGB/FocusRGB/issues).
- **Writing a plugin:** C# authors can use `FocusRgb.PluginSdk`. A documented,
  language-neutral protocol is planned ([#79](https://github.com/FocusRGB/FocusRGB/issues/79)).
- **Official plugins** are repositories in this organization that carry the
  `focusrgb-plugin` topic.

Licensed under MIT.
