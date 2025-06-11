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
