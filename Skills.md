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

