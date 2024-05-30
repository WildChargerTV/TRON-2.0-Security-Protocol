# Dev Branch
Welcome to the development branch for Security Protocol. Whether you have chosen to clone or fork this repository, you're probably gonna need a short tour.

Most of the files here are used for my own purposes. Assuming you're here to help with the documentation effort, you'll most likely be looking in the Attributes Folder, under Game.

## Directory

### Backups
This folder generally holds either clean copies or reversions of different things, just in case my tinkering with the game somehow corrupts it.

### Custom
The Custom directory is representative of a "compiled" version of the mod that an end user can install to their machine. This is the folder of content intended to be pushed to the main branch.

### Game
This is a replica of the game's existing directory structure, but only containing files that are affected, either directly or indirectly, by my mod. These are the files that, when the time comes to publish a release version, will be REZ'd and placed in the Custom directory.

### Texture Replacements
This is the simplest folder, just showing texture export/project/replacement files for textures Security Protocol modifies in TRON 2.0. This is unlikely to require your attention.

## General Advice/Notes to Self
For myself. You're welcome to follow it too! But I can't guarantee its usefulness.

### File Overrides
* When inside Custom/SecurityProtocol, all custom files must be REZ'd. No customrez.txt is needed.
* To test file overrides without neeing to REZ anything, create a separate folder structured in the same way the tcdg folder is, then add REZ commands to the command line arguments of both DEdit and the launcher. The game will use this to create a separate override.
    * Worlds should *NEVER* be in this override folder. Keep them in the Game folder so DEdit doesn't freak out.


### Texture-Related Points
* When hue shifting one of the game's blue textures, the average shift value is 140 for red, \[???\] for yellow, 160 for orange. Exact hue shifts do not need to be saved as original copies of textures should always be kept.
* Ensure textures are *NEVER* exported from GIMP with RLE compression. DEdit cannot import these.
* To preserve original textures in the Game folder, textures should be imported to a dedicated IMPORTS folder, and NOT back to their original directory. Ensure the texture properties mimic that of their original before placing it in the designated spot.

### Other
* Make sure Profiles are not carried over between Custom branches to prevent save corruption. (Retail saves can be loaded with or without the Killer App Mod, but this can still destabilize the game).