---
title: width
slug: Web/CSS/width
page-type: css-property
browser-compat: css.properties.width
sidebar: cssref
---

The **`width`** [CSS](/en-US/docs/Web/CSS) property sets an element's width. By default, it sets the width of the [content area](/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model#content_area), but if {{cssxref("box-sizing")}} is set to `border-box`, it sets the width of the [border area](/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model#border_area).

{{InteractiveExample("CSS Demo: width")}}

```css interactive-example-choice
width: 150px;
```

```css interactive-example-choice
width: 20em;
```

```css interactive-example-choice
width: 75%;
```

```css interactive-example-choice
width: auto;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="transition-all" id="example-element">
    This is a box where you can change the width.
  </div>
</section>
```

```css interactive-example
#example-element {
  display: flex;
  flex-direction: column;
  background-color: #5b6dcd;
  height: 80%;
  justify-content: center;
  color: #ffffff;
}
```

The specified value of `width` applies to the content area so long as its value remains within the values defined by {{cssxref("min-width")}} and {{cssxref("max-width")}}.

- If the value for `width` is less than the value for `min-width`, then `min-width` overrides `width`.
- If the value for `width` is greater than the value for `max-width`, then `max-width` overrides `width`.

> [!NOTE]
> As a geometric property, `width` also applies to the {{SVGElement("svg")}}, {{SVGElement("rect")}}, {{SVGElement("image")}}, and {{SVGElement("foreignObject")}} SVG elements, with `auto` resolving to `100%` for `<svg>` and `0` for other elements, and percent values being relative to the SVG viewport width for `<rect>`. The CSS `width` property value overrides any SVG {{SVGAttr("width")}} attribute value set on the SVG element.

## Syntax

```css
/* <length> values */
width: 300px;
width: 25em;
width: anchor-size(width);
width: anchor-size(--myAnchor inline, 120%);

/* <percentage> value */
width: 75%;

/* Keyword values */
width: max-content;
width: min-content;
width: fit-content;
width: fit-content(20em);
width: auto;
width: stretch;

/* Global values */
width: inherit;
width: initial;
width: revert;
width: revert-layer;
width: unset;
```

### Values

- {{cssxref("&lt;length&gt;")}}
  - : Defines the width as a distance value.
- {{cssxref("&lt;percentage&gt;")}}
  - : Defines the width as a percentage of the [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block)'s width.
- `auto`
  - : The browser will calculate and select a width for the specified element.
- `max-content`
  - : The intrinsic preferred width.
- `min-content`
  - : The intrinsic minimum width.
- `fit-content`
  - : Use the available space, but not more than [max-content](/en-US/docs/Web/CSS/max-content), i.e., `min(max-content, max(min-content, stretch))`.
- `fit-content({{cssxref("&lt;length-percentage&gt;")}})`
  - : Uses the fit-content formula with the available space replaced by the specified argument, i.e., `min(max-content, max(min-content, <length-percentage>))`.
- `stretch`
  - : Sets the width of the element's [margin box](/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model#parts_of_a_box) to the width of its [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block#identifying_the_containing_block). It attempts to make the margin box fill the available space in the containing block, so in a way behaving similar to `100%` but applying the resulting size to the margin box rather than the box determined by [box-sizing](/en-US/docs/Web/CSS/box-sizing).

## Accessibility

Ensure that elements set with a `width` aren't truncated and/or don't obscure other content when the page is zoomed to increase text size.

- [MDN Understanding WCAG, Guideline 1.4 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.4 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

## Formal definition

{{CSSInfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Default width

```css
p.gold {
  background: gold;
}
```

```html
<p class="gold">The MDN community writes really great documentation.</p>
```

{{EmbedLiveSample('Default_width', '500px', '64px')}}

### Example using pixels and ems

```css
.px_length {
  width: 200px;
  background-color: red;
  color: white;
  border: 1px solid black;
}

.em_length {
  width: 20em;
  background-color: white;
  color: red;
  border: 1px solid black;
}
```

```html
<div class="px_length">Width measured in px</div>
<div class="em_length">Width measured in em</div>
```

{{EmbedLiveSample('Example using pixels and ems', '500px', '64px')}}

### Example with percentage

```css
.percent {
  width: 20%;
  background-color: silver;
  border: 1px solid red;
}
```

```html
<div class="percent">Width in percentage</div>
```

{{EmbedLiveSample('Example using percentage', '500px', '64px')}}

### Example using "max-content"

```css
p.max-green {
  background: lightgreen;
  width: max-content;
}
```

```html
<p class="max-green">The MDN community writes really great documentation.</p>
```

{{EmbedLiveSample('Example using "max-content"', '500px', '64px')}}

### Example using "min-content"

```css
p.min-blue {
  background: lightblue;
  width: min-content;
}
```

```html
<p class="min-blue">The MDN community writes really great documentation.</p>
```

{{EmbedLiveSample('Example using "min-content"', '500px', '155px')}}

### Stretch width to fill the containing block

#### HTML

```html
<div class="parent">
  <div class="child">text</div>
</div>

<div class="parent">
  <div class="child stretch">stretch</div>
</div>
```

#### CSS

```css hidden
@supports not (width: stretch) {
  .parent {
    display: none !important;
  }

  body::after {
    content: "Your browser doesn't support the `stretch` value yet.";
  }
}
```

```css
.parent {
  border: solid;
  margin: 1rem;
  display: flex;
}

.child {
  background: #0999;
  margin: 1rem;
}

.stretch {
  width: stretch;
}
```

#### Result

{{EmbedLiveSample('Stretch width to fill the containing block', 'auto', 250)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("height")}}
- {{cssxref("box-sizing")}}
- {{cssxref("min-width")}}, {{cssxref("max-width")}}
- {{cssxref("block-size")}}, {{cssxref("inline-size")}}
- {{cssxref("anchor-size()")}}
- SVG {{SVGAttr("width")}} attribute
- [Introduction to the CSS box model](/en-US/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model) guide
- [CSS box model](/en-US/docs/Web/CSS/CSS_box_model) module
