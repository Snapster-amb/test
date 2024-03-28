---
title: Declarations
permalink: /docs/declarations/
---

I promise this is the last time you'll see this.

```lua
cake.Sets.Midcast['Elemental Magic'] = {
    Ear1 = "Moldavite Earring"
}

cake.Sets.Midcast['Enfeebling Elemental Magic'] = {
    Ear1 = "Elemental Earring"
}
```

The syntax for creating a set declaration should be unambiguous now.

## Declaration Format

Set declarations adhere to the following format.

```lua
cake.Sets.{Event}['{Classifier}'] = {}
```

**Event** — Tells Baklava when to equip the set<br>
**Classifier** — Tells Baklava what spells to equip the set for

You may also declare a set without using a classifier.

```lua
cake.Sets.Precast = {
    Head = "Warlock's Chapeau"
}
```

Sets declared without a classifier are known as base event sets.

## Multiple Classifiers

What happens if you define sets for multiple classifiers that affect the same spell? Baklava will combine the items in your set declarations in rank order using the event set as a base. The more specific sets will overwrite items in overlapping slots.

Let's walk through what would happen during the midcast event if we cast Burn or Firaga II using the sets declared in our example.

<table>
  <thead>
	<tr>
	  <th colspan="2">Burn Classifiers</th>
	</tr>
    <tr>
      <th>Rank</th>
      <th>Classifier</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><b>1</b></p>
      </td>
      <td>
        <p><b>Elemental Magic</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>2</b></p>
      </td>
      <td>
        <p><b>Enfeebling Elemental Magic</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>3</b></p>
      </td>
      <td>
        <p><b>Burn</b></p>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
	<tr>
	  <th colspan="2">Firaga II Classifiers</th>
	</tr>
    <tr>
      <th>Rank</th>
      <th>Classifier</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><b>1</b></p>
      </td>
      <td>
        <p><b>Elemental Magic</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>2</b></p>
      </td>
      <td>
        <p><b>Ga</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>3</b></p>
      </td>
      <td>
        <p><b>Ga II</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>4</b></p>
      </td>
      <td>
        <p><b>Firaga II</b></p>
      </td>
    </tr>
  </tbody>
</table>

During Burn, Baklava will use your **Midcast** set as a base and then layer the **Elemental Magic** → **Enfeebling Elemental Magic** → **Burn** midcast sets on top before finally equipping the set.

During Firaga II, Baklava will use your **Midcast** set as a base and then layer the **Elemental Magic** → **Ga** → **Ga II** → **Firaga II** midcast sets on top before finally equipping the set.

The outcome is that Baklava would equip a Moldavite Earring if we cast Firaga II and an Elemental Earring if we cast Burn.

This behavior can be handy. Consider the Singing taxonomy briefly.

<a href="{{ site.baseurl }}/img/singing.png" data-lightbox="singing" data-title="Singing">
    <img src="{{ site.baseurl }}/img/singing.png" alt="Singing">
</a>

Nearly all songs have instruments that enhance the related song families but would otherwise prefer the same gear. The Baklava declarations for this scenario are very simple.

```lua
cake.Sets.Midcast.Singing = {
    Head = "Demon Helm",
    Body = "Minstrel's Coat",
    Hands = "Choral Cuffs",
    Legs = "Choral Cannions",
    Feet = "Sha'ir Crackows",
    Neck = "Wind Torque",
    Ear1 = "Ethereal Earring"
}

profile.Sets.Midcast['March'] = {
    Range = "Faerie Piccolo"
}

profile.Sets.Midcast['Madrigal'] = {
    Range = "Traversiere +1"
}

profile.Sets.Midcast['Minuet'] = {
    Range = "Cornette +1",
}
```

<div class="note">
  <h5>Keep It Simple!</h5>
  <p>Baklava's classifiers permit much flexibility, although keeping things as simple as possible is best. Avoid doing fancy things with classifiers unless it's necessary or helps makes things more clear.</p>
</div>
