# Using Styling Libraries with React

Learning Objectives

1. Understand what React-Bootstrap is
2. Implement React-Bootstrap into React Applications
3. Using React-Bootstrap pre-styled components

### React Bootstrap Initialisation

React Bootstrap is a popular frontend styling library, it contains pre-built style and functionalities for out of the box easy implementation. This tool is integrated well with ReactJs and is geared for beginners to test out and implement styling libraries. Developers are even able to customize Bootstrap within custom scss stylesheets, feel free to learn more about it [here](https://react-bootstrap.github.io/getting-started/introduction#customize-bootstrap).&#x20;

To implement React Bootstrap into a React application open a CLI interface and change directory to your current project. Here you can run this command:

```
npm install react-bootstrap bootstrap
```

This will install React Bootstrap and the bootstrap package within the application, there is still one more step that must be taken before you can utilise all of React-Bootstrap in your app.

Go to the main.jsx within your React application and this line at the top of the file:

```jsx
import 'bootstrap/dist/css/bootstrap.min.css';
```

This line imports the CSS for bootstrap into your application, any child components of this file will be able to access and utilise React-Bootstrap styling, pre-made components, utilities and alignment system.&#x20;

Now that Bootstrap has been implemented in your application it might be a good idea to look at some of the pre-styled components you can implement, look at some examples and usage [here](https://react-bootstrap.github.io/components/alerts/).

To showcase implementing React Bootstrap into a React Application we will implement some new styled buttons on our previously edited boilerplate code from our previous section.

### React Bootstrap Component&#x20;

We will import Button from react-bootstrap such that we get pre-styled buttons without much effort. Alter the App.js file to reflect code below:

{% code lineNumbers="true" %}
```jsx
import logo from "./logo.svg";
import "./App.css";
import { Button } from "react-bootstrap";

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
        <Button variant="primary">Bootstrap Button</Button>
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

The output on the browser is as follows:

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-25 at 4.33.48 PM.png" alt=""><figcaption><p>Bootstrap added</p></figcaption></figure>

From the image above we can see a new blue button has been added into the application, we didnt style this button, it was all React-Bootstrap. This is how you can utilise React-Bootstrap within a React application. Utilise more complex components using this styling library to save yourself time during development.

Checkout more React-Bootstrap Components [here](https://react-bootstrap.netlify.app/docs/components/accordion). Use a combination of pre-styled and custom components to quickly develop applications that can be tailored to your need, just be aware of the props that you can pass. Constantly run your React application to see whether or not your application is being styled appropriately. And remember when styling with React-Bootstrap you just need to import the component's that you need at the top of the page, then you can use them like normal HTML tags in your JSX.

### React Bootstrap Grid System

One of the most powerful features of React-Bootstrap is its grid system, which facilitates mobile responsive websites without having to restyle every single element on your page. Learn more about the grid system:

{% embed url="https://react-bootstrap.netlify.app/docs/layout/grid/" %}
Grid System React Bootstrap
{% endembed %}

When implementing the grid system be sure to:

1. Use a react-bootstrap `Container` Component
2. Use `Row` and `Column` Components within the `Container` to display your information
   1. Note that each row can be broken into 12 columns
   2. Each section can take up multiple spaces
3. Uncover and understand the [Breakpoint system](https://react-bootstrap.netlify.app/docs/layout/breakpoints) in react-bootstrap
4. Wire-framing and planning out how your component will look will make using grid easier

Here is a simple implementation of the react-bootstrap grid system

```jsx
 <Container>
          <Row>
            <Col style={columnStyle}> 1 of 1</Col>
          </Row>
          <br />
          <Row>
            <Col style={columnStyle}> 1 of 2</Col>
            <Col style={columnStyle}> 2 of 2</Col>
          </Row>
          <br />
          <Row>
            <Col style={columnStyle}> 1 of 4</Col>
            <Col style={columnStyle}> 2 of 4</Col>
            <Col style={columnStyle}> 3 of 4</Col>
            <Col style={columnStyle}> 4 of 4</Col>
          </Row>
          <br />
          <Row>
            <Col style={columnStyle}> 1 of 6</Col>
            <Col style={columnStyle}> 2 of 6</Col>
            <Col style={columnStyle}> 3 of 6</Col>
            <Col style={columnStyle}> 4 of 6</Col>
            <Col style={columnStyle}> 5 of 6</Col>
            <Col style={columnStyle}> 6 of 6</Col>
          </Row>
 </Container>
```

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-26 at 10.48.04 AM.png" alt=""><figcaption><p>Simple Grid System</p></figcaption></figure>

It is possible to make the `Col` Components respond to the windows width, based off the breakpoints that were pointed out earlier. This allows columns to wrap and resize their content to ensure that data is shown exactly as intended, to do this we need to make use of Bootstraps breakpoint properties on our `Col` Components as shown below. You are able to apply as many breakpoint properties on a `Col` as are needed.&#x20;

<pre class="language-jsx"><code class="lang-jsx">&#x3C;Container>
          &#x3C;Row>
          
          {/* 
            xl = On an extra large screen the Col takes up the full width of the Container
            lg = On a large screen the Col takes up half the width of the Container
            md = On a medium screen the Col takes up a third of the width of the Container
            sm = On a small screen the Col takes up a quarter of the width of the Container
            This allows the columns to dynamically alter depending on the window size that the user is using. 
          */}
            
            &#x3C;Col style={columnStyle} xl={12} lg={6} md={4} sm={3}>
              1 of 6
            &#x3C;/Col>
            &#x3C;Col style={columnStyle} xl={12} lg={6} md={4} sm={3}>
              2 of 6
            &#x3C;/Col>
            &#x3C;Col style={columnStyle} xl={12} lg={6} md={4} sm={3}>
              3 of 6
            &#x3C;/Col>
            &#x3C;Col style={columnStyle} xl={12} lg={6} md={4} sm={3}>
              4 of 6
            &#x3C;/Col>
            &#x3C;Col style={columnStyle} xl={12} lg={6} md={4} sm={3}>
              5 of 6
            &#x3C;/Col>
            &#x3C;Col style={columnStyle} xl={12} lg={6} md={4} sm={3}>
              6 of 6
            &#x3C;/Col>
          &#x3C;/Row>
<strong>        &#x3C;/Container>
</strong></code></pre>

Below is the output of the code above, depending on the size of the window.

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-26 at 11.06.17 AM.png" alt=""><figcaption><p>Extra Large Screen ≥1200px</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-26 at 11.06.49 AM.png" alt=""><figcaption><p>Large Screen ≥992px</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-26 at 11.07.26 AM.png" alt=""><figcaption><p>Medium Screen ≥768x</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-26 at 11.07.50 AM.png" alt=""><figcaption><p>Small Screen ≥576px</p></figcaption></figure>

The Grid system in `react-bootstrap` affords developers an easy way to dynamically resize content dependant on their users screens. This system of Bootstrap Components comes together to build fully responsive webpages, it should be noted that the underlying system used here is flexbox. This system is a fantastic way to ensure that an applications content can be visible to users across multiple device sizes without the need to add in hundreds of @mediaqueries.&#x20;



