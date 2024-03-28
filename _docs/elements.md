---
title: Elements
permalink: /docs/elements/
---

You might have noticed that the taxonomies we've seen do not group things by element. Classifiers related to element and damage type have been appended to the taxonomical classifiers.

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
    <tr>
      <td>
        <p><b>5</b></p>
      </td>
      <td>
        <p><b>Fire Affinity</b></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><b>6</b></p>
      </td>
      <td>
        <p><b>Fire Magic Damage</b></p>
      </td>
    </tr>
  </tbody>
</table>

Doing this permits us the flexibility to declare elemental or damage-type sets that apply to many spells across the taxonomy.

```lua
cake.Sets.Midcast['Fire Magic Damage'] = {
    Main = "Fire Staff"
}

cake.Sets.Midcast['Earth Enfeeblement'] = {
    Main = "Earth Staff"
}

cake.Sets.Midcast['Restoration'] = {
    Main = "Light Staff"
}
```

<div class="note warning">
  <h5>Elemental Affinity</h5>
  <p>Using elemental affinity classifiers (<b>Fire Affinity</b>, <b>Ice Affinity</b>, etc.) may reduce the number of set declarations you must write. It's convenient but may lead to you equipping some gear when you don't want to, such as casting enhancement spells. To avoid this, you can use more specific (<b>Fire Enfeeblement</b>, <b>Fire Magic Damage</b>) classifiers.</p>
</div>
