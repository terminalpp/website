---
title: Configuration
layout: titled
---

Configuration of `terminalpp` is done via a JSON file in its configuration directory. Depending on the platform, this is located in:

- `%APPDATA%/terminalpp/settings.json` on Windows (note this folder is virtualized)
- `~/.config/terminalpp/settings.json` on Linux
- `~/Library/Application Support/terminalpp/settings.json` on macOS

Keyboard shortcut `A-F10` opens the configuration file on local editor associated with JSON files. 

> The settings file is a JSON-style file enhanced with JavaScript-like comments for better readability. 

### Initial Settings

When `terminalpp` starts and the settings file is not found, or its version is not same as the application's version, the settings file (if any) is analyzed and default values are provided:

- font is selected based on the system (either a font known to be present such as `Consolas` on Windows, or system fonts are searched for good font match)
- the process to launch in the terminal is determined (WSL and bypass are preferred on Windows, Linux and macOS show default prompt of the current user)
- various folders are set, usually to temporary folder bearing `terminalpp`'s name

> Note that on Windows, if WSL is detected, `terminalpp` may attempt to install the `tpp-bypass` in it automatically. 

### Example Settings File

<!--

TODO: The configuratiom should be able to generate its own JSON schema and the following section should be generated by jekyll from that schema automatically.

-->

The following is an example of a settings file with all possible settings, their short documentation and their values. 

