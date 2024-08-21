# Tags List

**Keep in mind, that this page contains only engine tags!**

> ## autobreak
>
> body
>
> Makes body require a smaller inertia to trigger a break event.

> ## boat
>
> vehicle
>
> Turns the vehicle into a boat.

> ## bomb=*time*
>
> shape
>
> Creates an explosion at shape's location and deletes it after the *time* runs out. Time is in seconds.

> ## bombstrength=*strength*
>
> shape
>
> Goes with **bomb** tag. Controls the explosion strenght (0.5 - 4) of **bomb**.

> ## booster=*time*
>
> shape
>
> Maximum *time* is 9 seconds, but if set to 7, flame particles will appear out of shape origin, going in +Z axis. Shape will act like a rocket booster when tagged.

> ## camera
>
> location
>
> Used to define pivot point of vehicle 3rd person camera.

> ## crane
>
> vehicle
>
> All hinge joints can be controlled with vehicle_raise/lower and vehicle displays bed controls. Hook can also hook.

> ## cranebottom
>
> vehicle
>
> Same as **crane**, but displays base crane contorls.

> ## cranetop
>
> vehicle
>
> Displays crane arm controls.

> ## dumptruck
>
> vehicle
>
> Same as **crane**, but without hook.

> ## exhaust=*amount*
>
> location
>
> Defines location of vehicle exhaust. If location is not present, vehicle won't output any smoke.
>
> *amount* is amount of smoke exhausted. The location can be rotated, where the exhaus comes out of opposite side of *location line*.

> ## exit
>
> location
>
> Defines where the player will exit from the vehicle, if not present, it defaults to left of **player** location.

> ## explosive=*power*
>
> shape
>
> Shape explodes when broken. Power is from 0.5 to 4.

> ## extend
>
> joint
>
> Joint can be controlled by vehicle_raise/lower on **crane** vehicle.

> # forklift
>
> vehicle
>
> Same as **dumptruck**, but showes forklift controls.

> ## frontloader
>
> vehicle
>
> Same as **forklift** and **dumptruck**.

> ## hook
>
> body, shape
>
> Acts as **crane** hook, controlled by vehicle_action.

> ## inherittags
>
> body, shape
>
> When tagged, the debris of broken shape will inherit the tags from the original (recursive).

> ## interact=*text*
>
> body, shape
>
> Makes tagged entities display an interaction prompt when player is close to shape. [GetPlayerInteractShape](https://teardowngame.com/modding/api.html#GetPlayerInteractShape)/[GetPlayerInteractBody](https://teardowngame.com/modding/api.html#GetPlayerInteractBody) only work on bodies/shapes with this tag.
>
> *text* can be any word (as long as it doesn't contain spaces) or localization entry.

> ## invisible
>
> shape
>
> Makes shape invisible to player, but it still acts like normal.

> ## level
>
> joint
>
> Force **skylift** joints to all have same rotation amount

> ## night
>
> light
>
> Tagged lights will be turned off when enviroment parameter *nightlight* is currently set to *false*.

> ## nocull
>
> shape
>
> Shape won't be culled (unloaded when out of player render distance).

> ## nodrive
>
> vehicle
>
> Tagged vehicle cannot be driven by player.

> ## nonav
>
> shape
>
> Shape is disreguarded by pathfinding.

> ## snow
>
> shape
>
> Tagged shape doesn't spawn with a layer of snow on it (when *snow* enviroment property is enabled).

> ## passive
>
> vehicle
>
> Makes tagged vehicle uncontrollable by player (disables controls such as going forward/revesing or bed and hook controls).

> ## player
>
> location
>
> Defines where the 1st person camera of parent vehicle is (rotation also aplies?).



