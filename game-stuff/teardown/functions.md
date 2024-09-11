# Undocumented Functions

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

    function tick(dt)
        if not IsAchievementCompleted("ACH_WATCH_ABOUT") then
            CompleteAchievement("ACH_WATCH_ABOUT")
        end
    end

---

# GetClipboardText

**Only works if called by a *privileged script***

> ### GetClipboardText()

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

> ### GetEvent()

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

> ### GetEventCound(event)

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

> ### GetPlayerCrouch()

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

> ### GetPlayerGrabPoint()

> ## Arguments
>
> none

> ## Return value
>
> grab point (Vec) - Vector position in world space

Gets the point in world space, where the player has grabbed a shape.

    function tick(dt)
        DebugWatch("player grab point", GetPlayerGrabPoint())
    end

---

# GetPlayerPitch

> ### GetPlayerPitch()

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

> ### GetPlayerToolRecoil()

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

> ### GetVehicleLocationWorldTransform(vehicle)

> ## Arguments
>
> vehicle (handle) - Vehicle handle

> ## Return value
>
> world (TTransform) - none?

Gets vehicle world space transform.

    function tick(dt)
        vehicle = FindVehicle("dumptruck", true)
        DebugWatch("vehicle world transform", GetVehicleLocationWorldTransform(vehicle))
    end

---

# IsAchievementCompleted

**Only works if called by *data/script/achievements.lua***

> ### IsAchievementCompleted(id)

> ## Arguments
>
> id (string) - Achievement id

> ## Return value
>
> completed (bool) - True if completed, false if not

Checks if given achievement is completed.

    fucntion tick(dt)
        if not IsAchievementCompleted("ACH_WATCH_ABOUT") then
            CompleteAchievement("ACH_WATCH_ABOUT")
        end
    end

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

    if not IsAchievementCompleted(PROGRESSIVE_ACH) then
        IndicateAchievementProgress(PROGRESSIVE_ACH, savegameValue, 300)
    end

---

# IsPlayerJumping

> ### IsPlayerJumping()

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

> ### GetScriptId()

> ## Arguments
>
> none

> ## Return value
>
> script id (handle) - Handle to script

Gets handle of script that ran the fucntion.

    function init()
        script = GetScriptId()
        DebugPrint(GetScriptId())
    end

---

# GetShapeStrength

> ### GetShapeStrength(shape)

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

> ### IsRunningOn...()
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
> is running (bool) - True if it is running, false if not

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

> ### SaveShape(shape, filename)

> ## Arguments
>
> shape (handle) - Shape
> 
> filename (string) - File name, mustn't contain \\/:*?<>\| (best is to keep to just text and numbers without spaces)

> ## Return value
>
> none

Saves shape (and its xml) to *Documents\Teardown\creativemode* and makes it spawnable.

    function init()
        shape = FindShape("saveable")
    end

    function tick(dt)
        If InputDown("ctrl") and InputPressed("s") then
            SaveShape(shape, "shape_" .. shape .. "-" .. math.random(0, 99))
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
> event - event name
>
> param - event param

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

Also check out [tags list](https://uwq-official.github.io/game-stuff/teardown/tags) :)
