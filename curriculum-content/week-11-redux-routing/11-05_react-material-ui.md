# React Material UI v4

[v4 Installation Docs](https://v4.mui.com/getting-started/installation/)

```
npm install @material-ui/core
npm install @fontsource/roboto
```

In App.jsx
`import '@fontsource/roboto';`

The Material UI docs can be overwhelming. Make sure you're using the correct version of the docs  -- we're using v4.

Be patient with them and yourself. Don't assume you need all the things. Start small and work through adding things slowly. 



## Make a button

```JSX
// SearchButton.js
import React from 'react';
import Button from '@material-ui/core/Button';

function SearchButton () {
    
  return (
    <Button variant="raised" color="primary">
      Search
    </Button>)
    
}

export default SearchButton;
```

### Style it in JavaScript


Import and define styles above the Component:

```JavaScript
import React from 'react';
import { makeStyles } from '@material-ui/core/styles';
import Button from '@material-ui/core/Button';

const useStyles = makeStyles({
  root: {
    background: 'linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)',
    border: 0,
    borderRadius: 3,
    boxShadow: '0 3px 5px 2px rgba(255, 105, 135, .3)',
    color: 'white',
    height: 48,
    padding: '0 30px',
  },
});

function CustomButton() {
  const classes = useStyles();
  return (
      <Button className={classes.root}>Custom!</Button>
    );
}
```

## Add a theme

```JSX

// v4 moved the ThemeProvider to /styles
// Adjust code below in render() to <ThemeProvider>
import { ThemeProvider } from '@material-ui/core/styles/';

import { createMuiTheme } from '@material-ui/core/styles';
import teal from '@material-ui/core/colors/teal';
import cyan from '@material-ui/core/colors/cyan';
import red from '@material-ui/core/colors/red';

const theme = createMuiTheme({
  palette: {
    primary: {
      main: purple[500],
    },
    secondary: {
      main: green[500],
    },
  },
});

function App () {

    return (
      <MuiThemeProvider theme={theme}>
        <SearchButton />
      </MuiThemeProvider>
    );
  
}

export default App;
```

## Add a font

Install it

```
npm install fontsource-roboto
```

Then, you can import it in your entry-point.

```
import 'fontsource-roboto';
```

this won't apply to everything, just the Material-UI things

## Add an icon

```
npm install @material-ui/icons
```

```JSX
import { Search, Call } from '@material-ui/icons';
```

then, where you want the icon to go in the HTML, add

```JSX
<Search color="primary"/>
<Call color="secondary"/>
```

Each icon also has a "theme": Filled (default), Outlined, Rounded, Two tone and Sharp. If you want to import the icon component with a theme other than default, append the theme name to the icon name. For example @material-ui/icons/Delete icon with:

Filled theme (default) is exported as `@material-ui/icons/Delete`,
Outlined theme is exported as `@material-ui/icons/DeleteOutlined`,
Rounded theme is exported as `@material-ui/icons/DeleteRounded`,
Twotone theme is exported as `@material-ui/icons/DeleteTwoTone`,
Sharp theme is exported as `@material-ui/icons/DeleteSharp`.


Note: The Material Design specification names the icons using "snake_case" naming (for example delete_forever, add_a_photo), while @material-ui/icons exports the respective icons using "PascalCase" naming (for example DeleteForever, AddAPhoto). There are three exceptions to this naming rule: 3d_rotation exported as ThreeDRotation, 4k exported as FourK, and 360 exported as ThreeSixty.
