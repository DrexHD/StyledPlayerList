![Logo](https://i.imgur.com/MV1mbYv.png)

# Styled Player List
It's a simple mod that allows server owners to style their player list as they like!
With full permission support, placeholder api support, multiple styles and player name overrides.

*This mod works only on Fabric Mod Loader and compatible!*

If you have any questions, you can ask them on my [Discord](https://pb4.eu/discord)

[Also check out my other mods and project, as you might find them useful!](https://pb4.eu)

![Example image](https://i.imgur.com/yIcm5dC.png)


## Commands (and permissions):
- `/styledplayerlist` - Main command (`styledplayerlist.main`, available by default)
- `/styledplayerlist reload` - Reloads configuration and styles (requires `styledplayerlist.reload`)
- `/styledplayerlist switch <style>` or `/plstyle <style>` - Changes selected style (`styledplayerlist.switch`, available by default)
- `/styledplayerlist switchothers <players> <style> ` - Changes selected style of players (`styledplayerlist.switch.others`)

## Configuration:
You can find config file in `./config/styledplayerlist/`.
```json5
{
  "defaultStyle": "default",                   // allows to select id of default player list
  "updateRate": 20,                            // change how often player list is updated (20 = every 1 second)
  "...Message": "...",                         // allows to change messages
  "changePlayerName": false,                   // if true, names of players on player list will be changed
  "playerNameFormat": "%player:display_name%", // format of player name (uses Text Parser and placeholders)
  "updatePlayerNameEveryChatMessage": false,   // if true, everytime player sends a message, theirs name will be updated 
  "playerNameUpdateRate": -1 ,                 // changes how often player name is updated (20 = every 1 second, -1 disables it)
  "permissionNameFormat": [                    // Permission based overrides of name format
    {
      "permission": "some.permission",         // Required permission
      "opLevel": -1,                           // Alternative OP level (-1 to disable)
      "style": "..."                           // format of player name (uses Text Parser and placeholders)
    }
  ]
}
```
### Styles:
This mod allows having multiple styles, that can be selected by players (just put them in `./config/styledplayerlist/styles/` and use `/styledplayerlist reload` command)
[Formatting uses PlaceholderAPI's Text Parser for which docs you can find here](https://github.com/Patbox/FabricPlaceholderAPI/blob/1.17/TEXT_FORMATTING.md).

```json5
{
  "id": "default",   // used internally and for commands
  "name": "Default", // used is messages
  "header": [        // header of player list, every element is in new line 
    "",
    "<gradient:#4adeff:#3d8eff><bold> Styled Player List</bold></gradient> ⛏ ",
    "",
    "<color:#555555><strikethrough>        </strikethrough>[ </color><color:#FF5555>%server:online%<color:#6666676>/</color>%server:max_players%</color><color:#555555> ]<strikethrough>        </strikethrough></color>",
    ""
  ],
  "footer": [        // footer of player list, every element is in new line 
    "",
    "<color:#555555><strikethrough>                          </strikethrough></color>",
    "",
    "<gray>TPS: %server:tps_colored% <dark_gray>|</dark_gray> <gray>Ping: <color:#ffba26>%player:ping%</color>",
    ""
  ],
  "hidden": false,   // hides in commands
  "permission": ""   // required permission, leave empty if you want to allow everyone
}
```

## Build in placeholders:
For supported placeholders list, see [Placeholder API's wiki](https://placeholders.pb4.eu/user/general/)

