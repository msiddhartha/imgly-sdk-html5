# Customizing the photo editor

We designed the photo editor to be easily customizable using our API. The
features explained on this page apply to our default UI ("Night UI").

## Selecting the available operations

Using the `selectOperations` function, you can decide which operations should
be available to the user. [Every operation has its own unique identifier](misc/operation-identifiers.md).

To select only the `crop` and `filters` operations, call `selectOperations`
with an object containing an `only` property *before* calling `kit.run()`:

```js
var kit = new ImglyKit({
  image: myImage,
  ui: true,
  container: document.querySelector("#container")
});

kit.selectOperations({ only: "crop, filters" });

kit.run();
```

To select all operations except the `text` and `stickers` operations, you
can pass an object containing an `except` property:

```js
kit.selectOperations({ except: "text, stickers" });
```

## Selecting the available filters

Using the `selectFilters` function of the `FiltersControl`, you can select
the available filters. [Every filter has its own unique identifier](misc/filter-identifiers.md).

Make sure you call this function *after* calling `kit.run()`:

```js
var filtersControl = kit.ui.controls.filters;
filtersControl.selectFilters({ only: ["semired, k1, k2, k6"] });
```

Since adding custom filters is more complicated, [we moved this to a separate page](creating-custom-filters.md).