> This is a fork of https://github.com/phindle/error-lens. Changes between this and the original repo should be reflected in the [CHANGELOG](https://github.com/usernamehw/vscode-error-lens/blob/master/CHANGELOG.md) file.

ErrorLens enhances Visual Studio Code's inbuilt diagnostic highlighting. Visual Studio Code's default behavior is to
underline errors and warnings and other diagnostic messages using a 'squiggly underline'. Whilst this is certainly
useful, the underline visual effect is subtle, and therefore can be easily overlooked in a busy file.

ErrorLens turbo-charges the language diagnostic features, by making diagnostics stand out more prominently, highlighting
the entire line wherever a diagnostic is generated by the language and also prints the diagnostic message(s) in-line at
the site of the line of code which is generating the diagnostic.

![ErrorLens example](img/demo.png)

## Features

* Lines containing errors or warnings or info are highlighted more obviously.
* Diagnostic descriptions are appended to the end of any line containing diagnostic info, meaning that you do not have to context-switch to the problems view.
* Show icons in gutter

## Extension Settings

This extension contributes the following settings:

* `errorLens.errorBackground`: The background color used to highlight lines containing errors. (Alpha component can be used)
* `errorLens.errorForeground`: The text color used to highlight lines containing errors. (Alpha component can be used)
* `errorLens.warningBackground`: The background color used to highlight lines containing warnings. (Alpha component can be used)
* `errorLens.warningForeground`: The text color used to highlight lines containing warnings. (Alpha component can be used)
* `errorLens.infoBackground`: The background color used to highlight lines containing info. (Alpha component can be used)
* `errorLens.infoForeground`: The text color used to highlight lines containing info. (Alpha component can be used)
* `errorLens.hintBackground`: The background color used to highlight lines containing hints. (Alpha component can be used)
* `errorLens.hintForeground`: The text color used to highlight lines containing hints. (Alpha component can be used)
* `errorLens.light`: Overwrite any of the above colors for light themes
* `errorLens.fontSize`: Font size of diagnostic messages in editor **Not officially supported property**
* `errorLens.fontFamily`: Font family of annotations. **Not officially supported property**
* `errorLens.fontStyle`: Show ErrorLens annotations in Italics, or not?
* `errorLens.fontWeight`: Specifies the font weight for ErrorLens annotations.
* `errorLens.margin`: Distance between end of the code line, and the start of the ErrorLens annotation. (CSS units)
* `errorLens.enabledDiagnosticLevels`: Customize which diagnostic levels to highlight.
* `errorLens.addAnnotationTextPrefixes`: If 'true', prefixes the diagnostic severity ('ERROR:', 'WARNING:' etc) to ErrorLens annotations.
* `errorLens.exclude`: Specify messages that should not be highlighted.
* `errorLens.delay`: Specify delay before showing problems.
* `errorLens.clearDecorations`: Works only when `delay` is set. When set to `true` extension clears all decorations at the time when diagnostic changes (but it could cause flickering if the delay is low). When set to `false` - decorations are not cleared and delay applied to clearing decorations also (but that causes messages being on screen even if the problem was solved).
* `errorLens.onSave`: Update decorations only on document save.
* `errorLens.gutterIconsEnabled`: Show gutter icons (In place of debug breakpoint icon).
* `errorLens.gutterIconSize`: Customize gutter icon size. Example: `"120%"`
* `errorLens.gutterIconSet`: Customize gutter icon style. Possible values: `"default"`, `"borderless"`
* `errorLens.errorGutterIconPath`: Absolute path for error gutter icon for dark themes.
* `errorLens.errorGutterIconPathLight`: Absolute path for error gutter icon for light themes.
* `errorLens.warningGutterIconPath`: Absolute path for warning gutter icon for dark themes.
* `errorLens.warningGutterIconPathLight`: Absolute path for warning gutter icon for light themes.
* `errorLens.infoGutterIconPath`: Absolute path for info gutter icon for dark themes.
* `errorLens.infoGutterIconPathLight`: Absolute path for info gutter icon for light themes.

## Extension Commands

This extension contributes the following commands:

* `errorLens.toggle` Enable/Disable ErrorLens.

## Extra

Example of using `source` & `code` or diagnostic message to exclude a problem:

```javascript
"errorLens.exclude": [
    // Use source and code
    {
        "code": "6133",// is declared but its value is never read.
        "source": "ts",
    },
    // Use diagnostic message
    "Unknown configuration setting"
],
```

---

Remove built-in problem decorations from `settings.json`:

```javascript
"workbench.colorCustomizations": {
    "editorError.border": "#fff0",
    "editorError.foreground": "#fff0",
    "editorWarning.border": "#fff0",
    "editorWarning.foreground": "#fff0",
    // ...
}
```
