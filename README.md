<div align="center" style="text-align: center;">
  <h1 style="border-bottom: none;">app-datepicker</h1>

  <p>Datepicker element built with lit-element and Material Design 2</p>
</div>

<hr />

<a href="https://www.buymeacoffee.com/RLmMhgXFb" target="_blank" rel="noopener noreferrer"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 20px !important;width: auto !important;" ></a>
[![tippin.me][tippin-me-badge]][tippin-me-url]
[![Follow me][follow-me-badge]][follow-me-url]

[![Version][version-badge]][version-url]
[![lit-element][lit-element-version-badge]][lit-element-url]
[![Node version][node-version-badge]][node-version-url]
[![MIT License][mit-license-badge]][mit-license-url]

[![Downloads][downloads-badge]][downloads-url]
[![Total downloads][total-downloads-badge]][downloads-url]
[![Packagephobia][packagephobia-badge]][packagephobia-url]
[![Bundlephobia][bundlephobia-badge]][bundlephobia-url]

[![CircleCI][circleci-badge]][circleci-url]
[![Dependency Status][daviddm-badge]][daviddm-url]

[![codebeat badge][codebeat-badge]][codebeat-url]
[![Language grade: JavaScript][lgtm-badge]][lgtm-url]
[![Code of Conduct][coc-badge]][coc-url]

> A different way of `datepicker`-ing on the web.
>
> 🛠 While it is still in RC release, feel free to try it out.

This marks another completion of an important milestone of `app-datepicker` with all the love from the [Web Components community][web-components-community-url] in making this element great and wonderful. As Web Components getting more and more traction and better at providing a web standard way of creating shareable components, it plays an important role in the JavaScript community as many developers depend on a plethora of development tools written in JavaScript for the web to create a better developer experience when developing a library, a component, or even a large scalable application.

