---
description: Helpers for beautiful typography on the web
---

# Typography

### `lineClamp(n)`

| `Argument` | Type | Description |
| :--- | :--- | :--- |
| `n` | `number` | Number of lines to clamp text to |

Mixin for applying `-webkit-line-clamp` and the necessary properties along with it to truncate blocks of to a set number of lines.

{% hint style="warning" %}
Line clamping is [supported in all evergreen browsers](https://caniuse.com/css-line-clamp), but **not Internet Explorer**
{% endhint %}

{% tabs %}
{% tab title="Code" %}
```javascript
import { lineClamp } from 'satchel-css';

`${lineClamp(3)}`
```
{% endtab %}

{% tab title="Output CSS" %}
```css
display: -webkit-box;
-webkit-line-clamp: 3;
-webkit-box-orient: vertical;
overflow: hidden;`
```
{% endtab %}
{% endtabs %}

### `lineCrop(lineHeight, modifier?)`

| Argument | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `lineHeight` | `number` | `-` | Desired corrected line height of the text |
| `modifier` | `number` | `1` | Height of the font's capital letters, as a percentage of `font-size` |

Crops block of text to respect the font's ascenders, descenders, and capitals by using psuedo-elements to provide offsets. Useful for buttons and other short spans of text.

{% tabs %}
{% tab title="Code" %}
```javascript
import { lineCrop } from 'satchel-css';

`${lineCrop(1.2)}`
```
{% endtab %}

{% tab title="Output CSS" %}
```css
&::before {
 content: '';
 display: block;
 height: 0;
 width: 0;
 margin-top: calc(-0.2 * 0.5em);
}
```
{% endtab %}
{% endtabs %}

