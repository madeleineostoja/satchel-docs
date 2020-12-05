---
description: >-
  Apply the shorthand value format from properties like margin and padding to
  positions.
---

# Position

### `position(position, values)`

Creates a `position` ruleset from a shorthand values string. It can take any valid CSS position property, and the values string follows the same rules as [margin and padding shorthand properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties#Margin_and_Padding_Properties).

```javascript
import { position } from 'satchel-css';

`${position('absolute', '0 2rem')}`;
```

### Shorthand values

Satchel’s position helper uses the same logic as CSS’s margin and padding shorthands to set `top`, `right`, `bottom`, and `left` properties.

* When one value is specified, it is applied to all four sides
* When two values are specified, the first value applies to the top and bottom, the second to the left and right
* When three values are specified, the first value applies to the top, the second to the left and right, the third to the bottom
* When four values are specified, the values apply to the top, right, bottom, and left in that order \(clockwise\)

{% tabs %}
{% tab title="Code" %}
```javascript
position('absolute', 0);
```
{% endtab %}

{% tab title="Output CSS" %}
```css
position: absolute;
top: 0;
right: 0;
bottom: 0;
left: 0;
```
{% endtab %}
{% endtabs %}

