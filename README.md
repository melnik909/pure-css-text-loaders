# CSS Text Loaders — the collection of only text CSS animations
Text might be a part of UI animations. And it will be more intuitive than object animation because it doesn't cause confusing feelings. [Check it out on Codepen](https://codepen.io/melnik909/full/wvZmOOa)! 
## Why it is cool
1. Animations are done with care about people with motor disabilities
2. Animations are friendly to Windows High Contrast Mode
3. Support any direction of multi-language
4. Easily customize using pure CSS
## How use it
Copy and paste the following HTML.
```html
<div class="uia-text-loader">
  <div class="uia-text-loader__text">
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">L</span>
      L
    </span>
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">o</span>
      o
    </span>
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">a</span>
      a
    </span>
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">d</span>
      d
    </span>
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">i</span>
      i
    </span>
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">n</span>
      n
      </span>
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">g</span>
      g
    </span>
  </div>
</div>
```
Import the core files inside your CSS file. 
```css
@import "uia-text-loader.css";
@import "uia-text-loader-loading.css";

/* your styles */
```
Choose the animation type and import a related file.
```css
@import "uia-text-loader.css";
@import "uia-text-loader-loading.css";
@import "uia-text-loader-type-1.css";

/* your styles */
```
**Note:** Don't forget to use build systems so that the @import CSS at-rule doesn't get on production.

You need to add the data-uia-text-loader-type attribute. Use the CSS file name as the value.
```html
<!--
  The example: if you wanna use the first animation your file name is uia-text-loader-type-1
-->
 
<div class="uia-text-loader" data-uia-text-loader-type="uia-text-loader-type-1"> 
  <!-- child elements are here -->
</div>
```
It's done 😉
## Customization
I've made options that you will use for customization. See the following:
| Name  | Description |
| ------------- | ------------- |
| --uia-text-loader-font-family  | What font do you want to use? Roboto? Use any! But don't forget to define safe font as a fallback.  |
| --uia-text-loader-font-size  | How large the text you use is. 2rem or 0.5rem?  | 
| --uia-text-loader-text-transform  | The capitalization of text.  | 
| --uia-text-loader-text-shadow  | The color of the text that you see before and after the end of the animation.  | 
| --uia-text-loader-letter-display  | The value for the display property of the letter.  | 
| --uia-text-loader-letter-color  | The color of the text during of the animation.  | 
| --uia-text-loader-animation-duration  | The time during which you are watching the animation.  | 

You should use the parent element or document root element to define the new value. 
```css
:root {
  --uia-text-loader-font-family: 'Roboto', sans-serif;
  --uia-text-loader-font-size: 2rem;
  --uia-text-loader-text-transform: lowercase;
  --uia-text-loader-text-shadow: rgba(0, 0, 0, 0);
  --uia-text-loader-letter-color: #800080;
  --uia-text-loader-letter-display: inline-grid;
  --uia-text-loader-animation-duration: 6s;
}
```
I have specified the allowed values here. You should use a value that is allowed for a CSS property from the second column.

| Name  | CSS property |
| ------------- | ------------- |
| --uia-text-loader-font-family  | font-family  |
| --uia-text-loader-font-size  | font-size  | 
| --uia-text-loader-text-transform  | text-transform  | 
| --uia-text-loader-text-shadow  | color  | 
| --uia-text-loader-letter-display  | display  | 
| --uia-text-loader-letter-color  | color  | 
| --uia-text-loader-animation-duration  | animation-duration  |

## Use a custom text
All text is inside the uia-text-loader__text element.
```html
<div class="uia-text-loader" data-uia-text-loader-type="uia-text-loader-type-1">
  <div class="uia-text-loader__text">
    <!-- Your text will be here -->
  </div>
</div>
```
Each letter must be wrapped by the uia-text-loader__letter element. Also, you need to add a copy of a letter in the  uia-text-loader__letter-placeholder element. For example, I wanna use the "Загрузка" text.
```html
<div class="uia-text-loader" data-uia-text-loader-type="uia-text-loader-type-1">
  <div class="uia-text-loader__text">
    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">З</span>
      З
    </span>

    <!-- From 2 to 7 letters are here -->

    <span class="uia-text-loader__letter">
      <span  class="uia-text-loader__letter-placeholder" aria-hidden="true">а</span>
      а
    </span>
  </div>
</div>
```
**Note:** Don't forget to add the aria-hidden attribute to avoid duplication voicing by screen readers.

Open the uia-text-loader-loading.css file and create styles for each letter.
```css
.uia-text-loader__letter {
   --_uia-text-loader-delay-step: var(--uia-text-loader-delay-step, 0.2s);
}

.uia-text-loader__letter:nth-child(2) .uia-text-loader__letter-placeholder {
   --uia-text-loader-animation-delay: calc(2 * var(--_uia-text-loader-delay-step))
}

/*
  Styles of with 2 to 7 letters are here
*/

.uia-text-loader__letter:nth-child(8) .uia-text-loader__letter-placeholder {
   --uia-text-loader-animation-delay: calc(8 * var(--_uia-text-loader-delay-step));
}
```
That's it! You have created a custom text 😊

## Promo
Also, this collection is created with the purpose of promoting my newsletter with CSS tips. I'm sure you find something what you don't know. Do you wanna check it? [Subscribe!](https://cssisntmagic.substack.com/) 
## Copyright
The files herein are all Stas Melnikov.
