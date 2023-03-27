[![Version](https://img.shields.io/visual-studio-marketplace/v/usernamehw.errorlens)](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens)
[![Installs](https://img.shields.io/visual-studio-marketplace/i/usernamehw.errorlens)](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens)
[![Rating](https://img.shields.io/visual-studio-marketplace/r/usernamehw.errorlens)](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens)
[![OpenVSX Downloads](https://shields.io/open-vsx/dt/usernamehw/errorlens?label=OpenVSX%20Downloads)](https://open-vsx.org/extension/usernamehw/errorlens)

ErrorLens turbo-charges language diagnostic features by making diagnostics stand out more prominently, highlighting
the entire line wherever a diagnostic is generated by the language and also prints the message inline.

![Demo image](https://raw.githubusercontent.com/usernamehw/vscode-error-lens/master/img/demo.png)

## Features

- Highlight lines containing diagnostics
- Append diagnostic as text to the end of the line
- Show icons in gutter
- Show message in status bar

<!-- COMMANDS_START -->
## Commands (7)

|Command|Description|
|-|-|
|errorLens.toggle|Error Lens: Toggle (Enable/Disable) Everything (toggle global setting `errorLens.enabled`)|
|errorLens.toggleError|Error Lens: Enable/Disable Errors in `errorLens.enabledDiagnosticLevels` setting.|
|errorLens.toggleWarning|Error Lens: Enable/Disable Warnings in `errorLens.enabledDiagnosticLevels` setting.|
|errorLens.toggleInfo|Error Lens: Enable/Disable Info in `errorLens.enabledDiagnosticLevels` setting.|
|errorLens.toggleHint|Error Lens: Enable/Disable Hint in `errorLens.enabledDiagnosticLevels` setting.|
|errorLens.copyProblemMessage|Error Lens: Copy problem message to the clipboard (at the active cursor).|
|errorlens.toggleWorkspace|Error Lens: Exclude/Include current workspace by path.|
<!-- COMMANDS_END -->
<!-- SETTINGS_START -->
## Settings (51)

> **Error Lens** extension settings start with `errorLens.`

|Setting|Default|Description|
|-|-|-|
|enabled|**true**|Controls all decorations and features (except commands).|
|enabledInMergeConflict|**true**|Controls if decorations are shown if the editor has git merge conflict indicators `<<<<<<<` or `=======` or `>>>>>>>`.|
|fontFamily|""|Font family of inline message.|
|fontWeight|"normal"|Font weight of inline message. `"normal"` is alias for 400, `"bold"` is alias for 700).|
|fontStyleItalic|**false**|When enabled - shows inline message in italic font style.|
|fontSize|""|Font size of inline message ([CSS units](https://developer.mozilla.org/en-US/docs/Web/CSS/length)).|
|margin|"4ch"|Distance between the last word on the line and the start of inline message ([CSS units](https://developer.mozilla.org/en-US/docs/Web/CSS/length)).|
|padding|""|Padding of the inline message. Visible when `#errorLens.messageBackgroundMode#` is set to "message".|
|borderRadius|"3px"|Border radius of the inline message. Visible when `#errorLens.messageBackgroundMode#` is set to "message".|
|enabledDiagnosticLevels|\["error","warning","info"\]|Customize which diagnostic levels to highlight.|
|messageTemplate|"$message"|Template used for all inline messages. Whitespace between items is important.<br>List of variables:<br>- `$message` - diagnostic message text<br>- `$count` - Number of diagnostics on the line<br>- `$severity` - Severity prefix taken from `#errorLens.severityText#`<br>- `$source` - Source of diagnostic e.g. "eslint"<br>- `$code` - Code of the diagnostic|
|messageMaxChars|**500**|Cut off inline message if it's longer than this value. (Improves performance when the diagnostic message is long). Set to **0** to disable inline message.|
|severityText|\["ERROR","WARNING","INFO","HINT"\]|Replaces `$severity` variable in `#errorLens.messageTemplate#`.|
|messageEnabled|**true**|Controls whether inline message is shown or not (Including background highlight).|
|messageBackgroundMode|"line"|Controls how inline message is highlighted in the editor (entire line / only message / none).|
|statusBarIconsEnabled|**false**|When enabled - shows highlighted error/warning icons in status bar.|
|statusBarIconsPriority|**-9000**|Move status bar icons left or right by adjasting the number priority.|
|statusBarIconsAlignment|"left"|Choose on which side the icons status bar is on: left or right.|
|statusBarIconsUseBackground|**true**|When enabled - highlights status bar icons with background, when disabled - with foreground.|
|statusBarIconsAtZero|"removeBackground"|What to do when there are 0 errors/warnings - hide the item or strip its background color.|
|statusBarMessageEnabled|**false**|When enabled - shows message in status bar.|
|statusBarMessagePriority|**-10000**|Move status bar message left or right by adjasting the number priority.|
|statusBarMessageAlignment|"left"|Choose on which side the message status bar is on: left or right.|
|statusBarColorsEnabled|**false**|When enabled - use message decoration foreground as color of Status Bar text.|
|statusBarMessageType|"activeLine"|Pick what to show in Status Bar: closest message or only message for the active line.|
|statusBarCommand|"goToProblem"|Pick command that activates on click for Status Bar.|
|statusBarMessageTemplate|""|Template for status bar message. Whitespace between items is important.<br>List of variables:<br>- `$message` - diagnostic message text<br>- `$count` - Number of diagnostics on the line<br>- `$severity` - Severity prefix taken from `#errorLens.severityText#`<br>- `$source` - Source of diagnostic e.g. "eslint"<br>- `$code` - Code of the diagnostic|
|exclude|\[\]|Specify messages that should not be highlighted (RegExp). Strings passed to the RegExp constructor: `new RegExp(EXCLUDE_ITEM, 'i');`|
|excludeBySource|\[\]|Specify source or source(code) pair that should not be highlighted. Examples: `["eslint"]`, `["eslint(padded-blocks)"]`|
|excludePatterns|\[\]|Exclude files by using glob pattern. Example `["**/*.{ts,js}"]`|
|excludeWorkspaces|\[\]|Exclude workspaces by path.|
|light||Specify color of decorations for when the light color theme is active.|
|delay|**0**|Delay (ms) before showing problem decorations (**0** to disable). Minimum delay of **500** is enforced by the extension. New errors will be added with this delay; old errors that were fixed should disappear faster.|
|onSave|**false**|When enabled - updates decorations only on document save (manual).|
|onSaveTimeout|**1000**|Time period (ms) that used for showing decorations after the document save.|
|enableOnDiffView|**false**|Enable decorations when viewing a diff view in the editor (e.g. Git diff).|
|followCursor|"allLines"|Highlight only portion of the problems.|
|followCursorMore|**0**|Augments `#errorLens.followCursor#`.<br>Adds number of lines to top and bottom when `#errorLens.followCursor#` is set to `activeLine`.<br> Adds number of closest problems when `#errorLens.followCursor#` is `closestProblem`|
|gutterIconsEnabled|**false**|When enabled - shows gutter icons (In place of the debug breakpoint icon).|
|gutterIconsFollowCursorOverride|**true**|When enabled and `#errorLens.followCursor#` setting is not `allLines`, then gutter icons would be rendered for all problems. But line decorations (background, message) only for active line.|
|gutterIconSize|"100%"|Change gutter icon size. Examples: `auto`, `contain`, `cover`, `50%`, `150%`.|
|gutterIconSet|"default"|Change gutter icon style.|
|errorGutterIconPath|""|Absolute path to error gutter icon.|
|warningGutterIconPath|""|Absolute path to warning gutter icon.|
|infoGutterIconPath|""|Absolute path to info gutter icon.|
|errorGutterIconColor|"\#e45454"|Error color of `circle` gutter icon set.|
|warningGutterIconColor|"\#ff942f"|Warning color of `circle` gutter icon set.|
|infoGutterIconColor|"\#00b7e4"|Info color of `circle` gutter icon set.|
|removeLinebreaks|**true**|When enabled - replaces line breaks in inline diagnostic message with whitespaces.|
|replaceLinebreaksSymbol|"⏎"|Symbol to replace linebreaks. Requires enabling `#errorLens.removeLinebreaks#`.|
|scrollbarHackEnabled|**false**|When enabled - prevents showing horizontal scrollbar in editor (caused by inline decorations).|
<!-- SETTINGS_END -->
<!-- COLORS_START -->
## Colors (26)

Can be specified in `settings.json` (**`workbench.colorCustomizations`** section)

|Color|Dark|Light|HC|Description|
|-|-|-|-|-|
|errorLens.errorBackground|`#e454541b`|`#e4545420`|`#e454541b`|Background color of the entire line containing error.|
|errorLens.errorMessageBackground|`#e4545419`|`#e4545419`|`#e4545419`|Background color of the error message.|
|errorLens.errorBackgroundLight|`#e4545420`|`#e4545420`|`#e4545420`|Background color of the entire line containing error (Only in light themes).|
|errorLens.errorForeground|`#ff6464`|`#e45454`|`#ff6464`|Text color used to highlight lines containing errors.|
|errorLens.errorForegroundLight|`#e45454`|`#e45454`|`#e45454`|Text color used to highlight lines containing errors (Only in light themes).|
|errorLens.warningBackground|`#ff942f1b`|`#ff942f20`|`#ff942f1b`|Background color used to highlight lines containing warnings.|
|errorLens.warningMessageBackground|`#ff942f19`|`#ff942f19`|`#ff942f19`|Background color of the warning message.|
|errorLens.warningBackgroundLight|`#ff942f20`|`#ff942f20`|`#ff942f20`|Background color used to highlight lines containing warnings (Only in light themes).|
|errorLens.warningForeground|`#fa973a`|`#ff942f`|`#fa973a`|Text color used to highlight lines containing warnings.|
|errorLens.warningForegroundLight|`#ff942f`|`#ff942f`|`#ff942f`|Text color used to highlight lines containing warnings (Only in light themes).|
|errorLens.infoBackground|`#00b7e420`|`#00b7e420`|`#00b7e420`|Background color used to highlight lines containing info.|
|errorLens.infoMessageBackground|`#00b7e419`|`#00b7e419`|`#00b7e419`|Background color of the info message.|
|errorLens.infoBackgroundLight|`#00b7e420`|`#00b7e420`|`#00b7e420`|Background color used to highlight lines containing info (Only in light themes).|
|errorLens.infoForeground|`#00b7e4`|`#00b7e4`|`#00b7e4`|Text color used to highlight lines containing info.|
|errorLens.infoForegroundLight|`#00b7e4`|`#00b7e4`|`#00b7e4`|Text color used to highlight lines containing info (Only in light themes).|
|errorLens.hintBackground|`#17a2a220`|`#17a2a220`|`#17a2a220`|Background color used to highlight lines containing hints.|
|errorLens.hintMessageBackground|`#17a2a219`|`#17a2a219`|`#17a2a219`|Background color of the hint message.|
|errorLens.hintBackgroundLight|`#17a2a220`|`#17a2a220`|`#17a2a220`|Background color used to highlight lines containing hints (Only in light themes).|
|errorLens.hintForeground|`#2faf64`|`#2faf64`|`#2faf64`|Text color used to highlight lines containing hints.|
|errorLens.hintForegroundLight|`#2faf64`|`#2faf64`|`#2faf64`|Text color used to highlight lines containing hints (Only in light themes).|
|errorLens.statusBarIconErrorForeground|`#ff6464`|`#e45454`|`#ff6464`|Status bar icon item error color. Foreground is used when the `errorLens.statusBarIconsUseBackground` setting is disabled.|
|errorLens.statusBarIconWarningForeground|`#fa973a`|`#ff942f`|`#fa973a`|Status bar icon item error color. Foreground is used when the `errorLens.statusBarIconsUseBackground` setting is disabled.|
|errorLens.statusBarErrorForeground|`#ff6464`|`#e45454`|`#ff6464`|Status bar item error color.|
|errorLens.statusBarWarningForeground|`#fa973a`|`#ff942f`|`#fa973a`|Status bar item warning color.|
|errorLens.statusBarInfoForeground|`#00b7e4`|`#00b7e4`|`#00b7e4`|Status bar item info color.|
|errorLens.statusBarHintForeground|`#2faf64`|`#2faf64`|`#2faf64`|Status bar item hint color.|
<!-- COLORS_END -->

> Line highlighting depends on the **`"errorLens.messageBackgroundMode"`** setting.

> `#fff0` - Completely transparent color.

## Upstream issues

Please upvote the following VS Code issues:

- [Api for editor insets](https://github.com/microsoft/vscode/issues/85682)
- [Access theme's colors programmatically](https://github.com/microsoft/vscode/issues/32813)
- [When completing color keys in settings, fill in current value](https://github.com/microsoft/vscode/issues/25633)
- [Inline text adornments break word wrapping](https://github.com/microsoft/vscode/issues/32856)
- [OnClick event on Gutter](https://github.com/microsoft/vscode/issues/5455)
- [Support hover decorations over the line numbers i.e. gutter](https://github.com/microsoft/vscode/issues/28080)

## More Documentation

https://github.com/usernamehw/vscode-error-lens/tree/master/docs/docs.md