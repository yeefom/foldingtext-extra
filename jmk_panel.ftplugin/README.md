# Panel Module for FoldingText 2.0 Plugins

By [Jamie Kowalski](github.com/jamiekowalski/foldingtext-extra)

## Constructor

The event callback functions are passed the event object and the panel object;
but there is no need to capture these in your functions if they are not needed.

None of the options are required; define as many as you need.

Return false from a function to prevent the default behavior (e.g. closing panel
on return).

```javascript
var Panel = require('./panel.js').Panel;

var panel = new Panel({
  className: 'MyPanel',
  placeholder: 'type some text...',
  onReturn: function (event, panel) {},
  onEscape: function (event, panel) {},
  onTextChange: function (event, panel) {},
  onBlur: function (event, panel) {},
  onCommand: function (event, panel) {},
  ignoreWhiteSpace: true,
  addToDOM: true
});
```

`onReturn` — called when the return or enter key is pressed.

`onEscape` — called when escape key is pressed.

`onTextChange` — called when the contents of the panel is changed.

`onBlur` — called when the panel’s text input is unfocused (e.g. by clicking outside the panel).

`onCommand` — called when a Command + key combination is pressed. Use `event.which` to determine which key is pressed.

`ignoreWhiteSpace` — don’t call `onTextChange` when leading or trailing whitespace changes; also trims return value for `panel.value()`.

`addToDOM` — add the panel to the DOM upon creation. Otherwise use the method `panel.addToDOM()`.

## Properties

panel.element — the panel’s containing element.

panel.input — the text `<input>` element of the panel.

## Methods

`panel.addToDOM()` — add panel to DOM (if you did not have it added upon creation)

`panel.show([string] text)` — show the panel (with optional text)

`panel.hide([bool] keepContents)` — hide the panel, optionally specifying whether to keep the contents (defaults to false).

panel.toggle() — toggle the panel.

panel.clear() — clear the contents of the panel.

panel.value() — get the contents of the text input. Unless `ignoreWhiteSpace` in the constructor is set to `false`, leading/trailing white space of the value will be trimmed.