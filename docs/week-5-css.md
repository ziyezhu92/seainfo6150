1\. CSS = Cascading Style Sheets

   1. Purpose:

      1. Visual appearance of HTML elements 

      2. Positioning  in relationship to one another

      3. Interaction between elements 

      4. Transition/animation of elements

   1. Context-free language

      1. Can be described by recursive rules

      2. Stylesheet parsing -- strict

      3. Unlike HTML, parsers can and will generate syntax errors based on incorrect syntax usage

         1. Style pre-processors, SASS: syntax error

         2. Vanilla CSS: browser will tag error and not display intended style

      1. Example

   1. Cascade: style sheets can "stack up" (cascade) until sum of calculated styles are reflected in the presentation

      1. Global scope

         1. Be cautious about far-ranging overrides that can cascade through doc

      1. Browser stylesheets

      2. Best practice: "reset"/"normalize" stylesheet

1\. Stylesheet locations

   1. Inline head = <style> tag within <head> tag

      1. Advantage = visibility within doc

      2. Disadvantage = only applies to current doc, not scalable

   1. Inline tag = style attribute on tag

      1. Advantage = only applies to current tag, high specificity

      2. Disadvantage = only applies to current tag

   1. External = linked stylesheet <link href="stylesheet"> within <head> tag

      1. Advantage = defined styles can be applied to any doc where stylesheet is linked, most common way of organizing styles

      2. Disadvantage = single stylesheet (or bundled) can be unwieldy, can import styles not present on page, wasteful

   1. CSS modules = CSS styles are included as js module

      1. Advantage = styles are namespaced within context of individual modules, no longer globally scoped = no unintentional style collisions

   1. Example + hands on

1\. Stylesheet rules

   1. What does a rule look like? 

   2. [selector] { [style rule] }

      1. Eg body { background-color: white; }

   1. Can group many style rules between braces, all will apply to the selector

   2. Can have multiple duplicate selectors, all style rules will be applied

      1. Eg body { background-color: white; }

      2. body { padding: 0; }

   1. Rules can override each other if they apply to the same selector and either

      1. Come later (farther down) in the style sheet

      2. Have a higher specificity

   1. Naming

      1. Give your style names (classes & ids) meaningful names that are easy to reuse

      2. Try not to reference how the class/id is styled within the name

         1. Eg. .blue-underline

         2. That may be how it's styled now, but what happens if that changes in the future? 

         3. You don't want your codebase full of .blue-underline that are actually green background colors

         4. Better name might be the purpose, like .content-highlight

            1. Reusable and not tied to specific implementation

            2. Has semantic meaning for people not familiar why the blue underline is used

