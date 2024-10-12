# Undocumented Functions

## Miscellaneous

Miscellaneous functions with no official documentation.

[AddSnow](#addsnow)

[Command](#command)

[CompleteAchievement](#completeachievement)

[GetClipboardText](#getclipboard)

[GetEvent](#getevent)

[GetEventCount](#geteventcount)

[DisableAllLights](#disablealllights)

[GetPlayerGrabPoint](#getplayergrabpoint)

[GetPlayerPitch](#getplayerpitch)

[GetPlayerToolRecoil](#getplayertoolrecoil)

[GetVehicleLocationWorldTransform](#getvehiclelocationworldtransformvehicle)

[IsAchievementCompleted](#isachievementcompleted)

[IndicateAchievementProgress](#indicateachievementprogress)

[IsPlayerJumping](#isplayerjumping)

[GetScriptId](#getscriptid)

[GetShapeStrength](#getshapestrength)

[IsRunningOn...](#isrunningon)

[RobotRemoveTaggedJointsCPP](#robotremovetaggedjointscpp)

[SaveShape](#saveshape)

[SetClipboardText](#setclipboardtext)

[TriggerEvent](#triggerevent)

[RadiolinkCheckConnectionCPP](#radiolinkcheckconnectioncpp)

[RadiolinkDrawLinesCPP](#radiolinkdrawlinescpp)

[GetFlashlight](#getflashlight)

[SetFlashlight](#setflashlight)

[HasInputController](#hasinputcontroller)

[SaveCameraOverrideTransform](#savecameraoverridetransform)

---

## User Interface

User Interface functions, that are not officially documented.

[UiTextInput](#uitextinput)

[UiDrawLater](#uidrawlater)

[UiTextUnderline](#uitextunderline)

<!-- [UiTextToLower](#uitexttolower) -->

<!-- [UiTextToUpper](#uitexttoupper) -->

[UiRichTextSplitByWords](#uirichtextsplitbywords)

<!-- [UiTextInputKeyBoardShortCutKey](#uitextinputkeyboardshortcutkey) -->

---

## Voxscript

Voxscript functions. <!-- Remove if you find official documentation of them. -->

[Randomize](#randomize)

[RandomFloat](#randomfloat)

[RandomInt](#randomint)

[CreateMaterial](#creatematerial)

[CreateBrush](#createbrush)

[FlipBrush](#flipbrush)

[RotateBrush](#rotatebrush)

[TranslateBrush](#translatebrush)

[GetBrushSize](#getbrushsize)

[Material](#material)

[GetImageSize](#getimagesize)

[GetImagePixel](#getimagepixel)

[Vox](#vox)

[Box](#box)

[Sphere](#sphere)

[Line](#line)

[Set](#set)

[Get](#get)

[Heightmap](#heightmap)

---
<!-- Types are:
 - handle     (number) - entity id
 - number     (number) - any number value
 - bool       (true|false) - boolean
 - string     (text) - any text
 - TVec       (table) - table with 3 entries / x;y;z   (axis)
 - TQuat      (table) - table with 4 entries / ?;?;?;? (has pitch and yaw?)
 - TTransform (table) - {TVec, TQuat}        
 - any        (number|true|false|text|table) - dependant on other input | undefined
 - table      (table) - any table
 - $type, optional - points out that argument is not required for function to work and has a default value when not given ; Show on example as [$in] (square brackets)
 -->

# AddSnow

> ### AddSnow(shape, point, amount)

> ## Arguments
>
> shape (handle) - Shape handle
> 
> point (vec) - Vector Point on shape
> 
> amount (number) - Amount of snow

> ## Return value
>
> none

Adds a snowball with defined size to shape.

    function init()
        shape = FindShape("shape", true)

        AddSnow(shape, Vec(.5, 0, 0), 0.25)
    end

---

# Command

> ### Command(cmd, param)

> ## Arguments
>
> cmd (string) - Command (check out [1ssnl's Dennispedia](https://x4fx77x4f.github.io/dennispedia/teardown/g/Command.html) for a list of commands (arguments))
> 
> param (depends on previous argument) - Parameter for given command (if any)

> ## Return Value
>
> none

Runs engine commands (e.g. taking a screenshot, opening a url/folder, etc.).

    function tick(dt)
        if InputPressed("f2") then
            Command("game.screenshot")
        end
    end

---

# CompleteAchievement

**Only works if called by *data/script/achievements.lua***

> ### CompleteAchievement(ach_id)

> ## Arguments
>
> ach_id (string) - Achievement id

> ## Return value
>
> none

Completes steam/ps/xbox achievement.

    -- redacted

---

# GetClipboardText

**Only works if called by a *privileged script***

> ### text = GetClipboardText()

> ## Arguments
>
> none

> ## Return value
>
> text (string) - Current clipboard content, nothing if clipboard isn't plain text

Gets device clipboard latest entry.

    fucntion tick(dt)
        clipboard = GetClipboardText()
        DebugPrint(clipboard)
    end

---

# GetEvent

> ### a, b, c, d = GetEvent()

> ## Arguments
>
> event (string) - event name
> 
> id (number) - event id (number in order of when events happened)

> ## Return Value
>
> Usually 4 outputs, but depends on *event*

Gets info about event

    function tick(dt)
        count = GetEventCount("playerhurt")

        for i=1, #count do
            player, before, after, attacker = GetEvent("playerhurt", i)
        end
    end

---

# GetEventCount

> ### count = GetEventCount(event)

> ## Arguments
>
> event (string) - event name

> ## Return value
>
> count (number) - amount of events with such name

Gets the amount of events that already happened

    function tick(dt)
        count = GetEventCount("playerhurt")

        for i=1, #count do
            player, before, after, attacker = GetEvent("playerhurt", i)
        end
    end

---

# DisableAllLights

> ### DisableAllLights()

> ## Arguments
>
> none

> ## Return value
>
> none

Disables all enabled lights.

    function init()
        DisableAllLights()
    end

---

# GetPlayerCrouch

> ### crouch = GetPlayerCrouch()

> ## Arguments
>
> none

> ## Return value
>
> crouch (number) - Crouch, usually ~2.802 when standing and ~0.999 when crouching

Gets player crouch (?).

    function tick(dt)
        crouch = GetPlayerCrouch()
        DebugPrint(crouch)
    end

---

# GetPlayerGrabPoint

> ### grabPoint = GetPlayerGrabPoint()

> ## Arguments
>
> none

> ## Return value
>
> grabPoint (TVec) - Vector position in world space

Gets the point in world space, where the player has grabbed a shape.

    function tick(dt)
        DebugWatch("player grab point", GetPlayerGrabPoint())
    end

---

# GetPlayerPitch

> ### pitch = GetPlayerPitch()

> ## Arguments
>
> none

> ## Return value
>
> pitch (number) - Player pitch ~-80.2 - straight down (not literally); ~80.2 - straight up (not literally)

Gets player pitch.

    function tick(dt)
        pitch = GetPlayerPitch()
        DebugPrint(pitch)
    end

---

# GetPlayerToolRecoil

**Only works if called by a *privileged script***

> ### recoil = GetPlayerToolRecoil()

> ## Arguments
>
> none

> ## Return value
>
> recoil (number) - 0 if tool doesn't have recoil or isn't used

Gets the current tool's recoil amount.

    function tick(dt)
        recoil = GetPlayerToolRecoil()
        DebugPrint(recoil)
    end

---

# GetVehicleLocationWorldTransform

> ### world = GetVehicleLocationWorldTransform(vehicle)

> ## Arguments
>
> vehicle (handle) - Vehicle handle

> ## Return value
>
> world (TVec) <!-- Seems to return nothing ;; Verify -->

Gets vehicle world space transform.

    function tick(dt)
        vehicle = FindVehicle("dumptruck", true)
        DebugWatch("vehicle world transform", GetVehicleLocationWorldTransform(vehicle))
    end

---

# IsAchievementCompleted

**Only works if called by *data/script/achievements.lua***

> ### completed = IsAchievementCompleted(id)

> ## Arguments
>
> id (string) - Achievement id

> ## Return value
>
> completed (bool) - True if completed, false if not

Checks if given achievement is completed.

    -- redacted

---

# IndicateAchievementProgress

**Only works if called by *data/script/achievements.lua***

> ### IndicateAchievementProgress(id, cur, max)

> ## Arguments
>
> id (string) - Achievement id
> 
> cur (number) - Current progress
> 
> max (number) - Maximum progress

> ## Return value
>
> none

Indicates how much of an achievement you've completed.

    -- redacted

---

# IsPlayerJumping

> ### jumping = IsPlayerJumping()

> ## Arguments
>
> none

> ## Return value
>
> jumping (bool) - True if jumping, false if not - *True only the tick the player presses jump*

Gets if the player is jumping.

    function tick(dt)
        jumping = IsPlayerJumping()
        if jumping then
            DebugPrint("Player Jumped!")
        else
            DebugPrint("Player isn't jumping.")
        end
    end

---

# GetScriptId

> ### script = GetScriptId()

> ## Arguments
>
> none

> ## Return value
>
> script (handle) - Handle to script

Gets handle of script that ran the fucntion.

    function init()
        script = GetScriptId()
        DebugPrint(script)
    end

---

# GetShapeStrength

> ### strength = GetShapeStrength(shape)

> ## Arguments
>
> shape (handle) - Shape

> ## Return value
>
> strength (number) - Shape Strength

Gets strength parameter of shape.

    function init()
        shape = FindShape("shape")
        strength = GetShapeStrength(shape)
        DebugPrint("Shape strength: " .. strength)
    end

---

# IsRunningOn...

> ### isRunning = IsRunningOn...()
List of available platforms:
- Apple
- Egs (Epic Games Store)
- IOS
- Mac
- PC
- PlayStation
- PlayStation5
- Steam
- SteamDeck
- Switch
- Xbox
- XboxS
- XboxX

> ## Arguments
>
> none

> ## Return value
>
> isRunning (bool) - True if it is running, false if not

Checks if game is being ran on specified platform.

    function draw(dt)
        if IsRunningOnXbox() then
            UiText("Use X to attack")
        end
    end

---

# RobotRemoveTaggedJointsCPP

> ### RobotRemoveTaggedJointsCPP(time, tag1, tag2)

> ## Arguments
>
> time (number) - time until removal
>
> tag1 (string) - tag №1 (usually "plank")
>
> tag2 (string) - tag №2 (usually "wire")

> ## Return Value
>
> none

Detaches joints connected to robot that are tagged with either **tag1** or **tag2**

    -- Make a proper code example :/
    function tick(dt)
        RobotRemoveTaggedJointsCPP(dt, "plank", "wire")
    end

---

# SaveShape

**Only works if called by a *privileged script***

> ### saved, error = SaveShape(shape, filename)

> ## Arguments
>
> shape (handle) - Shape
> 
> filename (string) - File name, mustn't contain \\/:*?<>\| (best is to keep to just text and numbers without spaces)

> ## Return value
>
> saved (bool) - True if shape was saved, false if not
>
> error (string) - Reason in case shape wasn't saved (either "no_space" or "invalid_name")

Saves shape (and its xml) to *Documents\Teardown\creativemode* and makes it spawnable.

    function init()
        shape = FindShape("saveable")
    end

    function tick(dt)
        if InputDown("ctrl") and InputPressed("s") then
            saved, error = SaveShape(shape, "shape_" .. shape .. "-" .. math.random(0, 99))
            if not saved and error == "no_space" then
                SetString("hud.notification", "Not enough memory")
            elseif error == "invalid_name" then
                SetString("hud.notification", "Invalid name")
            end
        end
    end

---

# SetClipboardText

**Only works if called by a *privileged script***

> ### SetClipboardText(text)

> ## Arguments
>
> text (string) - Clipboard text

> ## Return value
>
> none

Copies given text to device clipboard (ONLY RUN ONCE!).

    function init()
        SetClipboardText("Hello, World!")
    end

---

# TriggerEvent

> ### TriggerEvent(event, param)

> ## Arguments
>
> event (string) - event name
>
> param (any) - event param

> ## Return Value
>
> none

Triggers an event with given parameter

    -- Please, give a better example smh, don't copy data/script/characters.lua code
    local function UnlockCharacter(character)
        SetBool("savegame.characters." .. character, true)
        SetBool("savegame.freshcharacters." .. character, true)
        TriggerEvent("CharUnlocked", character)
    end

---

# RadiolinkCheckConnectionCPP

> ### connection, dir, length = RadiolinkCheckConnectionCPP(rPos, tPos, rShape, tShape)

> ## Arguments
>
> rPos (TVec) - reciever pos
>
> tPos (TVec) - transmitter pos
>
> rShape (handle) - reciever shape
>
> tShape (handle) - transmitter shape

> ## Return value
>
> connection (bool) - true if there are no shapes between *r* and *t* and if the points are close enough
>
> dir (TQuat) - direction <!-- Verify either TQuat, TVec or TTransform -->
>
> length (number) - distance between *r* and *t*

Checks if connection can be made between two points (*r* and *t*).

    -- No example available :/

---

# RadiolinkDrawLinesCPP

> ### RadiolinkDrawLinesCPP(radius, length, dir, tPos, rPos, timer, r, g, b, a)

> ## Arguments
>
> radius (number) - Line radius
>
> length (number) - Line length
>
> dir (TVec) - Line direction
>
> tPos (TVec) - transmitter pos
>
> rPos (TVec) - reciever pos
>
> timer (number)
>
> r (number) - red color value (between 0 and 1)
>
> g (number) - green color value (between 0 and 1)
>
> b (number) - blue color value (between 0 and 1)
>
> a (number) - alpha channel value (between 0 and 1)

> ## Return value
>
> none

Draws a line between two points (*t* and *r*) with given radius and color.

    -- No example available :/

---

# GetFlashlight

> ### flash = GetFlashlight()

> ## Arguments
>
> none

> ## Return value
>
> flashlight (handle) - handle to flashlight

Gets handle of current flashlight.

    function init()
        flash = GetFlashlight()
        DebugWatch("old", flash)
        
        --- Make a proper example

        new = FindLight("newflash", true)
        SetFlashlight(new)
        DebugWatch("new", new)
    end

---

# SetFlashlight

> ### SetFlashlight(light)

> ## Arguments
>
> light (handle) - any light on the level

> ## Return value
>
> none

Sets given light as player flashlight (doesn't work with all lights).

    function init()
        flash = GetFlashlight()
        DebugWatch("old", flash)
        
        --- Make a proper example

        new = FindLight("newflash", true)
        SetFlashlight(new)
        DebugWatch("new", new)
    end

---

# HasInputController

**Only works if called by a *privileged script***

> ### has = HasInputController()

> ## Arguments
>
> none

> ## Return value
>
> has (bool) - whether player has input controller or not

Checks whether the player has an input controller or not.

    function tick(dt)
        if (IsRunningOnXbox() or IsRunningOnPlaystation()) and not controllerDisconnectedShow and LastInputDevice() == UI_DEVICE_GAMEPAD and not HasInputController() then
            controllerDisconnectedShow = true
            controllerDisconnectedWasPaused = GetBool("game.paused")
            SetValue("controllerDisconnectedAlpha", 1, "easeout", 0.25)
            SetPaused(true)
        end
    end

---

# SaveCameraOverrideTransform

> ### SaveCameraOverrideTransform()

> ## Arguments
>
> none

> ## Return value
>
> none

Saves the camera override transform after exiting override mode.

    -- No example available :/

---

# ResumeLevel()

> ### ResumeLevel(id, file, \[layers\], \[qs\]) <!-- TOOD: Verify? -->

> ## Arguments
>
> id (string) - Level id
>
> file (string) - Path to level XML/bin (*bin* has limited use)
>
> layers (string, optional) - Level layers
>
> qs (string, optional) - Quicksave

> ## Return value
>
> none

Resumes level.

    function resumeCampaign()
        -- find next mission: opened but without required score
        -- otherwise start hub
        for id,mission in pairs(gMissions) do
            if GetInt("savegame.mission."..id) > 0 and GetInt("savegame.mission."..id..".score") < mission.required then
                ResumeLevel(id, mission.file, mission.layers, "quicksavecampaign")
                return
            end
        end
        startHub()
    end

---

# UiTextInput

> ### input, active = UiTextInput(str, w, h, focus, \[hideCursor\])

> ## Arguments
>
> str (string) - Default text
>
> w (number) - Input field width
>
> h (number) - Input field height
>
> focus (bool)
>
> hideCursor (bool, optional)

> ## Return value
>
> input (string) - Input text
>
> active (bool) - Whether text field is in focus (selected)

Creates a text field that detects text input from keyboard.

    -- No example avaliable :/

---

# UiDrawLater

> ### UiDrawLater(draw) <!--I have no idea how this works -->

> ## Arguments
>
> draw (table) - What to draw

> ## Return value
>
> none

Draws given components later.

    -- Structure is:
	UiDrawLater({
		draw = function(self) --Required, as is
			UiPush()
			-- Whatever you want to draw
		UiPop()
		end --of draw self function
	})

---

# UiTextUnderline

> ### UiTextUnderline(bool)

> ## Arguments
>
> bool (bool) - Whether to underline text

> ## Return value
>
> none

Underlines upcoming text.

    function draw(dt)
        UiPush()
            UiFont("bold.ttf", 20)
            UiTranslate(0, 20)
            UiTextUnderline(true) -- Will underline any UiText() underneath, until set to false
            UiText("Hello, World!")
            UiTextUnderline(false) -- End of underline
            UiTranslate(0, 20)
            UiText("Goodbye, Cruel world!")
        UiPop()
    end

---

<!-- # UiTextToLower

**Only works if called by a *privileged script***

> ### upper = UiTextToLower(text)


> ## Arguments
>
> 

> ## Return value
>
> none?

_desc

    -- No example available :/

--- -->

<!-- # UiTextToUpper

**Only works if called by a *privileged script***

> ### lower = UiTextToUpper(text)

> ## Arguments
>
> 

> ## Return value
>
> lower (number)

_desc

    -- No example available :/

--- -->

# UiRichTextSplitByWords <!-- Research more abt function and how it works -->

**Only works if called by a *privileged script***

> ### words = UiRichTextSplitByWords(text)

> ## Arguments
>
> text (string)

> ## Return value
>
> words (table) - Words (list of words, separated by a space. Retains punctuation (execpt for commas) and spaces)

Turns string into table of words, separated by spaces, rataining all types of punctuation (exept commas).

    function draw(dt)
        words = UiRichTextSplitByWords("(Lorem ipsum), {dolor,} sit amet :O")
        DebugPrint(words)
    end

---
<!-- Seems not to do anything?????
# UiTextInputKeyBoardShortCutKey

> ### UiTextInputKeyBoardShortCutKey(shortcut)

> ## Arguments
>
> shortcut (string)

> ## Return value
>
> none

Binds keyboard shortcut to upcomming [UiTextInput()](#uitextinput) call.

    -- No example available :/

--- -->
<!-- Start of Voxscript section -->
# Randomize

> ### Randomize(\[seed\])

> ## Arguments
>
> seed (number, optional) - Random seed. If omited, system time will be used

> ## Return value
>
> none

Randomizes seed.

    -- No example available :/

---

---

# RandomFloat

> ### r = RandomFloat(min, max)

> ## Arguments
>
> min (number) - Start of RNG range
>
> max (number) - End of RNG range

> ## Return value
>
> r (number) - Random floating point number between *min* and *max*

Generates a random floating point number from given range.

    function init()
        local r = RandomFloat(1.0, 6.0)
    end

---

# RandomInt

> ### r = RandomInt(lower, upper)

> ## Arguments
>
> lower (number) - Start of RNG range
>
> upper (number) - End of RNG range

> ## Return value
>
> r (number) - Random integer from lower bound to (and includng) upper bound

Generates a random integer from lower bound to (and including) upper bound.

    function init()
        local r = RandomInt(1, 3) -- Will reter either 1, 2 or 3
    end

---

# CreateMaterial

> ### mat = CreateMaterial(type, r, g, b, \[a\], \[reflect\], \[shiny\], \[metal\], \[emissive\])

> ## Arguments
>
> type (string) - Material; Either glass, wood, masonry, plaster, metal, heavymetal, rock, dirt, foliage, plastic, hardmetal, hardmasonry, ice or unphysical <!-- maybe hole and snow too?? -->
>
> r (number) -  Red color value, in range 0.0 to 1.0 
>
> g (number) - Green color value, in range 0.0 to 1.0 
>
> b (number) - Blue color value, in range 0.0 to 1.0 
>
> a (number, optional) - Alpha channel value, in range 0.0 to 1.0 (from image)
>
> reflect (number, optional) - Material reflectivity, in range 0.0 to 1.0
>
> shiny (number, optional) - Material shininess, in range 0.0 to 1.0
>
> metal (number, optional) - Material metalic value, in range 0.0 to 1.0
>
> emissive (number, optional) - Material light emission value, in range 0.0 to 32.0

> ## Return value
>
> mat (handle) - Material handle *

Creates a material.

    function init()
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    end

---

# CreateBrush

> ### CreateBrush(path, \[local\])

> ## Arguments
>
> path (string) - Path to vox file and optional object
>
> local (bool, optional) - Use local coordinates for all operations, false by default

> ## Return value
>
> none

Creates a brush.

    function init()
    	Vox(0,0,0)

    	brickWall = CreateBrush("MOD/brickwall.vox")
    	Material(brickWall)
    	Box(0, 0, 0, 10, 10, 10)

    	bulgarianFlag = CreateBrush("MOD/flags.vox:bulgaria")
    	Material(bulgarianFlag)
    	Box(0, 0, 0, 20, 15, 1)
    end

---

# FlipBrush

> ### FlipBrush(brush, axes)

> ## Arguments
>
> brush (handle)
>
> axes (string) - Etiher *x*, *y* or *z*

> ## Return value
>
> none

Flips given brush on specified axes.

    function init()
    	local brush = CreateBrush("brush/white.vox")
    	FlipBrush(brush, "x")
    	Material(brush)
    	Box(0, 0, 0, 20, 15, 5)
    end

---

# RotateBrush

> ### RotateBrush(brush, axes, angle)

> ## Arguments
>
> brush (handle)
>
> axes (string) - Either *x*, *y* or *z*
>
> angle (number)

> ## Return value
>
> none

Rotates given brush on specified axes and angle.

    function init()
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	--Draw box with brush rotated 90 degrees around y axis
    	RotateBrush(brush, "y", 90)
    	Material(brick)
    	Vox(0,0,0)
    	Box(0, 0, 0, 10, 10, 10)
    end

---

# TranslateBrush

> ### TranslateBrush(brush, x, y, z)

> ## Arguments
>
> brush (handle)
>
> x (number) - Offset along x axiz
>
> y (number) - Offset along y axiz
>
> z (number) - Offest along z axiz

> ## Return value
>
> none

Apply translation on given brush.

    function init()
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Vox(0,0,0)
    	Box(0, 0, 0, 10, 10, 10)
    	TranslateBrush(brush, 5, 0, 0)
	    Box(0, 0, 0, 10, 10, 10)
    end

---

# GetBrushSize

> ### x, y, z = GetBrushSize(brush)

> ## Arguments
>
> brush (handle)

> ## Return value
>
> x (number) - Size along x axis
>
> y (number) - Size along y axis
>
> z (number) - Size along z axis

Returns brush size in voxels.

    function init()
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Vox(0,0,0)
    	Box(0, 0, 0, 10, 10, 10)

    	local xs, ys, zs = GetBrushSize(brush)
    end

---

# Material

> ### Material(material)

> ## Arguments
>
> material (handle) - Material handle *

> ## Return value
>
> none

Set current material brush. Set *material* to zero to reset.

    function init()
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Vox(0,0,0)
    	Box(0, 0, 0, 10, 10, 10)

    	--Make box hollow
    	Material(0)
    	Box(2, 2, 2, 8, 8, 8)
    end

---

# LoadImage

> ### LoadImage(path, \[grassMapPath\])

> ## Arguments
>
> path (string) - Path to PNG image
>
> grassMapPath (string, optional) - Path to grass map PNG image

> ## Return value
>
> none

Load heightmap PNG.

    function init()
        LoadImage("MOD/heightmap.png", "MOD/grassmap.png")
    end

---

# GetImageSize

> ### w, h = GetImageSize()

> ## Arguments
>
> none

> ## Return value
>
> w (number) - Image width
>
> h (number) - Image height

Returns image size.

    function init()
    	LoadImage("MOD/image.png")
    	local w, h = GetImageSize()
    end

---

# GetImagePixel

> ### r, g, b, a = GetImagePixel(x, y)

> ## Arguments
>
> x (number) - Pixel position x coordinate
>
> y (number) - Pixel position y coordinate

> ## Return value
>
> r (number) - Red value
>
> g (number) - Green value
>
> b (number) - Blue value
>
> a (number) - Alpha channel value

Return color value for image pixel.

    function init()
    	LoadImage("MOD/image.png")
    	local r,g,b,a = GetImagePixel(50, 50)
    end

---

# Vox

> ### Vox(x, y, z, rx, ry, rz)

> ## Arguments
>
> x (number) - X position
>
> y (number) - Y position
>
> z (number) - Z position
>
> rx (number) - Rotation around x axis in degrees
>
> ry (number) - Rotation around y axis in degrees
>
> rz (number) - Rotation around z axis in degrees

> ## Return value
>
> none

Create new shape.

    function init()
    	--Create vox shape
        Vox(0,0,0)

    	--We can now fill it with content
        local brush = CreateBrush("brush/white.vox")
        local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
        Material(brick)
        Box(0, 0, 0, 10, 10, 10)
    end

---

# Box

> ### Box(x0, y0, z0, x1, y1, z1)

> ## Arguments
>
> x0 (number) - Start position on x axis
>
> y0 (number) - Start position on y axis
>
> z0 (number) - Start position on z axis
>
> x1 (number) - End position on x axis
>
> y1 (number) - End position on y axis
>
> z1 (number) - End position on z axis

> ## Return value
>
> none

Draw solid box into current shape using currently selected material.

    function init()
        Vox(0,0,0)
        local brush = CreateBrush("brush/white.vox")
        local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
        Material(brick)
        Box(0, 0, 0, 10, 10, 10)
    end

---

# Sphere

> ### Sphere(x, y, z, r)

> ## Arguments
>
> x (number) - Center position on x axis
>
> y (number) - Center position on y axis
>
> z (number) - Center position on z axis
>
> r (number) - Sphere radius

> ## Return value
>
> none

Draw solid sphere into current shape using the currently selected material.

    function init()
    	Vox(0,0,0)
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Sphere(0, 0, 0, 15)
    end

---

# Line

> ### Line(x0, y0, z0, x1, y1, z1, thicknessStart, thicknessEnd)

> ## Arguments
>
> x0 - Start position on x axis
>
> y0 - Start position on y axis
>
> z0 - Start position on z axis
>
> x1 - End position on x axis
>
> y1 - End position on y axis
>
> z1 - End position on z axis
>
> thicknessStart (number)
>
> thicknessEnd (number)

> ## Return value
>
> none

Draw a solid line between two points with given thickness.

    function init()
    	Vox(0,0,0)
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Line(0, 0, 0, 15)
    end

---

# Set

> ### Set(x, y, z)

> ## Arguments
>
> x (number) - X position
>
> y (number) - Y position
>
> z (number) - Z position

> ## Return value
>
> none

Sets a single voxel in specified position.

    function init()
    	Vox(0,0,0)
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Set(0, 0, 0)
    end

---

# Get

> ### mat = Get(x, y, z)

> ## Arguments
>
> x (number) - X position
>
> y (number) - Y position
>
> z (number) - Z position

> ## Return value
>
> mat (handle) - Material handle *

Returns voxel material's handle at specified position.

    function init()
    	Vox(0,0,0)
    	local brush = CreateBrush("brush/white.vox")
    	local brick = CreateMaterial("masonry", 0.6, 0.5, 0.3, 0, 0.1, 0, 0)
    	Material(brick)
    	Set(0, 0, 0)
    	Material(Get(0, 0, 0))
    end

---

# Heightmap

> ### Heightmap(x0, y0, x1, y1, \[height\], \[isntHollow\], \[cropBorder\])

> ## Arguments
>
> x0 (number) - Start position on x axis
>
> y0 (number) - Stat position on y axis
>
> x1 (number) - End position on x axis
>
> y1 (number) - End position on y axis
>
> height (number, optional) - Height scale
>
> isntHollow (bool, optional) - Unused, for legacy support
>
> cropBorder (bool, optional) - Use special handling of borders in heightmap, reduces amount of voxels and their size

> ## Return value
>
> none

---

Also check out [tags list](https://uwq-official.github.io/game-stuff/teardown/tags) :)
