## Naming Convention
BEM (Block, Element, Modifyers)
Don't use BEM for css tag or ID selection
- Block
	- Describe its purpose
	- Functional independent component that can be resued, represented by the class attribute
		- Ex: "header", "logo", "search-form"
	- Block should influence its enviornment, shouldnt set the external geometry (margin, positioning, etc)
- Element
	- Describe its purpose
	- Part of a block that can't be used seperately from it
		- EX: "item", "text"
	- Elements are seperated from the block using double underscore
		- EX: "block-name__element-name"
			- "search-form__input"
			- "search-form__button"
- Modifyers
	- Describes its appearance, state, or behavior of a block
	- Used on **BOTH** block and element
	- Ex:
		- "size_s", "disabled", "left-top"
	- Defined by single underscore
		- Ex: "logo_left-top", "search-form_disabled"
### Rules
- Elements can be used inside each other
- An element is always part of a block, **NOT** another element meaning "block__element-one__element-two" is bad
```
<form class="search-form">
    <div class="search-form__content">
        <input class="search-form__input">

        <button class="search-form__button">Search</button>
    </div>
</form>
```

- Elements cannot be used separately from the block its supposed to be from
- Elements are optional, not all blocks have elements
## Whitespace
Use soft tabs set to 4 spaces.

Place 1 space before the leading brace and place 1 space after the colon of a declaration.

```css

/* Bad */

.selector {

..display: flex;

}

/* Good */

.selector {

....display: flex;

}

```
Place 1 space before the leading brace and place 1 space after the colon of a declaration.
```css

/* Bad */

.selector {

position: relative;

}
/* Good */

.selector {

position: relative;

}

```
Place an empty newline at the end of the file.
```css

/* Bad */

.selector {

clear: both;

}
/* Good */

.selector {

clear: both;

}

```
## Formatting

The chosen code format ensures that code is: easy to read; easy to clearly comment; minimises the chance of accidentally introducing errors; and results in useful diffs and blames.

- Use 1 selector per line in multi-selector rulesets
- Use 1 declaration per line in a declaration block
- Use lowercase, longhand hex values
- Use single quotes `''` e.g. `input[type='checkbox']`
- Do not specify units for zero-values e.g. `margin: 0;` and not `margin: 0rem;`
- Do not add leading zeroes to decimal figures (`.8` instead of `0.8`)
- Include a space after each comma in comma-separated property or function values
- Include a semi-colon at the end of the last declaration in a declaration block
- Place the closing brace of a ruleset in the same column as the first character of the ruleset
- Separate each ruleset by a blank line

## Declaration Order

```
.selector {
	/* Positioning + Z Index */
	
	/* Display, Box Model, Margin, Padding */

	/* Typography, List Styles, Font, Text Styles */

	/* Background */

	/* Border styling */
	
	/* Animations and Transitions */

	/* Misc */
}
```

## Commenting

```
/* -----------------------------------------------------------------------------
 * Section block
 * -------------------------------------------------------------------------- */

/* Sub-section comment block
   ===================================== */

/* Basic comment */
```