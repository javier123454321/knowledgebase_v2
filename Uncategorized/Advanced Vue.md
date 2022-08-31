- Type:: [[Lecture]]
- Source:: [Youtube](https://www.youtube.com/watch?v=anzA27c7F5g&list=PLy0TFGrsXfC6ZowyW3od9dg_K6VY3dB-N&index=6)
- Author:: [[Evan You]]
- Subject:: [[Programming]] [[Vue]] [[Vue]].js
- Status:: [[In Progress]]
- Abstract::
- Summary::
    - **Reactivity**
        - The concept of reactivity is foundational to Vue
        - If you have an excell spreadsheet, and want to make it reactive to changes `cell x = cell y * n`
        - You would do something like establishing a callback function that gets run every time that cell x changes
            - `onCellChange(() => view = render(newState))`
            - you can set the state in two ways, 
                - in react you run `setState(newState);`
                - in vue you actually just manipulate the state directly `state.x = newX`
                    - This is because Vue uses the [Object.defineProperty](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty) function to react to getters and setters
        - Object.defineProperty
 ```javascript
Object.defineProperty(obj, 'foo', {
  enumerable: false, //will not show up in object.keys
  configurable: false, //Cannot be changed
  writable: false, //Will fail silently if trying to change it
  get() {
    // overrides the access function of the object.
  }
  set(){
    //overrides the setter function
  }
})```
