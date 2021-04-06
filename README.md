# Flexbox

[What the Flexbox?!](https://flexbox.io/) course by [Wes Bos](https://wesbos.com/).

official GitHub [repo](https://github.com/wesbos/What-The-Flexbox/blob/master/intro/style.css)

[Project hostest on GitHub Pages]() - ADD LINK

---

## Contents

1. [Introduction to Flexbox](#introduction-to-flexbox)
1. [Working with Flexbox flex-direction](#working-with-Flexbox-flex-direction)
1. [Wrapping elements with Flexbox](#wrapping-elements-with-Flexbox)
1. [Flexbox Ordering](#flexbox-ordering)
1. [Flexbox Alignment and Centering with justify-content](#flexbox-alignment-and-Centering-with-justify-content)
1. [Flexbox Alignment and Centering with align-items](#flexbox-alignment-and-Centering-with-align-items)
1. [Flexbox Alignment and Centering with align-content](#flexbox-alignment-and-Centering-with-align-content)
1. [Flexbox Alignment and Centering with align-self](#flexbox-alignment-and-Centering-with-align-self)
1. [Understanding Flexbox sizing with the flex property](#understanding-Flexbox-sizing-with-the-flex-property)
1. [Understanding Flexbox flex-grow, flex-shrink and flex-basis](#understanding-flexbox-flex-grow,-flex-shrink-and-flex-basis)
1. [How Flexbox's flex-basis and wrapping work together](#how-flexbox's-flex-basis-and-wrapping-work-together)
1. [Cross Browser Flexbox Support and Autoprefixer](#cross-browser-flexbox-Support-and-autoprefixer)
1. [Pure Flexbox navigation code along](#pure-flexbox-navigation-code-along)
1. [Mobile Content reordering with Flexbox](#mobile-content-reordering-with-Flexbox)
1. [Nesting Flexbox for vertical and horizontal centering with Flexbox](#nesting-flexbox-for-vertical-and-horizontal-centering-with-flexbox)
1. [Flexbox Pricing Grid](#flexbox-pricing-grid)
1. [Flexbox Equal height columns and leftover elements](#flexbox-equal-height-columns-and-leftover-elements)
1. [Flexbox single line form](#flexbox-single-line-form)
1. [Create a mobile app layout with Flexbox](#create-a-mobile-app-layout-with-flexbox)

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

[Live Demo]() - ADD LINK

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

[Live Demo]() - ADD LINK

A way to move your DOM elements without actually moving them in the html file.

Applying `flex: 1;` on the flex items, will take the items and evening distribute them across the main axis of the flex container.

The `order` property can be applied within the flex items

Default order is 0, `order: 0;`, so setting order of a flex item to >0 will move that item to the end, or <0 wll move that item to the start.

The `order` is helpful when working with responsive design, where you want to reorder elements in the mobile view.

If you set the an flex item to `order: 1;`, it'll be moved to the end, and if you then set another item to `order: 2;` it'll come after the item at order 1.

Caveat - if you select the items with your mouse, perhaps to copy text, what you'll actually copy and paste are the html elements in the order they were written. So, it's not wise to use the `order` property for html elements that are likely to be copied often.

## Flexbox Alignment and Centering with justify-content

[Live Demo]() - ADD LINK

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

[Live Demo]() - ADD LINK

While `justify-content` works along the main axis, `align-items` works on the cross axis.

See `align-items` in [CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#align-items) for visual examples.

If working with default `flex-direction` i.e. row, then the flex container needs some height to it for `align-items` to work.

By default, the items will take the height of the flex container, which is equivalent to `align-items: stretch`.

- `align-items: center` will center the items along the cross axis
- `align-items: flex-start` will place items at the start of the container on the cross axis
- `align-items: flex-end` will place items at the end of the container on the cross axis
- `align-items: baseline` looks at the text in your items will and ensures the bottom of every single text is aligned on the cross axis. Very handly for vertically (when `flex-direction: row`) aligning items of differnt sizes e.g. a title on the right and a data on the left

## Flexbox Alignment and Centering with align-content

[Live Demo]() - ADD LINK

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

[Live Demo]() - ADD LINK

while `align-items` distributed the items across the cross-axis, `align-self` allows for us to overwrite the rule for an individual item.

`align-self` has the same options as `align-items`.

## Understanding Flexbox sizing with the flex property

[Live Demo]() - ADD LINK

`flex` property goes on the individual flex items.
`flex` answers the question of what to do with extra space or when there isn't enough space.

Width of flex items is auto by default, where auto is the width of the content in the flex items.

- `flex: 1`, regardless of the amount of content inside the flex items, the extra space will be evenly given to the flex items
- `flex: 2`, giving one flex item a flex of 2, while all other items remain as flex 1, the flex 2 item will get twice the extra space across the main axis

`flex` can take decimal points as well.

## Understanding Flexbox flex-grow, flex-shrink and flex-basis

[Live Demo]() - ADD LINK

Within the `flex` property, there are actually three properties that are packed into it - `flex-grow`, `flex-shrink`, `flex-basis`

- `flex-grow`
  - answers when we have extra space, how should we divide by all the items on the same line?
  - By setting `flex: 1`, you're essentially setting `flex-grow: 1` and `flex-shrink: 1` at the same time
  - default `flex-grow: 0`, i.e. extra space is left alone, flex items won't fill it
- `flex-shrink`

  - how do slim the flex items down when there isn't enough space on the main axis
  - default `flex-shrink: 1`, i.e evenly divide the sapce on the main axis amongst the flex items
  - determines how much space the flex item should give up in proportion to the other items i.e. if item 1 has `flex-shrink: 10` while item 2 is on the default, then item 1 shirnks itself 10 times more space as item 2

- `flex-basis`, defines how wide the item should be along main axis, then `flex-grow` and `flex-shrink` will define how the extra space or lack of space should be used

Practically, you can use `flex` to specify `flex-grow`, `flex-shrink`, `flex-basis` like so `flex: 10 5 400px`. It's recommended to set these properties in the `flex` shorthand.

You do give up some control from setting hard widths in regular CSS, but that's the beauty of flexbox.

## How Flexbox's flex-basis and wrapping work together

[Live Demo]() - ADD LINK

With `flex-wrap: wrap` then `flex-grow`, `flex-shrink`, `flex-basis` only impact the items on the same row, for `flex-direction: row` (default)

For `flex-direction: column`, the items stack themselves vertically, and the main axis is top to bottom. `flex-grow`, `flex-shrink`, `flex-basis` will not have any impact unless the flex-container has a height e.g. `min-height: 100vh` or `height: 100vh` if your want items to wrap based on height of the browser. The wrapping with create as many columns needed acording to the browser height and the pixels set within `flex-basis` for each flex element. Then `flex-grow` and `flex-shrink`will only apply within the relevant column.

## Cross Browser Flexbox Support and Autoprefixer

[Live Demo]() - ADD LINK

Flexbox has been around for quite a while, but some browsers use the old version (2009) of Flexbox and other use the new version, Prefix Flexbox. We can run our code through a compile step to make our CSS compatible with older browser.

Autoprefixer takes your clean modern Flexbox CSS and prefixes it with the brwoser vendor prefixes and older display box syntax.

You can see what your clean CSS will be converted to using the tool: [Autoprefixer CSS online](http://autoprefixer.github.io/)

Toe use Autoprefixer, we need to setup a build step usign [Gulp](https://gulpjs.com/). Gulp will compile the CSS every time we update and save it.

To intall Gulp, you need to have [node.js](https://nodejs.org/en/) installed.

Using the terminal, initialize a node project in your folder using `npm init`. This will create a `package.json` file to track the dependencies and their versions.

Using the terminal, install Gulp globally with `npm install gulp -g` or `sudo npm install gulp -g`.

Next, using the terminal, create a gulp file with `touch gulpfile.js`.

Now install a local version of Gulp with `npm install gulp --save-dev`. You'll see that Gulp is added to the dependencies in `package.json` file.

Next, install the autoprefixer with `npm install gulp-autoprefixer --save-dev`. This will be added to the dependencies in `package.json` file.

In the `gulpfile.js` we'll need the entire Gulp library and all the plugins we need:

```js
var gulp = require("gulp");
var autoprefixer = require("gulp-autoprefixer");

gulp.task("styles", function () {
  gulp.src("css/styles.css").pipe(autoprefixer()).pipe(gulp.dest("build"));
});
```

In the terminal, excute `gulp styles` to run the Gulp styles task. This will create a new directory called _build_ where our autoprefixed CSS will be.

In the `index.html` file update the CSS reference to the autopreixed version i.e. `<link rel="stylesheet" href="build/style.css">`

We don't want to manually run the _styles_ Gulp task every time we make CSS changes, so we'll add a watch task to `gulpfile.js` to automatically run the _styles_ task when the CSS file changes.

```js
gulp.task("watch", function () {
  gulp.watch("css/styles.css", ["styles"]);
});
```

In the terminal, excute `gulp watch` to run the Gulp watch task, then every time the CSS file is saved, the _styles_ task will run.

## Pure Flexbox navigation code along

[Live Demo]() - ADD LINK

Building navigations is one of the most common and best use cases for Flexbox.

Here the `<ul>` will be the flex container and the `<li>` will be the flex items.

When dealing with mobile layouts, within the media query `@media all and (max-width: 1000px) {}`, we'll wrap the elements when the width is 1000px or less, using `flex-wrap: wrap` and by giving the items a width using `flex` property. Thenfor the 500px media query, set the flex-basis to 100%, to stack elements vertically.

## Mobile Content reordering with Flexbox

[Live Demo]() - ADD LINK

Always wrap your website html in a wrapper `<div>` just in case you need to turn it into a flex container i.e. `display: felx`, and all the children in the wrapper class will be flex items that your can easily reorder.

The default order of flex items is zero, so give a default order of the flex items within the wrapper to arbirarily high number ` .wrapper > * { order: 9999; }`.

Then set the order of the navigation to 1 to bring it to the top, `.flex-nav {order: 1;}`. Next set the toggle navigation to display `.toggleNav {display: block;}` and `.flex-nav ul {display: none;}` to hide the navigation list of elements.

As the the Nav toggle is clicked, the class of the nav is set to change to `open` and so for the nav items to appear once the toggle is clicked, we need to set `.flex-nav ul.open {display: flex;}`.

## Nesting Flexbox for vertical and horizontal centering with Flexbox
