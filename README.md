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
- computed
- watch
- Lifecycle hooks

### What Does not change?
props, emits, components

## More

- ref() works with everything (String, Number, Object) and has '.value' wrapper: user.value.age
- reactive() works only with objects and eliminates .value wrapper: user.age

## Installation

npm install


## Run

npm run serve (Development)

