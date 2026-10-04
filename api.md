# Blueprint and C++ reference

All Blueprint nodes are in the categories *Inclusa | …*.

## UInclusaAccessibilityLibrary (Blueprint function library)

| Node | Description |
|---|---|
| Open Settings Menu (Player Controller) → Menu | Opens the menu, switches to UI input, shows the cursor. |
| Show Subtitle (Text, Speaker, [Duration], [Priority]) → Id | Queues a subtitle. Duration ≤ 0 = automatic. |
| Clear Subtitles | Removes all queued and visible lines. |
| Get / Set Accessibility Settings | Read or write all player options at once. |
| Get Scaled Font Size (Base Size) | Font size after the player's text scale. |

## UInclusaAccessibilitySubsystem (Game Instance Subsystem)

`Get(WorldContext)`, `GetSettings()`, `SetSettings(Settings, bSave)`, `SaveSettings()`, `LoadSettings()`,
`ResetToDefaults(bSave)`, `ApplySettings()`, `SetTextScale`, `SetUIScale`, `SetColorVision(Type, Severity,
bSimulate)`, `GetScaledFontSize(Base, bIsSubtitle)`, `GetEffectiveSubtitleBackgroundOpacity()`,
static `Sanitize(Settings)`.
Events: `OnSettingsChanged` (Blueprint), `OnSettingsChangedNative` (C++).

## UInclusaSubtitleSubsystem (Game Instance Subsystem)

`ShowSubtitle(FInclusaSubtitleLine)`, `ShowText(Text, Speaker, Duration, Priority)`, `HideSubtitle(Id)`,
`ClearSubtitles()`, `GetVisibleSubtitles()`, static `GetSpeakerColor(Speaker)`, `EnsureSubtitleWidget()`.
Events: `OnSubtitlesChanged`, `OnSubtitlesChangedNative`.

## UInclusaRemapLibrary

`GetRemappableKeys(PC, OutEntries)`, `RemapKey(PC, MappingName, SlotIndex, NewKey, OutConflicts)`,
`ResetAllKeys(PC)`, `IsRemappingAvailable(PC)`.

## Widgets

- `UInclusaSubtitleWidget` – subtitle display; event *On Subtitles Updated*; optional `LinesBox`.
- `UInclusaSettingsMenuWidget` – full menu; `CloseMenu()`, event `OnMenuClosed`.
- `UInclusaRemapRowWidget` – one remapping row (used by the menu).
- `UInclusaScaledTextBlock` – *Scaled Text (Inclusa)*, `BaseFontSize`, `bUseSubtitleScale`.

## Types

- `FInclusaAccessibilitySettings` – all player options (see header for ranges).
- `FInclusaSubtitleLine` – Text, Speaker, SpeakerDisplayName, Duration, Priority.
- `FInclusaVisibleSubtitle` – Id, Text, SpeakerName, SpeakerColor.
- `FInclusaRemapEntry` – MappingName, DisplayName, DisplayCategory, SlotIndex, CurrentKey, DefaultKey, ConflictsWith.
- `EInclusaColorVision` – Normal, Protanopia, Deuteranopia, Tritanopia.

## Engine-independent core

`Source/InclusaAccessibility/Public/Core/InclusaCore.h` holds the rules (timing, splitting, queue,
palette hashing, WCAG contrast, scale steps, duplicate keys) in plain C++17 without engine types.
