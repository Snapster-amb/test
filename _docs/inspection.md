---
title: Explore
permalink: /docs/explore/
---

Let's review the declarations from our previous example.

```lua
cake.Sets.Midcast['Elemental Magic'] = {
    Ear1 = "Moldavite Earring"
}

cake.Sets.Midcast['Enfeebling Elemental Magic'] = {
    Ear1 = "Elemental Earring"
}
```

We can break down each statement and define some terminology.

<table>
  <thead>
    <tr>
      <th>Component</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><b>cake</b></p>
      </td>
      <td>
        <p>The Baklava library interface</p>
      </td>
    </tr>
	<tr>
      <td>
        <p><b>Sets</b></p>
      </td>
      <td>
        <p>Where we store our set declarations</p>
      </td>
    </tr>
	<tr>
      <td>
        <p><b>Midcast</b></p>
      </td>
      <td>
        <p>An <b>Event</b> that occurs after we begin casting a spell</p>
      </td>
    </tr>
	<tr>
      <td>
        <p><b>Elemental Magic</b></p>
      </td>
      <td>
        <p>A <b>Classifier</b> assigned to any spell that uses Elemental Magic skill</p>
      </td>
    </tr>
	<tr>
      <td>
        <p><b>Enfeebling Elemental Magic</b></p>
      </td>
      <td>
        <p>A <b>Classifier</b> assigned to the Burn, Choke, Drown, Frost, Rasp, and Shock spells</p>
      </td>
    </tr>
  </tbody>
</table>

There's some patterning to how the declarations are structured and some compelling things you can do with the library interface. We'll dive into those topics later. For now, let's take a brief look at events and classifiers.
