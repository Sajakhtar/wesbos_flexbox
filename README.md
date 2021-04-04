# Flexbox

[What the Flexbox?!](https://flexbox.io/) course by [Wes Bos](https://wesbos.com/).

official GitHub [repo](https://github.com/wesbos/What-The-Flexbox/blob/master/intro/style.css)

[Project hostest on GitHub Pages]() - ADD LINK

---

## Introduction to Flexbox

[Live Demo]() - ADD LINK

The CSS for your html element starts with `display: flex;` and this makes the content in flex container spans the width of the screen.

`display: inline-flex;` will only spand the width of the content

All the html children of the container become flex items.

When working with flexbox, having a container with some height on it helps you visualize, especially when dealing with direction. This height would be provided by your content elements in a real project.

## Working with Flexbox flex-direction

[Live Demo]() - ADD LINK

[CSS Tricks guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

`flex-direction` sets the axes, where Flexbox has a main and cross axis.

It's important to understand `flex-direction` as features such as `justify-content` and `align-items` aren't necessarily left to right or top to bottom, rather they depend entirely on the `flex-direction`

`flex-direction: row` is the default of any flex container, it aligns the container elements side by side horizontally, taking up the height of the container.

`flex-direction: column;` stacks elements withint the container vertically, within the height of the container

When we are defining things as `flex-direction`, we have 2 axes, main and cross, that are determined by the direction value.

For `flex-direction: row` (default):

- Main axis is left to right
- cross axis is top to bottom

For `flex-direction: column`:

- Main axis is top to bottom
- Cross axis is left to right

For `flex-direction: row-reverse`:

- Main axis is right to left
- cross axis is top to bottom

For `flex-direction: column-reverse`:

- Main axis is bottom to top
- Cross axis is left to right

## Wrapping elements with Flexbox

Flex container will try to work with the width that you the Flex items, but if it doesnt work out it'll evenly distribute the flex items within the flex container, unless the flex property is used to set the width of individual flex items.

`flex-wrap` is applied at the flex container level.

`flex-wrap: no-wrap` is the default.

`flex-wrap: wrap` will work with the flex items specified width, while stretching the height to fill the container

For `flex-direction: row` (default) and `flex-wrap: wrap-reverse`

- Main axis is left to right
- cross axis is bottom to top

For `flex-direction: row-reverse` (default) and `flex-wrap: wrap-reverse`

- Main axis is right to left
- cross axis is bottom to top

Filling in the empty space of a flex container

In the flex container, using `min-height: 100vh;` rather than `height: 100vh;` means that when `flex-direction: column` is set, the flex items would never need to wrap, as they would never exceed the min-height constraint.

Margin is not part of the box model, so using `margin: 10px` on the flex items would break through the flex container

Alternative, to stay within the flex container, would be to use `width: calc(33.333333% - 20px); margin: 10px;`.

Or you can use padding and border as they are a part of the box model.

## Flexbox Ordering

A way to move your DOM elements without actually moving them in the html file.

Applying `flex: 1;` on the flex items, will take the items and evening distribute them across the main axis of the flex container.

The `order` property can be applied within the flex items

Default order is 0, `order: 0;`, so setting order of a flex item to >0 will move that item to the end, or <0 wll move that item to the start.

The `order` is helpful when working with responsive design, where you want to reorder elements in the mobile view.

If you set the an flex item to `order: 1;`, it'll be moved to the end, and if you then set another item to `order: 2;` it'll come after the item at order 1.

Caveat - if you select the items with your mouse, perhaps to copy text, what you'll actually copy and paste are the html elements in the order they were written. So, it's not wise to use the `order` property for html elements that are likely to be copied often.

## Flexbox Alignment and Centering with justify-content

`justify-content` describes how items are aligned on the main axis.

See `justify-content` in [CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#justify-content) for visual examples.

- `justify-content: flex-start` sets items to the start of the flex container
- `justify-content: flex-end` sets items to the start of the flex container
- `justify-content: center` sets items to the center of the flex container, so there's no need for margin tricks
- `justify-content: space-between` distributes items evenly along the main axis, otherwise the items are as wide as the content i.e natural width. The first item will be at flex-start and the last item will be at flex-end, the rest of the items will be divied up in between
- `justify-content: space-around`similar to space-between but also adds same margin for the firt item after flex-start and the last item before flex-end, but of course the magin between items will be 2 times (one margin for each item)
- `justify-content: space-evenly`similar again, but now the space between flex-start and first item is the same as between each item and between last item and flex-end

All this works fine for the default `flex-direction`, i.e. row, where the main axis is left to right.

When `flex-direction: column`, where main axis is top to botton, the flex container is as tall as the content, so justify content won't work unless you give the container a height, `min-height: 100vh`.

Always stop to think the direction of the the main axis and cross axis.

## Flexbox Alignment and Centering with align-items

While `justify-content` works along the main axis, `align-items` works on the cross axis.

See `align-items` in [CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#align-items) for visual examples.

If working with default `flex-direction` i.e. row, then the flex container needs some height to it for `align-items` to work.

By default, the items will take the height of the flex container, which is equivalent to `align-items: stretch`.

- `align-items: center` will center the items along the cross axis
- `align-items: flex-start` will place items at the start of the container on the cross axis
- `align-items: flex-end` will place items at the end of the container on the cross axis
- `align-items: baseline` looks at the text in your items will and ensures the bottom of every single text is aligned on the cross axis. Very handly for vertically (when `flex-direction: row`) aligning items of differnt sizes e.g. a title on the right and a data on the left

## Flexbox Alignment and Centering with align-content

See `align-content` in [CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#align-content) for visual examples.

Whiles `justify-content` dictates when happens to the white space and distribution of items along the main axis, `align-content` takes the space along the cross axis and splits it up for the _wrapped_ items i.e. stacked items.

`align-content` has the same options as `justify-content`.

- `align-content: stretch` is the default, i.e. the items will take up the entire cross axis, split evenly
- `align-content: flex-start` places the items at the start of the cross axis and take up on the necessary space of the content contained in the item. In `flex-direction: row`, all items on the same row will be the same height, where the min height is based on the item with the maximum content.
- `align-content: flex-end` places the items at the end of the cross axis and take up on the necessary space of the content contained in the item. In `flex-direction: row`, all items on the same row will be the same height, where the min height is based on the item with the maximum content.
- `align-content: center` places the items at the center of the cross axis
- `align-content: sapce-between` set the first row to flex start and last row to flex end, and the in between rows are spaced evenly
- `align-content: space-around`similar to space-between but also adds same margin for the firt item after flex-start and the last item before flex-end, but of course the magin between items will be 2 times (one margin for each item)
- `align-content: space-evenly`similar again, but now the space between flex-start and first item is the same as between each item and between last item and flex-end

To align items both at the center both horizontally and vertically set:

- `align-content: center`
  - to align veritically i.e.cross axis top to bottom, when `flex-direction: row` i.e. default
  - to align horizontally i.e.cross axis left to right, when `flex-direction: column`
- `justify-content: center`
  - to align horizontally i.e.main axis left to right, when `flex-direction: row` i.e. default
  - to align veritically i.e.main axis top to bottom, when `flex-direction: column`

## Flexbox Alignment and Centering with align-self

while `align-items` distributed the items across the cross-axis, `align-self` allows for us to overwrite the rule for an individual item.

`align-self` has the same options as `align-items`.

## Understanding Flexbox sizing with the flex property
