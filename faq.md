# FAQ, compatibility, limits

## Compatibility

| Engine | Status |
|---|---|
| 5.8 | supported, built with `-StrictIncludes` and tested |
| 5.6, 5.7 | planned (the demo content is saved with 5.8 and does not open in older engines) |
| 5.5 and older | not supported (Enhanced Input user settings API differs) |

Platforms: Win64 tested. Mac and Linux are enabled in the plugin descriptor and the code is platform-neutral, but
they are not tested yet. Consoles: untested.

## FAQ

**Does it need any assets or a specific UI framework?**
No. Everything is C++/UMG. It works next to CommonUI; the menu is a plain User Widget you can host anywhere.

**Is the colour filter a post-process material I have to add to my volumes?**
No. It uses the engine's built-in colour vision filter, which is applied to the final image.

**Will subtitles show up during cutscenes / Sequencer?**
Yes, call Show Subtitle from a Sequencer event track or from your dialogue system.

**Can I localise the texts?**
All menu strings use `LOCTEXT` in the `InclusaMenu` namespace and are gathered by the localisation dashboard.

**My remappable keys do not show up.**
Check: Enhanced Input *User Settings* enabled; the mapping has *Player Mappable Key Settings* with a Name;
the context was added with *Notify User Settings*.

**Interface scale does nothing in the editor.**
By design: the global UI scale also affects the editor, so it is applied only in standalone/packaged games.

**Does the kit collect data?**
No. Nothing leaves the player's machine.

## Known limits

- Remapping covers single keys, not chords (Enhanced Input limitation).
- Screen reader output is not part of version 1.0 (planned).
