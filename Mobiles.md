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