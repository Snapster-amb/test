---
title: Welcome
permalink: /docs/home/
redirect_from: /docs/index.html
---

This site aims to be a comprehensive guide to Jekyll. We’ll cover topics such as getting your site up and running, creating and managing content, customizing your build, and deploying.

## What is Jekyll, exactly?

Jekyll is a simple, blog-aware, static site generator.

You create your content as text files ([Markdown](https://daringfireball.net/projects/markdown/)), and organize them into folders. Then, you build the shell of your site using [Liquid](https://shopify.github.io/liquid/)-enhanced HTML templates. Jekyll automatically stitches the content and templates together, generating a website made entirely of static assets, suitable for uploading to any server.

Jekyll happens to be the engine behind [GitHub Pages](https://pages.github.com), so you can host your project’s Jekyll page/blog/website on GitHub’s servers **for free**.

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

PDT = {
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

Enmity = {
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
