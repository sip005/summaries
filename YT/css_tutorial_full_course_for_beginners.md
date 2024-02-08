# [CSS Tutorial – Full Course for Beginners](https://youtu.be/OXGznpKZ_sA?si=3K8Wsrec7byR2y1U)  

[Chapter - 04: Units and Sizes](#chapter---04:-units-and-sizes)
[Chapter - 05: Box Model](#chapter---05:-box-model) 

### Chapter - 04: Units and Sizes

Default font size in a browser is `16px`. We only use the `px` unit, when we require absolute size. For example we can use `px` when defiing the size of border. In general we will use the relative sizing for the fonts.

H1 is block level element. We can use percentage to change its width and height. We need to remenber that percentage is relative to the parent.  

"REM" stands for "Root EM." It is a unit of measurement in CSS (Cascading Style Sheets) used for specifying sizes in a relative manner. The size is relative to the root element's font size, typically set on the `<html>` or `<body>` element.

Using REM units can make it easier to create a scalable and maintainable design, as it allows you to define sizes based on a single root font size, and adjustments to that root size will affect the entire layout consistently.

For example, if the root font size is set to 16 pixels, and you have an element with a font size of 2rem, it will be equivalent to 32 pixels (2 times the root font size).

```css
html {
  font-size: 16px; /* Set the root font size */
}

body {
  font-size: 1rem; /* This is 16px (1 times the root font size) */
}

.someElement {
  font-size: 2rem; /* This will be 32px (2 times the root font size) */
}

```

References:
1. [MDN web docs - CSS values and units ](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units)  

### Chapter - 05: Box Model  

The CSS Box Model has a hierarchical structure with four main components, each building upon the previous one. Here's the hierarchy of the CSS Box Model from innermost to outermost:

1. **Content:** This is the innermost part of the box, where the actual content, such as text or images, is placed. The size of the content area is determined by the `width` and `height` properties.

2. **Padding:** Surrounding the content is the padding, which is the space between the content and the border. Padding is defined using the `padding` property. It provides internal spacing within the element.

3. **Border:** The border surrounds the padding and content. It is defined using the `border` property and can have properties like `color`, `style`, and `width`. The border separates the content from the padding and provides a visual boundary.

4. **Margin:** The outermost part of the box is the margin, which is the space between the border of the element and its surrounding elements. The margin is defined using the `margin` property. It creates space between elements on the page.  

```css
                    +-----------------------------+
                    |          Margin             |
                    |                             |
                    |    +-------------------+    |
                    |    |       Border      |    |
                    |    |                   |    |
                    |    |   +-----------+   |    |
                    |    |   |  Padding  |   |    |
                    |    |   |           |   |    |
                    |    |   |  Content  |   |    |
                    |    |   |           |   |    |
                    |    |   +-----------+   |    |
                    |    |                   |    |
                    |    +-------------------+    |
                    |                             |
                    +-----------------------------+

```  


Understanding this hierarchy is crucial for designing and positioning elements on a web page. When you set properties like `width`, `height`, `padding`, `border`, and `margin`, we are essentially manipulating these different layers of the box model to achieve the desired layout.  

