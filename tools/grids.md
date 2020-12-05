---
description: >-
  Satchel includes several small, low-level helpers for making working with
  grids in CSS easier. You won't find complex grid systems here, we beleive in
  providing the tools you need to curate your own.
---

# Grids

## `flexGrid(gutter)`

| `Argument` | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `gutter` | `string` | `'2rem'` | Gutter between grid items |

Quickly create flex-based grids, using padding on children and negative margins on the parent element to achieve consistent gutters.

Once applied, set either `flex-basis` or `width` \(for legacy browser support\) on grid items to determine the number of columns. Eg: for a 2 column grid, give each item a `50%` width. `gutter` accepts any valid CSS unit.

{% tabs %}
{% tab title="Code" %}
```javascript
import { flexGrid } from 'satchel-css';';

// Two-column grid with 2rem gutters
`
${flexGrid('2rem')}
& > * {
  width: 50%;
}
`
```
{% endtab %}

{% tab title="Output CSS" %}
```css
display: flex;
flex-wrap: wrap;
margin: calc(0px - (2rem / 2));
& > * {
  padding: calc(2rem / 2);
  width: 50%;
}
```
{% endtab %}
{% endtabs %}

## `subgrid`

A simple mixin for shimming the missing `display: subgrid` behaviour from CSS grids, by making an element inherit its parent's grid. This is a basic shim that only works for full-width children, it can't account for partial subgrids.

{% tabs %}
{% tab title="Code" %}
```javascript
import { subgrid } from 'satchel-css';

`${subgrid}`;
```
{% endtab %}

{% tab title="Output CSS" %}
```css
display: grid;
grid-column: 1 / 99;
grid: inherit;
grid-gap: inherit;
grid-template-columns: inherit;
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
We use `1 / 99` for `grid-column` because IE11 doesn’t understand the `x / -1` syntax for extending to the final column
{% endhint %}

## `msGridRows(n)`

| `Argument` | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `n` | `number` | `5` | Number of rows to shim on IE |

Shims automatic row placement in simple CSS grids for IE11 by generating `nth-child()` statements with `-ms-grid-row` set appropriately.

{% tabs %}
{% tab title="Code" %}
```javascript
import { msGridRows } from 'satchel-css';

`${msGridRows(3)}`;
```
{% endtab %}

{% tab title="Output CSS" %}
```css
& > :nth-child(1) {
  -ms-grid-row: 1;
}
& > :nth-child(2) {
  -ms-grid-row: 2;
}
& > :nth-child(3) {
  -ms-grid-row: 3;
}
```
{% endtab %}
{% endtabs %}

