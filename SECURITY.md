# Security policy

FocusRGB plugins run as separate processes with the user's permissions, so a vulnerability in
the app, the plugin host, an SDK or an official plugin can matter.

## Reporting a vulnerability

**Please do not open a public issue.** Report privately through GitHub instead: open the affected
repository → **Security** → **Report a vulnerability**. Private vulnerability reporting is enabled
on every FocusRGB repository.

Include what you found, how to reproduce it, the affected version or commit, and the impact you
expect. You will get an acknowledgement as soon as the maintainer sees it. Fixes are released as
a new version, and the report is credited unless you ask otherwise.

## Supported versions

FocusRGB is in early development and has no stable release yet. Security fixes go to the latest
`develop` branch and the most recent published packages:

- the `FocusRgb.PluginSdk` NuGet package, and the npm and PyPI SDKs once they are published;
- the latest release of each official plugin.

Assisted-by: Claude
