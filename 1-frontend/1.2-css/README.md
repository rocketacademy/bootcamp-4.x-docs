# 1.2: CSS

## Learning Objectives

1. CSS enables us to style HTML pages by applying styles and layout properties on HTML elements
2. Know how to apply CSS styles to HTML elements via type, class and ID selectors
3. Understand the concept of CSS specificity

## Introduction

CSS (Cascading Style Sheets) enables styling of HTML pages by applying styles and layout properties on HTML elements. CSS styles customise size, borders, font, background, opacity, position and more.

The following CSS rule applies `text-align` and `color` properties to all HTML `p` tags.

```css
p {
  text-align: center;
  color: red;
}
```

## CSS Rules

CSS consists of **rules** like the example above, where rules consist of **selectors** (`p` tag above) and **declarations** (`text-align` and `color` declarations above).

CSS "selectors" can be HTML tags, CSS "classes", CSS "IDs", or any combination of tags, classes and IDs. CSS classes and IDs are typically kebab-case strings that we label HTML elements with to apply styles to those elements with CSS. Classes are reusable across multiple elements; IDs are meant for only 1 element. Class selectors are prefixed with `.` and ID selectors are prefixed with `#`. When developing applications, it is imperative that one utilises CSS "classes" to preserve style that is consistent across multiple pages or elements, this makes maintenance and alterations of these commonly styled elements straightforward and easy.&#x20;

```css
.my-class {
  color: red;
}

#my-id {
  color: green;
}

.my-class #my-id {
  color: blue;
}
```

We can tag HTML elements with classes and IDs by adding `class` and `id` attributes to HTML tags like in the following example.

```markup
<p class="my-class" id="my-id">I have both a class and an ID!</p>
```

CSS "declarations" tell our browsers what styles to apply to HTML elements that match the CSS rule's selector. Declarations consist of a **property** and a **value**.

```css
selector {
  property: value;
}
```

## Common CSS properties

