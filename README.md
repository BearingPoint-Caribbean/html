# BearingPoint HTML Style Guide
*Best practices and guidelines for writing HTML with approachable formatting, syntax, and more.*

## General formatting
* Use tabs with a 4 space indent.
* Both tags and attributes (incl. values) should be written in lowercase.
* Hyphens are used as separators.
* Paragraphs of text should always be placed in a `<p>` tag. Never use multiple `<br>` tags.
* Items in list form should always be in `<ul>`, `<ol>`, or `<dl>`. Never use a set of `<div>` or `<p>`.
* Every form input that has text attached should utilize a `<label>` tag. Especially radio or checkbox elements.
* Even though quotes around attributes is optional, always put (double) quotes around attributes for readability.
* Avoid writing closing tag comments, like `<!-- /.element -->`. This just adds to page load time. Plus, most editors have indentation * guides and open-close tag highlighting.
* Avoid trailing slashes in self-closing elements. For example, `<br>`, `<hr>`, `<img>`, and `<input>`.
* Don’t set tabindex manually—rely on the browser to set the order.

```html
<p class="line-note" data-attribute="106">
	This is my paragraph of special text.
</p>
```

## HTML5 doctype
We often use certain HTML elements and CSS properties that require the use of the HTML5 doctype. Include it at the beginning of all your pages.
```html
<!DOCTYPE html>
<html lang="en">
...
</html>
```
## Language attribute
From the HTML5 spec:
>Authors are encouraged to specify a lang attribute on the root html element, giving the document's language. This aids speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use, and so forth.
```html
<html lang="en-us">
  <!-- ... -->
</html>
```

## Character encoding
Always use UTF-8 encoding.

```html
<meta charset="utf-8">
```

Please note that your IDE should save files in UTF-8 encoding as well.

## CSS and JavaScript includes
Per HTML5 spec, typically there is no need to specify a `type` when including CSS and JavaScript files as `text/css` and `text/javascript` are their respective defaults.

```html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

## Boolean attributes
Many attributes don’t require a value to be set, like disabled or checked, so don’t set them.
```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```
For more information, read the [WhatWG section](https://html.spec.whatwg.org/multipage/infrastructure.html#boolean-attributes).

## Lean (semantic) markup
Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. For example:
```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

## Forms
* Lean towards radio or checkbox lists instead of select menus.
* Wrap radio and checkbox inputs and their text in `<label>`s. No need for `for` attributes here—the wrapping automatically associates the two.
* Form buttons should always include an explicit type. Use primary buttons for the `type="submit"` button and regular buttons for `type="button"`.
* The primary form button must come first in the DOM, especially for forms with multiple submit buttons. The visual order should be preserved with `float: right;` on each button.

## Tables
Make use of `<thead>`, `<tfoot>`, `<tbody>`, and `<th>` tags (and scope attribute) when appropriate. (Note: `<tfoot>` goes above `<tbody>` for speed reasons. You want the browser to load the footer before a table full of data.)

```
<table summary="This is a chart of invoices for 2011.">
  <thead>
    <tr>
      <th scope="col">Table header 1</th>
      <th scope="col">Table header 2</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Table footer 1</td>
      <td>Table footer 2</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Table data 1</td>
      <td>Table data 2</td>
    </tr>
  </tbody>
</table>
```

## Misc
* Make sure you indent your HTML tags accordingly.
* Inline styles are not allowed. Use stylesheets instead.
* Always provide a favicon.ico file (to avoid 404 errors)
