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
