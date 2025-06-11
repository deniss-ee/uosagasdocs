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