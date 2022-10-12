---
layout: post
title:  "AOL/Yahoo Style Bug"
date:   2022-10-03 20:41:23 -0400
categories: HTML CSS Bug
---

Small post, just learned that AOL/Yahoo styles wont work if there preceeded by a CSS comment. Keep an eye out for that. 


## Example

```css
<style type="text/css">
/*Comment Here*/
.ignoredByYahoo { display: block !important; }
</style>
```

---

This can be used as a way to create target for AOL/Yahoo if needed.

```html
<style type="text/css">
  .class { color: red; }
  /*yahoo ignores this next class, but works for all others*/
  .class { color: blue; }
</style>
```

---

There are a few ways to prevent this issue:
- Remove the CSS comment
- Make the CSS comment an HTML comment outside the `<style>` tag
- Add an empty style beneath it like this:

```html
<style type="text/css">
/*Comment Here*/
.{}
.notIgnoredByYahoo { display: block !important; }
</style>
```