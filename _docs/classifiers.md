---
title: Classifiers
permalink: /docs/classifiers/
---

Let's continue looking at our first example.

```lua
cake.Sets.Midcast['Elemental Magic'] = {
    Ear1 = "Moldavite Earring"
}

cake.Sets.Midcast['Enfeebling Elemental Magic'] = {
    Ear1 = "Elemental Earring"
}
```

You may wonder how Baklava knows which spells are elemental magic and which are enfeebling elemental magic. Baklava uses a taxonomy system to do this.

## Taxonomy Basics

Taxonomy is a system for classifying things. Taxonomy is widely applied in biology to classify living organisms. Baklava uses a hierarchical taxonomy to classify spells.

<a href="{{ site.baseurl }}/img/elemental.png" data-lightbox="elemental" data-title="Elemental Magic">
    <img src="{{ site.baseurl }}/img/elemental.png" alt="Elemental Magic">
</a>

This image is a visualization of the elemental magic section of the spell taxonomy. You can see that the Burn spell is classified as both elemental magic and enfeebling elemental magic.

<div class="note info">
  <h5>More than Magic!</h5>
  <p>The taxonomy system in Baklava is comprehensive. All of the game's actions, and even some things that aren't actions, have been classified with hierarchical taxonomies.</p>
</div>

## Classifier Ranks

When a spell has multiple classifiers, the classifiers are ranked. Baklava orders classifier ranks from least to most specific. The lower the number, the higher the rank, as shown below.

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

<!--
## More than Magic

The taxonomy system in Baklava is comprehensive. All of the game's actions, and even some things that aren't actions, have been classified with hierarchical taxonomies.

The taxonomies are hand-made with itemization in mind. Although most are structured in a natural way, a few contrived classifiers exist to permit easier set declarations to optimize Conserve MP, spell recast, and other situations.


What happens if you define sets for multiple classifiers that affect the same spell? Baklava will combine the items in your set declarations in the least-to-most specific order using the event set as a base. The more specific sets will overwrite items in overlapping slots.

Let's walk through what would happen during the Midcast event if we cast Burn or Firaga II using the sets declared in our example.

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

## More than Magic

The taxonomy system in Baklava is comprehensive. All of the game's actions, and even some things that aren't actions, have been classified with hierarchical taxonomies.

The taxonomies are hand-made with itemization in mind. Although most are structured in a natural way, a few contrived classifiers exist to permit easier set declarations to optimize Conserve MP, spell recast, and other situations.
-->