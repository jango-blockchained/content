---
title: omnibox.onInputCancelled
slug: Mozilla/Add-ons/WebExtensions/API/omnibox/onInputCancelled
page-type: webextension-api-event
browser-compat: webextensions.api.omnibox.onInputCancelled
sidebar: addonsidebar
---

Fired when the user has cancelled their interaction with your extension (for example, by clicking outside the address bar).

## Syntax

```js-nolint
browser.omnibox.onInputCancelled.addListener(listener)
browser.omnibox.onInputCancelled.removeListener(listener)
browser.omnibox.onInputCancelled.hasListener(listener)
```

Events have three functions:

- `addListener(listener)`
  - : Adds a listener to this event.
- `removeListener(listener)`
  - : Stop listening to this event. The `listener` argument is the listener to remove.
- `hasListener(listener)`
  - : Check whether `listener` is registered for this event. Returns `true` if it is listening, `false` otherwise.

## addListener syntax

The listener function is passed no parameters.

## Examples

```js
browser.omnibox.onInputCancelled.addListener(() => {
  console.log("The user cancelled the session.");
});
```

{{WebExtExamples}}

## Browser compatibility

{{Compat}}

> [!NOTE]
> This API is based on Chromium's [`chrome.omnibox`](https://developer.chrome.com/docs/extensions/reference/api/omnibox) API.
