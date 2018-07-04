# editor-widget

Editor widget for blessed used by the [slap](https://github.com/slap-editor/slap) text editor

Incorporating fixes and changes:

- Edited code reformatted with prettier. Might be a problem in the future, but I can't be bothered formatting on the basis of the non-specs of the original project.
- Using `--inspect` and `--inspect-brk` to support Node versions. [Pull request](https://github.com/slap-editor/editor-widget/pull/243)

## Example

```js
const blessed = require('blessed');
const Editor = require('editor-widget');

const screen = blessed.screen({
  smartCSR: true,
  title: 'editor-widget example'
});
const editor = new Editor({
  // normal blessed widget, use like you would any other blessed element
  parent: screen,
  top: 0,
  left: 0,
  width: '100%',
  height: '100%'
});

const filePath = './file.txt';
editor.open(filePath);
screen.key(['C-s'], (ch, key) => {
  editor.save(filePath);
});

screen.key(['escape', 'q', 'C-c'], (ch, key) => {
  process.exit(0);
});
screen.render();
```

## In use

Here are some projects that use editor-widget:

- [slap](https://github.com/slap-editor/slap)
- [derhuerst/js-playgrounds](https://github.com/derhuerst/js-playgrounds)
