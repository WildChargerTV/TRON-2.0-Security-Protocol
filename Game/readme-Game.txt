The intent of this folder is to replicate the TRON 2.0 Game folder structure, containing all files modified for, or in the development process of, TRON 2.0: Security Protocol.

Folder descriptions to be added over time.

[ATTRIBUTES]
The Attributes folder consists entirely of .txt files that function very similarly to .ini files, in that the game reads from them when performing a majority of its functions. With a few exceptions, every easily customizable aspect of the game is found here. All .txt files are not protected, so can be opened and modified using any text editor.
Although TRON 2.0: Security Protocol has made adjustments to these files to suit the mod's purposes, a majority of the changes in this folder consist of refreshed documentation, in order to compensate for the lack of official equivalents. If completed, the proposed documentation changes may be proposed for inclusion in the TRON 2.0 Killer App Mod as standard.
Full changelog not yet available.

[CHARS]
The Chars folder contains a majority of the assets used to load characters in the game. At this time, no exceptions have been found to use as examples. The folder holds character FX, Models, Render Styles, Skins, and Sounds.
TRON 2.0: Security Protocol inserts a new character model into its own subfolder, named "ICP_THROW.LTB". This model is explicitly intended for the Main Menu, as a replacement for the Jet model that comes with the Killer App Mod as standard.

[CLIENTFX]
The ClientFX folder contains, to my current understanding, a majority of (if not all) effect sequences used in the game. The most common filetypes in the folder are .FXF and .FCF files, because they are always in pairs - for example, the folder's "WORLDFX.FXF" file has a "WORLDFX.FCF" accompaniment. The .FXF files can be accessed and edited with fxED; however, in order to open one, its corresponding .FCF pair file must be in the same folder directory for the program to read from. It is unknown at this time why this is needed.
Three other file extensions can be found in the folder: .CFV, .KFV, .MFV, and .SFV. The functions of these extensions are not yet known.
TRON 2.0: Security Protocol supplies a modification to the file "MENUFX.FXF" that adjusts the animation in order to show an ICP Regular throwing a disc on the Main Menu instead of Jet.

[INTERFACE]
The Interface folder is one of the most expansive folders, containing various assets, models, textures, sprites, sounds, and fonts that apply to most, if not all, of the game's UX elements. These include menus, the HUD, loading screens, and icons. It's too large to cover in this summary file.
TRON 2.0: Security Protocol supplies texture replacements that modify the color scheme of the interface. It also supplies an unmodified copy of "JET_THROW.SPR", which is a menu sprite that simulates a deresolution when the character on the Main Menu throws their disc. This file is unmodified from the version provided alongside the TRON 2.0 Killer App Mod, and is only provided as an insurance policy in the event the game fails to properly load the version of the file installed alongside the TRON 2.0 Killer App Mod - an occurrence with unknown origins that is confirmed to occur.

[WORLDS]
The Worlds folder is pretty straightforward, in that it contains all of the game's maps. Subfolders split the maps into categories, and within those subfolders, files that contain map data can be found. Compiled worlds use the .DAT file extension. Decompiled worlds that come with the Retail installation use the .TBW (TRON Binary World) file extension. Worlds created in DEdit can be both saved and read in the .LTA, .LTC, and .TBW formats; DEdit will default to using .LTC when saving worlds.
It is unknown at this time whether there is a benefit to saving worlds as .TBW files. At this time, the worlds are the only assets that must be developed within the main Game folder, as there is no tangible benefit to copying all of the game's objects into a unique project file.
When the environments of TRON 2.0: Security Protocol are developed, they will be placed in this folder. For now, the folder contains an assortment of test files, as well as a world from the archived 2020 version of development.