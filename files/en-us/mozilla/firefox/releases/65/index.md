---
title: Firefox 65 for developers
short-title: Firefox 65
slug: Mozilla/Firefox/Releases/65
page-type: firefox-release-notes
sidebar: firefox
---

This article provides information about the changes in Firefox 65 that will affect developers. Firefox 65 was released on January 29, 2019.

## Changes for web developers

### Developer tools

- The [Flexbox inspector](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/examine_flexbox_layouts/index.html) is now enabled by default.
- Support has been added to the [JavaScript Debugger](https://firefox-source-docs.mozilla.org/devtools-user/debugger/index.html) for XHR Breakpoints ([Firefox bug 821610](https://bugzil.la/821610)).
- Right-click on an item in the accessibility tree from the Accessibility viewer to [print it as JSON](https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/index.html#print-accessibility-tree-to-json) to the JSON viewer.
- The [color contrast](https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/index.html#color-contrast) display of the Accessibility Picker has been updated so that if a text's background is complex (e.g., a gradient or complex image), it shows a range of color contrast values.
- The Headers tab of the [Network Monitor](https://firefox-source-docs.mozilla.org/devtools-user/network_monitor/index.html) now displays the Referrer Policy for the selected request ([Firefox bug 1496742](https://bugzil.la/1496742)).
- When displaying stack traces (e.g., in console logs or the JavaScript debugger), calls to framework methods are identified and collapsed by default, making it easier to home in on your code.
- In the same fashion as native terminals, you can now use reverse search to find entries in your JavaScript console history (`F9` on Windows/Linux or `Ctrl` + `R` on macOS, then type a search term, followed by `Ctrl` + `R`/`Ctrl` + `S` to toggle through results).
- The JavaScript console's `$0` shortcut (references the currently inspected element on the page) now has autocomplete available, so for example you could type `$0.te` to get autocomplete suggestions for properties like `$0.textContent`.
- The edits you make in the Rules view of the Inspector are now listed in the Changes panel ([Firefox bug 1503920](https://bugzil.la/1503920)).

### HTML

- Events are now dispatched on disabled HTML elements, i.e., {{htmlelement("button")}}, {{htmlelement("fieldset")}}, {{htmlelement("input")}}, {{htmlelement("select")}}, and {{htmlelement("textarea")}} elements with `disabled` attributes set on them ([Firefox bug 329509](https://bugzil.la/329509)).
- Removing the `src` attribute of an {{htmlelement("iframe")}} element now causes `about:blank` to be loaded into it, giving it parity with Chrome and Safari ([Firefox bug 1507842](https://bugzil.la/1507842)). Previously removing `src` had no effect on the `iframe` content.
- We have added support for the [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/script#referrerpolicy) attribute on {{htmlelement("script")}} elements ([Firefox bug 1460920](https://bugzil.la/1460920)).

### CSS

- The {{cssxref("image-rendering")}} property's `crisp-edges` value has now been unprefixed ([Firefox bug 1496617](https://bugzil.la/1496617)).
- A {{cssxref("scrollbar-color")}} value of `auto` now resolves to `auto`, rather than two colors ([Firefox bug 1501418](https://bugzil.la/1501418)).
- The `break-*` properties have been implemented, and the legacy `page-break-*` properties have been aliased to them ([Firefox bug 775618](https://bugzil.la/775618)):
  - {{cssxref("break-before")}} is now an alias for {{cssxref("page-break-before")}}.
  - {{cssxref("break-after")}} is now an alias for {{cssxref("page-break-after")}}.
  - {{cssxref("break-inside")}} is now an alias for {{cssxref("page-break-inside")}}.

- The {{cssxref("overflow-wrap")}} property's `anywhere` value has been implemented ([Firefox bug 1505786](https://bugzil.la/1505786)).
- The new step position keywords `jump-start`, `jump-end`, `jump-none`, and `jump-both` — usable inside the [`steps()` timing function](/en-US/docs/Web/CSS/easing-function/steps) — have been implemented ([Firefox bug 1496619](https://bugzil.la/1496619)). This also coincides with the removal of the `frames()` timing function, which was the previous way of implementing such functionality, now deprecated.
- Some new {{cssxref("appearance", "-webkit-appearance")}} values have been added, for compatibility with other browsers. In particular:
  - `meter`, which is now used as the default value for {{htmlelement("meter")}} elements in UA stylesheets. The existing value `meterbar` is now an alias for `meter` ([Firefox bug 1501483](https://bugzil.la/1501483)).
  - `progress-bar`, which is now used as the default value for {{htmlelement("progress")}} elements in UA stylesheets. The existing value `progressbar` is now an alias for `progress-bar` ([Firefox bug 1501506](https://bugzil.la/1501506)).
  - `textarea`, which is now used as the default value for {{htmlelement("textarea")}} elements in UA stylesheets. The existing value `textfield-multiline` is now an alias for `textarea` ([Firefox bug 1507905](https://bugzil.la/1507905)).

- The behavior of {{cssxref("user-select")}} has been changed to make it align more with other browsers ([Firefox bug 1506547](https://bugzil.la/1506547)). Specifically:
  - `user-select: all` set on an element no longer overrides other values of `user-select` set on children of that element. So for example in the following snippet:

    ```html
    <div style="-webkit-user-select: all">
      All
      <div style="-webkit-user-select: none">None</div>
    </div>
    ```

    The `<div>` with `none` set on it is now non-selectable. Previously this value would have been overridden by the `all` value set on the parent element.

  - non-`contenteditable` elements nested inside `contenteditable` elements are now selectable.
  - `user-select` now behaves consistently inside and outside shadow DOM.
  - The proprietary `-moz-text` value has been removed.

- CSS environment variables (the {{cssxref("env", "env()")}} function) have been implemented ([Firefox bug 1462233](https://bugzil.la/1462233)).

#### Removals

- The `layout.css.shape-outside.enabled` pref has been removed; {{cssxref("shape-outside")}}, {{cssxref("shape-margin")}}, and {{cssxref("shape-image-threshold")}} can no longer be disabled in `about:config` ([Firefox bug 1504387](https://bugzil.la/1504387)).
- Several Firefox-only values of the {{cssxref("user-select")}} property have been removed — `-moz-all`, `-moz-text`, `tri-state`, `element`, `elements`, and `toggle`. See [Firefox bug 1492958](https://bugzil.la/1492958) and [Firefox bug 1506547](https://bugzil.la/1506547).
- As mentioned above, the `frames()` timing function has been removed ([Firefox bug 1496619](https://bugzil.la/1496619)).

### SVG

_No changes._

### JavaScript

- {{jsxref("Intl/RelativeTimeFormat", "Intl.RelativeTimeFormat")}} is now supported ([Firefox bug 1504334](https://bugzil.la/1504334)).
- Strings now have a maximum {{jsxref("String/length","length","", 1)}} of `2**30 - 2` (\~1GB) instead of `2**28 - 1` (\~256MB) ([Firefox bug 1509542](https://bugzil.la/1509542)).
- The {{jsxref("globalThis")}} property, which always refers to the top-level global object, has been implemented ([Firefox bug 1317422](https://bugzil.la/1317422)).

### APIs

#### New APIs

- {{domxref("Streams_API/Using_readable_streams", "Readable Streams", "", "1")}} have been enabled by default ([Firefox bug 1505122](https://bugzil.la/1505122)).
- The {{domxref("Storage_Access_API", "Storage Access API", "", "1")}} has been enabled by default ([Firefox bug 1513021](https://bugzil.la/1513021)).

#### DOM

- {{domxref("Performance.toJSON()")}} has been exposed to {{domxref("Web_Workers_API", "Web Workers", "", "1")}} ([Firefox bug 1504958](https://bugzil.la/1504958)).
- {{domxref("XMLHttpRequest")}} requests will now throw a `NetworkError` if the requested content type is a `Blob`, and the request method is not `GET` ([Firefox bug 1502599](https://bugzil.la/1502599)).
- The `-moz-` prefixed versions of many of the {{domxref("Fullscreen API", "", "", "1")}} features have been deprecated, and will now display deprecation warnings in the JavaScript console when encountered ([Firefox bug 1504946](https://bugzil.la/1504946)).
- {{domxref("Window.createImageBitmap()")}} and {{domxref("WorkerGlobalScope.createImageBitmap()")}} now supports SVG images ({{domxref("SVGImageElement")}}) as an image source ([Firefox bug 1500768](https://bugzil.la/1500768)).

#### DOM events

- Going forward, only one {{domxref("Window.open()")}} call is allowed per event ([Firefox bug 675574](https://bugzil.la/675574)).
- The [`keyup`](/en-US/docs/Web/API/Element/keyup_event) and [`keydown`](/en-US/docs/Web/API/Element/keydown_event) events are now fired during IME composition, to improve cross-browser compatibility for CJKT users ([Firefox bug 354358](https://bugzil.la/354358).

#### Web workers

- {{domxref("SharedWorkerGlobalScope.connect_event", "SharedWorkerGlobalScope.connect")}}'s event object is a {{domxref("MessageEvent")}} instance — its `data` property is now an empty string value rather than `null` ([Firefox bug 1508824](https://bugzil.la/1508824)).

#### Fetch and Service workers

- The {{domxref("Response.redirect_static", "Response.redirect()")}} method now correctly throws a `TypeError` if a non-valid URL is specified as the first parameter ([Firefox bug 1503276](https://bugzil.la/1503276)).
- The {{domxref("ServiceWorkerContainer.register()")}} and {{domxref("WorkerGlobalScope.importScripts()")}} (when used by a service worker) methods will now accept any files with a valid [JavaScript MIME type](/en-US/docs/Web/HTTP/Guides/MIME_types#textjavascript) ([Firefox bug 1354577](https://bugzil.la/1354577)).
- The {{domxref("FetchEvent.replacesClientId")}} and {{domxref("FetchEvent.resultingClientId")}} properties are now supported ([Firefox bug 1264177](https://bugzil.la/1264177)).
- The {{domxref("ServiceWorkerGlobalScope.messageerror_event", "ServiceWorkerGlobalScope.onmessageerror")}} and {{domxref("ServiceWorkerContainer.messageerror_event", "ServiceWorkerContainer.onmessageerror")}} handler properties have been implemented ([Firefox bug 1399446](https://bugzil.la/1399446)).
- The {{httpheader("Origin")}} header is no longer set on Fetch requests with a method of {{HTTPMethod("HEAD")}} or {{HTTPMethod("GET")}} ([Firefox bug 1508661](https://bugzil.la/1508661)).

#### Media, Web Audio, and WebRTC

- The {{domxref("WebRTC API", "WebRTC", "", "1")}} {{domxref("RTCIceCandidateStats")}} dictionary has been updated according to the latest spec changes ([Firefox bug 1324788](https://bugzil.la/1324788), [Firefox bug 1489040](https://bugzil.la/1489040); RTCIceCandidateStats has been updated to the latest spec for more details on exactly what has changed).
- The {{domxref("MediaRecorder")}} `pause` and `resume` events (and their corresponding event handler properties were not previously implemented, even though compatibility tables claimed they had been. They have now been implemented ([Firefox bug 1458538](https://bugzil.la/1458538), [Firefox bug 1514016](https://bugzil.la/1514016)).

#### Canvas and WebGL

- The {{domxref("WebGL API", "WebGL", "", "1")}} {{domxref("EXT_texture_compression_bptc")}} and {{domxref("EXT_texture_compression_rgtc")}} texture compression extensions have been exposed to WebGL1 and WebGL2 contexts ([Firefox bug 1507263](https://bugzil.la/1507263)).

#### Removals

- [Mutation events](/en-US/docs/Web/API/MutationEvent) have been disabled in shadow trees ([Firefox bug 1489858](https://bugzil.la/1489858)).
- The non-standard {{domxref("MediaStream")}} property `currentTime` has been removed ([Firefox bug 1502927](https://bugzil.la/1502927)).
- The `dom.webcomponents.shadowdom.enabled` and `dom.webcomponents.customelements.enabled` prefs have been removed — Shadow DOM and Custom Elements can no longer be disabled in `about:config` ([Firefox bug 1503019](https://bugzil.la/1503019)).
- The non-standard DOM `text` event — fired to notify the browser editor UI of IME composition string data and selection range — has been removed ([Firefox bug 1288640](https://bugzil.la/1288640)).
- The {{domxref("Element/keypress_event", "keypress")}} event is no longer fired for [non-printable keys](/en-US/docs/Web/API/KeyboardEvent/keyCode#non-printable_keys_function_keys) ([Firefox bug 968056](https://bugzil.la/968056)), except for the `Enter` key, and the `Shift` + `Enter` and `Ctrl` + `Enter` key combinations (these were kept for cross-browser compatibility purposes).

### Security

- Additional CORS restrictions are now being enforced on allowable request headers ([Firefox bug 1483815](https://bugzil.la/1483815), see also [whatwg fetch issue 382: CORS-safelisted request headers should be restricted according to RFC 7231](https://github.com/whatwg/fetch/issues/382) for more details).

### Networking

_No changes._

### Plugins

_No changes._

### WebDriver conformance (Marionette)

#### API changes

- `WebDriver:ElementSendKeys` now handles `<input type=file>` more relaxed for interactability checks, and allows those elements to be hidden without raising a `not interactable` error anymore. If a strict interactability check is wanted the capability `strictFileInteractability` can be used ([Firefox bug 1502864](https://bugzil.la/1502864)).

#### Bug fixes

- The window manipulation commands `WebDriver:FullscreenWindow`, `WebDriver:MinimizeWindow`, `WebDriver:MaximizeWindow`, and `WebDriver:SetWindowRect` have been made more stable ([Firefox bug 1492499](https://bugzil.la/1492499)). It means that under special conditions they don't cause an infinite hang anymore, but instead timeout after 5s if the requested window state cannot be reached ([Firefox bug 1521527](https://bugzil.la/1521527)).
- `WebDriver:ElementClick` now correctly calculates the center point of the element to click, which allows interactions with dimensions of 1x1 pixels ([Firefox bug 1499360](https://bugzil.la/1499360)).

#### Others

- For `unexpected alert open` errors more informative messages are provided ([Firefox bug 1502268](https://bugzil.la/1502268)).

### Other

- Support for [WebP](/en-US/docs/Glossary/WebP) images has been added ([Firefox bug 1294490](https://bugzil.la/1294490)).
  - In addition, to facilitate cross-browser compatibility in certain situations the WebP MIMEType (`image/webp`) has been added to the standard HTTP Request {{httpheader("Accept")}} header for HTML files ([Firefox bug 1507691](https://bugzil.la/1507691)).

- The AV1 codec is now supported by default on Windows ([Firefox bug 1452146](https://bugzil.la/1452146)).

## Changes for add-on developers

### API changes

#### Tabs

- The {{WebExtAPIRef("tabs", "tabs API", "", "1")}} has been enhanced to support tab successors — a tab can have a successor assigned to it, which is the ID of the tab that will be active once it is closed ([Firefox bug 1500479](https://bugzil.la/1500479), also see [this blog post](https://qiita.com/piroor/items/ea7e727735631c45a366) for more information). In particular:
  - The {{WebExtAPIRef("tabs.Tab")}} type now has a `successorId` property, which can be used to store/retrieve the ID of the tab's successor.
  - The {{WebExtAPIRef("tabs.onActivated")}} event listener's callback has a new parameter available, `previousTabId`, which contains the ID of the previous activated tab, if it is still open.
  - The {{WebExtAPIRef("tabs.update()")}} function's `updateProperties` object has a new optional property available on it, `successorTabId`, so can be used to update it.
  - `successorTabId` is also returned by functions like {{WebExtAPIRef("tabs.get()")}} and {{WebExtAPIRef("tabs.query()")}}.
  - The new function `tabs.moveInSuccession()` allows manipulation of tab successors in bulk.

### Manifest changes

_No changes._

### Other

- The `headerURL`/`theme_frame` properties for [WebExtension themes](/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/theme) are now supported on Firefox for Android ([Firefox bug 1429488](https://bugzil.la/1429488)).

## See also

- Hacks release post: [Firefox 65: WebP support, Flexbox Inspector, new tooling & platform updates](https://hacks.mozilla.org/2019/01/firefox-65-webp-flexbox-inspector-new-tooling/)
