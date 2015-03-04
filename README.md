# SortSelect
Very simple jQuery Plugin which makes a set of child elements selectable and optionally sortable through drag and drop.

It offers:

- events
- multiple selection
- basic keyboard integration for Ctrl and Shift
- drag and drop helper for additional UI/UX

### Useage



### API

`SortSelect(jquery, options);`

- `jquery` can be a DOM object, xPath/CSS selector or jQuery selection
- `options` is an optional object for instantiation

Returns a SortSelect object for the first DOM found for `jquery`.

**Options**

You can change the default values via `SortSelect.fn`.

- `enabled` *Boolean* - If `true` enables select and sort functionality. Default is `true`.
- `sortable` *Boolean* - `true` if you want to enable drag and drop. `false` for only selecting. Default is `true`.
- `filter` *String* - Enables SortSelect only for child elements that match `filter`. Default is `li`.
- `distance` *Number* - Amount of pixels the mouse has to move before a selection or a sort starts. Default is `5`.
- `helper` *null|false|string|jQuery|function* - You can provide a helper which will follow the mouse during a sort. You can use it for additional UX. If you pass a function it will be called when the helper is created and it should return something that can be inserted into the DOM e.g `'<div class="ui-sort-helper" />'`. The function's arguments will be a jQuery containing the elements to be sorted. Default is `false`.

**Instance Properties**

All options used for creating a SortSelect object are added to it as well.
So if you change e.g `sortable` during runtime it will have the effect described above.

- `grid` *DOM Node* -  The container element.

**Instance Methods**

- `destroy()` - Reverts the DOM element to its original state before the SortSelect was created. The SortSelect object itself will be deleted as well so you can not use it after `destroy` was called.
- `select(jquery)` - Selects elements. If `jquery` is a String it is used as jQuery filter. Anything else is run through `jQuery()`. All elements are checked if their direct parent is `grid`.
- `deselect(jquery)` - Deselects elements. If `jquery` is omitted all elements will be deselected. If `jquery` is a String it is used as jQuery filter. Anything else is run through `jQuery()`. All elements are checked if their direct parent is `grid`.
- `cancel()` - Interrupts the SortSelect. Fires a `cancel` event
- `selection()` -  Returns a jQuery selection of child elements currently selected.
- `selecting()` - Returns `true` if the SortSelect is currently selecting. 
- `sorting()` - Returns `true` if the SortSelect is currently sorting.
- `on(event, callback)` - Adds a function to an event name.
- `off(event, callback)` - Removes a function from an event name.
- `trigger(event [, parameter1 [, parameter2 ...]])` - Triggers an event name with optional and an arbitrary number of parameters.

**Instance Events**

SortSelect internally uses following events names during different states of operation:

- `start` is fired when the mouse moved beyond `distance` and a selection or sorting starts.
- `select` is fired every time an element is selected.
- `deselect` is fired every time all or the last element gets deselected.
- `change` is fired if the selection changes.
- `update` is fired if at least one element was sorted.
- `sorting` is fired during a sorting operation.
- `stop` is fired after the mouse was released and a selecting or sorting stopped.
- `cancel` is fired if a selecting or sorting operation is interrupted.

**Event Callbacks**

`this` referes to the SortSelect object the callback is added to.


**Global Properties**

- `SortSelect.selected` *String* CSS class added to selected items
- `SortSelect.selecting` *String* CSS class added to the container during selection
- `SortSelect.sorting` *String* CSS class added to the container during sorting
- `SortSelect.marquee` *String* CSS class added to the marquee

**Global Methods**

- `SortSelect.get(jquery)` - `jquery` can be a DOM object, xPath/CSS selector or jQuery selection. Checks if `jquery` is already a SortSelect and if so returns it. Otherwise `null`.
