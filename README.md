# lit-ccm
## LitElement adapter for ccm

Mixin for LitElement subclasses that adds ccm API functions to the subclass:
* init
* ready
* start

```javascript
import { LitElement, html } from 'https://unpkg.com/@polymer/lit-element/lit-element.js?module';
import { ccmix } from 'https://mkaul.github.io/lit-ccm/lit-ccm.js';

class HelloWorld extends ccmix ( LitElement ) {
  /**
   * Define a template for the new element by implementing LitElement's
   * `render` function. `render` must return a lit-html TemplateResult.
   * 
   * The ccmix Mixin will mix the ccm API and the ccm helper functions into the element
   */
  render(){
    return html`
      <style>
        :host { display: block; }
        :host([hidden]) { display: none; }
      </style>
      <p>You like pie.</p>
    `;
  }
}
// Register the element with the browser
customElements.define('hello-world', HelloWorld);
```