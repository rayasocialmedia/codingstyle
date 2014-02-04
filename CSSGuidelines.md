# CSS Guidelines
---
	   
### CSS/SCSS

* Use **soft tabs** with a **two** spaces for indentation (*hard tabs are EVIL!*)
* Put spaces after `:` in property declarations
* Put space before `{` in rule declarations
* Use pre-defined **color variables** instead of adding a new one!
* Use **hex color** codes instead of using **RGBA**
* Use `/* */` not `//` for comments(`//` are not part of the CSS2 standard and may cause issues in some browser - mobile browsers!)
* Don't **nest** further than **3** levels deep in SCSS coding (either use CSS **specificity**, or update your markup **structure**)
* Elements that occur exactly once inside a page should use **IDs**, otherwise, use **classes**
* When modifying an existing element for a specific use, try to use specific class names. Instead of `.box.padded10` use rules like `.box`, `.normal-box`, and `.large-box`
* Don't over-use **line breaks** (Only one line between style definitions)
* Style new features without affecting existing features styling (use unique class names)
* Use short-hand css properties
* Avoid presentation-specific words in the name, like `blue`, `text-gray`, or `light-box` 
* Cascade the name, using a dash `-` as a separator
* Use full descriptive words for class names with only **lowercase**
* Use `em` instead of `px` for sizing fonts, line heights, etc
* Use one discrete selector per line in multi-selector rulesets
* Include one declaration per line in a declaration block
* Use double quotes for css strings
* avoid specifying units for zero-values
* Always place @extend statements on the first lines of a declaration block
* user `compass` mixins & functions
* Group your css properties by **type**
    
		.css-selector {
		
  		  /* Positioning */
  		  position: absolute;
  		  z-index: 10;
  		  top: 0;
		  right: 0;

		  /* Display & Box Model */
  		  display: inline-block;
  		  overflow: hidden;
  		  box-sizing: border-box;
  		  width: 100px;
  		  height: 100px;
  		  padding: 10px;
  		  border: 10px solid #333;
  		  margin: 10px;

  		  /* Color */
  		  background: #000;
  		  color: #fff
  
  		  /* Text */
  		  font-family: sans-serif;
  		  font-size: 16px;
  		  line-height: 1.4;
  		  text-align: right;

  		  /* Other */
  		  cursor: pointer;
		}
