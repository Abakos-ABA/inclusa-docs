# Getting started

## Install

- **From Fab:** install the plugin to your engine from the Fab library in the Epic Games Launcher, then
  enable *Inclusa Accessibility Kit* in *Edit > Plugins*.
- **Per project:** copy the `InclusaAccessibility` folder to `<YourProject>/Plugins/`. C++ projects
  compile it automatically; Blueprint-only projects use the precompiled binaries from Fab.

Restart the editor after enabling.

## Five-minute setup

1. **Subtitles.** Wherever a character speaks, add **Show Subtitle** (Text, Speaker). Done: the widget
   is created automatically for the first local player.
2. **Menu.** In your pause or options menu, add a button that calls **Open Settings Menu** with
   *Get Player Controller*.
3. **Remapping.** In *Project Settings > Enhanced Input*, enable *User Settings*. In each Input Mapping
   Context, for every key the player may change, set *Setting Behavior* to *Override Settings* and give
   *Player Mappable Key Settings* a unique *Name* and *Display Name*. When adding the context at runtime,
   tick *Notify User Settings* in the options. These keys now appear in the menu's *Controls* section.
4. **Your own text.** Replace *Text* widgets with **Scaled Text (Inclusa)** and set *Base Font Size*.
5. **Defaults.** In *Project Settings > Plugins > Inclusa Accessibility*, set the defaults new players
   start with, the reading speed and any fixed speaker colours.

## Try the demo

Open the level `/InclusaAccessibility/Demo/L_InclusaDemo` and press Play, or drop an
**Inclusa Demo Actor** into any level. A short conversation plays as subtitles; press **F1** or gamepad
**Start** for the menu.

## Where settings are saved

Player options: save slot `InclusaAccessibility` (configurable). Key bindings: Enhanced Input's own user
settings save. Both live in the platform's normal save location; nothing is sent anywhere.
