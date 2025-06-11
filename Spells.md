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
