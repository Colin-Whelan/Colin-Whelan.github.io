---
layout: post
title:  "Organic Shapes in Email"
date:   2022-10-04 21:21:23 -0400
categories: HTML CSS Outlook NewTech
---

![shapes](../../../../../../../assets/images/shapes.png)

I have been working on a new design capability and tool to bring a fresh look and feel to emails that I am ready to share with the world.

Over the past decade there has been a bigger push toward curved designs, which have mostly been locked away from email due to lack of support. I've found a solution to the problem, and it's so simple I'm surprised I haven't seen it earlier. 

![example](../../../../../../../assets/images/organicShape-example.jpg)

# Where is this supported?

This techniques works everywhere except AOL/Yahoo mail, and Outlook does require VML. I've developed a tool to automatically create the VML as doing it manually is very time consuming. [Check out my VML Pather tool for various VML generation needs.](https://vml-pather.glitch.me/)

Using classes, different mobile or darkmode designs are easy as ever, no considerations needed.

## Borders

Shapes can also be a border on their own for more customization.

# Shape Layering

In addition to creating tons of new shapes, several shapes can be layered on top one another for even more effects. With this technique it's possible to achieve the hand-drawn style seen above.

# How does it work?

Using [the border technique from the 9elements blog](https://9elements.com/blog/css-border-radius/), shapes can be easily made for non-outlook clients. 
To add support for Outlook I needed to delve into [the VML specs](https://www.w3.org/TR/NOTE-VML) a bit. There is a shape command that works very similar to the full 8 point control described in the blog post - 'ellipticalqaudrantx' and 'ellipticalquadranty'. The commands are used to draw curved corners which start and end on vertical and horizontal lines. Using this, as we as the simple line 'l' command to make straight lines, it is possible to define each of the 8 corner points, but with pixels instead of percentages.

For shape layering, there is `<v:group>` from the spec that allows for shapes to be grouped together and layerd. Be sure to select the grouping option on the Pather when generating this code.[^1]


[^1]: With shape layering, an arbitrary amount of padding may be needed for Outlook. Use  `mso-padding-bottom-alt:_px;` and test to adjust as needed.

---

## Code

Advanced shape layering[^1]

```html
<table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" role="presentation">
  <tr>
    <td align="center" style="mso-padding-bottom-alt:120px;" class="">
      <table border="0" cellpadding="0" cellspacing="0" width="560" class="w100" style="" role="presentation">
        <tr>
          <!--[if !mso]-->
          <td align="top" style="" class="fullshape2 bg_f4cc66">
            <table border="0" cellpadding="0" cellspacing="0" width="100%" style="" role="presentation">
              <tr>
                <td style="" class="fullshape1 bg_f4ab66">
                  <table border="0" cellpadding="0" cellspacing="0" style="" role="presentation">
                    <tr>
                      <td align="" style="" class="outline2">
                        <table width="100%" border="0" cellspacing="0" cellpadding="0" role="presentation">
                          <tr>
                            <!--<![endif]-->
                            <!--[if mso]>
                            <v:group id="GroupA" style='position:relative; width: 560; height: 200;' >
                            <v:shape style='left: 0; width: 1000; height: 1000; flip:y;'  fill="true" fillcolor="#F4CC66" stroke="false" coordorigin="0 0" coordsize="560 200">
                            <v:path v="m 0,76 qy 84,0 l 269,0 qx 560,100 l 560,114 qy 129,200 l 106,200 qx 0,84 x"/>
                            </v:shape>
                            <v:shape style='left: 0; width: 1000; height: 1000; flip:y;' fill="true" fillcolor="#F4AB66" stroke="false" coordorigin="0 0" coordsize="560 200">
                            <v:path v="m 0,36 qy 95,0 l 168,0 qx 560,96 l 560,122 qy 129,200 l 84,200 qx 0,58 x"/>
                            </v:shape>
                            <v:shape style='left: 0; width: 1000; height: 1000; flip:y;' strokeweight="1" strokecolor="#000000" fill="false" coordorigin="0 0" coordsize="560 200">
                            <v:path v="m 0,50 qy 106,0 l 241,0 qx 560,96 l 560,120 qy 118,200 l 90,200 qx 0,58 x"/>
                            <![endif]-->
                            <td>
                              Main Content Here
                            </td>
                            <!--[if mso]>
                            </v:shape>
                            </v:group>
                            <![endif]-->
                            <!--[if !mso]-->
                          </tr>
                        </table>
                      </td>
                    </tr>
                  </table>
                </td>
              </tr>
            </table>
          </td>
          <!--<![endif]-->
        </tr>
      </table>
    </td>
  </tr>
</table>
```

```css
.fullshape1 {
border-radius: 15% 77% 70% 17% / 71% 39% 48% 18% !important;
}
.fullshape2 {
border-radius: 51% 33% 32% 24% / 30% 58% 33% 30%  !important;
}
.outline2 {
border-radius: 65% 41% 31% 16% / 41% 41% 51% 31% !important;
border: 1px solid black !important;
mso-border-alt: none !important;
}
.bg_f4ab66 { background-color: #f4ab66; }
.bg_f4cc66 { background-color: #f4cc66; }
```


<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/ -->
