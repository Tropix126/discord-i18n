# discord-i18n
A SCSS database of every discord i18n string for theming purposes.

# What the hell is this?
This is a ~16mb SCSS file with about 180 thousand lines that contains every string that's translated through discord. It was pulled using the following snippet utilizing Powercord's API.
```
JSON.stringify(Object.keys(require('powercord/webpack').i18n._proxyContext.messages).sort().reduce((acc, key) => {
  acc[key] = require('powercord/webpack').i18n._proxyContext.messages[key];
  return acc;
}, {}), null, 2);
```
This outputted a JSON string which I then converted to SCSS variables.

# Why in gods name did you make this?
Several elements in discord are currently only accessable through the `aria-label` attribute which discord uses. The catch: `aria-label` attributes are automatically translated by discord's translation system. This meant users would either have to choose limiting their themes' features, or dropping support for foreign languages. This isn't exactly a great decision. The purpose of this database is not to be simply imported. In fact, **PLEASE DO NOT IMPORT THIS WHOLE THING FOR THE LOVE OF GOD**. It will compeltely bomb your loading times to most likely upwards of a minute. To use this file, ONLY take the strings you need, and impliment them one by one from each language as you go.
