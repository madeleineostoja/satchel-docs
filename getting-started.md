# Getting Started

All of Satchel’s utilities return plain strings, so they work almost everywhere. The only prerequisite is that your environment supports [nested CSS selectors](https://tabatkins.github.io/specs/css-nesting/#nest-selector). Popular CSS-in-JS frameworks like [styled-components](https://styled-components.com/), [Emotion](https://emotion.sh/), [Linaria](https://linaria.now.sh/), and any other tool built on top of the [Stylis](https://github.com/thysultan/stylis.js) preprocessor work out of the box.

### Installation

Install Satchel from NPM

```bash
npm i satchel-css
```

#### Alternatively include from a CDN

If you’re not using a module bundler you can also link to Satchel directly on the [unpkg](https://unpkg.com/) CDN. Add the following `<script>` tag to the bottom of your HTML:

```markup
<script src="https://unpkg.com/satchel-css/index.js"></script>
```

Satchel will then be available on the global `window` variable

```javascript
const buttonStyles = `
    ${window.satchel.reset('button')};
    background: blue;
    color: white;
`;
```

### Usage

Import Satchel’s utilities embed them in CSS template strings by wrapping them in `${ }` braces.

While Satchel’s utilities will work in plain strings, to support nested selectors out of the box you’ll probably want to use them alongside a CSS-in-JS library like [Emotion](https://emotion.sh) or [styled-components](https://styled-components.com).

{% hint style="info" %}
Note that unless you’re setting the value of an individual property you don’t need to add a semicolon after a Satchel expression like you would a line of CSS.
{% endhint %}

{% tabs %}
{% tab title="With Emotion" %}
```javascript
import { css } from '@emotion/core';
import { reset, fluid } from 'satchel-css';

const buttonStyles = css`
  ${reset('button')}
  background: blue;
  color: white;
`;

const headingStyles = css`
  ${fluid('font-size', '2rem', '3.5rem')};
`;
```
{% endtab %}

{% tab title="With Styled Components" %}
```javascript
import styled from 'styled-components';
import { reset, fluid } from 'satchel-css';

const Button = styled.button`
  ${reset('button')}
  background: blue;
  color: white;
`;

const Heading = styled.h1`
  ${fluid('font-size', '2rem', '3.5rem')};
`;
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Object styles \(ie: style rules written as plain JS objects\) aren’t currently supported
{% endhint %}

