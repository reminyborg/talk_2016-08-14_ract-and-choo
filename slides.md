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
background-image: url(http://memesvault.com/wp-content/uploads/Little-Girl-Meme-I-Dont-Know-03.jpg)
.left-column[
## Why?
]
---
.left-column[
## Why?
]
.right-column[
- Feel smart

- Framework for discussion

- Guidance in times of need

- I like the ones I am going to show you
]
---
background-image: url(http://image.slidesharecdn.com/functions-111009201256-phpapp02/95/ppt-on-functions-3-728.jpg)
.left-column[
## Why?

## Pure functions
]
---
.left-column[
## Why?

## Pure functions
]
.right-column[
Same parameters in -> Same view out!

```
function hello (name) { return 'Hello ' + name }

hello('Ole Edvard') // Hello Ole Edvard
```
]
--
.right-column[
But wait...
]
--
.right-column[
we can return
### DOM elements!

```
function hello (name) { return /* Dom element! */ }
```
]
---
.left-column[
## Why?

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
var user
```
]
---

