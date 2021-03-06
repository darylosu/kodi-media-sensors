# Kodi Recently Added Media for Home Assistant

[![](https://img.shields.io/github/release/jtbgroup/kodi-media-sensors/all.svg?style=for-the-badge)](https://github.com/jtbgroup/kodi-media-sensors)
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/hacs/integration)
[![](https://img.shields.io/github/license/jtbgroup/kodi-media-sensors?style=for-the-badge)](LICENSE)
[![](https://img.shields.io/github/workflow/status/jtbgroup/kodi-media-sensors/Python%20package?style=for-the-badge)](https://github.com/jtbgroup/kodi-media-sensors/actions)

This Home Assistant component is used to feed custom cards like [Upcoming Media Card](https://github.com/custom-cards/upcoming-media-card) and [Kodi Playlist Card](https://github.com/jtbgroup/kodi-playlist-card) with data coming from Kodi. It is based on the project of Aaron Godfrey (https://github.com/boralyl/kodi-recently-added). Check the [credits section](#credits).


![Upcoming Media Card](https://raw.githubusercontent.com/jtbgroup/kodi-media-sensors/master/assets/upcoming_media_card.png) ![Kodi Playlist Card](https://raw.githubusercontent.com/jtbgroup/kodi-media-sensors/master/assets/kodi_playlist_card.png)

# Table of Contents

- [Kodi Recently Added Media for Home Assistant](#kodi-recently-added-media-for-home-assistant)
- [Table of Contents](#table-of-contents)
  - [Installation](#installation)
    - [Pre-Installation](#pre-installation)
    - [HACS Install](#hacs-install)
    - [Manual Install](#manual-install)
    - [Integration Installation](#integration-installation)
  - [Configuration](#configuration)
    - [Configuring via Integrations](#configuring-via-integrations)
    - [Card Configuration](#card-configuration)
      - [Sample for ui-lovelace.yaml:](#sample-for-ui-lovelaceyaml)
  - [Available Sensors](#available-sensors)
  - [Upgrading from configuration.yaml to UI Integration](#upgrading-from-configurationyaml-to-ui-integration)
  - [Known Issues](#known-issues)
    - [Artwork does not load when using the upcoming-media-card](#artwork-does-not-load-when-using-the-upcoming-media-card)
    - [Genres, ratings and studios don't show up for TV Shows](#genres-ratings-and-studios-dont-show-up-for-tv-shows)
  - [Credits](#credits)

## Installation

### Pre-Installation

**NOTE: This component has been tested with Home Assistant 2021.1.3 only. Additionally Kodi must be setup via the UI in the integrations section of the Home Assistant configuration.**

### HACS Install

1. Search for `Kodi Media Sensors` under `Integrations` in the HACS Store tab.
2. **You will need to restart after installation for the component to start working.**
3. Go to [Integration Installation](#integration_installation) your sensor using the options.

### Manual Install

** This method is not recommended **

1. In your `/config` directory, create a `custom_components` folder if one does not exist.
2. Copy the [kodi_media_sensors](https://github.com/jtbgroup/kodi-media-sensors/tree/master/custom_components) folder and all of it's contents from to your `custom_components` directory.
3. Restart Home Assistant.
4. Go to [Integration Installation](#integration-installation) your sensor using the options.

### Integration Installation

1. After Automatic install or manual install, go to the Integration panel (under Configuration section) and search for the ne component by clicking on the button 'Add Integration'. Enter the name of the component (Kodi Media Sensors).
2. During the installation, choose the Kodi entity previously installed.
3. Select the sensors you want to use (see [Available Sensors](#available-sensors))
4. Click Submit
5. You should now see new entities in Home Assistant (one for each sensor activated)

It's not possible to add new sensors after installation, so if you need new ones (or if you don't need one anymore), just uninstall the integration and add it again. You will then be able to select the sensors you need.

## Configuration

### Configuring via Integrations

An `Options` button will appear on the integration. Clicking this will allow you to
toggle additional options. Currently the only option is whether or not the "recently added" should
ignore watched media or not. By default it does not.

### Card Configuration

#### Sample for ui-lovelace.yaml:

Depending on the sensors you added and the custom card you installed, you can use the code below to display information from Kodi. 

Here two examples with [Upcoming Media Card](https://github.com/custom-cards/upcoming-media-card) and [Kodi Playlist Card](https://github.com/jtbgroup/kodi-playlist-card)

```yaml
- type: custom:upcoming-media-card
  entity: sensor.kodi_recently_added_tv
  title: Recently Added Episodes
  image_style: fanart

- type: custom:kodi-playlist-card
  entity: sensor.kodi_playlist
```
## Available Sensors

   * `sensor.kodi_recently_added_tv` tracks your recently added tv shows 
   * `sensor.kodi_recently_added_movies` tracks your recently added movies
   * `sensor.kodi_playlist`tracks your playlist in Kodi (audio and video)

## Upgrading from configuration.yaml to UI Integration

1. Remove any sensors in your `configuration.yaml` that reference the `kodi_media_sensors`
   platform.
2. Restart Home Assistant.
3. Follow the steps from the begining in the section [Installation](#installation)

## Known Issues

Below is a list of known issues that either can't be fixed by changes to the component
itself due to external factors.

### Artwork does not load when using the upcoming-media-card

One reason this could occur is if you setup you Home Assistance instance to use SSL and
your Kodi instance does not use SSL. When the upcoming-media-card tries to load the
artwork it will fail to do so since modern browsers do not allow loading insecure requests.
See [#6](https://github.com/boralyl/kodi-recently-added/issues/6) for more details and
possible workarounds.

### Genres, ratings and studios don't show up for TV Shows

Currently genres, rating, and studio are only populated for Movies. This is a limitation
of the data Kodi stores for TV shows.

## Credits

[Aaron Godfrey](https://github.com/boralyl) is the original developer of this project and did an excellent job. As I needed 
something similar to display my running playlist in Kodi, I started to enhance the component. 
Thanks a lot Aaron for letting me enhance your project! Let's hope other people might find it useful.
Do not hesitate to support Aaron and his many projects.