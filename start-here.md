# Setup Basic App - Create React App

## create-react-app
Run `npx create-react-app .`

Run `npm start`.

![Image](/tutorial/app_basic.png)

As the message states, we can make changes to `App.js` to update the page. Let's make a few changes.

Edit `src/App.js`
``` javascript
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Hello World!
        </p>
      </header>
    </div>
  );
}

export default App;
```

So we've removed some unnecessary links, and changed the text. Let's save and update the site.

![Image](/tutorial/app_helloWorld.png)

Cool right?

For our Todo App, we are going to want to have a list of Todos, so let's go over making a new component.


## Basic Component
- Create a folder, `components`
- Create a new file, `List.js`

Edit `List.js`
``` javascript
import React from 'react'

function List() {
    return (
        
    );
}

export default List;
```

Here's our basic component. We are importing our necessary `React` library, defining our `List` component, and exporting it for use in `App.js`.

Let's think about this a bit. We are going to have a list of items, so let's define an array to hold that list, and make up some entries.

``` javascript
const itemList = ["Get milk", "Buy Amazon", "Take over the world"];
```

Now let's render this list by mapping each item in the array to a `<p>` tag.

Edit `List.js`
``` javascript
import React from 'react'

function List() {
    const itemList = ["Get milk", "Buy Amazon", "Take over the world"];

    return (
        itemList.map((item) => (
            <p>{item}</p>
        ))
    );
}

export default List;
```

Great! We've created our first custom component! Now we need to import it into `App.js` and use it.

Edit `App.js`
``` javascript
import logo from './logo.svg';
import './App.css';

import List from './components/List';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <List />
      </header>
    </div>
  );
}

export default App;
```

Now save, and reload the site.

![Image](/tutorial/app_withList.png)

Awesome! But that's just the start. We can make our component more dynamic using `props`.

## Component Props

Okay, so we have our `List.js` component, but it's not very dynamic. It just takes the array we specified and spits out each item as text. We can move the array out of the `List` component and provide it as a `prop` instead.

Edit `List.js`
``` javascript
import React from 'react'

function List(props) {
    const { itemList } = props;

    return (
        itemList.map((item) => (
            <p>{item}</p>
        ))
    );
}

export default List;
```

Now our `List` component is going to be looking for a `prop` called `itemList` that contains an array. We will provide that prop when we use the component.

``` javascript
<List itemList={["Get milk", "Buy Amazon", "Take over the world"]}/>
```

Let's add this to `App.js`.

Edit `App.js`
``` javascript
import logo from './logo.svg';
import './App.css';

import List from './components/List';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <List itemList={["Get milk", "Buy Amazon", "Take over the world"]}/>
      </header>
    </div>
  );
}

export default App;
```

What this allows us to do is reuse our `List` component for any given array. Let's add another `List` component.

``` javascript
<List itemList={["Get bread", "Get eggs"]} />
```

![Image](/tutorial/app_2lists.png)