If you would like to explore the endless styling and presentation possibilities that CSS offers please have a [look here](https://www.w3schools.com/css/). Otherwise here are some common CSS properties that you should become aware of.

| CSS property     | Description                                                                                                                                                                                                                                   | Example usage                                                                |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| color            | Set the text `color` using predefined colour names, or RGB, HEX, HSL, RGBA, HSLA values.                                                                                                                                                      | <p></p><p>p {<br>    color: #ffffff;<br>}</p>                                |
| background-color | Set the `background-color` using predefined colour names, or RGB, HEX, HSL, RGBA, HSLA values.                                                                                                                                                | <p>div {<br>    background-color : #fff;<br>}</p>                            |
| border           | The `border` property allows you to set the width, style and colour of the border. There are various styles border which are affected by colour and width. It is possible to set each of these properties individually.                       | <p>div { </p><p>    border: 2px solid #000;</p><p>}</p>                      |
| font-size        | Set the `font-size` property, this sets the size of the text. It is possible to apply relative or absolute size when setting this property.                                                                                                   | <p>p {<br>    font-size: 12px;<br>}</p>                                      |
| margin           | Set the space around the element, this is outside of any defined borders. You can define `margin` using shorthand or targeting individual sides. In the example we are using shorthand to define the top, right, bottom and then left margin  | <p>div { </p><p>    margin: 10px 15px 10px                15px;</p><p>}</p>  |
| padding          | Set the space inside the element, this is inside of any defined borders. You can define `padding` using shorthand or targeting individual sides. In the example we are using shorthand to define the top, right, bottom and then left padding | <p>div { </p><p>    padding: 10px 15px 10px                15px;</p><p>}</p> |
| height           | Set the `height` of the element. Commonly this is set with `length`, `%` or `inherit`. But there is more.  Note that this does not include margins, borders or padding.                                                                       | <p>div { </p><p>    height: 50%;</p><p>}</p>                                 |
| width            | Set the `width` of the element. Commonly this is set with `length`, `%` or `inherit`. Note that this does not include margins, borders or padding.                                                                                            | <p>div { </p><p>    width: 200px;</p><p>}</p>                                |
| overflow         | The `overflow` property informs the browser whether it should add scrollbars or clip the content when its too larger to fit in its specified area.                                                                                            | <p>div {<br>    overflow: scroll;<br>}</p>                                   |

## Using CSS classes&#x20;

When styling our HTML elements it is possible to apply multiple class names to the element, to do so just add the whatever class names within the class property separated by a space. Note that the last class takes precedence in terms of applied style.&#x20;

```html
    <p class="bordered centered red">Style me!</p>
```

## CSS Specificity

The word "cascading" in CSS refers to the hierarchy that CSS uses to apply styles to HTML elements, also known as "**specificity**". To illustrate specificity we will share 3 examples.

### Example 1: Selector hierarchy

Generally, styles applied to ID selectors take precedence over styles applied to class selectors, which take precedence over styles applied to HTML tag selectors (aka type selectors).

In the following example, the 1st paragraph will have colour red, the 2nd green, the 3rd blue. This is because styles applied to CSS IDs take precedence over styles applied to CSS classes, which take precedence over styles applied to HTML tags.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        color: red;
      }
      .para-class {
        color: green;
      }
      #para-id {
        color: blue;
      }
    </style>
  </head>
  <body>
    <p>Every paragraph will be affected by the style.</p>
    <p class="para-class">Me too!</p>
    <p class="para-class" id="para-id">And me!</p>
  </body>
</html>
```

### Example 2: Directness hierarchy

Regardless of selector type (ID, class or type selector), CSS rules that apply more directly to selected HTML elements will take precedence over CSS rules less directly applied. For example, if I apply a CSS rule with an ID selector on a parent HTML element and a CSS rule with a type selector on the child, the type selector's declarations will override the ID selector's.

In the following example, the paragraph text will be red even though its parent element's CSS rule specifies the colour blue. This is because the `p` selector applies more directly to the `p` tag than the `div-id` selector.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        color: red;
      }
      #div-id {
        color: blue;
      }
    </style>
  </head>
  <body>
    <div id="div-id">
      <p>Roses are red</p>
    </div>
  </body>
</html>
```

### Example 3: Style location hierarchy

CSS rules declared inline (aka "inline" styles) take precedence over CSS rules declared within `style` tags in the same file (aka "internal" styles), which take precedence over CSS rules declared in separate files (aka "external" styles).

Inline styles can be convenient for testing styles in development but are troublesome to maintain because it becomes difficult to keep track of which styles are declared where.

{% code title="Inline styles" %}
```html
<p style="color: red;">This text is red</p>
```
{% endcode %}

Internal styles allow us to centralise styles for a given HTML file in `head`. Not often used because internal styles cannot be re-used across HTML files.

{% code title="Internal styles" %}
```html
<html>
  <head>
    <style>
      p {
        color: green;
      }
    </style>
  </head>
  <body>
    <p>This text is green</p>
  </body>
</html>
```
{% endcode %}

External styles are styles declared in CSS-specific files and "imported" with `link` tags in relevant HTML files. Most apps use external styles to re-use CSS styles across multiple HTML files.

{% code title="External styles" %}
```html
<html>
  <head>
    <link rel="“stylesheet”" href="styles.css" />
  </head>
  <body>
    <p>This text is blue</p>
  </body>
</html>
```
{% endcode %}

{% code title="styles.css" %}
```css
p {
  color: blue;
}
```
{% endcode %}

Unless we have a strong reason not to, Rocket recommends using external styles for all CSS to keep our CSS rules centralised in CSS files that can be re-used across HTML files.

Unless we plan to be CSS specialists, we do not need to memorise exact CSS specificity of every permutation of selectors and HTML elements. Most browsers provide precise tools to debug CSS specificity, and [W3Schools documents](https://www.w3schools.com/css/css\_specificity.asp) how to calculate CSS specificity when we need to.

## Exercises

### Apply CSS to HTML

Apply CSS to an HTML file. Create an `index.html` file with the contents below and open it in Chrome.

{% code title="index.html" %}
```html
<html>
  <head>
    <title>My HTML Page</title>
  </head>
  <body>
    <h1>I will be styled</h1>
  </body>
</html>
```
{% endcode %}

Notice what the un-styled HTML looks like. Now insert the following `style` HTML element within the `head` tags in `index.html`.

```html
<style>
  h1 {
    background-color: blue;
    color: white;
  }
</style>
```

Refresh `index.html` in Chrome and observe the change to the `h1` element.

### Codecademy Learn CSS

Complete all exercises in the following Codecademy lessons when they are assigned in the Rocket course schedule. You will need to register a Codecademy account if you have not already.

1. [Setup and Syntax](https://www.codecademy.com/courses/learn-css/lessons/learn-css-setup-and-syntax/exercises/intro-to-css)
2. [Selectors](https://www.codecademy.com/courses/learn-css/lessons/learn-css-selectors/exercises/type)
3. [Visual Rules](https://www.codecademy.com/courses/learn-css/lessons/css-visual-rules/exercises/font-family)
4. [The Box Model](https://www.codecademy.com/courses/learn-css/lessons/box-model-intro/exercises/box-model)
5. [Changing the Box Model](https://www.codecademy.com/courses/learn-css/lessons/box-model-new/exercises/box-content)
