# lit-ccm
## LitElement adapter for ccm

Mixin for LitElement subclasses that adds ccm API functions to the subclass:
* init
* ready
* start

```javascript
import { LitElement, html, render as lit_render } from 'https://unpkg.com/@polymer/lit-element/lit-element.js?module';
import { ccm } from 'https://mkaul.github.io/lit-ccm/ccm/versions/ccm-18.6.5.mjs';
import { ccmix } from 'https://mkaul.github.io/lit-ccm/lit-ccm.mjs';
import { config } from 'https://mkaul.github.io/lit-ccm/config.mjs';

class HelloWorld extends ccmix( ccm, config )( LitElement ) { // or HTMLElement
  /**
   * Define a template for the new element by implementing LitElement's
   * `render` function. `render` must return a lit-html TemplateResult.
   * 
   * The ccmix Mixin will mix the ccm API and the ccm helper functions into this element
   * 
   * ccmix has two parameters:
   * 1. ccm is the chosen version of the ccm framework exporting the ccm global namespace
   * 2. config is the configuration for this element in JSON format, see ccm wiki
   */
  
  static get dependencies(){
    // Array of other components as static property 
  }
  
  init(){
    
  }
  
  ready(){
    
  }
  
  start(){
    if ( this.render ){
      this.element.parentNode.appendChild( lit_render( this.render() ) );
    }
  }
  
  render(){ 
    return html`
      <style>
        :host { display: block; }
        :host([hidden]) { display: none; }
      </style>
      <h1>Hello World</h1>
      <p>You like lit and you like <i>ccm</i>.</p>
    `;
  }
}
// Register the element with the browser
customElements.define('hello-world', HelloWorld);
```