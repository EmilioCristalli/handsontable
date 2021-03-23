---
title: Comments
permalink: /next/api/comments
canonicalUrl: /api/comments
editLink: false
---

# Comments

[[toc]]

## Description


This plugin allows setting and managing cell comments by either an option in the context menu or with the use of
the API.

To enable the plugin, you'll need to set the comments property of the config object to `true`:
```js
comments: true
```

or an object with extra predefined plugin config:

```js
comments: {
  displayDelay: 1000
}
```

To add comments at the table initialization, define the `comment` property in the `cell` config array as in an example below.

**Example**  
```js
const hot = new Handsontable(document.getElementById('example'), {
  data: getData(),
  comments: true,
  cell: [
    {row: 1, col: 1, comment: {value: 'Foo'}},
    {row: 2, col: 2, comment: {value: 'Bar'}}
  ]
});

// Access to the Comments plugin instance:
const commentsPlugin = hot.getPlugin('comments');

// Manage comments programmatically:
commentsPlugin.setCommentAtCell(1, 6, 'Comment contents');
commentsPlugin.showAtCell(1, 6);
commentsPlugin.removeCommentAtCell(1, 6);

// You can also set range once and use proper methods:
commentsPlugin.setRange({from: {row: 1, col: 6}});
commentsPlugin.setComment('Comment contents');
commentsPlugin.show();
commentsPlugin.removeComment();
```

## Members:

### range

_comments.range : object_

Current cell range, an object with `from` property, with `row` and `col` properties (e.q. `{from: {row: 1, col: 6}}`).


## Methods:

### clearRange

_comments.clearRange()_

Clears the currently selected cell.



### destroy

_comments.destroy()_

Destroys the plugin instance.



### disablePlugin

_comments.disablePlugin()_

Disables the plugin functionality for this Handsontable instance.



### enablePlugin

_comments.enablePlugin()_

Enables the plugin functionality for this Handsontable instance.



### getComment

_comments.getComment() ⇒ string | undefined_

Gets comment from a cell according to previously set range (see [setRange](#Comments+setRange)).


**Returns**: `string` | `undefined` - Returns a content of the comment.  

### getCommentAtCell

_comments.getCommentAtCell(row, column) ⇒ string | undefined_

Gets comment from a cell at the provided coordinates.


| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index. |
| column | `number` | Visual column index. |


**Returns**: `string` | `undefined` - Returns a content of the comment.  

### getCommentMeta

_comments.getCommentMeta(row, column, property) ⇒ Mixed_

Gets the comment related meta information.


| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index. |
| column | `number` | Visual column index. |
| property | `string` | Cell meta property. |



### hide

_comments.hide()_

Hides the comment editor.



### isEnabled

_comments.isEnabled() ⇒ boolean_

Checks if the plugin is enabled in the handsontable settings. This method is executed in [Hooks#beforeInit](./Hooks/#beforeInit)
hook and if it returns `true` than the [enablePlugin](#Comments+enablePlugin) method is called.



### refreshEditor

_comments.refreshEditor([force])_

Refreshes comment editor position and styling.


| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [force] | `boolean` | <code>false</code> | `optional` If `true` then recalculation will be forced. |



### removeComment

_comments.removeComment([forceRender])_

Removes a comment from a cell according to previously set range (see [setRange](#Comments+setRange)).


| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [forceRender] | `boolean` | <code>true</code> | `optional` If set to `true`, the table will be re-rendered at the end of the operation. |



### removeCommentAtCell

_comments.removeCommentAtCell(row, column, [forceRender])_

Removes a comment from a specified cell.


| Param | Type | Default | Description |
| --- | --- | --- | --- |
| row | `number` |  | Visual row index. |
| column | `number` |  | Visual column index. |
| [forceRender] | `boolean` | <code>true</code> | `optional` If `true`, the table will be re-rendered at the end of the operation. |



### setComment

_comments.setComment(value)_

Sets a comment for a cell according to the previously set range (see [setRange](#Comments+setRange)).


| Param | Type | Description |
| --- | --- | --- |
| value | `string` | Comment contents. |



### setCommentAtCell

_comments.setCommentAtCell(row, column, value)_

Sets a comment for a specified cell.


| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index. |
| column | `number` | Visual column index. |
| value | `string` | Comment contents. |



### setRange

_comments.setRange(range)_

Sets the current cell range to be able to use general methods like [setComment](#Comments+setComment), [removeComment](#Comments+removeComment), [show](#Comments+show).


| Param | Type | Description |
| --- | --- | --- |
| range | `object` | Object with `from` property, each with `row` and `col` properties. |



### show

_comments.show() ⇒ boolean_

Shows the comment editor accordingly to the previously set range (see [setRange](#Comments+setRange)).


**Returns**: `boolean` - Returns `true` if comment editor was shown.  

### showAtCell

_comments.showAtCell(row, column) ⇒ boolean_

Shows comment editor according to cell coordinates.


| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index. |
| column | `number` | Visual column index. |


**Returns**: `boolean` - Returns `true` if comment editor was shown.  

### updateCommentMeta

_comments.updateCommentMeta(row, column, metaObject)_

Sets or update the comment-related cell meta.


| Param | Type | Description |
| --- | --- | --- |
| row | `number` | Visual row index. |
| column | `number` | Visual column index. |
| metaObject | `object` | Object defining all the comment-related meta information. |



### updatePlugin

_comments.updatePlugin()_

Updates the plugin state. This method is executed when [Core#updateSettings](./Core/#updateSettings) is invoked.

