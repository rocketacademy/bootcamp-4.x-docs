---
description: ReactJs Styling
---

# Styling in ReactJs

Learning Objectives

1. Understand how to implement Style within ReactJs
2. Style Components using in-line style
3. Style Components using Stylesheet and classes

## Introduction

In a previous section we introduced CSS, which is used to apply styles to HTML pages beautifying content. Within ReactJs we can use CSS in order style our rendered output, you can apply any CSS style within React. It should be noted that because we are writing JSX, there are some different rules than applying style in HTML. An important distinction is that the className property is used on JSX elements to apply classes, this is because the word class in JavaScript is a reserved key word. We can use the boilerplate code that is generated from the npx Create React Application, we actually have some built in styling. Below is an example of the boilerplate output.

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 1.08.08 PM.png" alt=""><figcaption><p>Create React Application</p></figcaption></figure>



### In-line Styling

To apply style in ReactJs we can apply in-line style. This has the highest level of CSS precedence as it is evaluated last by the browser, at this stage the component is being styled by a stylesheet, but we can override this. To demonstrate this we will alter the text 'Edit src ....' such that it is bold and red.  A key difference that we can see below is that when applying in-line styling we write camelCased property names, not kebab-cased, like we would in pure HTML applications.

Go to the App.js file, alter the parent div of your local code to reflect the block below:

{% code title="" lineNumbers="true" %}
```jsx
 <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p style={{ color: "red", fontWeight: "bold" }}>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
```
{% endcode %}



Notice how the opening p tag on line 4 contains a style property which equals to a double set of curly braces. This code specifies a style object, the properties within must be camelCased and the values must be written in strings. Moreover each property and value should be seperated by a common.

This is the resulting render in the browser.

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 1.25.46 PM.png" alt=""><figcaption><p>Create React Application In-line style</p></figcaption></figure>

### Style Objects

Another way to apply style in ReactJs would be to use JavaScript style objects that are passed to the JSX using the style property. In order to do this we create a JavaScript object that contains style and value, apply that to the JSX element using the className. Checkout the code and sample output below:

```jsx
function App() {

  const customHeaderStyle = {
    fontWeight: "900",
    color: "#ffffff",
    textDecoration: "#1bdb22 wavy underline",
  };
  
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p style={{ color: "red", fontWeight: "bold" }}>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <h1 style={customHeaderStyle}>This new header</h1>
        <br />
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-25 at 4.30.02 PM.png" alt=""><figcaption><p>New header added </p></figcaption></figure>

If you have multiple style objects that are consistent and used across components you could make a .js file that contains all of the common properties and import them into necessary components.&#x20;

### Stylesheets React

Another way one can apply style within Reactjs is through the stylesheet, as stated previously the App.js component is already affect by some boilerplate style, that should be found in App.css. We can alter the content further by adding new classes into the App.css stylesheet and by adding new classes to our App.js code.&#x20;

Lets change the link below to remove all text decoration such that we can apply our own style.

Alter your App.css, target the App-link class to reflect the code below:

```css
.App-link {
  color: #3324bd;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid #ff0000;
  background-color: #ffffff;
}
```

The output should look like this within the browser.



<figure><img src="../../.gitbook/assets/Screenshot 2023-10-25 at 4.31.57 PM.png" alt=""><figcaption><p>Stylesheet applied</p></figcaption></figure>

Stylesheets are used within the Application by importing them at the top of the component. The full component should be similar to the code below.

{% code lineNumbers="true" %}
```jsx
import logo from "./logo.svg";
import "./App.css";

function App() {

const customHeaderStyle = {
    fontWeight: "900",
    color: "#ffffff",
    textDecoration: "#1bdb22 wavy underline",
  };
  
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p style={{ color: "Red", fontWeight: "bold" }}>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <h1 style={customHeaderStyle}>This new header</h1>
        <br />
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```
{% endcode %}

In the component above we can see that we apply classes to JSX tags using the property className. It is possible to apply more than one className to a JSX tag just like in HTML. Generally when creating React applications developers would create common stylesheets for style that is consistent across components, and individual stylesheets for unique components that do not share style with other parts of the application.&#x20;
