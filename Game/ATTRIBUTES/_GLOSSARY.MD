# Glossary

Not an actual game file. Designed to hold terminology and keep track of important terms. Not even really much of a glossary, it's like a fancy index with no strict ruleset to speak of. If an Object has a definition here, chances are it's treated as a proper noun in other Files.

## Structural Terms
All Attributes Files follow what appears to be the .INI file type format, forced into a plain .TXT file so the game can read it (assumedly due to a limitation in the LithTech engine). The traditional terminology of .INI files states that "key-value pairs" are grouped under sections. This is not the terminology that will be used here, however. Documentation of the Attributes Files will refer to the traditional .INI data structure using the following terms.

### Attributes File Structure
```
[Category]
Setting = Value
```
### Documentation Structure
```
**  ----------[Heading 1]----------
**
**  -----[Heading 2]-----
**
**  ---[Heading 3]---
**
**  ---<Heading 4>---
**  
**  Setting (Data Type)
**      - Definition(s) and additional information
```
### Additional Terms
* An **Attribute** will represent a single defined `Setting = Value` pair, following the namesake of the folder in which it resides.
* A **Sub-Category** will represent a _group_ of Attributes within an existing Category that are similar enough to one another to warrant their own short description. These can also be utilized when it is very obvious that a group of Attributes is acting as the child of another group, e.g. a Category that describes the contents of a tab menu inside a parent Screen.


## Data Types

### Integers
* **Integer**
    * An Integer is a whole number. Ignores the usage of decimals.
    * Example: `FontSize = 27`
* **Boolean Integer**
    * A Boolean Integer is still a whole number; however, Settings using them will only accept 1 or 0, representing True or False respectively.
    * Example: `UseAmmoBar = 0`

### Floats
* **Float**
    * A Float is a number that permits the usage of decimals. The amount of accepted decimal places can vary by Setting.
    * Example: `DelayTime = 0.35`
* **Percentage Float**
    * A Percentage Float is a number with permitted decimals; however, Settings with this Data Type will treat this number as a percentage value. To that extent, it will only be affected by Values between 0 and 1 (inclusive). Values outside of this range are technically accepted (most of the time), but will just have no effect (e.g. 3.75 counts as 1, and -2.3 counts as 0).
    * Example: `DodgeVectorCheckChance = 1.00`
* **Time Float**
    * A Time Float is something I only consider a Data Type by technicality. It's functionally indistinguishable from other Floats; rather, the primary purpose of this Data Type is to allow a time value to be more easily distinguished beyond the Setting name. _Unless otherwise specified_, all Time Floats are measured in seconds, with all decimal values being their respective fractions of a second.
    * Example: `MessageTime = 7.5`

### Booleans
* **Boolean**
    * A Boolean is a true/false Value. For Settings of this Data Type, the Value itself is usually formatted in all caps (`TRUE`/`FALSE`).
    * Example: `CanLipSync = TRUE`

### Strings
Represented by Values surrounded by quotation marks (`""`).
* **String**
    * A String is... text. Restrictions on which alphanumeric symbols may be used for the input Value are heavily context-dependent, but most of the time, basic letters and numbers are fine.
    * Example: `Light0 = "Main0"`
* **Path String**
    * A Path String is text that must explicitly link to a File for the game to reference. The path must use forward slashes, and must always include the file extension at the end. The root directory is _always_ the "Game" folder, and beginning the path with `./` is not allowed.
    * Example: `PowerupIconTexture0	= "Interface\HUD\LC_pickup_Shield.dtx"`

### Groups
Represented by values surrounded by parentheses (`()`).
* **2D Point**
    * A 2D Point is an absolutely-positioned point, where the output display is treated as the two-dimensional plane. Values for this Data Type must assume that the display resolution is 640x480, regardless of the output resolution or aspect ratio. The game will then scale that Value up as needed. 
    * This Group is made up of two Integer Values. 
        * The first Value represents the position on the X (horizontal) axis. A value of `0` is considered to be the left edge of the display area. Negative Values push the element to the left, and positive Values push the element to the right.
        * The second Value represents the position on the Y (vertical) axis. A value of `0` is considered to be the top edge of the display area. Negative Values push the element upward, and positive Values push the element downward.
    * Note that this does not dictate the origin reference point for the element being positioned. Most of the time, it considers the origin point to be the upper-left corner of the element, but this is not a universal rule. Pay attention to the origin position of an element in its definition.
    * Example: `TitlePos = (70, 50)`
* **Rectangle**
    * A Rectangle is like two mirrored 2D Points mashed together, effectively setting a boundary box for an element to utilize in all four potential directions. Just as with regular 2D Points, all Values must assume a 640x480 display resolution, and the game will scale it up as needed.
    * This Group is made up of four Integer Values.
        * The first and third Values represent the boundary on the X (horizontal) axis. A value of `0` is considered to be the left and right edges of the display area respectively. For the first Value, negative inputs push the bounding box left, and positive ones push it right. Inversely, for the third Value, negative inputs push the bounding box right, and positive ones push it left.
        * The second and fourth Values represent the boundary on the Y (vertical) axis. A value of `0` is considered to be the top and bottom edges of the display area respectively. For the second Value, negative inputs push the bounding box up, and positive ones push it down. Inversely, for the fourth Value, negative inputs push the bounding box down, and positive ones push it up.
    * Example: `OptimizerHitRect = (288, 208, 352, 272)`
* **Dimension**
    * A Dimension is a Group of two Integers that manually set an element's width and height respectively. This Data Type does not consider the element's position on the display; however, its Values assume that the display resolution is 640x480, and can scale itself up as needed for higher resolutions.
    * This Group is made up of two Integer Values, both measured in pixels.
        * The first Value represents the element's horizontal width.
        * The second Value represents the elements vertical height.
    * Example: `BarSize = (312, 25)`