```json
{
    /* Version information & checks
     */
    "version" : {
        /* Version of tpp the settings are intended for, to make sure the settings are useful and to detect version changes
         */
        "version" : "0.8.0",
        /* Release channel to be checked for new version upon start. Leave empty (default) if the check should not be performed.
         */
        "checkChannel" : ""
    },
    "application" : {
        /* If true, checks that profile shortcuts (if supported on given platform) will be updated at every startup
         */
        "detectSessionsAtStartup" : true
    },
    /* Telemetry Settings for bug and feature requests reporting
     */
    "telemetry" : {
        /* Directory where to store the telemetry logs
         */
        "dir" : "C:\\Users\\petam\\AppData\\Local\\Temp\\terminalpp\\telemetry",
        /* Names of event kinds that should be captured by the telemetry
         */
        "events" : [
        ],
        /* If true, unused telemetry logs are deleted when the application terminates
         */
        "deleteAtExit" : true
    },
    /* Renderer settings
     */
    "renderer" : {
        /* Maximum FPS
         */
        "fps" : 60,
        /* Font used to render the terminal
         */
        "font" : {
            /* Font to render default size characters
             */
            "family" : "Iosevka Term",
            /* Font to render bold characters, if different from normal font
             */
            "boldFamily" : "",
            /* Font to render double width characters
             */
            "doubleWidthFamily" : "Iosevka Term",
            /* Size of the font in pixels at zoom level 1.0
             */
            "size" : 18,
            /* Spacing between lines.
             */
            "lineSpacing" : 1,
            /* Font to render bold double width characters, if different from doubleWidth font
             */
            "doubleWidthBoldFamily" : "",
            /* Spacing between characters.
             */
            "charSpacing" : 1
        },
        "window" : {
            /* Number of columns the non-maximized window should have.
             */
            "cols" : 80,
            /* Number of rows the non-maximized window should have.
             */
            "rows" : 25,
            /* Determines the behavior of the session when the attached command terminates.
             */
            "fullscreen" : false,
            /* Determines the behavior of the session when the attached command terminates.
             */
            "waitAfterPtyTerminated" : false,
            /* Determines the maximum number of lines the terminal will remember in the history of the buffer. If set to 0, terminal history is disabled.
             */
            "historyLimit" : 10000
        }
    },
    "sequences" : {
        /* Determines whether pasting into terminal should be explicitly confirmed. Allowed values are 'never', 'always', 'multiline'.
         */
        "confirmPaste" : "multiline",
        /* If true, bold text is rendered in bright colors.
         */
        "boldIsBright" : true,
        /* Determines whether terminal applications can set local clipboard. Allowed values are 'allow', 'deny' and 'ask'
         */
        "allowClipboardUpdate" : "allow",
        /* If true bold font will be used when appropriate.
         */
        "displayBold" : true
    },
    "sessionDefaults" : {
        /* Determines whether local, or bypass PTY should be used. Useful only for Windows, ignored on other systems.
         */
        "pty" : "local",
        "palette" : {
            /* Overrides the predefined palette. Up to 256 colors can be specified in HTML format. These colors will override the default xterm palette used.
             */
            "colors" : [
            ],
            /* Specifies the index of the default foreground color in the palette.
             */
            "defaultForeground" : "#ffffff",
            /* Specifies the index of the default background color in the palette.
             */
            "defaultBackground" : "#000000"
        },
        "cursor" : {
            /* UTF codepoint of the cursor
             */
            "codepoint" : 9601,
            /* Color of the cursor
             */
            "color" : "#ffffff",
            /* Determines whether the cursor blinks or not.
             */
            "blink" : true,
            /* Color of the rectangle showing the cursor position when not focused.
             */
            "inactiveColor" : "#00ff00"
        }
    },
    /* Settings for opening remote files from the terminal locally.
     */
    "remoteFiles" : {
        /* Directory to which the remote files should be downloaded. If empty, temporary directory will be used.
         */
        "dir" : "C:\\Users\\petam\\AppData\\Local\\Temp\\terminalpp\\remoteFiles"
    },
    /* Name of the default session which will be opened when terminal starts
     */
    "defaultSession" : "Ubuntu-18.04",
    /* List of known sessions
     */
    "sessions" : [
        /* cmd.exe
         */
        {
            "name" : "cmd.exe",
            /* Can hide the session from menus, such as the jumplist. Hidden session can still be explicitly started via the --session argument
             */
            "hidden" : false,
            /* Determines whether local, or bypass PTY should be used. Useful only for Windows, ignored on other systems.
             */
            "pty" : "local",
            "palette" : {
                /* Overrides the predefined palette. Up to 256 colors can be specified in HTML format. These colors will override the default xterm palette used.
                 */
                "colors" : [
                ],
                /* Specifies the index of the default foreground color in the palette.
                 */
                "defaultForeground" : "#ffffff",
                /* Specifies the index of the default background color in the palette.
                 */
                "defaultBackground" : "#000000"
            },
            "command" : [
                "cmd.exe"
            ],
            "workingDirectory" : "C:\\Users\\petam",
            "cursor" : {
                /* UTF codepoint of the cursor
                 */
                "codepoint" : 9601,
                /* Color of the cursor
                 */
                "color" : "#ffffff",
                /* Determines whether the cursor blinks or not.
                 */
                "blink" : true,
                /* Color of the rectangle showing the cursor position when not focused.
                 */
                "inactiveColor" : "#00ff00"
            }
        },
        /* Powershell - with the default blue background and white text
         */
        {
            "name" : "powershell",
            /* Can hide the session from menus, such as the jumplist. Hidden session can still be explicitly started via the --session argument
             */
            "hidden" : false,
            /* Determines whether local, or bypass PTY should be used. Useful only for Windows, ignored on other systems.
             */
            "pty" : "local",
            "palette" : {
                /* Overrides the predefined palette. Up to 256 colors can be specified in HTML format. These colors will override the default xterm palette used.
                 */
                "colors" : [
                ],
                "defaultForeground" : "ffffff",
                "defaultBackground" : "#0000ff"
            },
            "command" : [
                "powershell.exe"
            ],
            "workingDirectory" : "C:\\Users\\petam",
            "cursor" : {
                /* UTF codepoint of the cursor
                 */
                "codepoint" : 9601,
                /* Color of the cursor
                 */
                "color" : "#ffffff",
                /* Determines whether the cursor blinks or not.
                 */
                "blink" : true,
                /* Color of the rectangle showing the cursor position when not focused.
                 */
                "inactiveColor" : "#00ff00"
            }
        },
        /* WSL distribution Ubuntu-18.04 (default)
         */
        {
            "name" : "Ubuntu-18.04",
            /* Can hide the session from menus, such as the jumplist. Hidden session can still be explicitly started via the --session argument
             */
            "hidden" : false,
            "pty" : "bypass",
            "palette" : {
                /* Overrides the predefined palette. Up to 256 colors can be specified in HTML format. These colors will override the default xterm palette used.
                 */
                "colors" : [
                ],
                /* Specifies the index of the default foreground color in the palette.
                 */
                "defaultForeground" : "#ffffff",
                /* Specifies the index of the default background color in the palette.
                 */
                "defaultBackground" : "#000000"
            },
            "command" : [
                "wsl.exe",
                "--distribution",
                "Ubuntu-18.04",
                "--",
                "~/.local/bin/tpp-bypass"
            ],
            "workingDirectory" : "C:\\Users\\petam",
            "cursor" : {
                /* UTF codepoint of the cursor
                 */
                "codepoint" : 9601,
                /* Color of the cursor
                 */
                "color" : "#ffffff",
                /* Determines whether the cursor blinks or not.
                 */
                "blink" : true,
                /* Color of the rectangle showing the cursor position when not focused.
                 */
                "inactiveColor" : "#00ff00"
            }
        },
    ]
}
```

### Command-line arguments

The following command-line arguments can be used to override the global configuration settings for the particular execution:

- `--here` makes the terminal start in current folder instead of the folder provided in the configuration 
- `--session` overides which session will start
- `--pty` sets the PTY used (`session.pty`)
- `--fps` sets the renderer's maximum FPS rate (`renderer.fps`)
- `--cols, -c` sets the number of columns for the terminal window (`session.cols`)
- `--rows, -r` sets the number of rows for the terminal window (`session.rows`)
- `--font` sets the default font family (`font.family`)
- `--font-size` sets the size of the font in pixels (`font.size`)
- `-e` specifies the command (`session.command`), all arguments after `-e` are considered parts of the command to execute

The arguments can be specified either using the `--arg=value`, or `--arg value` notation, i.e:

    terminalpp --cols=80 --rows=25 

or:

    terminalpp --cols 80 --rows 25



