# Solarflow Control Home Assistant Add-On

[Solarflow Control][sf-control] is a full local control for Zendure Solarflow Hub components
developed by [Reinhard Weber (Brandstaedter)][reinhard-brandstaedter]. It has the following main
features:

- Read live telemetry data locally without the Zendure app and cloud
- Update the settings locally without the Zendure app and cloud
- Automatically control the charging/discharging and the power output based on the acutal consumption

## Prerequisites

In order to use this addon you need to disconnect your Solarflow Hub from the Zendure cloud and have it
only report to your local MQTT broker. You can disconnect it via the [Solarflow Bluetooth Manager][sf-bt-manager].

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Home Assistant add-on.

1. Add this repository to have addons by Daniel Figus:
   [![Home Assistant with repository URL pre-filled][my-ha-shield]][my-ha-repo]
1. Search for the "Solarflow Control" add-on in the Supervisor add-on store and install it.
1. Go to the configuration tab and configure the mandatory parameters
1. Start the "Solarflow Control" add-on.
1. Check the logs of the "Solarflow Control" to see if everything went well. Solarflow Control will
   output status messages regularily

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The Home Assistant [Community Forum][forum].
- You could also [open an issue here][issue] GitHub.

## Authors & contributors

This repository is owned and maintained by [Daniel Figus][dfigus].

This has been possible thanks to the community add-ons initiative by [Frenck][frenck]

## License

MIT License

Copyright (c) 2024-2025 Daniel Figus

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[reinhard-brandstaedter]: https://github.com/reinhard-brandstaedter
[sf-control]: https://github.com/reinhard-brandstaedter/solarflow-control
[sf-bt-manager]: https://github.com/reinhard-brandstaedter/solarflow-bt-manager
[forum]: https://community.home-assistant.io/
[frenck]: https://github.com/frenck
[dfigus]: https://github.com/dfigus
[my-ha-shield]: https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg
[issue]: https://github.com/dfigus/addon-solarflow-control/issues
[semver]: http://semver.org/spec/v2.0.0.htm
[my-ha-repo]: https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fdfigus%2Fhassio-addons
[releases]: https://github.com/dfigus/addon-solarflow-control/releases