### Arrays
Represented by values surrounded by square brackets (`[]`).
* **Array**
    * An Array is a set of Values which, although usually of the same Data Type, do not have to be. Arrays are highly context-dependent, so make sure to pay attention to each of its definitions to understand their utilization.
    * Unlike Groups, Arrays are not necessarily restricted by how many Values are inside of it, either; however, it is _not at all recommended_ to change the amount of Values in an Array unless the context permits doing so.
    * Example: `AttackChaseTimeRandom = [-0.250000, 0.250000]`

### Vectors
Represented by values surrounded by angle brackets (`<>`).
* **Vector**
    * A Vector is a set of three Float Values that determines the color of applicable elements. A Vector will always utilize the RGB scale, with each of the three Floats corresponding to the color's Red, Blue, and Green Values, in that order.
    * Example: `CompletedCircuitColor = <251.0, 193.0, 193.0>`
* **3D Point**
    * A 3D Point is an absolutely-positioned point on a three-dimensional plane. The X and Y axes correspond to the output display, and the Z axis roughly translates to how far forward or backward the display is relative to the element.
    * This Vector is made up of three Float Values, although it is recommended to treat them as if they are Integers instead (which can be done by simply ending all of the Values in "`.0`").
        * The first Value represents the position on the X (horizontal) axis. A value of `0.0` is considered to be the left edge of the display area. Negative Values push the element to the left, and positive Values push the element to the right.
        * The second Value represents the position on the Y (vertical) axis. A value of `0.0` is considered to be the top edge of the display area. Negative Values push the element upward, and positive Values push the element downward.
        * The third Value represents the position on the Z (optical) axis. A value of `0.0` is considered to be "level" with the display area. Negative Values push the element "forward" (in which the element would be seen moving further away), and positive Values push the element "backward" (in which the element is doing the same thing in the other direction; however, this will not be seen, because the camera is fixed in one direction).
    * Example: `Pos = <100.0, -100.0, -100.0>` (as seen in the "Screen Lights Layout" section of the "Layout" Attributes File)

## Important Differentiations

### **Position vs. Offset**
A lot of Settings in the "Layout" Attributes File go by the names "Position" (or "Pos") and "Offset". Although both terms refer to where an element appears on your screen, there's a distinct difference to be noted. 
* _Positions_ are absolute points (set using a 2D Point or 3D Point Data Type) on a display. Most of the time, their only constraint is the bounding box according to the current resolution (and that's not always true either!). What's important is that Positions (by way of using the aforementioned Data Types) are able to scale up and adapt to higher resolutions, based on where they would be positioned on a 640x480 display.
* _Offsets_, on the other hand, are much more context-dependent. When an element determines its position based on an Offset, it usually takes into account the elements around it, or the elements of which it is a child, meaning they are less likely to just use the edge of the display as a reference point. Furthermore, because they use Integers as Values, each Offset Attribute can only cover one axis at a time; as a result, a fair amount of these Attributes come in pairs, in order to cover both horizontal and vertical Offsets. And to top it all off, they cannot scale to higher resolutions, where Positions can.

### **Screen vs. Menu vs. Window**
It's not known if the differentiation between these three terms is unique to the LithTech engine. However, it's important to understand that these terms are non-interchangable.
* A _Screen_ is considered to be a fullscreen menu. It seems to be a shorthand for the term "Menu Screen" based on Monolith's original documentation, but that can't be said for sure.
* A _Menu_ is, unfortunately, not yet clearly defined. The only Menu in TRON 2.0 is the Pause Menu, so without any second example to compare it to, it's impossible to create any kind of pattern recognition to infer what the game considers a Menu to be. For now, just know any references to a Menu (with a capital M) should _only_ be referring to the Pause Menu.
* A _Window_ is the term used to cover most pop-ups. The most prominent example would be the "Decision Window Layout" section of the "Layout" Attributes File, which is the little options box that can appear when opening a Core Dump or an Archive Bin. Some pop-up elements do not fall under this terminology, and can instead be referred to by other names, such as "tooltips".

### **NPC vs. AI**
This might be one of the more egregious differentiations, but nonetheless still necessary in order to keep everyone on the same page. It's impossible to enforce these terms with 100% accuracy, as this is very much a gray area in terms of language.
* An _NPC_, or Non-Player Character, refers to the actual entity in place on the map itself. The body that performs the actions that the AI sets up.
* An _AI_, or Artificial Intelligence, refers to the brain of an NPC (not to be confused with the Brain object created in the "AIButes" Attribute File). Putting aside the fact that AI in TRON 2.0 is more artificial than it is intelligent, it's the code framework that determines what an NPC will want to do, as well as what it takes into consideration when choosing any actions.

## Object Terms

* **Activate Type**
    * An Activate Type is a property in DEdit that directly corresponds to either a linear or a binary action in TRON 2.0. These are usually reserved for things like opening/closing doors, activating energy bridges, etc.
    * See the "ActivateTypes" Attribute File for more details.
* **Damage Type**
    * A Damage Type refers to the type of damage dealt by a weapon. This does not concern how much damage the type itself deals; rather, this concerns potential extra side effects and drawbacks that are inflicted on an entity that gets hit by the Damage Type.
    * See the "DamageTypes" Attributes File for more details.
* **Scale**
    * A Scale is an FX object that is referenced in the "FX" Attributes File, as opposed to one pulled directly from FXEd.
* **TriggerType**
    * A Trigger Type is a property in DEdit that associates a Trigger Class to an icon that gets displayed on the player's HUD, informing them the trigger is active and nearby.
    * See the "TriggerTypes" Attributes File for more details.