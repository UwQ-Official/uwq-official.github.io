# Teardown Editor Elements

[animator](#animator)
[body](#body)
[boundary](#boundary)
[comment](#comment)     <!-- editor -->
[compound](#compound)   <!-- shape -->
[environment](#environment) <!-- resolved -->
[group](#group)     <!-- editor -->
[instance](#instance) <!-- resolved -->
[joint](#joint)
[light](#light)
[location](#location)
[postprocessing](#postprocessing) <!-- resolved -->
[rope](#rope)
[screen](#screen)
[script](#script)
[spawnpoint](#spawnpoint) <!-- resolved -->
[trigger](#trigger)
[vehicle](#vehicle)
[vox](#vox)             <!-- shapes -->
[voxbox](#voxbox)
[voxagon](#voxagon)
[voxscript](#voxscript) <!-- -->
[water](#water)
[wheel](#wheel)

---

## Overall

Format:

> property (type) - description \[default values\]

Most elements have these properties:

> name (string) - name to show in editor 
>
> template (string) - template id to apply
>
> tags (string, list) - list of tags (separated by spaces)
>
> pos (vec) - position in world \[0.0 0.0 0.0\]
>
> rot (vec) - rotation \[0 0 0\]

---

# scene

>
> ### version (version) {invisible} - game version in which the level was last saved
>
> name
> 
> template
>
> tags - doesn't matter, doesn't exist
>
> pos
>
> rot
>
> ### shadowVolume (vec) - Area in which shadows will be cast and proper lighting will exist

The scene contains the entire level's components. One scene per level.

A outline of a box with a gray grid on the bottom.

**OR**:

# prefab

### Element is invisible, but differentiates between normal level and instance

> ### version (version) {invisible} - game version in which the level was last saved

---

# animator

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### file (full path) - xml file

Used for rigs and animations.

Invisible unless clicked, a box with white outlines

---

# body

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### dynamic (bool) - if body is dynamic or not \[✓ true\]
>
> ### desc (string) - description (text appears at the bottom of the screen when looking at body)

Used to group shapes toghether while being detectable by scripts (unlike *group*s).

Invisible unless clicked, a box with white outlines

---

# boundary

> name
>
> template
>
> tags - doesn't matter, can't be found by scripts
>
> pos
>
> rot
>
> ### padleft (number) - left padding \[5\]
>
> ### padright (number) - right padding \[5\]
>
> ### padtop (number) - top padding \[5\]
>
> ### padbottom (number) - bottom padding \[5\]
>
> ### maxheight (number) - max height (places a wall at limit) \[0\]

Adds 4 walls surrounding you that prevent you from exiting the map area (going out of the boundary sometimes crashes the game).

Invisible unless clicked, a yellow outline of a polygon (with a second one on top of it, if **maxheight** property is greater than 0)

---

# comment

> name
>
> pos {invisible}
>
> rot {invisible}
>
> ### text (string, multiline) - comment

Comment.

Invisible unless clicked, a box with a green outline.

---

# compound

> name
>
> template
>
> tags - doesn't matter, can't be found by scripts as its resolved
>
> pos
>
> rot
>
> ### desc (string) - description
>
> ### texture (number, list) - texture to be applied over children (has two inputs *texture* and *opacity* (range 0 - 1), separated by spaces)
>
> ### blendtexture (number, list) - same as **texture**
>
> ### density (number) - multiplies children weight by inputted number \[1.0\]
>
> ### strength (number) - makes children more/less prone to breakage by other shapes (tools still deal the same damage) \[1.0\]
>
> ### collide (bool) - whether children have collision or not \[true\]
>
> ### prop (bool) - dynamic \[false\]
>
> ### tilesize (number) - size of tiles to split the children into, also deletes any empty ones. Can contribute to better performance

Combines all of its children (shapes) into one.

Invisible unless clicked, a box with a pale outline.

---

# environment

> name
>
> template
>
> tags - doesn't matter, can't be found by scripts
>
> pos
>
> rot
>
> ### skybox (string) \[cloudy.dds\]
>
> ### skyboxtint (rgb) \[1 1 1\]
>
> ### skyboxbrightness (number) \[1.0\]
> 
> ### skyboxrot (number) - skybox rotation in Y axiz \[0.0\]
>
> ### constant (rgb) - constant light (unaffected by skybox and light sources) \[0.003 0.003 0.033\]
>
> ### ambient (number) - ambient light \[1.0\]
>
> ### ambientexponent (number) - shadow contrast \[1.3\]
>
> ### fogType (string) \[classic\]
> 
> ### fogColor (rgb) \[1 1 1\]
>
> ### fogParams (number, list) - *start*, *end*, *max amount*, *height* \[40 100 0.9 4\]
>
> ### fogHeightOffset (number) \[0.0\]
>
> ### sunBrightness (number) \[0\]
>
> ### sunColorTint (rgb) \[1 1 1\]
>
> ### sunDir (string) \[auto\]
>
> ### sunSpread (number) \[0\]
>
> ### sunLength (number) - maximum length of sunligth shadows (keep as low as possible for best performance) \[32\]
>
> ### sunFogScale (number) - volumetric fog caused by sun \[1.0\]
>
> ### sunGlare (number) \[1.0\]
>
> ### exposure (number, list) - *min*/*max* automatic exposure \[0 10\]
>
> ### brightness (number) - scene brightness (also controls exposure) \[1\]
>
> ### wetness (number) \[0\]
>
> ### puddleamount (number) \[0\]
>
> ### puddlesize (number) - average puddle size \[0.5\]
>
> ### rain (number) \[0\]
>
> ### nightligth (bool) - if false, all lights with [night](https://uwq-official.github.io/game-stuff/teardown/tags#night) tag will be disabled \[true\]
>
> ### ambience (partial path) - path starts from *data\snd\ambience* \[outdoor/field.ogg\]
>
> ### fogscale (number) \[1.0\]
>
> ### slippery (number) - makes outdoors slippery (affects vehicles) \[0.0\]
>
> ### waterhurt (number) - amount of damage for every second while player is in water \[0.0\]
>
> ### snowdir (number, list) - the direction it's snowing (*x*, *y*, *z* and *spread*) \[0 -1 0 0.2\]
>
> ### snowamount (number, optional list) - particle amount and optional speed \[0\]
>
> ### snowground (bool) - whether there is a layer of snow on every exposed shape's top \[false\]
>
> ### wind (vec) - wind direction (*x*, *y*, *z*) \[0 0 0\]

Used to controll the skybox, fog, sun, etc.

Invisible unless clicked, a box with a white outline.

---

# group

> name - if beggining with *instance=***path** it'll point to an instance
>
> template
>
> tags - doesn't matter, can't be found by scripts as it doesn't exist
>
> pos
>
> rot
>
> ### layer (string) - layer name ([read more about layers](https://teardowngame.com/modding/#editor/layers))
>
> ### prop0 (string, property) - custom property to be applied to all children (i.e. *tags=unbreakable nocull*)
>
> ### prop1 (string, property)
>
> ### prop2 (string, property)
>
> ### prop3 (string, property)

Groups elements toghether.

Invisible unless clicked, a box with a yellow outline.

---

# instance

> name
>
> template
>
> tags - can't be found by tags as its resolved
>
> pos
>
> rot
>
> ### file (string, full path) - xml file to load

Loads xml files with instances.

White outline.

---

# joint

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### type (string) - joint type \[ball\]
>
> ### size (number) \[0.1\]
>
> ### rotstrength (number) \[0.0\]
>
> ### rotspring (number) \[0.5\]
>
> ### collide (bool) - whether jointed shapes collide with each other \[false\]
>
> ### limits (number, list, conditional) - *min* and *max* limits (*cone* and *twist* angles for cone type)
>
> ### iklimits (number, list, conditional, optional) - same as previous, can be left empty to use normal limits
>
> ### sound (bool) - whether the joint squeaks when rotated \[false\]
>
> ### autodisable (bool, conditional) - whether the joint unjoints when shapes slide apart (for prismatic joints)

Joints shapes toghether in a lot of ways.

A blue outline of a box and a circle inside of it (box only visible when clicked).

---

# light

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### type (string) \[sphere\]
>
> ### color (rgb) \[1 1 1\]
>
> ### scale (number) - light intensity \[1\]
>
> ### angle (number, conditional) - light angle (for cone lights)
>
> ### penumbra (number, conditional) - penumbra angle (for cone lights)
>
> ### size (number, conditional, list) - *size* for sphere, *length* and *radius* for capsule, *width* and *height* for area \[0.1\]
>
> ### reach (number) - maximum light reach \[0.0\]
>
> ### undshadowed (number) - radius of small circle around light that light will shine through (even if blocked) and won't make shadows \[0.0\]
>
> ### fogscale (number) \[1\]
>
> ### fogiter (number) - fog quality, for important lights you can increase it to avoid flickering \[1\]
>
> ### sound (full path) - sound to be played while light is enabled
>
> ### glare (number) \[0\]
>
> ### enabled (bool) \[true\]

Light source.

Sphere: pink outline of a box and a circle inside of it (box only visible when clicked)
Capsule: pink outline of a cuboid 
Cone:  pink outline of a box and a cone inside of it pointing forward and a gray cone spreading from inside to reach point (box and gray cone only visible when clicked)
Area: pink outline of rectangle with given size

---

# location

> name
>
> template
>
> tags
>
> pos
>
> rot

An invisible point in space with no special properties.

A green outline of a box with a line pointing the opposite way of where the location is facing.

---

# postprocessing

> name
>
> template
>
> tags - doesn't matter
>
> pos
>
> rot
>
> ### saturation (number) \[1\]
>
> ### colorbalance (rgb) \[1 1 1\]
>
> ### brightness (number) \[1\]
>
> ### gamma (number) \[1\]
>
> ### bloom (number) \[1\]

Post-processing. One per scene.

default

---

# rope

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### size (number) - radius of attachment \[0.2\]
>
> ### color (rgb) \[0 0 0\]
>
> ### slack (number) - negative for tension, positive for slack \[0.0\]
>
> ### strength (number) - negative is infinite \[1.0\]
>
> ### maxstretch (number) - rope breaks when stretched more that this (zero for infinite) \[0.0\]

Creates a rope between two points (both points have to have a shape in their radius or no rope will be created).

█

---

# screen

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### size (number, list) - *width*, *height* \[0.9 0.5\]
>
> ### bulge (number) \[0.08\]
>
> ### resolution (number, list) - *width*, *height* in pixels \[640 480\]
>
> ### script (string, full path) - lua file to draw
>
> ### enabled (bool) \[false\]
>
> ### interactive (bool) - whether screen can be interacted with \[false\]
>
> ### emissive (number) - amount \[1\]
>
> ### fxraster (number) - amount \[0\]
>
> ### fxca (number) - chromatic abberation amount \[0\]
>
> ### fxnoise (number) - amount \[0\]
>
> ### fxglitch (number) - amount \[0\]

Screen that can display anything and can be interacted with.

█

---

# script

> name
>
> template
>
> tags - doesn't matter, only findable through [GetScriptId](https://uwq-official.github.io/game-stuff/teardown/functions#getscriptid)
>
> pos
>
> rot
>
> ### file (string, full path) - lua file

Parameters (defined by chosen script) can be either bool, number or string.

Executes given script.

█

---

# spawnpoint

> name
>
> template
>
> tags - doesn't matter, can't be found by scripts
>
> pot
>
> rot

Defines where the player will spawn. One per level.

█

---

# trigger

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### type (string) \[sphere\]
>
> ### size (number) \[10\]
>
> ### sound (string, full path) - sound to be played while in trigger
>
> ### soundramp (number) - sound rampup distance \[2.0\]

Trigger.

█

---

# vehicle

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### driven (bool) - if the vehicle is driven when entering level \[false\]
>
> ### sound (string, file name) - path starts from *data\snd\vehicle* \[medium\]
>
> ### spring (number) \[1.0\]
>
> ### damping (number) \[1.0\]
>
> ### topspeed (number) \[70.0\]
>
> ### acceleration (number) \[1.0\]
>
> ### strength (number) - engine strength \[1.0\]
>
> ### antispin (number) - prevent wheels from spining during acceleration (between 0 and 1) \[0.0\]
>
> ### antiroll (number) - prevent vehicle form tipping over \[0.0\]
>
> ### difflock (number) - differential control (increase for heavier vehicles) \[0.0\]
>
> ### steerassist (number) \[0.0\]
>
> ### friction (number) \[1.3\]

Vehicle. Also needs **wheels** as children.

█

---

# vox

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### desc (string)
>
> ### texture (number, list) - *texture*, *opacity*
>
> ### blendtexture (number, list) - *texture*, *opacity*
>
> ### density (number) - weight multiplier \[1.0\]
>
> ### strength (number) \[1.0\]
>
> ### collide (bool) \[true\]
>
> ### prop (bool) - dynamic \[false\]
>
> ### file (string, full path) - vox file
>
> ### layer (string) - vox file layer
>
> ### object (string) - vox file object
>
> ### scale (number) - scale multiplier (any scale other that 1 disables collision) \[1\]
>
> ### color (rgb) - shape tint \[1 1 1\]
>
> ### pbr (number, list) - *reflectivity*, *shinyness*, *metalness*, *emissive* \[0 0 0 0\]

Shape.

█

---

# voxbox

> name
>
> template
>
> tags
>
> pos
>
> rot
>
> ### desc (string)
>
> ### texture (number, list)
>
> ### blendtexture (number, list)
>
> ### density (number) \[1.0\]
>
> ### strength (number) \[1.0\]
>
> ### collide (bool) \[true\]
>
> ### prop (bool) \[false\]
>
> ### size (vec) - box size \[50 30 20\]
>
> ### brush (string, full path) - path to vox file or *hole*
>
> ### layer (string)
>
> ### object (string)
>
> ### offset (vec) - shape offset \[0 0 0\]
>
> ### material (string) - shape material (if no file is selected)
>
> ### color (rgb) \[1 1 1\]
>
> ### pbr (number, list) \[0 0 0 0\]

Shape box.

█

---