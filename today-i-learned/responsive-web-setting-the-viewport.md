# Responsive Web: Setting the Viewport

The viewport is the user's visible area of a webpage, be it on a laptop screen, phone, external monitor, etc. 

HTML5 introduced a method to let web designers take control over the viewport, through the `<meta>` tag.

You should include the following `<meta>` viewport element in all your web pages: 

```markup
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This gives the browser instructions on how to control the page's dimensions and scaling.

The `width=device-width` part sets the width of the page to follow the screen-width of the device \(which will vary depending on the device\).

The `initial-scale=1.0` part sets the initial zoom level when the page is first loaded by the browser. 

{% embed url="https://www.w3schools.com/css/css\_rwd\_viewport.asp" %}

