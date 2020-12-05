---
description: Work more easily with web fonts.
---

# Font

### `fontFace(name, files, opts?)`

| `Argument` | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | Name of the font family |
| `files` | `string[]` | Array of paths to font files |
| `opts` | `object` | Font options — `style`, `weight`, and `display` |

Quickly create flex-based grids, using padding on children and negative margins on the parent element to achieve consistent gutters.

Generates `@font-face` rules from an array of font files. Since `@font-face` declarations are global, you should use `fontFace()` with a global CSS helper from your CSS-in-JS library of choice.

{% tabs %}
{% tab title="With Emotion" %}
```javascript
import { css, Global } from '@emotion/core';
import { fontFace } from 'satchel-css';
import myFontWoff2 from './assets/my-font.woff2';
import myFontWoff from './assets/my-font.woff';

render(
  <>
    <Global
      styles={css`
        ${fontFace('My Font', [myFontWoff2, myFontWoff])}
      `}
    />
    {/* Rest of your app */}
  </>
);
```
{% endtab %}

{% tab title="With Styled Components" %}
```javascript
import { createGlobalStyle } from 'styled-components';
import { fontFace } from 'satchel-css';
import myFontWoff2 from './assets/my-font.woff2';
import myFontWoff from './assets/my-font.woff';

const Fonts = createGlobalStyle`
  ${fontFace('My Font', [myFontWoff2, myFontWoff])}
`;

render(
  <>
    <Fonts />
    {/* Rest of your app */}
  </>
);
```
{% endtab %}
{% endtabs %}

Sources are generated in the order of the files array, so the most progressive formats \(eg: `woff2`/`woff`\) should be first.

You can of course also provide paths to file paths as plain strings if you don't want to let Webpack et al handle bundling them

```javascript
fontFace('My Font', ['/path/to/my-font.woff2']);
```

### Options

You can set `font-weight`, `font-style`, and `font-display` by passing `options` to `fontFace`.

```javascript
fontFace('My Font', [...files], {
  weight: 700,
  style: 'italic',
});
```

