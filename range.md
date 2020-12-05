---
description: >-
  Style the notoriously difficult <input type="range" /> element across browsers
  with helper tags for tracks and thumbs.
---

# Range

### ``range.track`{styles}```  and ``range.thumb`{styles}```

Applies styles to the track \(ie: the ‘line’\) and thumb \(ie: the ‘button’\) of a range input respectively;

```javascript
import { css } from '@emotion/core';
import { range } from 'satchel-css';

const trackStyles = range.track`
    height: 2px;
    background: grey;
  `,
  thumbStyles = range.thumb`
    height: 8px;
    width: 8px;
    background: #ea356b;
  `;

const rangeInput = css`
  ${trackStyles}
  ${thumbStyles}
`;
```

### How it works

The range mixins apply your styles to vendor-specific pseudo elements offered and reset browser defaults where necessary.

{% tabs %}
{% tab title="Track CSS" %}
```css
-webkit-appearance: none;
&::-moz-focus-outer {
  border: 0;
}
&::-webkit-slider-runnable-track {
  -webkit-appearance: none;
  /* user styles */
}
&::-moz-range-track {
  -moz-appearance: none;
  /* user styles */
}
&::-ms-track {
  /* user styles */
}
```
{% endtab %}

{% tab title="Thumb CSS" %}
```css
&::-webkit-slider-thumb {
  -webkit-appearance: none;
  /* user styles */
}
&::-moz-range-thumb {
  -moz-appearance: none;
  /* user styles */
}
&::-ms-thumb {
  /* user styles */
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The output can’t be grouped because if a browser doesn’t understand a single selector in a group it ignores the whole rule \(see the W3Cs spec on [selector conformance](https://www.w3.org/TR/selectors-3/#Conformance)\).
{% endhint %}

