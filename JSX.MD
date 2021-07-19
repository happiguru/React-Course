### Understanding JSX

Now that we know what React is, let's take a look at a few terms and concepts that will come up throughout the rest of the series.

### JSX/ES5/ES6

- ES5 (the ES stands for ECMAScript) is basically "regular JavaScript." It has been supported by all major browsers for several years.

ES6 is a new version of JavaScript that adds some nice syntactical and functional additions. It was finalized in 2015. ES6 is almost fully supported by all major browsers.

#### JSX
As we'll see, all of our React components have a render function that specifies what the HTML output of our React component will be. JavaScript eXtension, or more commonly JSX, is a React extension that allows us to write JavaScript that looks like HTML.

Example is:

```
class HelloWorld extends React.Component {
  render() {
    return (
      <h1 className='large'>Hello World</h1>
    );
  }
}
```

The render() function in the HelloWorld component looks like it's returning HTML, but this is actually JSX. The JSX is translated to regular JavaScript at runtime. That component, after translation, looks like this:

```
class HelloWorld extends React.Component {
  render() {
    return (
      React.createElement(
        'h1',
        {className: 'large'},
        'Hello World'
      )
    );
  }
}
```

While JSX looks like HTML, it is actually just a terser way to write a React.createElement() declaration. When a component renders, it outputs a tree of React elements or a virtual representation of the HTML elements this component outputs. React will then determine what changes to make to the actual DOM based on this React element representation. In the case of the HelloWorld component, the HTML that React writes to the DOM will look like this:

```
<h1 class='large'>Hello World</h1>
```

The class extends syntax we used in our first React component is ES6 syntax. It allows us to write objects using a familiar Object-Oriented style. In ES5, the class syntax might be translated as:

```
var HelloWorld = function() {}
Object.extends(HelloWorld, React.Component)
HelloWorld.prototype.render = function() {}
```

If we want to write pure JavaScript instead of rely on a JSX compiler, we can just write the React.createElement() function and not worry about the layer of abstraction. But we like JSX. It's especially more readable with complex components. Consider the following JSX:

```
<div>
  <img src="profile.jpg" alt="Profile photo" />
  <h1>Welcome back Ari</h1>
</div>
```

The JavaScript delivered to the browser will look like this:

```React.createElement("div", null,
  React.createElement("img", {src: "profile.jpg", alt: "Profile photo"}),
  React.createElement("h1", null, "Welcome back Ari")
);
```