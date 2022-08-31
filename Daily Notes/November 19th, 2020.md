- Centrality tells us the measure of signigificance in a node in a network  {{[[∆]]:3+2}}
- [[Gratitude List]] 
- [[Spheres]] 
    - [[Keypath]]
        - {{[[query]]: {and: [[TODO]] [[Keypath]] {not: {or: [[query]][[Memory Captures]][[Other]][[Personal]]}}}}}
    - [[Memory Captures]]
        - {{[[query]]: {and: [[TODO]] [[Memory Captures]] {not: {or: [[query]][[Keypath]][[Other]][[Personal]]}}}}}
    - [[Other]]
        - {{[[query]]: {and: [[TODO]] [[Other]] {not: {or: [[query]][[Keypath]][[Memory Captures]][[Personal]]}}}}}
    - [[Personal]]
        - {{[[query]]: {and: [[TODO]] [[Personal]] {not: {or: [[query]][[Keypath]][[Memory Captures]][[Other]]}}}}}
    - [[Generalized Specialized]]
        - {{[[query]]: {and: [[TODO]] [[Generalized Specialized]] {not: {or: [[query]][[Keypath]][[Memory Captures]][[Other]]}}}}}
- [[Quick Capture]]
    - Micro front ends
        - https://micro-frontends.org/
            - {{[[drawing]]}}
            - Tech agnostic
            - Isolated Code
            - Team prefixes
            - Native Browser features
            - Resilient Site
            - You can create a class that extends the HTML elements of a site and trigger behavior on rendering
            - ```javascript
class BuyButton extends HTMLElement {
  connectedCallback() {
    this.innerHTML = `<button type="button">buy</button>`;
  }

  disconnectedCallback() { ... }
}
window.customElements.define('buy-button', BuyButton);```
                - This means that every time you create a `<buy-button></buy-button>` element, it will be rendered as ```html
<buy-button>
  <button>buy</button>
</buy-button>```
    - Money is a form of communication, and an effective one. It quantifies something profound, how much we value something.
    - 
- [[Literature Notes]]
- [[Reflection]]
    - [[What did I learn]]
        - About the ability to extend the HTMLElement class in HTML markup and javascrips
    - [[What went well?]]
        - Ran 10k, didn't feel too bad.
    - [[What could be better?]]
        - Could have 
