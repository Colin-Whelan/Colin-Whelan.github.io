---
layout: post
title:  "Yahoo Style Bug"
date:   2022-10-03 20:41:23 -0400
categories: HTML CSS Bug
---

Small post, just learned that Yahoo styles wont work if there preceeded by a CSS comment. Keep an eye out for that. 


## Example

```css
<style type="text/css">
/*Comment Here*/
.ignoredByYahoo { display: block !important; }
</style>
```

---

There are a few ways to prevent this issue:
1. Remove the CSS comment
2. Make the CSS comment an HTML comment outside the `<style>` tag
3. Add an empty class beneath it like this:

```css
<style type="text/css">
/*Comment Here*/
.{}
.notIgnoredByYahoo { display: block !important; }
</style>
```