---
title: transition-delay
slug: Web/CSS/transition-delay
page-type: css-property
browser-compat: css.properties.transition-delay
sidebar: cssref
---

The **`transition-delay`** [CSS](/en-US/docs/Web/CSS) property specifies the duration to wait before starting a property's [transition effect](/en-US/docs/Web/CSS/CSS_transitions/Using_CSS_transitions) when its value changes.

{{InteractiveExample("CSS Demo: transition-delay")}}

```css interactive-example-choice
transition-delay: 250ms;
transition-property: margin-right;
```

```css interactive-example-choice
transition-delay: 1s;
transition-property: background-color;
```

```css interactive-example-choice
transition-delay: 1s;
transition-property: margin-right, color;
```

```css interactive-example-choice
transition-delay: 1s, 250ms;
transition-property: margin-right, color;
```

```html interactive-example
<section id="default-example">
  <div id="example-element">Hover to see<br />the transition.</div>
</section>
```

```css interactive-example
#example-element {
  background-color: #e4f0f5;
  color: #000;
  padding: 1rem;
  border-radius: 0.5rem;
  font: 1em monospace;
  width: 100%;
  transition: margin-right 2s;
}

#default-example:hover > #example-element {
  background-color: #909;
  color: #fff;
  margin-right: 40%;
}
```

The delay may be zero, positive, or negative:

- A value of `0s` (or `0ms`) will begin the transition effect immediately.
- A positive value will delay the start of the transition effect for the given length of time.
- A negative value will begin the transition effect immediately, and partway through the effect. In other words, the effect will be animated as if it had already been running for the given length of time.

You may specify multiple delays, which is useful when transitioning multiple properties. Each delay will be applied to the corresponding property as specified by the {{cssxref("transition-property")}} property, which acts as a master list. If there are fewer delays specified than in the master list, the list of delay values will be repeated until there are enough. If there are more delays, the list of delay values will be truncated to match the number of properties. In both cases, the CSS declaration remains valid.

## Syntax

```css
/* <time> values */
transition-delay: 3s;
transition-delay: 2s, 4ms;

/* Global values */
transition-delay: inherit;
transition-delay: initial;
transition-delay: revert;
transition-delay: revert-layer;
transition-delay: unset;
```

### Values

- {{cssxref("&lt;time&gt;")}}
  - : Denotes the amount of time to wait between a property's value changing and the start of the transition effect.

## Formal definition

{{CSSInfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Example showing different delays

#### HTML

```html
<div class="box delay-1">0.5 seconds</div>

<div class="box delay-2">2 seconds</div>

<div class="box delay-3">4 seconds</div>

<button id="change">Change</button>
```

#### CSS

```css
.box {
  margin: 20px;
  padding: 10px;
  display: inline-block;
  width: 100px;
  height: 100px;
  background-color: red;
  font-size: 18px;
  transition-property: background-color, font-size, transform, color;
  transition-timing-function: ease-in-out;
  transition-duration: 3s;
}

.transformed-state {
  transform: rotate(270deg);
  background-color: blue;
  color: yellow;
  font-size: 12px;
  transition-property: background-color, font-size, transform, color;
  transition-timing-function: ease-in-out;
  transition-duration: 3s;
}

.delay-1 {
  transition-delay: 0.5s;
}

.delay-2 {
  transition-delay: 2s;
}

.delay-3 {
  transition-delay: 4s;
}
```

#### JavaScript

```js
function change() {
  const elements = document.querySelectorAll("div.box");
  for (const element of elements) {
    element.classList.toggle("transformed-state");
  }
}

const changeButton = document.querySelector("#change");
changeButton.addEventListener("click", change);
```

#### Result

{{EmbedLiveSample("Example_showing_different_delays",275,200)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using CSS transitions](/en-US/docs/Web/CSS/CSS_transitions/Using_CSS_transitions)
- {{domxref("TransitionEvent")}} API
