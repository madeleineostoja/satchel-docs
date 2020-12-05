---
description: >-
  Constrain boxes to any aspect ratio, either with absolute sizing or expandable
  to fit its children.
---

# Aspect

## `aspect(x, y, options?)`

| `Argument` | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `x` | `number` | - | X axis aspect |
| `y` | `number` | - | Y axis aspect |
| `options.mode` | `string` | `'absolute'` | Method used for aspect ratio |

Calculates a relative height based on an aspect ratio and uses `::before` and `::after` elements with a `padding-top` offset to achieve an aspect-constrained box.

You can allow children to expand the box vertically, absolutely position children to maintain a perfect aspect, or only create the padding-top offset.

```javascript
import { aspect } from 'satchel-css';

// Expandable box
`${aspect(16,9)}`

// Absolute box
`${aspect(16,9 { mode: 'absolute' })}`

// Padding-top offset only
`${aspect(16,9, { mode: 'lite' })}`
```

## Absolute boxes

By default `aspect` absolutely positions direct children to ensure boxes retain their aspect ratio

{% tabs %}
{% tab title="Code" %}
```javascript
aspect(16, 9, { mode: 'absolute' });
```
{% endtab %}

{% tab title="Output CSS" %}
```css
position: relative;
& > * {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
&::before {
  content: '';
  display: block;
  padding-top: 56.25%;
  position: relative;
}
```
{% endtab %}
{% endtabs %}

## Expandable boxes

By setting `mode` to `'expandable'` will allow children to expand the box vertically. This is achieved with a dummy `::before` element to set an initial height.

{% tabs %}
{% tab title="Code" %}
```javascript
aspect(16, 9, { mode: 'expandable' });
```
{% endtab %}

{% tab title="Output CSS" %}
```css
&::before {
  content: '';
  display: block;
  padding-top: 56.25%;
  width: 1px;
  margin-left: -1px;
  float: left;
}
&::after {
  content: '';
  display: table;
  clear: both;
}
```
{% endtab %}
{% endtabs %}

## Minimal output

If you want to handle your own layout logic for aspect ratios, set `mode` to `lite` to just output the `padding-top` offset.

{% tabs %}
{% tab title="Code" %}
```javascript
aspect(16, 9, { mode: 'minimal' });
```
{% endtab %}

{% tab title="Output CSS" %}
```css
&::before {
  content: '';
  display: block;
  padding-top: 56.25%;
}
```
{% endtab %}
{% endtabs %}

