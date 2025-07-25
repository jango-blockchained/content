---
title: DelegatedInkTrailPresenter
slug: Web/API/DelegatedInkTrailPresenter
page-type: web-api-interface
status:
  - experimental
browser-compat: api.DelegatedInkTrailPresenter
---

{{APIRef("Ink API")}}{{SeeCompatTable}}

The **`DelegatedInkTrailPresenter`** interface of the [Ink API](/en-US/docs/Web/API/Ink_API) provides the ability to instruct the OS-level compositor to render ink strokes between pointer event dispatches.

{{InheritanceDiagram}}

## Instance properties

- {{domxref("DelegatedInkTrailPresenter.expectedImprovement", "expectedImprovement")}} {{Deprecated_Inline}} {{Non-standard_Inline}} {{ReadOnlyInline}}
  - : Returns a value, in milliseconds, indicating the latency improvement that can be expected using this presenter.
- {{domxref("DelegatedInkTrailPresenter.presentationArea", "presentationArea")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : Returns the {{domxref("Element")}} inside which rendering of ink strokes is confined.

## Instance methods

- {{domxref("DelegatedInkTrailPresenter.updateInkTrailStartPoint", "updateInkTrailStartPoint()")}} {{Experimental_Inline}}
  - : Passes the {{domxref("PointerEvent")}} that was used as the last rendering point for the current frame, allowing the OS-level compositor to render a delegated ink trail ahead of the next pointer event being dispatched.

## Example

In this example, we draw a trail onto a 2D canvas. Near the start of the code, we call {{domxref("Ink.requestPresenter()")}}, passing it the canvas as the presentation area for it to take care of and storing the promise it returns in the `presenter` variable.

Later on, in the `pointermove` event listener, the new position of the trailhead is drawn onto the canvas each time the event fires. In addition, the `DelegatedInkTrailPresenter` object returned when the `presenter` promise fulfills has its {{domxref("DelegatedInkTrailPresenter.updateInkTrailStartPoint", "updateInkTrailStartPoint()")}} method invoked; this is passed:

- The last trusted pointer event representing the rendering point for the current frame.
- A `style` object containing color and diameter settings.

The result is that a delegated ink trail is drawn ahead of the default browser rendering on the app's behalf, in the specified style, until the next time it receives a `pointermove` event.

```js
const ctx = canvas.getContext("2d");
let presenter = navigator.ink.requestPresenter({ presentationArea: canvas });
let move_cnt = 0;
let style = { color: "rgb(0 0 255 / 100%)", diameter: 10 };

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

canvas.addEventListener("pointermove", (evt) => {
  const pointSize = 10;
  ctx.fillStyle = "#000000";
  ctx.fillRect(evt.pageX, evt.pageY, pointSize, pointSize);
  if (move_cnt === 50) {
    let r = getRandomInt(0, 255);
    let g = getRandomInt(0, 255);
    let b = getRandomInt(0, 255);
    style = {
      color: `rgb(${r} ${g} ${b} / 100%)`,
      diameter: 10,
    };
    move_cnt = 0;
    document.getElementById("div").style.backgroundColor =
      `rgb(${r} ${g} ${b} / 100%)`;
  }
  move_cnt += 1;
  presenter.then((v) => {
    v.updateInkTrailStartPoint(evt, style);
  });
});

window.addEventListener("pointerdown", (evt) => {
  evt.pointerId;
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height);
});

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```

> [!NOTE]
> See this example running live — [Delegated ink trail](https://mabian-ms.github.io/delegated-ink-trail.html).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
