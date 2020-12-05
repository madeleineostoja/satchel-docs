---
uid: reset
title: Resets
description: Reset the styles of just the specific elements you need.
---

# Reset

### `reset(element)`

| `Argument` | Type | Description |
| :--- | :--- | :--- |
| `element` | `string` | Element to apply the reset to |

Applies an element-specific style reset.

```javascript
import { reset } from 'satchel-css';

`${reset('button')`;
```

## Available resets

{% tabs %}
{% tab title="button" %}
```css
border: none;
margin: 0;
padding: 0;
width: auto;
overflow: visible;
background: transparent;
color: inherit;
font: inherit;
line-height: normal;
-webkit-appearance: none;
&::-moz-focus-inner {
  border: 0;
  padding: 0;
}
```
{% endtab %}

{% tab title="input" %}
```css
margin: 0;
border: 0;
padding: 0;
display: inline-block;
vertical-align: middle;
white-space: normal;
background: none;
line-height: 1;
overflow: auto;
-webkit-appearance: none;
```
{% endtab %}

{% tab title="list" %}
```css
list-style: none;
padding: 0;
margin: 0;
```
{% endtab %}

{% tab title="blockquote" %}
```css
margin: 0;
padding: 0;
vertical-align: baseline;
&::before,
&::after {
  content: '';
}
```
{% endtab %}

{% tab title="fieldset" %}
```css
border: 0;
padding: 0.01em 0 0 0;
margin: 0;
min-width: 0;

body:not(:-moz-handler-blocked) & {
  display: table-cell;
}
```
{% endtab %}

{% tab title="legend" %}
```css
padding: 0;
display: table;
```
{% endtab %}
{% endtabs %}

