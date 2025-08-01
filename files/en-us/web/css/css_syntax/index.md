---
title: CSS syntax
slug: Web/CSS/CSS_syntax
page-type: css-module
spec-urls: https://drafts.csswg.org/css-syntax
sidebar: cssref
---

The **CSS syntax** module describes, in general terms, the structure and syntax of cascading stylesheets, or CSS. It defines CSS as the language for describing the rendering of structured documents (such as HTML and XML), on the web and elsewhere.

This module doesn't define any properties, [data types](/en-US/docs/Web/CSS/CSS_Values_and_Units/CSS_data_types), [functions](/en-US/docs/Web/CSS/CSS_Values_and_Units/CSS_Value_Functions), or [at-rules](/en-US/docs/Web/CSS/CSS_syntax/At-rule). Rather, it elaborates on how all of these features should be defined and how user agents should parse CSS.

## At-rules

- none

> [!NOTE]
> The module explicitly states that {{cssxref("@charset")}} is not an actual at-rule, but rather an unrecognized legacy rule that should be omitted when a stylesheet is grammar-checked. The only valid `@charset` usage is at the very beginning of a stylesheet, where it is interpreted as a special byte sequence stripped before processing the content.

## Reference

### Key concepts

- {{cssxref("at-rule")}}
- [character escaping](/en-US/docs/Web/CSS/custom-ident#escaping_characters)
- [CSS comments](/en-US/docs/Web/CSS/CSS_syntax/Comments)
- [CSS declaration](/en-US/docs/Web/API/CSS_Object_Model/CSS_Declaration)
- [CSS declaration block](/en-US/docs/Web/API/CSS_Object_Model/CSS_Declaration_Block)
- [CSS function](/en-US/docs/Web/CSS/CSS_Values_and_Units/CSS_Value_Functions)
- [invalid](/en-US/docs/Web/CSS/CSS_syntax/Error_handling)
- [style rule](/en-US/docs/Web/API/CSSStyleRule)

### Glossary terms

- {{glossary("CSS_Descriptor", "CSS descriptor")}}
- {{glossary("parse")}}
- {{glossary("stylesheet")}}
- {{glossary("whitespace")}}

## Guides

- [Introduction to CSS syntax: declarations, rulesets, and statements](/en-US/docs/Web/CSS/CSS_syntax/Syntax)
  - : Explains the overall CSS syntax and how declarations, declaration blocks, rulesets, and statements form the style rules.

- [Value definition syntax](/en-US/docs/Web/CSS/CSS_Values_and_Units/Value_definition_syntax)
  - : Explains the formal grammar for defining valid values for CSS properties and functions, along with semantic constraints. A guide for understanding CSS component value types, combinators, and multipliers.

- [CSS error handling](/en-US/docs/Web/CSS/CSS_syntax/Error_handling)
  - : Overview of how browsers handle invalid CSS.

- [Learn CSS first steps: CSS syntax](/en-US/docs/Learn_web_development/Core/Styling_basics/What_is_CSS#css_syntax_basics)
  - : Introductory guide to CSS, including an introduction to CSS syntax.

## Related concepts

[CSS selectors](/en-US/docs/Web/CSS/CSS_selectors) module:

- [CSS specificity](/en-US/docs/Web/CSS/CSS_cascade/Specificity)

[CSS cascading and inheritance](/en-US/docs/Web/CSS/CSS_cascade) module:

- {{cssxref("@import")}} at-rule
- {{cssxref("important")}} flag
- [Initial values](/en-US/docs/Web/CSS/CSS_cascade/Value_processing#initial_value)
- [Computed values](/en-US/docs/Web/CSS/CSS_cascade/Value_processing#computed_value)
- [Used values](/en-US/docs/Web/CSS/CSS_cascade/Value_processing#used_value)
- [Actual values](/en-US/docs/Web/CSS/CSS_cascade/Value_processing#actual_value)
- [CSS inheritance](/en-US/docs/Web/CSS/CSS_cascade/Inheritance)
- {{Glossary("Property/CSS", "CSS property")}}

[CSS custom properties for cascading variables](/en-US/docs/Web/CSS/CSS_cascading_variables) module:

- [custom property (`--*`)](/en-US/docs/Web/CSS/--*)
- {{cssxref("var")}} function

[CSS conditional rules](/en-US/docs/Web/CSS/CSS_conditional_rules) module:

- {{cssxref("@media")}} at-rule
- {{cssxref("@supports")}} at-rule

[CSS Object Model (CSSOM)](/en-US/docs/Web/API/CSS_Object_Model) API:

- {{domxref("CSSValue.cssText", "cssText")}} property
- {{domxref("CSSStyleSheet.insertRule()", "insertRule(rule)")}} method
- {{domxref("CSSStyleSheet.replace()", "replace(text)")}} method

[WHATWG](/en-US/docs/Glossary/WHATWG) specification:

- {{HTMLElement("style")}} element
- {{HTMLElement("link")}} element
- [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) attribute
- [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel#stylesheet) attribute

## Specifications

{{Specifications}}

## See also

- [CSS at-rule functions](/en-US/docs/Web/CSS/CSS_syntax/At-rule_functions)
- [CSS selectors](/en-US/docs/Web/CSS/CSS_selectors) module
- [CSS values and units](/en-US/docs/Web/CSS/CSS_Values_and_Units) module
