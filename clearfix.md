---
description: Apply a clearfix with a simple mixin
---

# Clearfix

#### `clearfix`

{% tabs %}
{% tab title="Code" %}
```javascript
import { clearFix } from 'satchel-css';

`${clearfix}`;
```
{% endtab %}

{% tab title="Output CSS" %}
```css
&::after {
  content: '';
  display: block;
  clear: both;
}
```
{% endtab %}
{% endtabs %}

