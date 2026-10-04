# Features in detail

## Subtitles

- **Timing:** without an explicit duration a line stays `characters / reading speed` seconds
  (default 15 chars/s), clamped to 1.5–8 s. With an explicit duration, split parts share it by length.
- **Splitting:** lines longer than *Max Chars Per Subtitle* (default 84, about two lines) are split at
  word boundaries into consecutive subtitles.
- **Queue and priority:** at most *Max Visible Subtitles* lines (default 2) are on screen. Higher
  *Priority* lines are shown first; waiting lines are not lost and only start counting down once visible.
  Display order on screen is always chronological.
- **Speakers:** the speaker name is shown in front of the line (player option). Each speaker gets a colour
  from the Okabe–Ito palette, chosen by a stable hash of the name, so "Mara" has the same colour in every
  session and on every machine. Fixed colours: *Project Settings > Speaker Colors*.
- **Readability:** with *Keep text readable on bright scenes* on (default), the background box never gets
  more transparent than needed for WCAG AA contrast (4.5:1) over a white scene, whatever the opacity
  slider says.
- **Player options:** on/off, size (75–250 %), background opacity, speaker names, speaker colours.
- **Custom look:** subclass `UInclusaSubtitleWidget` in Blueprint and either keep the C++ layout and react
  to *On Subtitles Updated*, or design your own tree with a Vertical Box named `LinesBox`. Set the class in
  *Project Settings > Subtitle Widget Class*.
- **Engine subtitles (experimental):** *Capture Engine Subtitles* routes subtitles of Sound Waves into the
  kit's display.

## Colour vision

Uses the engine's built-in colour vision deficiency filter, applied to the final image (3D scene and UI):

- Modes: Off, Protanopia, Deuteranopia, Tritanopia; strength 0–100 %.
- *Simulate instead of correct* shows how your game looks to players with that deficiency: use it to check
  your own art (e.g. red/green pickups).
- Because the engine applies it, there is no shader to maintain and no per-platform cost.

## Text and UI scale

- **Text size** (75–200 %, limits in project settings) scales all text drawn by the kit and every
  **Scaled Text (Inclusa)** widget, live.
- **Interface scale** (75–150 %) scales the whole Slate UI of the game. It is applied in standalone and
  packaged games; during Play-In-Editor only text size is previewed, so the editor UI is not resized.
- For custom layouts call **Get Scaled Font Size** (Base Size) or listen to *On Settings Changed*.

## Remapping

Built on Enhanced Input's player-mappable key profiles (UE 5.3+ system):

- Lists every player-mappable key of the active profile, grouped by display category, primary and
  alternative slots.
- Click a key, press the new key (Esc cancels). Mouse, keyboard and gamepad keys are allowed; modifier
  combinations are not (Enhanced Input maps single keys).
- Keys used by more than one action are flagged with *Also used by: …*. The kit warns instead of blocking,
  because many games share keys across contexts on purpose.
- *Reset to defaults* restores every customised key.
- Bindings are saved by Enhanced Input's own save game and restored on start.

## Settings menu

- Sections: Subtitles (with live preview line), Colour vision, Text and interface, Controls.
- Keyboard, mouse and gamepad; Esc / gamepad B closes and saves.
- Every change previews live; the save happens on close, so dragging a slider does not write to disk
  every frame.
- All text follows the player's text size.
- Replace it completely: subclass `UInclusaSettingsMenuWidget` or build your own menu on the same
  subsystem functions, and set *Settings Menu Class* in the project settings.