1\. Styling HTML

   1. Stylesheet rule is associated with selector, combination of ids, classes, tags, combinators, etc.

      1. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors

      2. IDs

         1. HTML tag is given id attribute

         2. Id must be unique, 1 ID per document

         3. Stylesheet rule begins with #

      1. Classes

         1. HTML tag is given class attribute

         2. Classes do not need to be unique, can have same class several times per document

         3. Many classes can be applied to the same tag

      1. Pseudo selectors/pseudo classes

         1. Used when you want to style a selected element but only when it is in a certain state

         2. Eg :hover, :selected, :checked, :first-child, :nth-of-type

         3. https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#Pseudo-classes

      1. Pseudo elements

         1. keywords preceded by two colons (::) added to the end of selectors to select a certain part of an element

         2. Only 6: ::after, ::before, ::first-letter, ::first-line, ::selection, ::backdrop

      1. Attribute Selectors

         1. Styling is applied to HTML tag based on characteristics inherent to the tag

         2. Brittle, will probably break styles if HTML structure is changed

      1. Combinators

         1. Ways of combining classes and ids 

         2. Descendent: element is a descendent of previous element

            1. Use a space

            2. Eg section p matches <section><div><p>text</p></div></section>

         1. Child: element is a direct descendent of previous element

            1. Use a >

            2. Eg section > div matches, section > p does not <section><div><p>text</p></div></section>

         1. Sibling: element is a sibling of previous element (they have the same parent but don't necessarily follow directly)

            1. Use a ~

            2. Eg div ~ button matches <section><div><p>text</p></div><img src="foo.jpg" /><button>bar</button></section>

         1. Adjacent: element is an adjacent of previous element

            1. Use a +

            2. Eg div + img matches, div + button does not <section><div><p>text</p></div><img src="foo.jpg" /><button>bar</button></section>

   1. Specificity

      1. Rules browser uses to calculate precedence of styling

      2. If two or more selectors apply to the same element, the one with higher specificity wins

      3. Four distinct categories which define the specificity level of a given selector

         1. inline styles

         2. IDs & classes 

         3. Attributes

         4. Tag elements

      1. Rules: 

         1. Give every id selector ("#foo") a value of 100

         2. Give every class selector (".bar") a value of 10

         3. Give every pseudo selector (":hover",":selected") a value of 10

         4. Give every HTML selector ("div") a value of 1

         5. Give every pseudo element ("::before", "::first-letter") a value of 1

         6. Add them all up to get the specificity value

         7. If selectors have an equal specificity value, the latest rule is the one that counts

         8. The embedded style sheet has a greater specificity than other rules

      1. !important

         1. Add to a style rule to apply style rule regardless of specificity of others

            1. If 2 conflicting rules have !important, specificity decides

         1. If everything is important, nothing is

         2. Best practice: add ids instead of !important

   1. Units

      1. Px

         1. "Magic" unit of CSS

         2. not related to the current font

         3. 'reference' pixel, not a device pixel. 

         4. px is an abstract unit where a ratio controls 

            1. How it maps to actual device pixel

            2. How it maps to physical units (in a fixed way, the ratio is always 96 CSS px to an inch)

         1. designed to be roughly equivalent across devices

      1. Percentage (relative to parent container)

      2. Em (relative to current font size)

         1. 1em = current font size of element to style

      1. Rem (relative to current font size)

         1. 1rem = current font size of root em (html font-size) 

         2. Inherited font sizes have no effect

      1. Vh = 100th height of viewport

      2. Vw = 100th width of viewport

      3. For screen, recommended using em, px, %

1\. visibility

   1. Hidden: hide the element but leave the space it occupied (almost like making it transparent)

   2. Visible (default): show the element

1\. Color

   1. Named colors: https://htmlcolorcodes.com/color-names/

   2. Hexadecimal colors

      1. = #[0-9a-f]{6}

      2. # + 6 digits/3 tuples: #[rr][gg][bb], 0-255 rgb value

         1. 0-255 → 0-9, A-F

         2. No need to calculate yourself

            1. Designer will give you RGB/hex values 

            2. https://www.google.com/search?q=rgb+to+hex

      1. #ffffff = [255][255][255] = pure white

      2. #000000 = [0][0][0] = pure black

      3. Can use hexadecimal shorthand notation to save space 

         1. Eg .dark-yellow {color:#ffcc00;} → .dark-yellow {color:#fc0;}

         2. This only works if all 3 tuples are matching (ie cannot shorthand #ccfeff to #cf3f)

   1. Rgb/rgba

      1. Use full RGB values as rgb(R, G, B)

         1. Eg rgb(255, 255, 255) = #ffffff = pure white

         2. Eg rgb(0, 0, 0) = #000000 = pure black

      1. Rgba

         1. adds opacity value at some decimal value between 0 and 1

         2. 0 = full transparency

         3. 1 = full opacity

         4. Eg rgba(255, 255, 255, .5) = #ffffff at .5 transparency

      1. example

1\. Background

   1. We'll cover background during images in week 6

   2. Change the background of any element, ie what paints underneath the content in that element

   3. Background-color

      1. applies solid colors as background on an element

1\. Box model

   1. Each HTML element is rendered as a box

      1. Block box

         1. Always appear below each other in default browser display

         2. "Static" flow

         3. Width is based on the width of its parent container

         4. Height is based on the content it contains

      1. Inline box

         1. Not for determining layout but for styling inside blocks

         2. Width is based on the content it contains

         3. Adding block styling like margins, height, width don't have any effect

      1. Can override behavior, ie block → inline + inline  → block

      2. Display

         1. Inline = default value for elements

            1. Browser stylesheets reset many to "block"

            2. Inline within a block container

            3. Accepts margin and padding but still sits inline within text

            4. Does not accept height/width

         1. Inline-block

            1. Similar to inline but will accept height/width

         1. Block = creates its own bounding box

         2. Flex = defines a flex container

         3. Grid = defines a grid container

         4. Table, et. al = force non-tabular elements to behave like a table

            1. https://css-tricks.com/almanac/properties/d/display/#display-table

         1. None

            1. Not displayed, 

            2. Still in the DOM, removed visually and ignored by screen readers (unlike visibility: hidden)

   1. border

      1. Line at boundary of box of content

      2. Border-width

         1. thickness of the border

         2. Named: 

            1. Thick = 5px 

            2. Medium = 3px

            3. Thin = 1px

         1. Length 

            1. px, em, rem, vh and vw units

      1. Border-style

         1. Specifies the type of line drawn around the element

         2. https://developer.mozilla.org/en-US/docs/Web/CSS/border-style

         3. solid: A solid, continuous line

         4. none (default): No line is drawn

         5. hidden: A line is drawn, but not visible. this can be handy for adding a little extra width to an element without displaying a border

         6. dashed: A line that consists of dashes

         7. dotted: A line that consists of dots

         8. double: Two lines are drawn around the element

         9. groove: Adds a bevel based on the color value in a way that makes the element appear pressed into the document

         10. ridge: Similar to groove, but reverses the color values in a way that makes the element appear raised

         11. inset: Adds a split tone to the line that makes the element appear slightly depressed

         12. outset: Similar to inset, but reverses the colors in a way that makes the element appear slightly raised

      1. Border-color

         1. Specifies the color of the border

      1. Border-collapse

         1. Use on <table> elements (display: table, etc. elements)

            1. separate (default): 

               1. all cells have their own independent borders

               2. there may be space between those cells

            1. Collapse:

               1. both the space and the borders between table cells collapse so there is only one border and no space between cells

      1. Border-image: We'll cover background during images in week 6 

      2. Border-radius

         1. give any element "rounded corners"

         2. Eg border-radius: 4px 

         3. Can specify the value of border-radius in percentages to create a circle or ellipse shape

            1. can be used any time you want the border radius to be directly correlated with the elements width

            2. Border-radius: 50%

         1. rounding doesn't have to be perfectly circular, it can be elliptical

            1. Can specify the radiuses in which the corner is rounded by

            2. border-radius: 10px/30px

   1. padding

      1. Spacing inside box of content

      2. Independent values

      3. Cannot be negative

   1. margin

      1. Spacing outside box of content

      2. Independent values

      3. Can be negative 

         1. top/left: pulls element in that direction

         2. bottom/right: pulls other elements into overlapping element

      1. Vertical margin collapse

         1. Instead of adding margins together, only largest is taken

      1. Example + hands on

   1. box-sizing

      1. Allows you to change how the width of the box is calculated

      2. Content-box

         1. Built up from content box

         2. Eg 600px container, 3 boxes 200px wide

         3. Boxes are actually 202px wide with border

      1. Border-box

         1. Built down from external width

         2. Forces actual width of entire box to "width", accounting for padding/border

         3. Best practice: set your blocks to use border-box

1\. Lists

   1. list-style-type: Sets the type of bullets to use for the list, for example, square or circle bullets for an unordered list, or numbers, letters or roman numerals for an ordered list

      1. https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type#Values

      2. Disc: A filled circle (default value)

      3. Circle: A hollow circle

      4. Square: A filled square

      5. Decimal: numbers

      6. Upper-roman: roman numerals

      7. None: removes the bullets from the list

   1. list-style-position: Sets whether the bullets appear inside the list items, or outside them before the start of each item

      1. Outside (default): outside the bounds of the list item

      2. Inside: inside the bounds of the list item

   1. list-style-image: Allows you to use a custom image for the bullet, rather than a simple square or circle.

   2. 1. Typography

   1. Explanation of typography

      1. Baseline

      2. ascenders/descenders

      3. Line-height

      4. https://builttoadapt.io/8-point-grid-vertical-rhythm-90d05ad95032

   1. Font-family = specifies a prioritized list of one or more font family names and/or generic family names for the selected element

      1. Font stack

      2. Serif, sans serif, monospace, cursive, fantasy, system-ui

      3. Best practice: always include at least one generic font family

         1. Cannot count on what fonts a user has installed

      1. Importing a font to use

         1. <link>

         2. @import

         3. @font-face

            1. Specified font-family should match actual name of font-family

            2. Need font file somewhere in file structure

         1. Google Fonts example

   1. Font-size

      1. Named: Xx-small, x-small, small, medium, large, x-large, xx-large

      2. Relative: smaller, larger (roughly corresponding to named values)

      3. Length: em, rem, px, etc.

      4. Percentage: relative to parent's font size

   1. Line-height

      1. amount of space between lines in the same block

   1. Font-weight

      1. Named weights: normal, bold

      2. Relative: lighter, bolder

      3. Numeric: between 1 and 1000, inclusive

         1. Earlier browsers supported 100, 200, etc.

         2. Now 1-1000 supports finer grained control from fonts

         3. Not supported by all browsers

   1. Color

      1. Change text color of content box

   1. Font-style

      1. Normal

      2. Italic 

      3. Oblique

      4. Italic vs. oblique = oblique is usually just sloped, italic is usually a different font style, often cursive

   1. Text-decoration

      1. Shorthand for text-decoration-line, text-decoration-color, and text-decoration-style

      2. Appearance of decorative lines used on text

      3. Best practice: Do not use underlining except on links

      4. Style: dashed, dotted, wavy, solid, double

      5. Line: underline, overline, line-through

      6. Eg. text-decoration: green dashed underline

      7. Example

   1. Transform

      1. Takes language specific cases into account

      2. Capitalize

      3. Uppercase

      4. lowercase

   1. HTML entities

      1. special character that can't be represented as plain text in an HTML document

      2. Reserved = <, >, and &

      3. Quotation marks

      4. https://dev.w3.org/html5/html-author/charref

   1. Example

1\. Positioning with CSS

   1. float

      1. Concept comes from print design

      2. Images/elements set into layout so that text wraps ("flows") around them

      3. Removed from the flow of the page, but remain part it to affect other elements

      4. Floating an element usually changes display: attribute to "block" 

   1. position

      1. Can help you manipulate the location of an element in the page or relative to the other other elements around it. 

      2. Static

         1. every element has static position by default

         2. will conform to normal page flow.

      1. Relative

         1. Continues to appear in normal page flow

         2. left/right/top/bottom can now be applied

         3. Element will be nudged in that direction

         4. Example

      1. Absolute

         1. element is removed from the flow of the document

         2. other elements will behave as if it's not there

         3. Positional properties will work on it 

         4. If no other positioning is set on parent, child positioning will be relative to the document.

            1. To make positioning relative to parent, set position: relative on parent

         1. Example

      1. Fixed

         1. Similar to absolute

         2. Position relative to document

         3. Not affected by scrolling

         4. Example

   1. Z-index

      1. controls the vertical stacking order of elements that overlap

         1. relative positioning has nudged it over something else

         2. negative margin has pulled the element over another

         3. absolutely positioned elements overlap each other

      1. Ie, which one appears as if it is physically closer to you

      2. z-index only affects elements not statically positioned (ie, position absolute, relative, etc.)

      3. Without z-index value

         1. elements stack in the order that they appear in the DOM

         2. Ie the lowest one down at the same hierarchy level appears on top

      1. Stacking context

         1. an element that contains a set of layers

            1. root stacking context, created by the html element

            2. local stacking context, created by specific properties and values

               1. Within local stacking context, z-index values of its children are set relative to that element rather than to the document root

               2. Layers outside stacking context can't stack between layers within it

         1. Rules that determine the stacking and painting order of elements

            1. Elements with a negative stack level, typically elements with z-index: -1

            2. Elements with static position

            3. Elements with a stack level of 0

               1. positioned elements with a z-index value of auto

            1. Elements with positive stack levels

               1. a positioned element with a z-index value of 1 or higher

            1. Elements with the same stack level are layered based on their DOM order

               1. elements stack on top of their predecessors

         1. CSS properties and values trigger a new stacking context

            1. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context

         1. Example

1\. CSS shorthand

   1. Way of collapsing some number of style rules that act on a certain set of values into a single rule  

   2. A value which is not specified is set to its initial value. That sounds anecdotal, but it really means that it overrides previously set values

      1. Eg background-color: red;

      2. background: url(images/bg.gif) no-repeat left top;

      3. Background-color will be transparent (initial value) and not red (previously set value)

      4. Solution is to set background-color individually after background to override by style further down 

   1. Shorthand properties try not to force a specific order for the values of the properties they replace

      1. If values could all be the same and would be difficult to determine which is which, certain orders are followed

         1. Shorthands handling properties related to edges of a box, like border-style, margin or padding use 1-to-4-value syntax:

            1. border-width: 1em --- value = all edges

            2. border-width: 1em 2em

               1. first value = top and bottom

               2. second value = left and right 

            1. border-width: 1em 2em 3em

               1. first value = top

               2. second value = left and right 

               3. third value = bottom

            1. border-width: 1em 2em 3em 4em 

               1. first value = top

               2. second value = right 

               3. third value = bottom

               4. fourth value = left 

         1. Shorthands handling properties related to corners of a box, like border-radius use 1-to-4-value syntax:

            1. border-radius: 1em --- value = all corners

            2. border-radius: 1em 2em

               1. first value = top left and bottom right

               2. second value = top right and bottom left

            1. border-radius: 1em 2em 3em

               1. first value = top left

               2. second value = top right  and bottom left 

               3. third value = bottom right

            1. border-radius: 1em 2em 3em 4em 

               1. first value = top left

               2. second value = top right 

               3. third value = bottom right

               4. fourth value = bottom left 

               5. Clockwise from top left

   1. Inherit = take computed value of property from parent element

   2. Initial = apply initial/default value of property

1\. CSS modules

   1. CSS files where class names are scoped locally by default

      1. not an official spec or an implementation in the browser

      2. a process in a build step (w/ the help of Webpack or Browserify)

      3. changes class names and selectors to be namespaced

      4. identifier is guaranteed to be globally unique

   1. Key benefits

      1. Step towards modular and reusable components that will not have side effects

      2. Cleaner CSS

      3. Avoidance of monolithic CSS files (each component will have its own file)

   1. Disadvantages

      1. not as human-readable DOM

      2. Need special webpack setup

   1. How does it work? 

      1. Normal css = styles are linked into the page and available globally

      2. Tries to solve inadvertent collisions/cascades in disparate components, esp in larger apps

      3. With modules, we import the styles like JS import

      4. This transforms the CSS rules, namespacing all classes

      5. css-loader injects stylesheet into the document

      6. value returned from the import is an object mapping of local CSS class names to their namespaced versions

         1. Eg, { foo:"foo_foo_abcde", bar:"foo_bar_abcde" }

      1. Setting class={style.foo} in HTML = setting it to the local version of that named class, class="foo_foo_abcde".

   1. Extending/sharing

      1. Can still use global styles for overall layout, theming, etc.

      2. Can also use css modules extend functionality

         1. can be used across files with the from keyword

      1. Composes keyword

         1. way of composing multiple classes together to form new classes

         2. similar to how you might compose two java classes together to build more complex objects

         3. allows you to build a new class out of styles from other predefined classes

         4. can import styles from other modules

         5. flexibility can lead to more efficient and reusable css class design
