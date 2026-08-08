# esp-web-tools (vendored)

esp-web-tools 10.4.0, Apache-2.0, from https://github.com/esphome/esp-web-tools

Served from this repository rather than a CDN. The installer page previously
loaded it from unpkg.com, which meant the Install button silently did nothing
if the visitor had no internet — including the entirely plausible case of
someone connected to the KestrelOne access point while trying to update. It
also meant a third party could change what the page executes.

The whole module graph is here. Most of it is loaded only on demand: the page
fetches `install-button.js`, the dialog arrives when the button is pressed, and
the chip-specific flasher and stub only when a device is identified. The files
for chips we do not use cost repository space, not page weight, and are kept so
the tool behaves normally if someone points it at something else.

To update: fetch `install-button.js` from unpkg for the new version, then
follow its `import("./...")` references transitively — the filenames are
content-hashed, so they change every release.
