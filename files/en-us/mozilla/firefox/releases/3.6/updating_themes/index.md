---
title: Updating themes for Firefox 3.6
slug: Mozilla/Firefox/Releases/3.6/Updating_themes
page-type: guide
sidebar: firefox
---

This article intends to help theme authors update Firefox-3.5-compatible themes for Firefox 3.6 compatibility.

## Chrome registration change

[`contents.rdf` is not supported anymore](https://www.oxymoronical.com/blog/2009/06/Farewell-contentsrdf/), you need to use `chrome.manifest` instead.

## Empty text styling

XUL textboxes don't have the `empty` attribute anymore, but `isempty` instead. So instead of `textbox[empty="true"]`, you need to use `textbox[isempty="true"]`.

## Right-to-left UI support

The `[chromedir="rtl"]` and `[chromedir="ltr"]` selectors have been obsoleted and won't work anymore on most elements. Instead, you need to use the new {{ cssxref(":-moz-locale-dir_rtl", ":-moz-locale-dir(rtl)") }} and {{ cssxref(":-moz-locale-dir_ltr", ":-moz-locale-dir(ltr)") }} selectors. See also: [Making sure your theme works with RTL locales](https://web.archive.org/web/20210509011412/https://developer.mozilla.org/en-US/docs/Archive/Themes/Making_sure_your_theme_works_with_RTL_locales).

## Cross-platform tabbed browser styling

The tabbed browser implementation no longer has a Mac-specific `tabs-closebutton-box`; instead, all platforms use the same names to identify the components of the tab strip.

## Full Screen toolbar button

There's a new [Full Screen toolbar button](https://bugzil.la/206544) available from the Customize Toolbar dialog.

## See also

- [MozillaZine forum: Mozilla 1.9.2 / Firefox 3.6 theme changes](https://forums.mozillazine.org/viewtopic.php?f=18&t=975065)
- [Themes](https://web.archive.org/web/20210422190409/https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/Themes)
- [Building a theme](https://web.archive.org/web/20210506064733/https://developer.mozilla.org/en-US/docs/Archive/Themes/Building_a_Theme)
