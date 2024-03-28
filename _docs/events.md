---
title: Events
permalink: /docs/events/
---

Let's again look at our first example.

```lua
cake.Sets.Midcast['Elemental Magic'] = {
    Ear1 = "Moldavite Earring"
}

cake.Sets.Midcast['Enfeebling Elemental Magic'] = {
    Ear1 = "Elemental Earring"
}
```

Most people reading this guide already know what a midcast event is. Baklava defines some other events, so let's review them all now.

## Event Basics

Events happen while you play the game and occur when you do something. Many events have a taxonomy associated with them.

## Player Events

Player events relate to player actions.

<table>
  <thead>
    <tr>
      <th>Event</th>
      <th>Description</th>
      <th>Taxonomy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><b>Precast</b></p>
      </td>
      <td>
        <p>Occurs before you begin casting a spell</p>
      </td>
      <td>
        <p><b>Spell</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Midcast</b></p>
      </td>
      <td>
        <p>Occurs during spell casting and completion</p>
      </td>
      <td>
        <p><b>Spell</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Preshot</b></p>
      </td>
      <td>
        <p>Occurs before you begin a ranged attack</p>
      </td>
      <td>
        <p></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Midshot</b></p>
      </td>
      <td>
        <p>Occurs during ranged attack aiming and completion</p>
      </td>
      <td>
        <p></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Weaponskill</b></p>
      </td>
      <td>
        <p>Occurs when you use a weaponskill</p>
      </td>
      <td>
        <p><b>Weaponskill</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Item</b></p>
      </td>
      <td>
        <p>Occurs during item usage and completion</p>
      </td>
      <td>
        <p><b>Item</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Ability</b></p>
      </td>
      <td>
        <p>Occurs when you use a job ability</p>
      </td>
      <td>
        <p><b>Spell</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Idle</b></p>
      </td>
      <td>
        <p>Occurs when you are standing</p>
      </td>
      <td>
        <p></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Engaged</b></p>
      </td>
      <td>
        <p>Occurs when you have your weapons drawn</p>
      </td>
      <td>
        <p></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>Resting</b></p>
      </td>
      <td>
        <p>Occurs when you are resting</p>
      </td>
      <td>
        <p></p>
      </td>
    </tr>
  </tbody>
</table>

<div class="note info">
  <h5>Passive Events</h5>
  <p>The <b>Idle</b>, <b>Engaged</b>, and <b>Resting</b> events are passive and only occur when you're not performing an action.</p>
</div>

## Pet Events

Pet events relate to pet actions.

<table>
  <thead>
    <tr>
      <th>Event</th>
      <th>Description</th>
      <th>Taxonomy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><b>PetMidcast</b></p>
      </td>
      <td>
        <p>Occurs during your pet's spell casting and completion</p>
      </td>
      <td>
        <p><b>Spell</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>PetWeaponskill</b></p>
      </td>
      <td>
        <p>Occurs when your pet uses a Blood Pact, Ready Move, or Wyvern Breath</p>
      </td>
      <td>
        <p><b>PetWeaponskill</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>PetIdle</b></p>
      </td>
      <td>
        <p>Occurs when your pet is standing</p>
      </td>
      <td>
        <p><b>Pet</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>PetEngaged</b></p>
      </td>
      <td>
        <p>Occurs when your pet is engaged</p>
      </td>
      <td>
        <p><b>Pet</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>PetResting</b></p>
      </td>
      <td>
        <p>Occurs when your pet is resting</p>
      </td>
      <td>
        <p><b>Pet</b></p>
      </td>
    </tr>
  </tbody>
</table>

<div class="note info">
  <h5>Player Event Priority</h5>
  <p>Active player events take precedence over pet events. Baklava will not handle any pet events unless your character is in a passive player event.</p>
</div>

Next, we'll examine how events are combined with classifiers to construct our set declarations and shape Baklava's behavior.
