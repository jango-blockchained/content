---
title: HTML slot global attribute
short-title: slot
slug: Web/HTML/Reference/Global_attributes/slot
page-type: html-attribute
browser-compat: html.global_attributes.slot
sidebar: htmlsidebar
---

The **`slot`** [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) assigns a slot in a [shadow DOM](/en-US/docs/Web/API/Web_components/Using_shadow_DOM) shadow tree to an element: An element with a `slot` attribute is assigned to the slot created by the {{HTMLElement("slot")}} element whose [`name`](/en-US/docs/Web/HTML/Reference/Elements/slot#name) attribute's value matches that `slot` attribute's value. You can have multiple elements assigned to the same slot by using the same slot name. Elements without a `slot` attribute are assigned to the unnamed slot, if one exists.

For examples, see our [Using templates and slots](/en-US/docs/Web/API/Web_components/Using_templates_and_slots) guide.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- HTML [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- HTML {{HTMLElement("slot")}} element
- HTML {{HTMLElement("template")}} element
- CSS {{CSSXref("::slotted")}} pseudo-element
- [CSS scoping](/en-US/docs/Web/CSS/CSS_scoping) module
- [Web components](/en-US/docs/Web/API/Web_components)
