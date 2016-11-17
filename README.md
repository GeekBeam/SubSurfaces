# SubSurfaces
currently working with Raw files

Initially meant to be an update to Stanfear's own subsurfaces mod for factorio, upon looking at the code and attempting to fix it, it proved to be too unwieldy, messy, and processing intensive to be useful.

looking into other mods of similar typing (MagmaMcFry's Factorissimo, Simcra's Surfaces, and XiaoHong's NESTT), I realized that the SubSurfaces mod, while looking quite pretty and having good gameplay ideas to keep the spirit of factorio consistent, simply did not have the code efficiency it would need to hold up to high intensity gameplay (most particularly in megabases) nor the ability to add types of paired data in an expandable manner (like with the need to add electricity management due to the removal of Connect_Neighbour.copper as a viable method of connecting electric poles between surfaces)

the solution? recode the entire mod from the ground up to have an expandable system in the spirit of factorissimo's "rotating update queue" using a flag based system that has a single "onTickFunction" that will call subfunctions to handle more processing heavy work based on the existence of certain variables in a set of paired entities.

the whole system will require five basic "functions" to tie into the "Updater" onTickFunction,
-Belt_updt
-fluid_updt
-chest_updt
-electricity_updt
-player_tlprt

each function will move it's pertinent data from location "A" to location "B" and will be passed this data by the updater TickFunction.

outside this, other features will include requiring research to unlock the ability to move between surfaces, a need to manage pollution intensity within a subsurface to prevent "suffocation" movement of resources via chest/belt and fluids, and also another type of resource movement that uses wire conditions (which can be set by the player) that will "exchange" the inventory data of paired chests and render their partner entity non-interactable via a "sync_inventory" function.

current base requirements for movement from alpha to beta include:
-working entity prototypes that include appropriate placeholder icons and textures to tell at a glance what their operation is
-working exchange of resources between surface("nauvis") and surface("subsurface_nauvis_1") of type: electric, fluid, inventory, player, and belt
-(?)potential API hook-ins with other surface based mods (such as factorissimo) to be able to teleport the player between these surfaces with a GUI
