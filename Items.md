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