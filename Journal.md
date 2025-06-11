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

