# UO Sagas Lua API Documentation

## Gumps

## Overview
```lua
Gumps.GetByText(text)
Gumps.WaitForGump(gumpSerial, milliseconds)
Gumps.IsActive(gumpSerial)
Gumps.PressButton(gumpSerial, buttonId)
```

![image](https://github.com/uosagas/assistant/assets/4610892/9940074e-5fae-4565-bf7e-fc20bcec881e)


## GetByText
```lua
Gumps.GetByText(text)
```
**Parameters**<br/>
`text: String value of the text to search for in gumps`

**Returns**<br/>
`Numeric: the serial of the gump containing the text, or 0 if not found`

**Example**
```lua
-- Get the serial of the gump containing the text 'Welcome'
gumpSerial = Gumps.GetByText('Welcome')
if gumpSerial ~= 0 then
    Messages.Print('Gump found with serial: ' .. gumpSerial)
else
    Messages.Print('Gump not found')
end
```

## WaitForGump
```lua
Gumps.WaitForGump(gumpSerial, milliseconds)
```
**Parameters**<br/>
`gumpSerial: Numeric value of the gump serial to wait for`<br/>
`milliseconds: Numeric value in milliseconds to wait`

**Returns**<br/>
`Boolean: true if the gump is found within the time limit, false otherwise`

**Example**
```lua
-- Find an item to use
hammer = Items.FindBySerial(1076881147)
-- If item is found use it
if hammer ~= nil then
	Messages.Print('found')
	Player.UseObject(hammer.Serial)
end
-- Wait maximum 2 seconds for the gump to open
if Gumps.WaitForGump(2653346093, 2000) then
	Messages.Print('Gump opened!')
	Pause(1000)
        -- Sends a button click to the gump
	Gumps.PressButton(2653346093, 21)
end
```

## IsActive
```lua
Gumps.IsActive(gumpSerial)
```
**Parameters**<br/>
`gumpSerial: Numeric value of the gump serial to check`

**Returns**<br/>
`Boolean: true if the gump is active, false if not`

**Example**
```lua
-- Check if a gump with a specific serial is active
gumpSerial = 123456
if Gumps.IsActive(gumpSerial) then
    Messages.Print('Gump is active')
else
    Messages.Print('Gump is not active')
end
```

## PressButton
```lua
Gumps.PressButton(gumpSerial, buttonId)
```
**Parameters**<br/>
`gumpSerial: Numeric value of the gump serial containing the button`<br/>
`buttonId: Numeric value of the button to press`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Find an item to use
hammer = Items.FindBySerial(1076881147)
-- If item is found use it
if hammer ~= nil then
	Messages.Print('found')
	Player.UseObject(hammer.Serial)
end
-- Wait maximum 2 seconds for the gump to open
if Gumps.WaitForGump(2653346093, 2000) then
	Messages.Print('Gump opened!')
	Pause(1000)
        -- Sends a button click to the gump
	Gumps.PressButton(2653346093, 21)
end
```

## Targeting

## Overview
```lua
Targeting.Target(Serial)
Targeting.TargetSelf()
Targeting.TargetLast()
Targeting.WaitForTarget(Timeout in Milliseconds)
```

## Target
```lua
Targeting.Target(Serial)
```
**Parameters**<br/>
`Serial: Numeric value of the serial of an entity`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Find the mobile
friendplayer = Mobiles.FindByName('Herald')
-- If mobile is not found stop the script
if friendplayer == nil then
   return
end
-- Cast a spell 
Spells.Cast('Heal')
-- Wait for target by timeout of 2 seconds and on fail stop the script
if not Targeting.WaitForTarget(2000) then
   return
end
-- Target friend player
Targeting.Target(friendplayer.Serial)
```

## TargetSelf
```lua
Targeting.TargetSelf()
```
**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Cast a spell 
Spells.Cast('Heal')
-- Wait for target by timeout of 2 seconds
if Targeting.WaitForTarget(2000) then
   Targeting.TargetSelf()
end
```

## TargetLast
```lua
Targeting.TargetLast()
```
**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Cast a spell 
Spells.Cast('Heal')
-- Wait for target by timeout of 2 seconds
if Targeting.WaitForTarget(2000) then
   Targeting.TargetLast()
end
```

## WaitForTarget
```lua
Targeting.WaitForTarget(Milliseconds)
```
**Parameters**<br/>
`Numeric: Timeout as numeric value in milliseconds`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Find the mobile
friendplayer = Mobiles.FindByName('Herald')
-- If mobile is not found stop the script
if friendplayer == nil then
   return
end
-- Cast a spell 
Spells.Cast('Heal')
-- Wait for target by timeout of 2 seconds and on fail stop the script
if not Targeting.WaitForTarget(2000) then
   return
end
-- Target friend player
Targeting.Target(friendplayer.Serial)
```

## Spells

## Overview
```lua
Spells.Cast(spellName)
```

## Cast
```lua
Spells.Cast(spellName)
```
**Parameters**<br/>
`spellName: String value of the spell name to cast`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Find the mobile
friendplayer = Mobiles.FindByName('Herald')
-- If mobile is not found stop the script
if friendplayer == nil then
   return
end
-- Cast a spell 
Spells.Cast('Heal')
-- Wait for target by timeout of 2 seconds and on fail stop the script
if not Targeting.WaitForTarget(2000) then
   return
end
-- Target friend player
Targeting.Target(friendplayer.Serial)
```

### List of Spells
- Clumsy
- CreateFood
- Feeblemind
- Heal
- MagicArrow
- NightSight
- ReactiveArmor
- Weaken
- Agility
- Cunning
- Cure
- Harm
- MagicTrap
- MagicUntrap
- Protection
- Strength
- Bless
- Fireball
- MagicLock
- Poison
- Telekinesis
- Teleport
- Unlock
- WallOfStone
- ArchCure
- ArchProtection
- Curse
- FireField
- GreaterHeal
- Lightning
- ManaDrain
- Recall
- BladeSpirits
- DispellField
- Incognito
- MagicReflection
- MindBlast
- Paralyze
- PoisonField
- SummonCreature
- Dispel
- EnergyBolt
- Explosion
- Invisibility
- Mark
- MassCurse
- ParalyzeField
- Reveal
- ChainLightning
- EnergyField
- FlameStrike
- GateTravel
- ManaVampire
- MassDispel
- MeteorSwarm
- Polymorph
- Earthquake
- EnergyVortex
- Resurrection
- AirElemental
- SummonDaemon
- EarthElemental
- FireElemental
- WaterElemental
- SongOfProvocation
- SongOfPeacemaking
- SongOfDiscordance
- SongOfHealing

## Skills

## Overview
```lua
Skills.Use(SkillName)
Skills.GetValue(SkillName)
```

## Use
```lua
Skills.Use(SkillName)
```
**Parameters**<br/>
`String: Name of the skill`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
Skills.Use('Hiding')
```

## GetValue
```lua
Skills.GetValue(SkillName)
```
**Returns**<br/>
`Numeric: Value of the skill`

**Example**
```lua
skillvalue = Skills.GetValue('Magery') 
Messages.Print('The current value is: '..skillvalue)
```

## Player

Here is the documentation for the `Player` class, adapted to Lua, similar to the format you provided for the `Mobiles` class:

## Overview
```lua
Player.Say(message[, hue[, type[, font]]])
Player.SayParty(message)
Player.SayGuild(message)
Player.SayAlliance(message)
Player.SayWhisper(message)
Player.SayYell(message)
Player.SayChat(message)
Player.SayEmote(message)
Player.UseObject(serial)
Player.UseObjectByType(type)
Player.ClickObject(serial)
Player.Attack(serial)
Player.ToggleFly()
Player.ClearHands(command)
Player.Turn(direction)
Player.Equip(serial)
Player.PickUp(serial)
Player.DropInBackpack()
Player.DropInContainer(serial)
Player.ToggleWarMode()
Player.PopPouch()
```
### Attributes

| **Attribute** | **Type**  | **Description**                                                                 |
|---------------|-----------|---------------------------------------------------------------------------------|
| `X`           | `Integer` | The x-coordinate of the game object's position.                                 |
| `Y`           | `Integer` | The y-coordinate of the game object's position.                                 |
| `Z`           | `Integer` | The z-coordinate of the game object's position.                                 |
| `Hue`         | `Integer` | The hue or color of the game object.                                            |
| `Graphic`     | `Integer` | The graphic ID representing the game object.                                    |
| `Name`            | `String`   | The name of the entity.                                                        |
| `Serial`          | `Integer`  | The unique serial number of the entity.                                        |
| `Distance`        | `Integer`  | The distance of the entity from the player.                                    |
| `Direction`       | `String`   | The direction the entity is facing (e.g., North, South).                       |
| `IsDestroyed`     | `Boolean`  | Indicates whether the entity is destroyed. |
| `Hits`                     | `Integer`   | The current health of the mobile.                              |
| `HitsMax`                  | `Integer`   | The maximum health of the mobile.                              |
| `DiffHits`                 | `Integer`   | The difference between the mobile's maximum and current health.|
| `Stamina (Stam)`           | `Integer`   | The current stamina of the mobile.                             |
| `MaxStam`                  | `Integer`   | The maximum stamina of the mobile.                             |
| `Mana`                     | `Integer`   | The current mana of the mobile.                                |
| `MaxMana`                  | `Integer`   | The maximum mana of the mobile.                                |
| `IsRunning`                | `Boolean`   | Indicates whether the mobile is running.                       |
| `IsParalyzed`              | `Boolean`   | Indicates whether the mobile is paralyzed.                     |
| `IsDead`                   | `Boolean`   | Indicates whether the mobile is dead.                          |
| `IsHidden`                 | `Boolean`   | Indicates whether the mobile is hidden.                        |
| `IsPoisoned`               | `Boolean`   | Indicates whether the mobile is poisoned.                      |
| `IsMounted`                | `Boolean`   | Indicates whether the mobile is mounted.                       |
| `IsFlying`                 | `Boolean`   | Indicates whether the mobile is flying.                        |
| `IsHuman`                  | `Boolean`   | Indicates whether the mobile is human.                         |
| `IsGargoyle`               | `Boolean`   | Indicates whether the mobile is a gargoyle.                    |
| `IsYellowHits`             | `Boolean`   | Indicates whether the mobile's health bar is yellow.           |
| `IsRenamable`              | `Boolean`   | Indicates whether the mobile can be renamed.                   |
| `IsFemale`                 | `Boolean`   | Indicates whether the mobile is female.                        |
| `IgnoreCharacters`         | `Boolean`   | Indicates whether the mobile ignores other characters.         |
| `NotorietyFlag`            | `String`    | The notoriety flag of the mobile (e.g., criminal).             |
| `Race`                     | `String`    | The race of the mobile (e.g., human, elf).                     |
| `Title`                    | `String`    | The title or profession of the mobile.                         |
| `SpeedMode`                | `String`    | The speed mode of the mobile.                                  |
| `PhysicalResistance`       | `Integer`   | The player's physical resistance.                              |
| `FireResistance`           | `Integer`   | The player's fire resistance.                                  |
| `ColdResistance`           | `Integer`   | The player's cold resistance.                                  |
| `PoisonResistance`         | `Integer`   | The player's poison resistance.                                |
| `EnergyResistance`         | `Integer`   | The player's energy resistance.                                |
| `Str`                      | `Integer`   | The player's strength.                                         |
| `Dex`                      | `Integer`   | The player's dexterity.                                        |
| `Int`                      | `Integer`   | The player's intelligence.                                     |
| `DamageMin`                | `Integer`   | The player's minimum combat damage.                           |
| `DamageMax`                | `Integer`   | The player's maximum combat damage.                           |
| `Followers`                | `Integer`   | The number of creatures currently following the player.        |
| `MaxFollowers`             | `Integer`   | The maximum number of creatures that can follow the player.    |
| `Gold`                     | `Integer`   | The amount of gold the player has.                            |
| `Luck`                     | `Integer`   | The player's luck.                                             |
| `TithingPoints`            | `Integer`   | The player's tithing points.                                  |
| `Weight`                   | `Integer`   | The player's current weight.                                  |
| `MaxWeight`                | `Integer`   | The player's maximum weight.                                  |
| `DiffWeight`               | `Integer`   | The difference between the player's maximum and current weight.|
| `StatsCap`                 | `Integer`   | The total cap for the player's stats.                         |
| `SwingSpeedIncrease`       | `Integer`   | Bonus to the player's weapon swing speed.                     |
| `HitPointsRegeneration`    | `Integer`   | The rate of the player's health regeneration.                 |
| `ManaRegeneration`         | `Integer`   | The rate of the player's mana regeneration.                   |
| `StaminaRegeneration`      | `Integer`   | The rate of the player's stamina regeneration.                |
| `LowerManaCost`            | `Integer`   | Reduction in mana cost for the player.                        |
| `LowerReagentCost`         | `Integer`   | Reduction in reagent cost for the player.                     |
| `HitChanceIncrease`        | `Integer`   | Bonus to the player's hit chance.                             |
| `DefenseChanceIncrease`    | `Integer`   | Bonus to the player's defense chance.                         |
| `SpellDamageIncrease`      | `Integer`   | Bonus to the player's spell damage.                           |
| `ReflectPhysicalDamage`    | `Integer`   | The percentage of physical damage reflected by the player.    |
| `Backpack`    | `Item`   | Item representation of the player's backpack.    |



**Example**
```lua
Messages.Print('Location of myself is x:'..Player.X..' y:'..Player.Y)
```

## Say
```lua
Player.Say(message[, hue[, type[, font]]])
```
**Parameters**<br/>
`message: String value representing the message to say`<br/>
`hue: Optional numeric value representing the hue (default: regular hue)`<br/>
`type: Optional numeric value representing the message type (default: regular message type)`<br/>
`font: Optional numeric value representing the font (default: regular font)`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Say a message with default settings
Player.Say("Hello, world!")

-- Say a message with custom hue, type, and font
Player.Say("Hello, world!", 33, 1, 3)
```

## SayParty
```lua
Player.SayParty(message)
```
**Parameters**<br/>
`message: String value representing the party message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Say a party message
Player.SayParty("Let's regroup at the entrance!")
```

## SayGuild
```lua
Player.SayGuild(message)
```
**Parameters**<br/>
`message: String value representing the guild message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Say a guild message
Player.SayGuild("Guild meeting at 8 PM.")
```

## SayAlliance
```lua
Player.SayAlliance(message)
```
**Parameters**<br/>
`message: String value representing the alliance message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Say an alliance message
Player.SayAlliance("Prepare for the upcoming battle!")
```

## SayWhisper
```lua
Player.SayWhisper(message)
```
**Parameters**<br/>
`message: String value representing the whisper message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Whisper a message
Player.SayWhisper("Keep it secret, keep it safe.")
```

## SayYell
```lua
Player.SayYell(message)
```
**Parameters**<br/>
`message: String value representing the yell message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Yell a message
Player.SayYell("Charge!")
```

## SayChat
```lua
Player.SayChat(message)
```
**Parameters**<br/>
`message: String value representing the chat message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Chat a message
Player.SayChat("Hello everyone.")
```

## SayEmote
```lua
Player.SayEmote(message)
```
**Parameters**<br/>
`message: String value representing the emote message to say`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Emote a message
Player.SayEmote("*waves hello*")
```

## UseObject
```lua
Player.UseObject(serial)
```
**Parameters**<br/>
`serial: Numeric value representing the serial of the object to use`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Use an object by serial
Player.UseObject(123456)
```

## UseObjectByType
```lua
Player.UseObjectByType(type)
```
**Parameters**<br/>
`type: Numeric value representing the type/graphic of the object to use`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Use an object by type
Player.UseObjectByType(3178)
```

## ClickObject
```lua
Player.ClickObject(serial)
```
**Parameters**<br/>
`serial: Numeric value representing the serial of the object to click`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Click an object by serial
Player.ClickObject(123456)
```

## Attack
```lua
Player.Attack(serial)
```
**Parameters**<br/>
`serial: Numeric value representing the serial of the mobile to attack`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Attack a mobile by serial
Player.Attack(123456)
```

## ToggleFly
```lua
Player.ToggleFly()
```
**Parameters**<br/>
`None`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Toggle fly mode for gargoyles
Player.ToggleFly()
```

## ClearHands
```lua
Player.ClearHands(command)
```
**Parameters**<br/>
`command: String value representing the hand(s) to clear ("left", "right", or "both")`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Clear items from both hands
Player.ClearHands("both")
```

## Turn
```lua
Player.Turn(direction)
```
**Parameters**<br/>
`direction: String value representing the direction to turn ("North", "South", "East", "West", "Up", "Down", "Left", "Right")`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- Turn the player to the north
Player.Turn("North")
```


## Equip
```lua
Player.Equip(serial)
```
**Parameters**<br/>
`Serial: Numeric value representing the entity serial`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
item = Items.FindByType(5486)
Player.Equip(item.Serial)
```

## PickUp
```lua
Player.PickUp(serial)
```
**Parameters**<br/>
`Serial: Numeric value representing the entity serial`
`Amount: Numeric value representing the amount you want to pickup`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
item = Items.FindByType(5486)
Player.PickUp(item.Serial)
```
or
```lua
item = Items.FindByType(5486)
Player.PickUp(item.Serial, 1000)
```

## DropInBackpack
```lua
Player.DropInBackpack()
```
**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- drops an item in the backpack if holding
Player.DropInBackpack()
```

## DropInContainer
```lua
Player.DropInContainer(serial)
```
**Parameters**<br/>
`Serial: Numeric value representing the entity serial`

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- drops an item in the container by serial if holding
Player.DropInContainer(1234567)
```

## ToggleWarMode
```lua
Player.ToggleWarMode()
```

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- toggles the war mode of a player
Player.ToggleWarMode()
```

## PopPouch
```lua
Player.PopPouch()
```

**Returns**<br/>
`Boolean: True if the action is successful, false otherwise`

**Example**
```lua
-- pops a trapped pouch inside your backpack
Player.PopPouch()
```

## Mobiles

## Overview
```lua
Mobiles.FindBySerial(serial)
Mobiles.FindByType(type)
Mobiles.FindByName(name)
Mobiles.FindByFilter(filter)
Mobiles.Rename(serial, name)
```

## Attributes
| **Attribute** | **Type**  | **Description**                                                                 |
|---------------|-----------|---------------------------------------------------------------------------------|
| `X`           | `Integer` | The x-coordinate of the game object's position.                                 |
| `Y`           | `Integer` | The y-coordinate of the game object's position.                                 |
| `Z`           | `Integer` | The z-coordinate of the game object's position.                                 |
| `Hue`         | `Integer` | The hue or color of the game object.                                            |
| `Graphic`     | `Integer` | The graphic ID representing the game object. |
| `Name`            | `String`   | The name of the entity.                                                        |
| `Serial`          | `Integer`  | The unique serial number of the entity.                                        |
| `Distance`        | `Integer`  | The distance of the entity from the player.                                    |
| `Direction`       | `String`   | The direction the entity is facing (e.g., North, South).                       |
| `IsDestroyed`     | `Boolean`  | Indicates whether the entity is destroyed.                                     |
| `Hits`                     | `Integer`   | The current health of the mobile.                              |
| `HitsMax`                  | `Integer`   | The maximum health of the mobile.                              |
| `DiffHits`                 | `Integer`   | The difference between the mobile's maximum and current health.|
| `Stamina (Stam)`           | `Integer`   | The current stamina of the mobile.                             |
| `MaxStam`                  | `Integer`   | The maximum stamina of the mobile.                             |
| `Mana`                     | `Integer`   | The current mana of the mobile.                                |
| `MaxMana`                  | `Integer`   | The maximum mana of the mobile.                                |
| `IsRunning`                | `Boolean`   | Indicates whether the mobile is running.                       |
| `IsParalyzed`              | `Boolean`   | Indicates whether the mobile is paralyzed.                     |
| `IsDead`                   | `Boolean`   | Indicates whether the mobile is dead.                          |
| `IsHidden`                 | `Boolean`   | Indicates whether the mobile is hidden.                        |
| `IsPoisoned`               | `Boolean`   | Indicates whether the mobile is poisoned.                      |
| `IsMounted`                | `Boolean`   | Indicates whether the mobile is mounted.                       |
| `IsFlying`                 | `Boolean`   | Indicates whether the mobile is flying.                        |
| `IsHuman`                  | `Boolean`   | Indicates whether the mobile is human.                         |
| `IsGargoyle`               | `Boolean`   | Indicates whether the mobile is a gargoyle.                    |
| `IsYellowHits`             | `Boolean`   | Indicates whether the mobile's health bar is yellow.           |
| `IsRenamable`              | `Boolean`   | Indicates whether the mobile can be renamed.                   |
| `IsFemale`                 | `Boolean`   | Indicates whether the mobile is female.                        |
| `IgnoreCharacters`         | `Boolean`   | Indicates whether the mobile ignores other characters.         |
| `NotorietyFlag`            | `String`    | The notoriety flag of the mobile (e.g., criminal).             |
| `Race`                     | `String`    | The race of the mobile (e.g., human, elf).                     |
| `Title`                    | `String`    | The title or profession of the mobile.                         |
| `SpeedMode`                | `String`    | The speed mode of the mobile.                                  |

## FindBySerial
```lua
Mobiles.FindBySerial(serial)
```
**Parameters**<br/>
`serial: Numeric value representing the serial number of the mobile to search`

**Returns**<br/>
`Table: Mobile table if the mobile is found, or nil if not found`

**Example**
```lua
-- Find the mobile by its serial number
mobile = Mobiles.FindBySerial(123456)
if mobile ~= nil then
    Messages.Print('Mobile found at location x:'.. mobile.X..' y: '..mobile.Y)
else
    Messages.Print('Mobile not found')
end
```

## FindByType
```lua
Mobiles.FindByType(type)
```
**Parameters**<br/>
`type: Numeric value representing the graphic type of the mobile to search`

**Returns**<br/>
`Table: Mobile table if the mobile is found, or nil if not found`

**Example**
```lua
-- Find the mobile by its type
mobile = Mobiles.FindByType(3854)
if mobile ~= nil then
    Messages.Print('Mobile found with serial: ' .. mobile.Serial)
else
    Messages.Print('Mobile not found')
end
```

## FindByName
```lua
Mobiles.FindByName(name)
```
**Parameters**<br/>
`name: String value representing the name of the mobile to search`

**Returns**<br/>
`Table: Mobile table if the mobile is found, or nil if not found`

**Example**
```lua
-- Find the mobile by its name
mobile = Mobiles.FindByName('John')
if mobile ~= nil then
    Messages.Print('Mobile found with serial: ' .. mobile.Serial)
else
    Messages.Print('Mobile not found')
end
```

## FindByFilter
```lua
Mobiles.FindByFilter(filter)
```
**Parameters**<br/>
`filter: Table containing filter criteria`

**Returns**<br/>
`Table: A table of Mobile tables that match the filter criteria`

**Notoriety Flags**
- Unknown = `0`,
- Innocent = `1`,
- Ally = `2`,
- Gray = `3`,
- Criminal = `4`,
- Enemy = `5`,
- Murderer = `6`,
- Invulnerable = `7`

**Filter Options**
- `dead: Boolean (optional)`: Whether the mobile is dead
- `female: Boolean (optional)`: Whether the mobile is female
- `human: Boolean (optional)`: Whether the mobile is human
- `poisoned: Boolean (optional)`: Whether the mobile is poisoned
- `paralyzed: Boolean (optional)`: Whether the mobile is paralyzed
- `rangemin: Integer (optional)`: The minimum range to search
- `rangemax: Integer (optional)`: The maximum range to search
- `names: Table of string (optional)`: A list of names
- `hues: Table of ushort (optional)`: A list of hues
- `bodies: Table of ushort (optional)`: A list of body types
- `notorieties: Table of Notoriety (optional)`: A list of notoriety statuses
- `serials: Table of ushort (optional)`: A list of serial numbers

**Example**
```lua
-- Find mobiles by filter criteria
filter = {female=true, rangemax=5, notorieties={0,1,2,3}}

list = Mobiles.FindByFilter(filter)
for index, mobile in ipairs(list) do
    Messages.Print('Found mobile at location x:'..mobile.X..' y:'..mobile.Y)
end
```
Alternatively, the filter can be directly passed as a parameter instead of defining a variable beforehand:
```lua
list = Mobiles.FindByFilter({female=true, rangemax=5})
```

## Rename
```lua
Mobiles.Rename(serial, name)
```
**Parameters**<br/>
`serial: Numeric value representing the serial number of the mobile`
`name: String value representing the new name of the mobile`

**Example**
```lua
-- Find the mobile by its name
mobile = Mobiles.FindByName('a horse')
if mobile ~= nil then
    Mobiles.Rename(mobile.Serial, 'tamed')
else
    Messages.Print('Mobile not found')
end
```

## Messages

## Overview
```lua
Messages.Print(message)
Messages.Print(message, hue)
Messages.Print(message, hue, type)
Messages.Print(message, hue, type, font)
Messages.Print(message, hue, type, font, unicode)
Messages.Overhead(message, serial)
Messages.Overhead(message, hue, serial)
```

## Print
```lua
Messages.Print(message)
Messages.Print(message, hue)
Messages.Print(message, hue, type)
Messages.Print(message, hue, type, font)
Messages.Print(message, hue, type, font, unicode)
```
**Parameters**<br/>
`message: String value of the message to print`<br/>
`hue: Optional numeric value for the hue of the message (default is 0)`<br/>
`type: Optional numeric value representing the message type (default is 0)`<br/>
`font: Optional numeric value representing the font of the message (default is 0)`<br/>
`unicode: Optional boolean value indicating if the message is in unicode (default is false)`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Print a simple message
Messages.Print("Hello, world!")

-- Print a message with a specific hue
Messages.Print("Hello, world!", 34)

-- Print a message with a specific hue and type
Messages.Print("Hello, world!", 34, 1)

-- Print a message with a specific hue, type, and font
Messages.Print("Hello, world!", 34, 1, 3)

-- Print a message with a specific hue, type, font, and unicode
Messages.Print("Hello, world!", 34, 1, 3, true)
```

## Overhead
```lua
Messages.Overhead(message, serial)
Messages.Overhead(message, hue, serial)
```
**Parameters**<br/>
`message: String value of the message to display overhead`<br/>
`serial: Numeric value of the serial of an entity`<br/>
`hue: Optional numeric value for the hue of the message (default is 0)`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
-- Find the mobile
friendplayer = Mobiles.FindByName('Herald')
-- If mobile is not found stop the script
if friendplayer == nil then
   return
end

-- Display a message overhead the friend player
Messages.Overhead("Hello, Herald!", friendplayer.Serial)

-- Display a message with a specific hue overhead the friend player
Messages.Overhead("Hello, Herald!", 34, friendplayer.Serial)
```

## Journal

## Overview
```lua
Journal.Contains('your string to search')
Journal.Clear()
```

## Contains
```lua
Journal.Contains('your string to search')
```
**Parameters**<br/>
`String: The string you search for in journal`

**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
if Journal.Contains('Maj the weaponsmith') then
   Messages.Print('found')
end
```

## Clear
```lua
Journal.Clear()
```
**Returns**<br/>
`Boolean: true on success, false on failure`

**Example**
```lua
if Journal.Contains('Maj the weaponsmith') then
   Messages.Print('found')
end
Journal.Clear()
```

## Items

## Overview
```lua
Items.FindByLayer(layer)
Items.FindBySerial(serial)
Items.FindByType(type)
Items.FindByName(name)
Items.FindByFilter(filter)
```

## Attributes
| **Attribute** | **Type**  | **Description**                                                                 |
|---------------|-----------|---------------------------------------------------------------------------------|
| `X`           | `Integer` | The x-coordinate of the game object's position.                                 |
| `Y`           | `Integer` | The y-coordinate of the game object's position.                                 |
| `Z`           | `Integer` | The z-coordinate of the game object's position.                                 |
| `Hue`         | `Integer` | The hue or color of the game object.                                            |
| `Graphic`     | `Integer` | The graphic ID representing the game object.                                    |
| `Name`            | `String`   | The name of the entity.                                                        |
| `Serial`          | `Integer`  | The unique serial number of the entity.                                        |
| `Distance`        | `Integer`  | The distance of the entity from the player.                                    |
| `Direction`       | `String`   | The direction the entity is facing (e.g., North, South).                       |
| `IsDestroyed`     | `Boolean`  | Indicates whether the entity is destroyed.                                     |
| `Amount`                   | `Integer`   | The number of items in the stack.                              |
| `IsDamageable`             | `Boolean`   | Indicates whether the item can take damage.                    |
| `IsCoin`                   | `Boolean`   | Indicates whether the item is a stack of coins.                |
| `IsCorpse`                 | `Boolean`   | Indicates whether the item is a corpse.                        |
| `IsEmpty`                  | `Boolean`   | Indicates whether the item has no contents.                    |
| `IsLocked`                 | `Boolean`   | Indicates whether the item is locked.                          |
| `IsHidden`                 | `Boolean`   | Indicates whether the item is hidden.                          |
| `IsMulti`                  | `Boolean`   | Indicates whether the item is part of a multi-object (e.g., house, boat). |
| `IsLootable`               | `Boolean`   | Indicates whether the item can be looted.                      |
| `OnGround`                 | `Boolean`   | Indicates whether the item is on the ground.                   |
| `DisplayedGraphic`         | `Integer`   | The displayed graphic ID of the item.                          |
| `MultiGraphic`             | `Integer`   | The graphic ID for multi-objects the item represents.          |
| `Layer`                    | `String`    | The layer the item is in (e.g., equipped layer).               |
| `LightID`                  | `Integer`   | The light effect ID of the item.                               |
| `Price`                    | `Integer`   | The price of the item.                                         |
| `RootContainer`            | `Integer`   | The root container of the item.                                |

## FindByLayer
```lua
Items.FindByLayer(layer)
```
**Parameters**<br/>
`layer: Numeric value representing the layer to search for the item`<br/>
where layer is:<br/>
`Invalid` : 0
`OneHanded` : 1
`TwoHanded` : 2
`Shoes` : 3
`Pants` : 4
`Shirt` : 5
`Helmet` : 6
`Gloves` : 7
`Ring` : 8
`Talisman` : 9
`Necklace` : 10
`Hair` : 11
`Waist` : 12
`Torso` : 13
`Bracelet` : 14
`Face` : 15
`Beard` : 16
`Tunic` : 17
`Earrings` : 18
`Arms` : 19
`Cloak` : 20
`Backpack` : 21
`Robe` : 22
`Skirt` : 23
`Legs` : 24
`Mount` : 25
`ShopBuyRestock` : 26
`ShopBuy` : 27
`ShopSell` : 28
`Bank` : 29

**Returns**<br/>
`Table: Item table if the item is found, or nil if not found`

**Example**
```lua
-- Find the item in a specific layer
item = Items.FindByLayer(5)
if item ~= nil then
    Messages.Print('Item found with serial: ' .. item.Serial)
else
    Messages.Print('Item not found')
end
```

## FindBySerial
```lua
Items.FindBySerial(serial)
```
**Parameters**<br/>
`serial: Numeric value representing the serial number of the item to search`

**Returns**<br/>
`Table: Item table if the item is found, or nil if not found`

**Example**
```lua
-- Find the item by its serial number
item = Items.FindBySerial(123456)
if item ~= nil then
    Messages.Print('Item found at location x:'.. item.X..' y: '..item.Y)
else
    Messages.Print('Item not found')
end
```

## FindByType
```lua
Items.FindByType(type)
```
**Parameters**<br/>
`type: Numeric value representing the graphic type of the item to search`

**Returns**<br/>
`Table: Item table if the item is found, or nil if not found`

**Example**
```lua
-- Find the item by its type
item = Items.FindByType(3854)
if item ~= nil then
    Messages.Print('Item found with serial: ' .. item.Serial)
else
    Messages.Print('Item not found')
end
```

## FindByName
```lua
Items.FindByName(name)
```
**Parameters**<br/>
`name: String value representing the name of the item to search`

**Returns**<br/>
`Table: Item table if the item is found, or nil if not found`

**Example**
```lua
-- Find the item by its name
item = Items.FindByName('Katana')
-- If item was found
if item ~= nil then
    Messages.Print('Item found with serial: ' .. item.Serial)
else
    Messages.Print('Item not found')
end
```

## FindByFilter
```lua
Items.FindByFilter(filter)
```
**Parameters**<br/>
`filter: Table containing filter criteria`

**Returns**<br/>
`Table: A table of Item tables that match the filter criteria`

**Filter Options**
- `corpse: Boolean (optional)`: Whether the item is a corpse
- `container: Boolean (optional)`: Whether the item is a container
- `movable: Boolean (optional)`: Whether the item is movable
- `onground: Boolean (optional)`: Whether the item is on the ground
- `name: String (optional)`: The name of the item
- `rangemin: Integer (optional)`: The minimum range to search
- `rangemax: Integer (optional)`: The maximum range to search
- `graphics: Table of ushort (optional)`: A list of graphic types
- `layers: Table of Layer (optional)`: A list of layers
- `hues: Table of ushort (optional)`: A list of hues

**Simple Example**
```lua
---Finds and iterates over items in backpack what is type of clean bandage

filter = {onground=false, graphics=0x0E21}

list = Items.FindByFilter(filter)
for index, item in ipairs(list) do
    Messages.Print('Found item at location x:'..item.X..' y:'..item.Y..' '..item.Name)
end
```
Alternatively the filter can be directly passed as parameter instead defigning a variable in before:
```lua
list = Items.FindByFilter({onground=false, graphics=0x0E21})
```

**Complexer Example (Simple Scavenger)**
You have to adjust the pauses between the calls to fit your needs.
```lua
--=================
-- SETUP HERE
--=================
itemsToSearchFor = {
        0x0f7a, -- Black Pearl
        0x0f7b, -- Blood Moss
        0x0f86, -- Mandrake Root
        0x0f84, -- Garlic
        0x0f85, -- Ginseng
        0x0f88, -- Nightshade
        0x0f8d, -- Spider's Silk
        0x0f8c, -- Sulphurous Ash
       }

--================
-- MAIN ROUTINE
--================
while true do
	filter = {onground=true, rangemax=2, graphics=itemsToSearchFor}
	
	list = Items.FindByFilter(filter)
	for index, item in ipairs(list) do
	    Messages.Print('Picking up '..item.Name..' at location x:'..item.X..' y:'..item.Y)
	    Player.PickUp(item.Serial, 1000)
	    Pause(100)
	    Player.DropInBackpack()
	    Pause(100)
	end
	-- Important Pause for CPU
	Pause(150)
end
```

