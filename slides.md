class: center, middle, inverse
# Hi
### [whoami](http://reminyborg.com/Whoami/)
---
class: center, inverse
# Agenda
--

### Concepts
--

### React
--

### Choo
---
class: center, middle, inverse
# Concepts
---
.left-column[
## Pure functions
]
.right-column.center-image[![Functions!](assets/function.jpg)]
---
.left-column[
## Pure functions
]
.right-column[
Same parameters in -> Same result out!

```
function hello (name) { return 'Hello ' + name }

hello('Ole Edvard') // Hello Ole Edvard
hello('Remzoor') // Hello Remzoor
```
gives us
- predictability
- testability
- reusability
]
--
.right-column[
We can return
### DOM elements!

```
function hello (name) { return /* Dom element! */ }
```
]
---
.left-column[
## Pure functions

## Functional composition
]
.right-column[
Composing views with function trees are great!

Reuse - Refactor - Rule!

```
const header = /*header(title, content)*/
const list = /*user list*/
const user = /*user details*/

header('Users', list)
header('Selected user', user)

// Combine views with at combine functions
header('Combined', combine(list, user))
```

Data and event handlers are passed down the tree

```
function view (props) {
  return /*<button onClick=props.add> props.value </button>*/
}

// state = { counter: 0 }
function container (state) {
  function add () { state.counter++ }

  return counter({ add: add, value: state.counter })
}
```
]
---
layout: true
.left-column[
## Pure functions

## Functional composition

## Virtual DOM
]
---
.right-column.center[### Model -> DOM]
.right-column.center-image[![Virtual dom](assets/vdom.png)]
---
.right-column.center[### Mutating the DOM]
.right-column.center-image[![I can do it](assets/icandoit.jpg)]
---
.right-column.center[### Mutating the DOM]
.right-column.center-image[![Virtual dom](assets/butterfly.jpg)]
---
layout: true
.left-column[
## Pure functions

## Functional composition

## Virtual DOM

## Immutable
]
---
.right-column.center[### Mutating]
.right-column.center-image[![Simply not mutate](assets/immutability.png)]
---
.right-column[
Mutating state
```
let state = { name: 'Remi', age: 29 }

let newState = state
newState.name = 'Remzoor'

console.log(newState) // { name: 'Remzoor', age: 29 }
console.log(state)    // { name: 'Remzoor', age: 29 }

function doINeedToDoSomeExpensiveRedrawing (state, newState) {
  state === newState
} // Returns False!
```
]
--
.right-column[
Immutable state
```
let state = { name: 'Remi', age: 29 }

let newState = Object.assign({}, state, { name: 'Remzoor' })

console.log(newState) // { name: 'Remzoor', age: 29 }
console.log(state)    // { name: 'Remi', age: 29 }

function doINeedToDoSomeExpensiveRedrawing (state, newState) {
  state === newState
} // Returns true!
```
]
---
layout: false
class: center, middle, inverse
# React
---
.left-column[
## React?

## JSX
]
.right-column[
## What React is:

- View layer

- Html templating

- A very cool component needed for application development

## What react is not:

- Everything else
]
--
.right-column[
### That is what the React community is for!
]
---
.left-column[
## React?

## JSX
]
.right-column[
What is JSX?

- A way to define HTML templates in JavaScript
- Transpiles into JavaScript

```
// Input (JSX):
let app = <div id="mydiv"/>
```

```
// Output (JS):
let app = React.createElement('div', {id:"mydiv"})
```

Inject values with **{ value }** syntax
```
let id
let app = <div id={id}>
```
]
---
layout: true
.left-column[
## React?

## JSX

## Component
]
---
.right-column[
How do we use it?

- Define components
- Compose!

```
const User = ({ id, picture, name, profession, select }) => {
  <div className='user-description' onClick={select}>
    <img src={picture}/>
    <h3>{name}</h3>
    {profession}
  </div>
}

export default User
```

```
import User from './user'

const UserList = ({ users = [], selectUser) => (
  <ul>
    { users.map((user) => (
      <User key={user.id}
        id={user.id}
        picture={user.picture}
        name={user.name}
        profession={user.profession}
        select={() => selectUser(user.id)}
      />
    ))}
  </ul>
)
export default UserList
```
]

---
.right-column[
How do we use it?

- Define components
- Compose!

```
const User = ({ id, picture, name, profession, select }) => {
  <div className='user-description' onClick={select}>
    <img src={picture}/>
    <h3>{name}</h3>
    {profession}
  </div>
}

export default User // Pure Function!
```

```
import User from './user'

const UserList = ({ users = [], selectUser) => (
  <ul>
    { users.map((user) => ( // Functional composition
      <User key={user.id}
        {...user}
        select={() => selectUser(user.id)}
      />
    ))}
  </ul>
)
export default UserList // Pure Function!
```
]
---
.right-column.center[

### Pro tip:

One component to rule them all.

And in the darkness bind them.

\- J.R.R Tolkien

]
---
.right-column[

Keep your components as dumb as you can.

The top controller should do all the magic.
]
.right-column[
This is where the magic happens
```
class SelectYourUser extends React.Component {
  constructor()         // your initial state
  render()              // your basic render func
  componentWillMount()  // prepare your dom
  componentDidMount()   // dom has been changed
  shouldComponentUpdate // perf optimization
  ... // many more
}
```
]
--
.right-column.center[
With great power comes great responsibility.

\- Uncle Ben
]
---
.right-column.center[### Now we are ready to]
.right-column.center-image[![All the things](assets/allthethings.jpg)]
---
.right-column.center[### Not likely]
.right-column.center-image[![No](assets/no.jpg)]
---
layout: false
.left-column[
## React?

## JSX

## Components

## Redux
]
.right-column[
![Redux](assets/redux.jpg)


- Centralized store

- Well defined actions

- Immutable data structure

- Facilitates Magic!
]
---
layout: true
.left-column[
## React?

## JSX

## Components

## Redux
]
---
.right-column.center[
# Redux Flow
![Redux](assets/ui_workflow.png)
]
---
.right-column[
```
function App(state = initialState, action) {
  switch (action.type) {
    case SET_USER:
      return Object.assign({}, state, {
        user: action.user
      })
    default:
      return state
  }
}
```

Create the store
```
import { createStore } from 'redux'

let store = createStore(App)
```

Dispatch some actions
```
store.dispatch({
  type: 'SET_USER',
  user: 314159
})
```
```
console.log(store.getState())
// { user: 314159 }
```
]
---
layout: false
.left-column[
## React?

## JSX

## Components

## Redux

## Community
]
.right-column[
### React is cool.

### The community is awesome!
]
--
.right-column[
- Redux / State

- Connectors

- Widgets

- Routing

- Tabs

- +++

À la carte
]
---
.left-column[
## React?

## JSX

## Components

## Redux

## Community
]
.right-column[
.center[https://www.npmjs.com/]
```bash
npm install --save react-redux
```
]
--
.right-column[
```
import { Provider } from 'react-redux'

<Provider store={store}>
  <App />
</Provider>
```

```
import UserList from './user-list'
import { connect } from 'react-redux'
let App = ({ users, selectUser}) => (
  <div>
    <UserList user={users} selectUser={selectUser}/>
  </div>
)

const mapState = (state) => ({ users: state.users })
const mapDispatch = (dispatch) => ({
    selectUser: (id) => {
      dispatch({ type: 'SET_USER', user: id })
    }
})

App = connect(mapState, mapDispatch)(App)
```

]
---
layout: true
.left-column[
## React?

## JSX

## Components

## Redux

## Community

## Build
]
---
.right-column.center-image[![Build?](assets/build.jpg)]
--
.right-column[
- Transpile ES2015 Awesomeness -> Regular ES5

- Include all the modules

- Maby minimize?
]
---
.right-column.center[
### Javascript fatigue
Too much, too fast, so tired.
]
--
.right-column[
Not any more!

```bash
npm install -g create-react-app

create-react-app my-app
cd my-app/
npm start
```
]
---
layout: false
class: center, middle, inverse
# Choo
---
.left-column[
## Choo
]
.right-column.center-image[![Build?](assets/chooyoung.png)]
--
.right-column[
- Exiting future

- No transpiling (For brand new browsers)

- Built from small interchangable modules!

- Its fast, its fun!

- Tiny, 5kb.

- We are still figuring things out
]
---
.left-column[
## Choo

## Models

## Template strings
]
.right-column[
### Pragmatic redux
```
const app = choo()

app.model({
  namespace: 'main',
  state: { title: '' },
  reducers: {
    update: (data, state) => ({ title: data })
  }
})

send('main:update', 'React and Choo')
```

```
app.model({
  namespace: 'users',
  state: { list: [] },
  reducers: {
    add: (data, state) => ({ list: state.list.concat(data) })
  }
})

send('users:add', { id: 1, name: 'Remi' })
```
]
---
.left-column[
## Choo

## Models

## Template strings
]
.right-column[
### Tagged template literals
backtick saves the day
```
let name = 'Remi'
let hello = `Hello ${name}`
```
]
--
.right-column[
no need for JSX or transpiling
```
const html = require('choo/html')

const mainView = (state, prev, send) => html`
  <main>
    <h1>Title: ${state.title}</h1>
    <input
      type="text"
      oninput=${(e) => send('update', e.target.value)}>
  </main>
`
```
]
---
.left-column[
## Choo

## Models

## Template strings

## No virtual DOM
]
.right-column[
### The real truth is in the dom!
### Wake up sheeple!

Choo uses morphdom:

Lightweight module for morphing an existing DOM node tree to match a target DOM node tree. It's fast and works with the real DOM—no virtual DOM here!

https://github.com/patrick-steele-idem/morphdom#benchmarks
]
