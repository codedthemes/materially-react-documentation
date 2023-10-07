# Default Theme

Customize Material-UI with your theme. You can change the colors, the typography, and much more.

### Theme configuration variables

Changing the theme configuration variables is the most effective way to match Material-UI to your needs. The following sections cover the most important theme variables:

* [Palette](https://mui.com/material-ui/customization/palette/)
* [Typography](https://mui.com/material-ui/customization/typography/)
* [Spacing](https://mui.com/material-ui/customization/spacing/)
* [Breakpoints](https://mui.com/material-ui/customization/breakpoints/)
* [z-index](https://mui.com/material-ui/customization/z-index/)
* [Globals](https://mui.com/material-ui/customization/theme-components/)

You can check out the [default theme section](https://mui.com/material-ui/customization/theme-components/) to view the default theme in full.

**Examples**

```
import * as React from 'react';
import { createTheme, ThemeProvider } from '@mui/material/styles';
import Button from '@mui/material/Button';

const theme = createTheme({
  components: {
    // Name of the component
    MuiButtonBase: {
      defaultProps: {
        // The default props to change
        disableRipple: true, // No more ripple, on the whole application 💣!
      },
    },
  },
});

export default function DefaultProps() {
  return (
    <ThemeProvider theme={theme}>
      <Button>This button has disabled ripples.</Button>
    </ThemeProvider>
  );
}
```

{% hint style="info" %}
You can edit this file at **`[ ../src/themes/index.js]`**
{% endhint %}

```

// material-ui
import { createTheme } from '@mui/material/styles';
import { grey } from '@mui/material/colors';

// project import
import value from '../assets/scss/_themes-vars.scss';



export function theme(customization) {
  let textPrimary;
  let textSecondary;
  let textDark;
  let textHint;
  let background;
  let paper;
  let menuCaption;
  let textInversePrimary;

  switch (customization.navType) {
        case 'dark':
            ...
        case 'nav-dark':
            ...
        case 'light':
        default:
            ...
    }


    return createTheme({

        palette: {
            ...
        },
        typography: {
            fontFamily: `'Inter', sans-serif`,
            ....
        },
        breakpoints: {
            values: {
                xs: 0,
                sm: 600,
                md: 960,
                lg: 1280,
                xl: 1920,
                mobile: 430
            }
        },
        overrides: {
            ...
        },
    });
};

export default theme;

```

If you want to learn more about how the theme is assembled, take a look at [`mui/style/createTheme.js`](https://mui.com/material-ui/customization/theming/), and the related imports which `createTheme` uses.
