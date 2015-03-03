# SortSelect
Very simple jQuery Plugin which makes a set of child elements selectable and optionally sortable through drag and drop.

It offers:

- events
- multiple selection
- basic keyboard integration for Ctrl and Shift
- drag and drop helper for additional UI/UX

### API

`SortSelect(jquery, options);`

- `jquery` can be a DOM object, xPath/CSS selector or jQuery selection
- `options` is an optional object for instantiation

Returns a SortSelect object for the first DOM found for `jquery`.

**Options**

You can change the default values via `SortSelect.fn`.

- `enabled` *Boolean* - If `true` enables select and sort functionality. Default is `true`
- `sortable` *Boolean* - `true` if you want to enable drag and drop. `false` for only selecting. Default is `true`
- `filter` *String* - Enables SortSelect only for thoes child elements that match `filter`. Default is `li`
- `distance` *Number* - Amount of pixels the mouse has to move before a selection or a sort starts
- `helper` *null|false|string|jQuery|function* - You can provide a helper which will follow the mouse during a sort. You can use it for additional UX. If you pass a function it will be called when the helper is created and it should return something that can be inserted into the DOM e.g `'<div class="ui-sort-helper" />'`. The function's arguments will be a jQuery containing the elements to be sorted. Default is `false`

**Instance Properties**

All options used for creating a SortSelect object are added to it as well.
So if you change e.g `sortable` during runtime it will have the effect described above.

**Instance Methods**

- `destroy()` - Reverts the DOM element to its original state before the SortSelect was created. The SortSelect object itself will be deleted as well so you can not use it after `destroy` was called.
- `select` - Selects
- `deselect` - Deselects
- `cancel`
- `selection`
- `selecting`
- `sorting`
- `on(event, callback)`
- `off(event, callback)`
- `trigger(event [, parameter1 [, parameter2 ...]])`

**Instance Events**

- `start` Fired when
- `select`
- `deselect`
- `change`
- `update`
- `sorting`
- `stop`
- `cancel`

**Global Properties**

- `SortSelect.selected` *String* CSS class added to selected items
- `SortSelect.selecting` *String* CSS class added to the container during selection
- `SortSelect.sorting` *String* CSS class added to the container during sorting
- `SortSelect.marquee` *String* CSS class added to the marquee

**Global Methods**

- `SortSelect.get(mixed)`
