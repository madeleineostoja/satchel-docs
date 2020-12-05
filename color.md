---
description: Use Satchel’s color functions to convert between RGBA and hex values.
---

# Color

### `rgba(hex, alpha)`

Generates the RGBA value of a hex code with an alpha channel.

```javascript
import { rgba } from 'satchel-css';

`background: ${rgba('#ea356b', 0.75)};`;
```

### `hex(r,g,b)`

Generates the hex code for an RGB color value.

```javascript
import { hex } from 'satchel-css';

`background: ${hex(234, 53, 107)};`;
```

