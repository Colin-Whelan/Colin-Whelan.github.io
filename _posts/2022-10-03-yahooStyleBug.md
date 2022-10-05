---
layout: post
title:  "Yahoo Style Bug"
date:   2022-10-03 20:41:23 -0400
tags: HTML CSS Bug
---

Small post, just learned that Yahoo styles wont work if there preceeded by a CSS comment. Keep an eye out for that. 

To prevent this issue, 

---

## Example

```css
<style type="text/css">
.everywhere { display: block !important; }
/**/
.notYahoo { display: block !important; }
</style>
```