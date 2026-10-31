# LG WebOS Magic Remote Custom

A customized version of the [LG WebOS Remote Control](https://github.com/madmicio/LG-WebOS-Remote-Control) Home Assistant Lovelace card.

This project preserves the original card's functionality and appearance while adding support for custom local image icons in the `sources` configuration.

## Customization

- Support for custom local images using Home Assistant `/local/` paths in `sources.icon`.
- Existing Material Design Icons (`mdi:`), built-in icons and special application icons remain supported.
- Includes custom RTL+ Magyarország and CANAL+ application icons.

The original card functionality, configuration options and visual appearance are preserved.

## Credits and license

Original project: [LG WebOS Remote Control](https://github.com/madmicio/LG-WebOS-Remote-Control)

Original developers: [Maurizio (madmicio)](https://github.com/madmicio) and [Piotr Machowski](https://github.com/PiotrMachowski).

This project retains the original MIT license. See [LICENSE](LICENSE) for details.

## HACS installation

1. Open Home Assistant.
2. Navigate to **HACS → Integrations → Custom repositories** (or the custom repository option in your HACS interface).
3. Add the following repository URL:

   `https://github.com/krisztianszoke/lg-webos-magic-remote-custom`

4. Select **Dashboard** as the repository category.
5. Add the repository and install **LG WebOS Magic Remote Custom**.
6. Add the resource if it is not registered automatically:

```yaml
resources:
  - type: module
    url: /hacsfiles/lg-webos-magic-remote-custom/lg-remote-control.js
```

7. Refresh the browser and add the card to your dashboard.

### Manual installation

1. Download `lg-remote-control.js` from the latest GitHub Release.
2. Copy it into your Home Assistant `www` directory.
3. Register the resource:

```yaml
resources:
  - type: module
    url: /local/lg-remote-control.js
```

### Custom local image icons

This custom version supports local image files in the `sources.icon` configuration.

You can use:
- Material Design Icons, such as `mdi:netflix`
- Built-in application icons
- Special icons such as `disney`, `amazon` and `dazn`
- Custom local images using Home Assistant `/local/` paths

#### Example

```yaml
sources:
  - name: Netflix
    icon: mdi:netflix

  - name: YouTube
    icon: mdi:youtube

  - name: CANAL+
    icon: /local/images/canal_plus_icon.png

  - name: RTL+ Magyarország
    icon: /local/images/rtl_logo_icon.png
```

#### Image installation

1. Create an `images` directory inside your Home Assistant `www` directory.
2. Copy your PNG files into that directory.
3. Reference them using `/local/images/filename.png`.

Example directory structure:

```text
/config/
└── www/
    └── images/
        ├── canal_plus_icon.png
        └── rtl_logo_icon.png
```

**Important:** Home Assistant maps the `/config/www/` directory to the `/local/` URL prefix. Do not use `/config/www/` in the card configuration.