A practical, minimalist CSS grid system for Stylus
==================================================

Even though that's incredibly unique already, here are some semi-distinguishing features:

- uses the awesome [Stylus](http://learnboost.github.com/stylus/)
- fluid, responsive & configurable
- allows easy definition of different grids depending on screen size
- ~100 lines, does only grids, nothing else

Basic Usage
-----------

Import the grid into an existing stylus file.

```css
@import grid
```

Set the grid class on elements that will contain grid items (rows).

```html
<div class="row"></div>
```

Set column widths on grid items (columns).

```html
<div class="row">
  <div class="col-1-4">1/4 Column</div>
  <div class="col-3-4">3/4 Column</div>
</div>
```

Alternatively, set column widths on the row to affect all columns equally.

```html
<div class="row row-3">
  <div class="col">1/3 Column</div>
  <div class="col">1/3 Column</div>
  <div class="col">1/3 Column</div>
</div>
```

Semantic Usage
--------------

Grid styles can also be included in other classes for clean markup.

```css
@media only screen and (min-width: 481px)
  #container
    row()

    > div
      column(1, 3)
```

```html
<div id="container">
  <div>1/3 Column</div>
  <div>1/3 Column</div>
  <div>1/3 Column</div>
</div>
```

Adaptive usage & offsets discussed below work as expected. Half size and no gutter row do not (yet).

Adaptive Usage
--------------

To use different grid setups on different screen sizes define them in a stylus file. The names will become part of the class name.

```css
// typical tablet layout
@media only screen and (min-width: 481px) and (max-width: 799px)
  setup-columns('t')

// typical desktop layout
@media only screen and (min-width: 800px)
  setup-columns('d')
```

This will create additional classes that only apply the grid at the specified screen size.

```html
<div class="row">
  <div class="col-t-1-3 col-d-1-2">1/3 on tablets, 1/2 on desktops</div>
  <div class="col-t-2-3 col-d-1-2">2/3 on tablets, 1/2 on desktops</div>
</div>

<div class="row row-t-2 row-d-3">
  <div class="col">1/2 on tablets, 1/3 on desktops</div>
  <div class="col">1/2 on tablets, 1/3 on desktops</div>
  <div class="col">1/2 on tablets, 1/3 on desktops</div>
</div>
```

Advanced Usage
--------------

Override size and/or naming options.

```css
// grid settings
gutter-size   = 20px

// class names
row-class     = 'row'
column-class  = 'col'
offset-class  = 'off'
```

Offseting columns works as expected.

```html
<div class="row">
  <div class="col-1-3">1/3 Column</div>
  <div class="col-1-3 off-1-3">1/3 Column offset by 1/3</div>
</div>

<div class="row">
  <div class="col-t-1-3 col-d-1-2">1/3 Column on tablets, 1/2 on desktops</div>
  <div class="col-t-1-3 off-t-1-3 col-d-1-2">1/3 Column offset by 1/3 on tablets, 1/2 on desktops</div>
</div>
```
