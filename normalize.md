---
uid: normalize
title: Normalize
description: >-
  Lightweight, modern, and configurable CSS normalization to give your project a
  consistent base across browsers.
---

# Normalize

### `normalize(options)`

Injects global normalize styles based on the options provided. Note that since `normalize` is meant to apply globally, you should use it with the global CSS helper in your CSS-in-JS library of choice.

{% tabs %}
{% tab title="With Emotion" %}
```javascript
import { css, Global } from '@emotion/core';
import { normalize } from 'satchel-css';

render(
  <>
    <Global
      styles={css`
        ${normalize({ base: 'normalize' })}
      `}
    />
    {/* Rest of your App */}
  </>
);
```
{% endtab %}

{% tab title="With Styled Components" %}
```javascript
import { createGlobalStyle } from 'styled-components';
import { normalize } from 'satchel-css';

const Normalize = createGlobalStyle`${normalize({ base: 'normalize' })}`;

render(
  <>
    <Normalize />
    {/* Rest of your app */}
  </>
);
```
{% endtab %}
{% endtabs %}

## Options

| `Option` | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `base` | `string` | `'normalize'` | Which base reset to use |
| `saneEmbeds` | `boolean` | `true` | Normalize embed elements |
| `hiddenProp` | `boolean` | `true` | Patch `hidden` prop |
| `reduceMotion` | `boolean` | `true` | Automatically respect user 'reduce motion' preferences |
| `fontSmoothing` | `boolean` | `false` | Apply default font smoothing |
| `resetMargins` | `boolean` | `false` | Remove margins on block elements |
| `resetHeadings` | `boolean` | `false` | Reset all headings |

The normalize provided by Satchel is highly configurable and comes with sane defaults for modern development.

#### `base`

Sets the base normalize to use, from a few high quality options:

* `'normalize'` — [modern-normalize](https://github.com/sindresorhus/modern-normalize), a fork of the classic `normalize.css` for modern browsers and developer expectations.
* `'normalize-legacy'` — The classic [normalize.css](https://csstools.github.io/normalize.css/) stylesheet, with patches for legacy browers and zero opinionated resets.
* `'remedy'` — [CSS Remedy](https://github.com/jensimmons/cssremedy), an opinionated CSS override by Mozilla for saner defaults \(note: CSS Remedy is currently in beta\)

Set `base` to `null` to remove the all base normalization and just use Satchel-specific resets.

#### `saneEmbeds`

Makes replaced elements \(images, videos, objects, etc\) block level and respect their parent container's sizing by default.

```css
img,
svg,
video,
canvas,
audio,
iframe,
embed,
object {
  display: block;
  vertical-align: middle;
  max-width: 100%;
}

img,
svg,
video,
canvas {
  height: auto;
}
```

#### `hiddenProp`

Forces browsers to respect the `hidden` attribute's intended behaviour.

```css
[hidden] {
  display: none !important;
}
```

#### `reduceMotion`

Adds support for 'reduce motion' user preferences by short-circuiting transitions

```css
@media (prefers-reduced-motion: reduce) {
  *,
  ::before,
  ::after {
    animation-delay: -1ms !important;
    animation-duration: 1ms !important;
    animation-iteration-count: 1 !important;
    background-attachment: initial !important;
    scroll-behavior: auto !important;
    transition-delay: 0s !important;
    transition-duration: 0s !important;
  }
}
```

#### `fontSmoothing`

Applies vendor prefixed font-smoothing globally.

```css
html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

#### `resetMargins`

Removes the default margins on block level elements \(except for `p`\), to give a foundation for consistent vertical rhythm.

```css
blockquote,
dl,
dd,
h1,
h2,
h3,
h4,
h5,
h6,
figure,
pre {
  margin: 0;
}
```

#### `resetHeadings`

Resets the font styles of headings so they have purely semantic rather than stylistic function by default.

```css
h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: inherit;
}
```

