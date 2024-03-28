---
title: Installation
description: Official guide to install Baklava on Ashita and Windower
permalink: /docs/installation/
---

- [Ashita v4 Installation Guide](#ashita-v4)
- [Windower Installation Guide](#windower)

## Ashita v4

Before you start, make sure you have the following.

- [LuAshitacast](https://github.com/ThornyFFXI/LuAshitacast)

If you've never used LuAshitacast, you must create a job file by issuing the following in-game command.

```sh
/lac newlua
```

LuAshitacast generates and searches for job files in the following location.

```sh
Game
└── config
    └── addons
        └── luashitacast
            └── CharName_CharId
                └── Job.lua
```

### Installation

Download the zip file and extract the contents to the following location.

```sh
Game
└── config
    └── addons
        └── luashitacast
            └── baklava
                ├── classifiers
                |   ├── abilities.lua
                |   ├── pets.lua
                |   ├── petweaponskills.lua
                |   ├── spells.lua
                |   └── weaponskills.lua
                ├── shims
                |   ├── constants.lua
                |   ├── gearswap.lua
                |   ├── hotkeys.lua
                |   └── luashitacast.lua
                ├── cake.lua
                ├── callbacks.lua
                ├── chat.lua
                ├── commands.lua
                ├── constants.lua
                ├── core.lau
                ├── globals.lua
                ├── hotkeys.lua
                ├── layers.lua
                ├── logger.lua
                ├── taxonomy.lua
                └── utils.lua
```

### Job File Contents

You can replace the entire contents of your Job.lua with the following.

```lua
local cake = gFunc.LoadFile('baklava\\cake')

-- Add set declarations here

return cake
```

## Windower

Before you start, make sure you have the following.

- [GearSwap](https://docs.windower.net/addons/gearswap/)

If you've never used GearSwap, you must create a job file in the following location.

```sh
Windower
└── addons
    └── GearSwap
        └── data
            └── CharName
                └── CharName_Job.lua
```

<div class="note info">
  <h5>Job File Locations</h5>
  <p>GearSwap may search for job files in other locations, although we will not cover those in this guide.</p>
</div>

### Installation

Download the zip file and extract the contents to the following location.

```sh
Windower
└── addons
    └── GearSwap
        └── libs
            └── baklava
                ├── classifiers
                |   ├── abilities.lua
                |   ├── pets.lua
                |   ├── petweaponskills.lua
                |   ├── spells.lua
                |   └── weaponskills.lua
                ├── shims
                |   ├── constants.lua
                |   ├── gearswap.lua
                |   ├── hotkeys.lua
                |   └── luashitacast.lua
                ├── cake.lua
                ├── callbacks.lua
                ├── chat.lua
                ├── commands.lua
                ├── constants.lua
                ├── core.lau
                ├── globals.lua
                ├── hotkeys.lua
                ├── layers.lua
                ├── logger.lua
                ├── taxonomy.lua
                └── utils.lua
```

### Job File Contents

You can create a job file 

```lua
local cake = require('baklava/cake')

-- Add set declarations here
```

<div class="note warning">
  <h5>User Event Functions</h5>
  <p>Baklava connects to GearSwap through User Event Functions.</p>
</div>