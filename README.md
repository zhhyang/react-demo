Demo01: Render JSX (source)

The template syntax in React is called JSX. It is allowed in JSX to put HTML tags directly into JavaScript codes. ReactDOM.render() is the method which translates JSX into HTML, and renders it into the specified DOM node.

ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
Attention, you have to use <script type="text/babel"> to indicate JSX codes, and include browser.min.js, which is a browser version of Babel and could be get inside a babel-core npm release, to actually perform the transformation in the browser.

Before v0.14, React use JSTransform.js to translate <script type="text/jsx">. It has been deprecated (more info).

Demo02: Use JavaScript in JSX (source)

You could also use JavaScript in JSX. It takes angle brackets (<) as the beginning of HTML syntax, and curly brackets ({) as the beginning of JavaScript syntax.

var names = ['Alice', 'Emily', 'Kate'];

ReactDOM.render(
  <div>
  {
    names.map(function (name) {
      return <div>Hello, {name}!</div>
    })
  }
  </div>,
  document.getElementById('example')
);
Demo03: Use array in JSX (source)

If a JavaScript variable is array, JSX will implicitly concat all members of the array.

var arr = [
  <h1>Hello world!</h1>,
  <h2>React is awesome</h2>,
];
ReactDOM.render(
  <div>{arr}</div>,
  document.getElementById('example')
);
Demo04: Define a component (source)

React.createClass() creates a component class, which implements a render method to return an component instance of the class. You don't need to call new on the class in order to get an instance, just use it as a normal HTML tag.

var HelloMessage = React.createClass({
  render: function() {
    return <h1>Hello {this.props.name}</h1>;
  }
});

ReactDOM.render(
  <HelloMessage name="John" />,
  document.getElementById('example')
);
Components can have attributes, and you can use this.props.[attribute] to access them, just like this.props.name of <HelloMessage name="John" /> is John.