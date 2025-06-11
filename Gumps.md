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
