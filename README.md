# s19-composition

Udemy Vue3 course Section 19

Illustrate Composition API features and behaviour


## What does Composition API solve?

Issues that would occur in a large project

### Issues in Options API:
- code that belongs together is split up across multiple options (lots of scrolling to make a change)
- re-using logic across components is tricky

### What Changes?

These will be merged into setup()
- data()
- methods
  - define inside setup() then define/return a 'pointer' in return object

- computed
  -

- watch
  - single watch can handle all variables with an array
  - order of declaration influences array location

- Lifecycle hooks



### What Does not change?
props, emits, components

## More

- ref() works with everything (String, Number, Object) and has '.value' wrapper: user.value.age
- reactive() works only with objects and eliminates .value wrapper: user.age

- you can mix Options API with Composition API:
  - e.g. UserData.vue has Options API computed properties, App.Vue has Composition API style

setup(props, context) params:

  props - 

  context.attrs - properties not defined as properties which fall through
  context.slots - access slots programatically
  context.emit - can be used to call a custom event

## Helper methods

- isRef() and isReactive() - tell which kind we are working with
- toRefs() - turn an objects' properties into refs


## Installation

npm install


## Run

npm run serve (Development)

