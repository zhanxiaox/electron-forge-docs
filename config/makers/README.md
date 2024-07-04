---
description: >-
  Generate platform specific distributables for Electron apps using Electron
  Forge.
---

# Makers

Makers are Electron Forge's way of taking your packaged application and making platform specific distributables like DMG, EXE, or Flatpak files \(amongst others\).

Each maker has to be configured in the `makers` section of your forge configuration with which platforms to run for and the maker specific config. E.g.

{% tabs %}
{% tab title="forge.config.js" %}
```javascript
module.exports = {
  makers: [
    {
      name: '@electron-forge/maker-zip',
      platforms: ['darwin', 'linux'],
      config: {
        // the config can be an object
      }
    },
    {
      name: '@electron-forge/maker-dmg',
      config: (arch) => ({
        // it can also be a function taking the currently built arch
        // as a parameter and returning a config object, e.g.
      })
    }
  ]
};
```
{% endtab %}
{% tab title="package.json" %}
```jsonc
// If your config is only in package.json:
// Only showing the relevant configuration for brevity
{
  "config": {
    "forge": {
      "makers": [
        {
          "name": "@electron-forge/maker-zip",
          "platforms": ["darwin", "linux"], // optional
          "config": {
              // Config here
          }
        }
      ]
    }
  }
}
```
{% endtab %}
{% endtabs %}

Please note that all makers have logical defaults for the `platforms` value so you normally don't need to specify that property.

