# Command() arguments

## Game

[game.applydisplay](#gameapplydisplay)

[game.applygraphics](#gameapplygraphics)

[game.openfolder](#gameopenfolder)

[game.openurl](#gameopenurl)

[game.path.has](#gamepathhas)

[game.path.load](#gamepathload)

[game.path.record](#gamepathrecord)

[game.path.save](#gamepathsave)

[game.path.stop](#gamepathstop)

[game.pausemenu](#gamepausemenu)

[game.quickload](#gamequickload)

[game.quicksave](#gamequicksave)

[game.quit](#gamequit)

[game.screenrecord](#gamescreenrecord)

[game.screenshot](#gamescreenshot)

[game.selectmod](#gameselectmod)

[game.startui](#gamestartui)

[game.steam.showbindingpanel](#gamesteamshowbindingpanel)

[game.restart](#gamerestart)

## Hydra / Pros

[pros.eventToolUpgrade](#proseventtoolupgrade)

[pros.eventSettings](#proseventsettings)

[pros.eventTutorial](#proseventtutorial)

## Mods

[mods.activate](#modsactivate)

[mods.browsesubscribed](#modsbrowsesubscribed)

[mods.browse](#modsbrowse)

[mods.deactivate](#modsdeactivate)

[mods.delete](#modsdelete)

[mods.edit](#modsedit)

[mods.makelocalcopy](#modsmakelocalcopy)

[mods.new](#modsnew)

[mods.options](#modsoptions)

[mods.play](#modsplay)

[mods.publishbegin](#modspublishbegin)

[mods.publishcancel](#modspublishcancel)

[mods.publishend](#modspublishend)

[mods.publishupload](#modspublishupload)

[mods.refresh](#modsrefresh)

[mods.sanitycheck](#modssanitycheck)

[mods.refreshcharacters](#modsrefreshcharacters)

[mods.openeditor](#modsopeneditor)

[mods.unsubscribe](#modsunsubscribe)

[mods.updateselecttime](#modsupdateselecttime)

[mods.subscribe](#modssubscribe)

## Options

[options.audio.resettodefault](#optionsaudioresettodefault)

[options.input.gamepad.resettodefault](#optionsinputgamepadresettodefault)

[options.input.gamepad.resetparams](#optionsinputgamepadresetparams)

[options.gfx.resettodefault](#optionsgfxresettodefault)

[options.input.keymap.resettodefault](#optionsinputkeymapresettodefault)

## DLC

[dlc.openstore](#dlcopenstore)

---

> ## game.applydisplay
>
> Applies display settings from the registry.

> ## game.applygraphics
>
> Applies display settings from the registry. <!---Verify -->

> ## game.openfolder
>
> ### path (string)
>
> Opens given path in File Explorer.

> ## game.openurl
> 
> ### url (string)
>
> Opens given URL in default browser.

> ## game.path.has

> ## game.path.load
>
> ### path id (string) - File in %localappdata%\Teardown\path-{id}.pth ({id} - path id)
>
> Loads pth file with given id. <!-- Probably does nothing if id is invalid? - Verify -->

> ## game.path.record
>
> Starts recording a path in memory.

> ## game.path.save
>
> ### path id(string) - File in %localappdata%\Teardown (same format as [game.path.load](#gamepathload))
>
> Saves last recorded path from memory to given file.

> ## game.path.stop
>
> Stops the recording of path to memory (usually followed by [game.path.save](#gamepathsave)).

> ## game.pausemenu
>
> ### button id (string)
>
> Indicates that specified pause menu button was pressed

> ## game.quickload
>
> Loads %localappdata%\Teardown\quicksave.bin OR ...\quicksavecampaign.bin ([more info](https://github.com/Teardown-Issue-Tracker-Maintainers/Teardown-Issue-Tracker/issues/633))

> ## game.quicksave
>
> Bakes and saves current level to %localappdata%\Teardown\quicksave.bin OR ...\quicksavecampaign.bin ([more info](https://github.com/Teardown-Issue-Tracker-Maintainers/Teardown-Issue-Tracker/issues/633))

Baking is turning a level from a MOD folder with files to a bin file that contains a pre-compiled level (this is what happens when you play a level, but the bin is saved in memory, instead on disk).

Unlike built-in levels, quicksave bin files aren't compressed, so they take up more space.

> ## game.quit
>
> Fades to black and closes the game.

> ## game.screenrecord
>
> ### hide ui (bool)
>
> Starts capturing every frame of the game and puts it in Documents\Teardown\movies\capture ; Core function of the in-game screen recorder <!-- How do you stop it then?? -->

> ## game.startui
>
> ### script (string) - Path to script
>
> Simular to pressing the "Options" button of a mod; Fades to black, enters "UI" game state and executes given script, pressing escape or *pause* puts you on the main menu.

> ## game.steam.showbindingpanel
>
> Shows steam bindings panel. <!-- Verify -->

> ## game.restart
>
> Restarts the game. <!-- Verify -->

> ## pros.eventToolUpgrade
>
> ### tool id (string)
>
> ### upgrade id (string)
>
> ### upgrade level (number)
>
> ### upgrade price (number)
>
> Sends your score, amount of money, number of total voxels destroyed and other info to a telemetry server.

> ## pros.eventSettings
>
> Sends your display mode (fullscreen, windowed, etc.), game resolution, key binds, graphics settings, audio settings, accessibility settings and control prefrences (basically all settings) to a telemetry server.

> ## pros.eventTutorial
>
> ### progress (number) - Tutorial progress (range 1-6)
>
> Sends parameter to a telemetry server.

> ## mods.activate
>
> ### id (string) - Mod id
>
> Activates mod.

> ## mods.browsesubscribed
>
> ### id (string)
<!-- Describe - Probably checks if you're subscribed to the mod -->

> ## mods.browse
<!-- Describe - Probably lists all available mods :shrug: -->

> ## mods.deactivate
>
> ### id (string)
>
> Deactivates mod.

> ## mods.delete
>
> ### id (string)
>
> Deletes MOD folder.

> ## mods.edit
>
> ### id (string)
>
> Opens MOD/main.xml (opens empty editor if file doesn't exist).

> ## mods.makelocalcopy
>
> ### id (string)
>
> Copies MOD folder to Documents\Teardown\mods, excluding preview.jpg , spawn.txt , id.txt and ignore.txt .

> ## mods.new
>
> ### type (string) - Either global or content
>
> Makes a new MOD folder including info.txt , preview.jpg , ignore.txt , main.lua/.xml (depends on type)

> ## mods.options
>
> ### id (string)
>
> Fades to black, switches to "UI" game state, executing MOD/options.lua ; Using escape or *pause* returns to the mod manager.

> ## mods.play
>
> ### id (string)
>
> Plays MOD/main.xml

> ## mods.publishbegin
>
> ### id (string)
>
> Starts publishing MOD folder to steam workshop, creates id.txt (containing the workshop mod id).

> ## mods.publishcancel
>
> Stops publishing, but keeps id.txt

> ## mods.publishend
<!-- What's the point of that? ; What does it do? -->

> ## mods.publishupload
>
> Uploads MOD folder to steam workshop.

> ## mods.refresh

> ## mods.sanitycheck
>
> ### id (string)
<!-- Checks if mod structure is right? -->

> ## mods.refreshcharacters

> ## mods.openeditor
>
> Opens editor without loading any XML; Used by the main menu "Mod Editor" button.

> ## mods.unsubsribe
>
> ### id (string) - Mod id with steam- preffix
>
> Unsubscribes from mod.

> ## mods.updateselecttime
>
> ### id (string) - Mod id
>
> Sets the mod's last select time to the current one.

> ## mods.subscribe
>
> ### id (string) - Mod id with steam- preffix
>
> Subscribes from mod.

> ## options.audio.resettodefault
>
> Resets audio settings to default.

> ## options.input.gamepad.resettodefault
>
> Resets gamepad key binds to default.

> ## options.input.gamepad.resetparams
<!-- Resets parameters? -->

> ## options.gfx.resettodefault
>
> Resets graphics settings to default.

> ## options.input.keymap.resettodefault
>
> Resets keyboard key binds to default.

> ## dlc.openstore
>
> ### id (string) - DLC id (data\serviceconfigs\dlc_naming_table.xml)
>
> Opens store page of given DLC ; ArtVandals = 0 ; TimeCampers = [2657050](https://steamdb.info/app/2657050) ; Folkrace = [2657060](https://steamdb.info/app/2657060/); QuilezRoller = [2657080](https://steamdb.info/app/2657080); DLC3 = [2657090](https://steamdb.info/app/2657090/)