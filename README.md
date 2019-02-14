# pHTML Template [<img src="https://phtmlorg.github.io/phtml/logo.svg" alt="pHTML" width="90" height="90" align="right">][phtml]

[![NPM Version][npm-img]][npm-url]
[![Build Status][cli-img]][cli-url]
[![Support Chat][git-img]][git-url]

[pHTML Template] lets you create [templates and slots] that can be used to
define [Custom Elements] in HTML.

```html
<custom-element as-template="custom-p">
  <style>
    :host {
      box-shadow: 0 0 0 .5em #d2d2d2;
      display: block;
    }
  </style>
  <p as-slot="text">...</p>
</custom-element>

<custom-p as-slot-text="Hello, World!"></custom-p>

<!-- becomes -->

<custom-element name="custom-p">
  <template>
    <style>
      :host {
        box-shadow: 0 0 0 .5em #d2d2d2;
        display: block;
      }
    </style>
    <p><slot name="text">...</slot></p>
  </template>
</custom-element>

<custom-p><slot slot="text">Hello, World!</slot></custom-p>
```

## Usage

From the command line, transform HTML files that use template and slot
shorthands:

```bash
npx @phtml/template SOURCE.html TRANSFORMED.html
```

That’s it. A 295 byte script will automatically be added to the HTML that works
in all browsers supporting Custom Elements.

## Advanced Usage

Add [pHTML Template] to your project:

```bash
npm install @phtml/template --save-dev
```

Use [pHTML Template] to process your HTML:

```js
const phtmlTemplate = require('@phtml/template');

phtmlTemplate.process(YOUR_HTML /*, processOptions, pluginOptions */);
```

Or use it as a [pHTML] plugin:

```js
const phtml = require('phtml');
const phtmlTemplate = require('@phtml/template');

phtml([
  phtmlTemplate(/* pluginOptions */)
]).process(YOUR_HTML /*, processOptions */);
```

[pHTML Template] runs in all Node environments, with special instructions for:

| [Node](INSTALL.md#node) | [pHTML CLI](INSTALL.md#phtml-cli) | [Webpack](INSTALL.md#webpack) | [Create React App](INSTALL.md#create-react-app) | [Gulp](INSTALL.md#gulp) | [Grunt](INSTALL.md#grunt) |
| --- | --- | --- | --- | --- | --- |

## Options

### script

The `script` option determines whether scripts will automatically be added to
the HTML that allow you to define [Custom Elements] as templates.

A string value will determine the tag name of the Custom Element used to define
custom elements in HTML.

```bash
npx @phtml/template --script decorate-element
```

```js
phtmlTemplate({ script: 'decorate-element' })
```

```html
<decorate-element as-template="custom-p">
  <style>
    p {
      color: white;
      background-color: #666;
      padding: .25em;
    }
  </style>
  <p as-slot="text">...</p>
</decorate-element>

<custom-p as-slot-text="Hello, World!"></custom-p>

<!-- becomes -->

<decorate-element name="custom-p">
  <template>
    <style>
      p {
        color: white;
        background-color: #666;
        padding: .25em;
      }
    </style>
    <p><slot name="text">...</slot></p>
  </template>
</decorate-element>

<custom-p><slot slot="text">Hello, World!</slot></custom-p>
```

Alternatively, you can add this script to your transformed HTML:

```html
<script src="https://unpkg.com/@phtml/template/browser"></script>
<script>asTemplate('decorate-element')</script>
```

[cli-img]: https://img.shields.io/travis/phtmlorg/phtml-template.svg
[cli-url]: https://travis-ci.org/phtmlorg/phtml-template
[git-img]: https://img.shields.io/badge/support-chat-blue.svg
[git-url]: https://gitter.im/phtmlorg/phtml
[npm-img]: https://img.shields.io/npm/v/@phtml/template.svg
[npm-url]: https://www.npmjs.com/package/@phtml/template

[Custom Elements]: https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements
[pHTML]: https://github.com/phtmlorg/phtml
[pHTML Template]: https://github.com/phtmlorg/phtml-template
[templates and slots]: https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_templates_and_slots
