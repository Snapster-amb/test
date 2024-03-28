---
title: Welcome
permalink: /docs/home/
redirect_from: /docs/index.html
---

This site aims to be a comprehensive guide to Baklava. We'll review the basic concepts behind the library, how to get a simple job file set up, and explore some features more in-depth.

## What is Baklava?

Baklava is an extension to [LuAshitacast](https://github.com/ThornyFFXI/LuAshitacast) and [GearSwap](https://docs.windower.net/addons/gearswap/) that supports taxonomical set declaration, layered gear sets with convenient keybindings, level sync support, and several other convenient features aimed at reducing the effort required to create a robust and functional job file.

## What does all of that mean?

Sometimes it's easier to learn by example. Consider how we want to itemize for Elemental Magic. We will only differentiate between elemental enfeebles and other elemental magic for brevity. Doing this could lead to the following LuAshitacast code.

```lua
profile.HandleMidcast = function()
    local spell = gData.GetAction()
    if spell.Skill == 'Elemental Magic' then
        if (spell.Name == 'Burn' or
            spell.Name == 'Choke' or
            spell.Name == 'Drown' or
            spell.Name == 'Frost' or
            spell.Name == 'Rasp' or
            spell.Name == 'Shock') then 
            gFunc.EquipSet({
                Ear1 = "Elemental Earring"
            })
        else
            gFunc.EquipSet({
                Ear1 = "Moldavite Earring"
            })
        end
    end
end
```

The skill and name conditionals to determine which gear to equip are nested in the midcast function. The code can become complicated and challenging to maintain as you get more equipment and optimize more spells.

The corresponding Baklava declarations are more concise and easier to understand.

```lua
cake.Sets.Midcast['Elemental Magic'] = {
    Ear1 = "Moldavite Earring"
}

cake.Sets.Midcast['Enfeebling Elemental Magic'] = {
    Ear1 = "Elemental Earring"
}
```

There are no skill or name conditionals or other procedural code. We have focused solely on stating what we want rather than how we want it to happen. This model is easier to work with, approachable to those with limited or no coding experience, and less time-consuming to debug.

<!--<div class="note info">
  <h5>But I like coding!</h5>
  <p>Baklava is also extendible.  If something specific you'd like to do is tricky to handle declaratively, you can always tag on some imperative code before or after Baklava handles the set declarations.</p>
</div>


```lua
profile.HandleMidcast = function()
    local spell = gData.GetAction()
    if spell.Skill == 'Enfeebling Magic' then
        local mndEnfeebles = {
            ['Slow'] = true,
            ['Slow II'] = true,
            ['Paralyze'] = true,
            ['Paralyze II'] = true,
            ['Silence'] = true,
            ['Indunation'] = true,
            ['Addle'] = true,
            ['Addle II'] = true
        }
        local enfeeblingBaseSet = {
            Neck = 'Enfeebling Torque'
        }
        if mndEnfeebles[spell.Name] then
            enfeeblingBaseSet = gFunc.Combine(enfeeblingBaseSet, {
                Ring1 = 'Aqua Ring',
                Ring2 = 'Aqua Ring'
            })
        else
            enfeeblingBaseSet = gFunc.Combine(enfeeblingBaseSet, {
                Ring1 = 'Snow Ring',
                Ring2 = 'Snow Ring'
            })
        end
        gFunc.EquipSet(enfeeblingBaseSet)
        if spell.Element == 'Earth' then
            gFunc.Equip('Main', 'Earth Staff')
        elseif spell.Element == 'Ice' then
            gFunc.Equip('Main', 'Ice Staff')
        else
            gFunc.Equip('Main', 'Mistilteinn')
        end
    end
end
```

The corresponding Baklava code is simpler and easier to understand.

```lua
cake.Sets.Midcast['Enfeebling Magic'] = {
    Main = 'Mistilteinn',
    Neck = 'Enfeebling Torque'
}
cake.Sets.Midcast['Dark Magic Enfeebling'] = {
    Ring1 = 'Snow Ring',
    Ring2 = 'Snow Ring'
}
cake.Sets.Midcast['White Magic Enfeebling'] = {
    Ring1 = 'Aqua Ring',
    Ring2 = 'Aqua Ring'
}
cake.Sets.Midcast['Ice Enfeeblement'] = {
    Main = 'Ice Staff'
}
cake.Sets.Midcast['Earth Enfeeblement'] = {
    Main = 'Earth Staff'
}
```

Something about declarative code.

## Navigating the Guide

Throughout this guide, you'll see these special sections that help you get the most out of Jekyll:

<div class="note">
  <h5>ProTips™</h5>
  <p>Tips and tricks that'll make you a Jekyll wizard!</p>
</div>

<div class="note info">
  <h5>Notes</h5>
  <p>Extra tidbits that are sometimes necessary to understand Jekyll.</p>
</div>

<div class="note warning">
  <h5>Warnings</h5>
  <p>Common pitfalls to avoid.</p>
</div>

<div class="note unreleased">
  <h5>Unreleased</h5>
  <p>Features planned for future versions of Jekyll, but not available yet.</p>
</div>

If you find anything we haven’t covered, or would like to share a tip that others might find handy, please [file an issue]({{ site.repository }}/issues/new) and we’ll see about adding it to the guide.

```lua
local layers = gFunc.LoadFile('layers\\layers')

local combatMode = layers.CreateModeGroup('Combat', {'Off', 'Tanking'}, '@t')
local weaponMode = layers.CreateModeGroup('Weapon', {'SenjiFudo', 'Mamushitos', 'Staves'}, '@w')

local PDT = {
    Head = "Arh. Jinpachi +1",
    Body = "Arhat's Gi +1",
    Hands = "Dst. Mittens +1",
    Legs = "Dst. Subligar +1",
    Feet = "Yasha Sune-Ate",
    Neck = "Evasion Torque",
    Waist = "Warwolf Belt",
    Ammo = "Happy Egg",
    Ear1 = "Pigeon Earring",
    Ear2 = "Pigeon Earring",
    Ring1 = "Sattva Ring",
    Ring2 = "Jelly Ring"
}

local Enmity = {
    Head = "Arh. Jinpachi +1",
    Body = "Arhat's Gi +1",
    Legs = "Yasha Hakama",
    Feet = "Arhat's Hakama +1",
    Waist = "Warwolf Belt",
    Neck = "Harmonia's Torque",
    Ammo = "Nokizaru Shuriken",
    Ear1 = "Eris' Earring +1",
    Ear2 = "Eris' Earring +1",
    Ring1 = "Sattva Ring",
    Ring2 = "Mermaid Ring"
}

layers.Sets.Engaged = {
    Head = "Panther Mask",
    Body = "Ninja Chainmail",
    Hands = "Ochimusha Kote",
    Legs = "Byakko's Haidate",
    Feet = "Sarutobi Kyahan",
    Neck = "Peacock Amulet",
    Waist = "Swift Belt",
    Back = "Amemet Mantle",
    Ear1 = "Eris' Earring +1",
    Ear2 = "Eris' Earring +1",
    Ring1 = "Jaeger Ring",
    Ring2 = "Venerer Ring",
    Ammo = "Bailathorn"
}

layers.Sets.Weaponskill = {
    Head = "Voyager Sallet",
    Body = "Ryl.Kgt. Chainmail",
    Hands = "Ochimusha Kote",
    Legs = "Byakko's Haidate",
    Feet = "Luisant Sollerets",
    Neck = "Spike Necklace",
    Waist = "Warwolf Belt",
    Back = "Amemet Mantle",
    Ear1 = "Beetle Earring +1",
    Ear2 = "Beetle Earring +1",
    Ring1 = "Courage Ring",
    Ring2 = "Courage Ring",
    Ammo = "Bailathorn"
}

layers.Sets.Ability = Enmity
layers.Sets.Idle = PDT
layers.Sets.Midcast = PDT

layers.Sets.Midcast.Ninjutsu = {
    Head = "Ninja Hatsuburi",
    Neck = "Ninjutsu Torque",
    Feet = "Sarutobi Kyahan",
    Waist = "Swift Belt"
}

layers.Sets.Midcast['Elemental Ninjutsu'] = {
    Waist = "Ryl.Kgt. Belt",
    Ring1 = "Eremite's Ring",
    Ring2 = "Eremite's Ring",
    Ear2 = "Moldavite Earring",
    Ammo = "Morion Tathlum"
}

layers.Sets.Midcast.Utsusemi = {
    Head = "Panther Mask",
    Legs = "Byakko's Haidate",
    Feet = "Sarutobi Kyahan",
    Waist = "Swift Belt"
}

layers.Sets.Tanking.Engaged = PDT
layers.Sets.Tanking.Midcast.Enfeebling = Enmity
layers.Sets.Tanking.Midcast['Enfeebling Ninjutsu'] = Enmity
layers.Sets.Tanking.Midcast['Utsusemi: Ichi'] = gFunc.Combine(PDT, {
    Waist = "Swift Belt",
})

layers.Sets.SenjiFudo.Idle = {
    Main = "Senjuinrikio",
    Sub = "Fudo"
}
layers.Sets.SenjiFudo.Engaged = layers.Sets.SenjiFudo.Idle

layers.Sets.Mamushitos.Idle = {
    Main = "Mamushito",
    Sub = "Mamushito"
}

layers.Sets.Mamushitos.Engaged = layers.Sets.Mamushitos.Idle

layers.Sets.Staves.Idle = {
    Main = "Earth Staff",
    Back = "High Brth. Mantle",
}

layers.Sets.Staves.Engaged = layers.Sets.Staves.Idle
layers.Sets.Staves.Midcast['Ice Magic Damage'] = { Main = "Ice Staff" }
layers.Sets.Staves.Midcast['Lightning Magic Damage'] = { Main = "Thunder Staff" }

layers.RegisterCallback("PostHandleIdle", function()
    local environment = gData.GetEnvironment()
    if environment.Time >= 18.00 or environment.Time <= 6.00 then
        gFunc.Equip("Feet", "Ninja Kyahan")
    end
end, "EquipNinjaKyahan")

layers.RegisterCallback("PostHandleEngaged", function()
    local player = gData.GetPlayer()
    if player.HPP <= 75 and combatMode.current ~= "Tanking" then
        gFunc.Equip("Ring2", "Shinobi Ring")
    end
end, "Engaged Shinobi Ring")

layers.RegisterCallback("PostHandleMidcast", function(spell)
    local player = gData.GetPlayer()
    if player.HPP <= 75 and (combatMode.current ~= "Tanking" or spell.Name ~= "Utsusemi: Ichi") then
        gFunc.Equip("Ring2", "Shinobi Ring")
    end
end, "Midcast Shinobi Ring")

return layers
```
-->
