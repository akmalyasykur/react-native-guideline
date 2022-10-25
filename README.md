# Coding Guidelines - React Native

# Table of Contents

<!--ts-->
* [Basic Rules](#basic-rules)
* [Folder Structure](#folder-structure)
* [Rules](#rules)
    * [Naming](#naming)
    * [Ordering](#ordering)
    * [Alignment](#alignment)
    * [Quotes](#quotes)
    * [Tags](#tags)
    * [Props](#props)
    * [Multi-line JSX](#multi-line-jsx)
    * [Stateless function components](#stateless-function-components)
    * [Commenting Conventions](#commenting-conventions)
    * [PropTypes declarations](#proptypes-declarations)
    * [Prefixing none React methods](#prefixing-none-react-methods)
    * [Prefixing component wide variables](#prefixing-component-wide-variables)
    * [Using handler methods](#using-handler-methods)
    * [Closing Components without children](#closing-components-without-children)
    * [Formatting Attributes](#formatting-attributes)
    * [Inline CSS styles](#inline-css-styles)
* [Attention](#attention)
    * [Don’t Repeat Yourself](#dont-repeat-yourself)
    * [Remove all trash from the final app build](#remove-all-trash-from-the-final-app-build)
* [Working with DOM listeners](#working-with-dom-listeners)
* [Sources](#sources)
<!--te-->

## Basic Rules

- Only include one React component per file.
- Always use JSX syntax.
- Using english for all naming.

## Folder Structure
- All the components except global components should be written inside the components folder under src folder.
- All the global components, global styles, global data etc .. should be written in the globals folder under src folder.
```
project
├── android
├── ios
├── node_modules
├── src
│   ├── assetss
│   │   ├── fonts
│   │   │   └── **/*.ttf
│   │   └── images
│   │       └── **/*.png
│   ├── components
│   │   ├── Component1.js
│   │   ├── Component2.js
│   │   ├── index.js
│   │   └── ...
│   ├── cofigs
│   │   ├── provider.js
│   │   ├── url.js
│   │   └── wl.js
│   ├── navigations
│   │   ├── routes
│   │   │   ├── ppob
│   │   │   │   └── **/*.js
│   │   │   └── **/*.js
│   │   └── **/*.js
│   ├── pages
│   │   ├── page
│   │   │   ├── subpage
│   │   │   │   ├── Component1.js
│   │   │   │   ├── Component2.js
│   │   │   │   ├── index.js
│   │   │   │   └── ...
│   │   │   └── ...
│   │   └── ...
│   ├── reducers
│   │   ├── action
│   │   ├── config
│   │   ├── reducer
│   │   └── **/*.js
│   ├── styles
│   │   ├── colors.js
│   │   ├── font.js
│   │   ├── index.js
│   │   └── style.js
│   ├── utilities
│   │   ├── datas
│   │   ├── functions
│   │   ├── helpers
│   │   └── global.js
│   ├── index.js
├── App.js
├── app.json
├── index.js
├── metroconfig.js
├── react-native.config.js
├── README.md
├── package.json
└── .gitignore
```

## Rules

### Naming
- Use english for all naming
- The object and variable declaration should always in camel case statement. If we use semicolon then use in all places at the end of statement or do not use.
````javascript
let textExample = “Hello World”;

OR

let textExample = “Hello World”
````
- File- and component name need to be identical, The class name should be declared as the file name that will be easy during importing and to maintain the standard declaration.
- Use the PascalCase naming convention for filenames as well as component names except index.js, e.g. GlobalHeader.js
```javascript
// Bad
// Filename: foo.js
class Foo extends React.Component {}
export default Foo;

// Good
// Filename: Foo.js
class Foo extends React.Component {}
export default Foo;

//except index.js
class Index extends React.Component {}
export default Index;
```
- A folder and sub folder name should always start with small letters and the files belongs the folders is always in pascal case. The term “PascalCase” comes from software development, it may describe any compound word in which the first letter of each word is capitalized. Examples include the company “MasterCard” the video game “StarCraft” and of course, the website “TechTerms”
```
project
├── account
├── buy
├── downline
├── home
│   ├── components
│   │   ├── FlashSale.js
│   │   ├── index.js
│   │   └── ...
│   └── index.js
└── ...
```
- When the file is in a folder with same name, we don’t need to repeat the name. That means, `components/user/form/Form.js`, would be named as `components/user/form/index.js`.

### Ordering

- Ordering for class extends React.Component:

1. optional static methods
2. constructor
1. getChildContext
1. componentWillMount
1. componentDidMount
1. componentWillReceiveProps
1. shouldComponentUpdate
1. componentWillUpdate
1. componentDidUpdate
1. componentWillUnmount
1. *getter methods for render* like `_getServerData()` or `_getApiData()`
1. *clickHandlers or eventHandlers* like `_onSelect()` or `_onChangeDescription()`
1. *Optional render methods* like `_renderView()` or `_renderProfilePicture()`
1. render

```javascript
React.createClass({
    propTypes: {},
    mixins : [],
    static:  navigationOptions = {},
    constructor(props) {},

    getInitialState: function() {},
    getDefaultProps: function() {},

    componentWillMount : function() {},
    componentDidMount : function() {},
    componentWillReceiveProps: function() {},
    shouldComponentUpdate: function() {},
    componentWillUpdate: function() {},
    componentWillUnmount : function() {},

    _getServerData : function() {},
    _onSelect : function() {},
    _renderView : function() {},

    render : function() {}

})
```

### Alignment
- Follow these alignment styles for JSX syntax

```javascript
// bad
<Foo superLongParam="bar"
     anotherSuperLongParam="baz" />
// good
<Foo
  superLongParam="bar"
  anotherSuperLongParam="baz"
/>
// if props fit in one line then keep it on the same line
<Foo bar="bar" />
// children get indented normally
<Foo
  superLongParam="bar"
  anotherSuperLongParam="baz"
>
    <Spazz />
</Foo>
```


### Quotes

- Always use double quotes (`"`) for JSX attributes, but single quotes for all other JS.

```javascript
// bad
<Foo bar='bar' />
// good
<Foo bar="bar" />
// bad
<Foo style={{ left: "20px" }} />
// good
<Foo style={{ left: '20px' }} />

// bad
<Foo
    UserName="hello"
    phone_number={12345678}
/>
// good
<Foo
    userName="hello"
    phoneNumber={12345678}
/>
```
### Tags
- Always self-close tags that have no children.
```javascript
// bad
<Foo className="stuff"></Foo>
// good
<Foo className="stuff" />
```

### Props
- Always use camelCase for prop names.
- If your component has multi-line properties, close its tag on a new line.
```javascript
// bad
<Foo
    bar="bar"
    baz="baz" />
// good
<Foo
    bar="bar"
    baz="baz"
/>
```

### Multi-line JSX
No matter how few elements are being returned, I choose to write any JSX which contains nested elements across multiple lines with indentation to enhance readability, i.e:
```javascript
//bad
return (<div><ComponentOne /><ComponentTwo /></div>);

//good
return (
    <div>
        <ComponentOne />
        <ComponentTwo />
    </div>
);
````

### Stateless function components
- We should create class component when we have to use state otherwise we should use functional component.
- Add at least one blank line between method and property definitions.
- There should be no line space between two similar looking statements or similar bunch of code applies to the same activity.
````javascript
const [loading, setLoading] = useState(false);
const [name, setName] = useState(‘Ramu’);
const [age, setAge] = useState(‘22’);

if (apiInProgress){
    setLoading(true);
    setName(null);
}
````

- For stateless components use the function syntax, introduced in React 0.14.
```javascript
// Using an ES2015 (ES6) arrow function:
var Aquarium = (props) => {
    var fish = getFish(props.species);
    return <Tank>{fish}</Tank>;
};
// Or with destructuring and an implicit return, simply:
var Aquarium = ({species}) => (
    <Tank>
        {getFish(species)}
    </Tank>
);
// Then use: <Aquarium species="rainbowfish" />
```

[Read More](http://facebook.github.io/react/blog/2015/09/10/react-v0.14-rc1.html#stateless-function-components)

### Commenting Conventions
- Place the comment on a separate line, not at the end of a line of code.
- Begin comment text with an uppercase letter.
- End comment text with a period.
- Insert one space between the comment delimiter (//) and the comment text.
- Attach comments to code only where necessary.


### PropTypes declarations

- Group them into required/none-required
- Alphabetically sort each group
- Separate them by a new line

```javascript
static propTypes = {
    blank: React.PropTypes.bool.isRequired,
    block: React.PropTypes.bool.isRequired,
    size: React.PropTypes.string.isRequired,
    to: React.PropTypes.string.isRequired,
    disabled: React.PropTypes.bool,
};
```


### Prefixing none React methods
Prefix all none React methods within a component with an underscore.

```javascript
class Foo extends React.Component {
    componentDidMount() {
        this._update();
    }
    
    _update() {
        // e.g. update position
    }
    
    render() {
        return (
            <div>foo</div>
        );
    }
}   
```

### Prefixing component wide variables
In the exception that you do not want to place a component wide variables on the state, you have to prefix it with an underscore.

```javascript
class Foo extends React.Component {
    componentDidMount() {
        this._el = React.FindDOMNode(this.refs.foo);
    }
    
    render() {
        return (
            <div>foo</div>
        );
    }
}   
```


### Using handler methods

- Name methods using `'_handle' + triggering event`, e.g. `_handleClick`
- Bind handler using the ES6 arrow syntax, so inside the callback it has always the right context

```javascript
class Foo extends React.Component {
    _handleClick = (e) => {
        this.setState(
            {
                clicked: true
            }
        );
    }
    
    render() {
        return (
            <button onClick={this._handleClick}>Submit</button>
        );
    }
}
```



### Closing Components without children

```javascript
render() {
    return (
        <Foo>
            <Bar />
        </Foo>
    );
}
```

### Formatting Attributes

```javascript
<input
    type="text"
    value={this.state.foo}
    onChange={this._handleInputChange.bind(this, 'foo')}
/>
```

### Inline CSS styles
Static properties should be set in the SCSS, dynamic ones in JS.

```css
.Foo {
    background-color: #ff0;
}
```

```javascript
class Foo extends React.Component {
    render() {
        
        const styles = {
            'transform': 'translateX(' + this.state.position + ' + px)'
        };
    
        return (
            <div className="Foo" styles={classes}>Foo Header</div>
        )
    };
}
```

## Attention

### Don’t Repeat Yourself
One of the basic principles of software development is Don’t Repeat Yourself. We must not write the same piece of code twice. Whenever you write the same piece of code twice, you must try to refactor it into something reusable, even if not completely.

You can create your own reusable components. For example, if your app contains multiple modals, you can create a reusable `<Modal>` component and use it across any screen within your app. Not only input fields, if your app contains multiple buttons, but you can also create a reusable `<Button>` component and use it anywhere within your app. Likewise, you can create any number of reusable components based on your app architecture.

if component is used in many different folders put component in `./src/components` folder as global component. otherwise put it in components folder parallel to file

### Less Dependencies
it's better to make your own components if you feel you can than add the dependencies. too many dependencies will affect react performance and make it difficult to upgrade version.

if you have to add dependencies, try using one that still supports updates and is widely used

### Remove all trash from the final app build
Remove all the `console.log()`, `console.warn()` statements and unused `plugins/dependencies`, `imports`, `variable`, `method/function`, `components`, `images`, etc... from the final build as too many trash may impact the performance of the app and to keep the coding clean.


## Working with DOM listeners
http://facebook.github.io/react/tips/dom-event-listeners.html


## Sources

- https://github.com/kriasoft/react-starter-kit/blob/master/docs/react-style-guide.md
- https://web-design-weekly.com/2015/01/29/opinionated-guide-react-js-best-practices-conventions/

## Happy Coding 😁🤘☕