![screen shot 2019-01-30 at 12 49 30](https://user-images.githubusercontent.com/10607759/51959002-857c1100-248d-11e9-8d1a-9abbafdb2385.png)

Today, `app-datepicker` has been completely rewritten to adapt to the best of both worlds by leveraging the modern technologies the community most familiar with since year 2018.

The following are the list of tools used that makes it shine:

  1. [TypeScript][typescript-url]
  2. [lit-element][lit-element-url]

## Table of contents <!-- omit in toc -->

- [Pre-requisite](#pre-requisite)
- [Installation](#installation)
- [How to use](#how-to-use)
- [Browser compatibility](#browser-compatibility)
- [API references](#api-references)
- [Demo](#demo)
- [Older versions](#older-versions)
- [License](#license)

## Pre-requisite

- [Node.js][node-js-url] >= 10.18.1
- [NPM][npm-url] >= 6.13.4 ([NPM][npm-url] comes with [Node.js][node-js-url] so there is no need to install separately.)
- [lit-element][lit-element-url] >= 2.2.1
- [TypeScript][typescript-url] >= 3.7.4

## Installation

- NPM

  ```sh
  $ npm i app-datepicker@next
  ```

- Alternatively, it can be downloaded from any of the following awesome CDNs:

  1. [jsdelivr (ESM)][jsdelivr-url]
  2. [unpkg (ESM)][unpkg-url]

## How to use

**Polyfills**

Please make sure you have all these features available on the browsers you are supporting. If no, please consider polyfilling in order to run the datepicker element.

* [Array.prototype.find]
* [Intl.DateTimeFormat]

The following snippet shows a simple script used in the demo to load polyfills via feature detection on different browsers:

```html
<script>
  if (null == Array.prototype.find) {
    Object.defineProperty(Array.prototype, 'find', {
      value: function arrayFind(cb) {
        const filtered = this.filter(cb);
        return !filtered.length ? void 0 : filtered[0];
      }
    });
  }

  if (!window.Intl) {
    const wa = document.createElement('script');
    /** FIXME: Pin package version due to https://github.com/andyearnshaw/Intl.js/issues/256 */
    wa.src = 'https://unpkg.com/intl@1.2.4/dist/Intl.complete.js';
    wa.onload = () => console.info('🌐 Intl polyfill loaded');
    wa.onerror = console.error;
    document.head.appendChild(wa);
  }

  if (!(Element.prototype.animate)) {
    const wa = document.createElement('script');
    wa.src = 'https://unpkg.com/web-animations-js@latest/web-animations.min.js';
    wa.onload = () => console.info('⚒ Web Animations Next lite loaded');
    wa.onerror = console.error;
    document.head.appendChild(wa);
  }

</script>
```

**my-app.ts**

```ts
/**
 * Say you've already installed the element via NPM, simply import the package to your application.
 * Here I'm using `lit-element` for developing my application.
 */
import { css, customElement, html, LitElement } from 'lit-element';
import 'app-datepicker';

@customElement(MyApp.is)
export class MyApp extends LitElement {
  static is() { return 'my-app'; }

  static styles = [
    css`
    :host {
      display: block;
    }

    * {
      box-sizing: border-box;
    }
    `
  ];

  protected render() {
    return html`<app-datepicker></app-datepicker>`;
  }
}
```

**index.html**

```html
<!doctype html>
<html>
  <!-- Using ES modules to load the app -->
  <script type="module" src="/my-app.js"></script>
  ...
  <body>
    <my-app>
      <!-- <AppDatepicker> will be rendered when <MyApp> loads. -->
    </my-app>
  </body>
  ...
</html> 
```

## Browser compatibility

Both `app-datepicker` and `app-datepicker-dialog` works in all major browsers (Chrome, Firefox, IE, Edge, and Safari).

[Heavily tested](/.circleci/config.yml) on the following browsers:

| Name | OS |
| --- | --- |
| Edge 17 | Windows 10 |
| Edge 15 | Windows 10 |
| Internet Explorer 11 | Windows 10 |
| Safari 10.1 | Mac OS 10.12 |
| Safari 9 | Mac OS X 10.11 |
| Firefox 62 (w/o native Shadow DOM) | macOS Mojave (10.14) |
| Chrome 69 ([WRE 2019][wre-2019-url]) | Windows 10 |

## API references

- [AppDatepicker][app-datepicker-api-reference-url]
- [AppDatepickerDialog][app-datepicker-dialog-api-reference-url]

## Demo

[Configurable demo powered by Firebase]

## Older versions

Meantime, feel free to check the older version out at:

  1. [`2.x` branch][2-x-url] - Built with Material Design and [Polymer 2][polymer-2-url], published at Bower.
  2. [`3.x` branch][3-x-url] - Built with Material Design and [Polymer 3][polymer-3-url], published at NPM.

## License

[MIT License](http://motss.mit-license.org/) © Rong Sen Ng

<!-- References -->
[2-x-url]: https://github.com/motss/app-datepicker/tree/2.x?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[3-x-url]: https://github.com/motss/app-datepicker/tree/3.x?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[app-datepicker-api-reference-url]: /api-references.md#appdatepicker
[app-datepicker-dialog-api-reference-url]: /api-references.md#appdatepickerdialog
[Array.prototype.find]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find
[Configurable demo powered by Firebase]: https://motss-app.web.app/demo/app-datepicker/app-datepicker.html
[Intl.DateTimeFormat]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/DateTimeFormat
[jsdelivr-url]: https://www.jsdelivr.com/package/npm/app-datepicker?version=next&amp;utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[lit-element-url]: https://github.com/Polymer/lit-element?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[material-design-2-url]: https://material.io/design/?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[node-js-url]: https://nodejs.org?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[node-releases-url]: https://nodejs.org/en/download/releases?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[npm-url]: https://www.npmjs.com?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[polymer-2-url]: https://polymer-library.polymer-project.org/2.0/docs/devguide/feature-overview?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[polymer-3-url]: https://polymer-library.polymer-project.org/3.0/docs/devguide/feature-overview?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[typescript-url]: https://github.com/Microsoft/TypeScript?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[unpkg-url]: https://unpkg.com/app-datepicker@next/?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[web-components-community-url]: https://www.webcomponents.org?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[wre-2019-url]: https://www.deepcrawl.com/blog/news/what-version-of-chrome-is-google-actually-using-for-rendering
[wre-url]: https://developers.google.com/search/docs/guides/rendering

<!-- Browsers logo -->
[ie-img-url]: https://cdn.jsdelivr.net/npm/@browser-logos/internet-explorer_9-11@1.1.3/internet-explorer_9-11_64x64.png

<!-- MDN -->
[map-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map?utm_source=github.com&amp;utm_medium=referral
[string-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String?utm_source=github.com&amp;utm_medium=referral
[object-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object?utm_source=github.com&amp;utm_medium=referral
[number-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number?utm_source=github.com&amp;utm_medium=referral
[boolean-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean?utm_source=github.com&amp;utm_medium=referral
[html-style-element-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/API/HTMLStyleElement?utm_source=github.com&amp;utm_medium=referral
[promise-mdn-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise?utm_source=github.com&amp;utm_medium=referral

<!-- Badges -->
[tippin-me-badge]: https://badgen.net/badge/%E2%9A%A1%EF%B8%8Ftippin.me/@igarshmyb/F0918E
[follow-me-badge]: https://flat.badgen.net/twitter/follow/igarshmyb?icon=twitter

[version-badge]: https://flat.badgen.net/npm/v/app-datepicker/next?icon=npm
[lit-element-version-badge]: https://flat.badgen.net/npm/v/lit-element/latest?icon=npm&label=lit-element
[node-version-badge]: https://flat.badgen.net/npm/node/app-datepicker
[mit-license-badge]: https://flat.badgen.net/npm/license/app-datepicker

[downloads-badge]: https://flat.badgen.net/npm/dm/app-datepicker
[total-downloads-badge]: https://flat.badgen.net/npm/dt/app-datepicker?label=total%20downloads
[packagephobia-badge]: https://flat.badgen.net/packagephobia/install/app-datepicker%40next
[bundlephobia-badge]: https://flat.badgen.net/bundlephobia/minzip/app-datepicker@next

[circleci-badge]: https://flat.badgen.net/circleci/github/motss/app-datepicker?icon=circleci
[daviddm-badge]: https://flat.badgen.net/david/dep/motss/app-datepicker

[codebeat-badge]: https://codebeat.co/badges/3a212108-43cd-4a1f-ab2c-fe890ad734b6
[lgtm-badge]: https://flat.badgen.net/lgtm/grade/javascript/g/motss/app-datepicker?icon=lgtm
[coc-badge]: https://flat.badgen.net/badge/code%20of/conduct/pink

<!-- Links -->
[tippin-me-url]: https://tippin.me/@igarshmyb
[follow-me-url]: https://twitter.com/igarshmyb?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker

[version-url]: https://www.npmjs.com/package/app-datepicker/v/next?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[node-version-url]: https://nodejs.org/en/download?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[mit-license-url]: https://github.com/motss/app-datepicker/blob/master/LICENSE?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker

[downloads-url]: http://www.npmtrends.com/app-datepicker?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[packagephobia-url]: https://packagephobia.now.sh/result?p=app-datepicker%40next&utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[bundlephobia-url]: https://bundlephobia.com/result?p=app-datepicker@next&amp;utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker

[circleci-url]: https://circleci.com/gh/motss/app-datepicker/tree/master?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[daviddm-url]: https://david-dm.org/motss/app-datepicker?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker

[codebeat-url]: https://codebeat.co/projects/github-com-motss-app-datepicker-master-68699d41-3539-4c5f-81df-c9202be34919?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[lgtm-url]: https://lgtm.com/projects/g/motss/app-datepicker/context:javascript?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker
[coc-url]: https://github.com/motss/app-datepicker/blob/master/code-of-conduct.md?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=motss/app-datepicker

<!-- [intl-polyfill-url]: https://github.com/andyearnshaw/Intl.js -->
<!-- [web-animations-js-polyfill-url]: https://www.npmjs.com/package/web-animations-js -->
<!-- [polymer-3-browser-support-url]: https://polymer-library.polymer-project.org/3.0/docs/browsers -->
