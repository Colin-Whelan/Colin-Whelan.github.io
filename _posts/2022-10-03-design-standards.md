---
layout: post
title:  "WIP: Email Design Standards"
date:   2022-10-03 15:41:23 -0400
categories: Standards
---

This will be the living documentation of my email design standards and decisions behind them.

# Methodology
My HTML methodology is all about making it easier for humans to understand and work with. Sometimes this can add a bit more HTML, but overall this is easier as everything is a breeze to work with. For an even easier time, add this code to a templating system like Nunjucks or Maizzle for some awesome HTML emails.

# Basic HTML Template

Using my basic HTML template, code is easy to keep consistent even with dozens of clients with individual styles and page layouts.

## Modules

HTML templates are built by stacking Modules on top one another. 

Modules are table-based, meaning they are built with `<table>` tags rather than `<row>` or `<div>`. 

This is chosen mostly for working with dynamic content and/or templating systems. When previewing HTML in browsers, content between `<row>'s` will all be boiled to the top, where as content between `<table>'s` are treated as text content. This makes reading and troubleshooting from the browser much easier to solve.

Also, in sending platforms like Salesforce Marketing Cloud (SFMC), the preferred method for storing reusable modules previews best when starting from a `<table>`

## CSS

My CSS is very standard, using an atomic CSS approach. This keeps the CSS consistent across dozens of types designs while still offering maximum customization. This also means that modules developed for one client can be easily shared with others, and the required styles likely already exist.

At the same time, the CSS is very human readable, mimicking the Emmet CSS shorthand standards for the most part.


[expand]

```css
/*WIDTHS*/
.w100 { width: 100% !important;}
.w75 { width: 75% !important;}
.w60 { width: 60% !important;}
.w50 { width: 50% !important;}
.w40 { width: 40% !important;}
.w33 { width: 33% !important;}
.w25 { width: 25% !important;}
/*PADDING*/
.p0 { padding: 0px !important; }
.p5 { padding: 5px !important; }
.p10 { padding: 10px !important; }
.p15 { padding: 15px !important; }
.p20 { padding: 20px !important; }
.p25 { padding: 25px !important; }
.p30 { padding: 30px !important; }
.pt0 { padding-top: 0px !important; }
.pt5 { padding-top: 5px !important; }
.pt10 { padding-top: 10px !important; }
.pt15 { padding-top: 15px !important; }
.pt20 { padding-top: 20px !important; }
.pt25 { padding-top: 25px !important; }
.pt30 { padding-top: 30px !important; }
.pr0 { padding-right: 0px !important; }
.pr5 { padding-right: 5px !important; }
.pr10 { padding-right: 10px !important; }
.pr15 { padding-right: 15px !important; }
.pr20 { padding-right: 20px !important; }
.pr25 { padding-right: 25px !important; }
.pr30 { padding-right: 30px !important; }
.pb0 { padding-bottom: 0px !important; }
.pb5 { padding-bottom: 5px !important; }
.pb10 { padding-bottom: 10px !important; }
.pb15 { padding-bottom: 15px !important; }
.pb20 { padding-bottom: 20px !important; }
.pb25 { padding-bottom: 25px !important; }
.pb30 { padding-bottom: 30px !important; }
.pl0 { padding-left: 0px !important; }
.pl5 { padding-left: 5px !important; }
.pl10 { padding-left: 10px !important; }
.pl15 { padding-left: 15px !important; }
.pl20 { padding-left: 20px !important; }
.pl25 { padding-left: 25px !important; }
.pl30 { padding-left: 30px !important; }
/*STACKING*/
.expand { width: 100% !important; display: block !important; }
.expand2 { display: block !important; }
/*IMAGE SIZING*/
.resize { max-width: 100% !important; height: auto !important; width: 100% !important; }
.resize2 { width: 100% !important; height: auto !important; }
.resize3 { height: auto !important; }
/*HIDE-SHOW*/
.hide { display: none !important; }
.show { display: inline !important; overflow: visible !important; width: 100% !important; height: auto !important; max-height: inherit !important; line-height: 120% !important; }    
```

[/expand]

The 'Width' and 'Padding' styles alone account for over 90% of mobile classes needed

## Text

For simplicity and to make it easier to read, `<p></p>` tags are preferred. The built in margins are usually fine as is, but can be easily customized in CSS as well.

## Images

All images should be exported at at least 2X resolution for best performance on mobile phones and high resolution monitors.

### Sizes

It's best to keep assets small and light so they are faster to load and cheaper to host. 

**Soft limit**: 1MB - At this size some slow connections may take a second or 2 to load, depending on device and settings.

**Hard limit**: 2MB - Any larger than this and there is real risk of assets not loading before recipient exits the message. 

### Formats

Icons, illustrations, and logos are PNG24 which delivers optimal transparency for crisp edges. 

Photographs are JPGs saved at 70-100% quality, depending on the need to reduce filesize.

