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
.right-column.center-image[![Functions!](http://image.slidesharecdn.com/functions-111009201256-phpapp02/95/ppt-on-functions-3-728.jpg)]
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
var header = /*header(title, content)*/
var list = /*user list*/
var user = /*user details*/

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
.right-column.center-image[![Virtual dom](http://i.stack.imgur.com/S1vng.png)]
---
.right-column.center[### Mutating the DOM]
.right-column.center-image[![Virtual dom](http://static.musictoday.com/store/bands/2117/product_medium/6EAM0478.JPG)]
---
.right-column.center[### Mutating the DOM]
.right-column.center-image[![Virtual dom](http://chieforganizer.org/wp-content/uploads/2016/08/50_no_mere_coincidence.jpg)]
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
.right-column.center-image[![Simply not mutate](http://vitiy.info/wp-content/uploads/2015/06/immutability.png)]
---
.right-column[
Mutating state
```
var state = { name: 'Remi', age: 29 }

var newState = state
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
var state = { name: 'Remi', age: 29 }

var newState = Object.assign({}, state, { name: 'Remzoor' })

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
]
.right-column[
### What is react?
View layer. Nothing more. Nothing less.
### Why would you use it?
]
