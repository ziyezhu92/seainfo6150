1\. DOM

   1. Document Object Model

   2. Even though it has functions, not a programming language

   3. DOM is an in-memory, object-oriented representation of web pages, HTML documents, XML documents, and their component parts as objects and nodes which can be modified with a scripting language

      1. The page content is stored in the DOM and may be accessed and manipulated via JS

   1. DOM as an object

      1. describes how every element in HTML page relates

         1. HTML document = the topmost structure

         2. each element on the page = separate object that with own relationship to the document

      1. Allows interaction w/individual elements and page as a whole

         1. Modify elements

         2. retrieve and set element properties

         3. add and remove elements or objects

         4. capture and respond to user or browser actions/events

   1. Viewing DOM

      1. HTML in devtools = visual representation of the DOM

      2. created directly from your HTML, but it's often not the same, possible reasons:

         1. mistakes in HTML →  browser has fixed them for you

            1. Eg table

               1. browser will insert missing <tbody> 

               2. Viewable in DOM

         1. Manipulated DOM via JS

            1. Eg empty container injected with content via js (react app node)

   1. Structure

      1. Live DOM viewer: http://software.hixie.ch/utilities/js/live-dom-viewer/

      2. every element of the document = object or a node

         1. organized in a hierarchical fashion

         2. has a function and an identity 

         3. each node can also have any number of child nodes

            1. may be other elements or text nodes

      1. browsers read an HTML page and turn data into objects logically arranged as a data structure tree (DOM tree)

         1. parent node (the node right above it)

         2. child nodes (the nodes below it)

         3. siblings nodes (other nodes belonging to the same parent)

      1. Types of nodes

         1. 12 node types: https://dom.spec.whatwg.org/#node

         2. Element Nodes

            1. individual tags or tag pairs in HTML

         1. Text Nodes

            1. content in between the open/close HTML tags

            2. usually have a parent node and sometimes sibling nodes 

            3. cannot have their own child nodes.

         1. Comment Node

            1. Doesn't affect presentation

            2. Everything in HTML becomes DOM

   1. Accessing and using DOM

      1. As soon as JS is loaded, can immediately use API for the document or window elements

         1. manipulate the document itself 

         2. get at the children of document (elements in the web page)

      1. Objects borrow from several different interfaces. 

         1. Eg table object

            1. HTMLTableElement interface, which includes such methods as createCaption and insertRow

            2. Element interface

            3. basic Node interface

      1. Document and window objects used most often

         1. window object = the browser

            1. global scope

            2. all functions and methods built into JS are built off the window object

            3. JS checks window for any variables we haven't defined 

         1. document object = root of the document itself

            1. DOM representation is a property of window (window.document)

      1. DOM scripting

         1. Build elements from text up

         2. createTextNode

         3. createElement

         4. element.appendChild

         5. setAttribute

         6. Example

1\. HTML continued

   1. Lists 

      1. 3 types 

         1. Unordered: lists that do not have inherent order 

         2. List item: markup list items within ordered and unordered tags 

         3. Ordered: lists that represent ordered information 

            1. Example: series of steps 

         1. Definition list: list of related term & definition pairs 

            1. Example: implement a glossary or to display metadata (a list of key-value pairs) 

   1. Image 

      1. Embeds image into a document 

      2. Src attribute = path for images 

         1. Relative 

         2. Absolute  

      1. Width & height attributes inherent on tag to set layout for stable page layout 

         1. CSS for width & height 

      1. Each browser supports different set of image formats 

         1. Eg Firefox: JPEG; GIF, including animated GIFs; PNG; APNG; SVG; BMP; BMP ICO; PNG ICO 

      1. Alt attribute: alternate text displayed  

         1. Eg while loading, loading error 

   1. H1-H6 

      1. Outline concept 

         1. H1 highest level content 

      1. 1 h1 per page 

      2. Header for block of content 

      3. Reduce header numbering as traversing outline 

      4. Try not to skip headers 

         1. Start with h1, next level h2, etc. 

         2. Use in conjunction with <header> tags 

   1. More content blocks 

      1. Header 

         1. introductory content 

         2. navigational aids 

         3. may contain logo, search form, author name, and so on 

         4. Multiple blocks can have headers 

         5. Group headers in <hgroup> 

      1. Footer 

         1. footer for its nearest sectioning content.  

         2. typically contains information about the author, copyright data, publishing data 

      1. Figure 

         1. self-contained content 

         2. Often with figcaption 

         3. typically referenced as a single unit 

         4. image, illustration, diagram, code snippet, etc., that is referenced in the main flow of a document 

         5. Can be moved elsewhere without affecting main flow 

         6. figcaption  

            1. caption or legend for the rest of the contents its parent figure 

   1. Tables 

      1. Presentation of tabular data 

      2. Data that can be represented as a 2 dimensional display of columns and rows 

      3. Tables were used for content layout, should only be used for tabular data now 

      4. Caption 

         1. caption/title of a table 

         2. Always comes after table (first child) 

      1. Thead 

         1. set of rows defining the head of the columns 

      1. Tbody 

         1. Set of rows defining the body of the table 

      1. Tfoot 

         1. set of rows summarizing the columns of the table 

         2. Example: totals in a spreadsheet 

      1. Tr 

         1. row of cells in a table 

         2. Container for combination of th and td cells 

      1. Th 

         1. Header of a group of table cells 

         2. Scope col or row defines directionality of heading 

      1. Td 

         1. cell of a table that contains data 

      1. Rowspan/colspan

         1. Allows a single table cell to span the width or height of more than one cell or column

            1. Picture "merge cell" in spreadsheet programs

         1. Rowspan: Allows a single table cell to span the height of more than one cell or row

         2. Colspan: Allows a single table cell to span the width of more than one cell or column

         3. might be used for a header cell that titles a group of columns or a side-bar that groups rows of entries.

         4. colspan= and rowspan= are attributes th and td

         5. The value of either attribute must be a positive integer (a whole number)

            1. specifies the number of columns or rows that the cell fills

   1. Forms 

      1. document section that contains interactive controls 

         1. submitting information to a web server 

         2. capturing/handling interactive actions in a human-usable way 

         3. Action = URI of a program that processes the form information 

            1. Often not used for React app 

               1. Variables -> state -> API calls, etc.

            1. Would be used to send data to form processing script on a server (ruby, php, perl, etc.) 

         1. Method = HTTP verb method of sending data. POST, GET, etc. 

         2. In modern single-page apps (eg, react), inputs are often used independent of full forms in order to add hooks for interactivity via handlers on elements (buttons and inputs)  

      1. Fieldset 

         1. Used to group multiple related fields/controls/labels within a form 

         2. Example: first/middle/last name 

         3. Browser default is to put border around, can be removed with CSS 

      1. Legend 

         1. Caption/title for content of its parent fieldset 

      1. Label 

         1. title/caption for interactive form element 

         2. Best practice: associate label + input with "for" 

            1. allows screen readers and other non-visual browsers to make link between label and input 

            2. allows input to be activated when label is activated, especially on very small inputs (eg, checkbox, radio) 

         1. Best practice: 1 label per input 

            1. can have multiple labels  

            2. Screen readers can have problems with them 

      1. Input 

         1. create interactive controls for web-based forms in order to accept data from the user 

         2. Multiple control widgets 

            1. Listing most common, several more depending on application you need 

            2. https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input 

            3. Not all supported by all browsers 

            4. [type=button]: button widget with no default behavior 

               1. Use for any action where you need to capture javascript action and trigger code 

            1. [type=text]: default text inputs 

            2. [type=checkbox]: allows multiple values to be selected for an input response 

               1. Value: not seen in the browser, corresponds to the value to be given to as the input response 

                  1. If value is omitted, default value is "on" 

               1. Multiple checkboxes 

                  1. Server will receive values separated by "&" 

            1. [type=radio]: allows only 1 value to be selected for an input response 

            2. [type=submit]: button widget with default behavior of submitting the form 

            3. [type=password]: password inputs 

            4. [type=number]: number inputs 

               1. Mobile browsers will launch number-only keypad 

               2. Browser provides automatic validation entered text is a number 

               3. set of up and down buttons to step the value up and down 

            1. [type=tel]: telephone inputs 

               1. Mobile browsers will launch telephone keypad 

               2. makes adding custom validation and handling of phone numbers more convenient 

               3. the input value is not automatically validated to a particular format 

         1. Disabled 

            1. State where user cannot interact with the control 

               1. Not clickable 

               2. User cannot activate/input value 

         1. Readonly 

            1. User cannot modify the value of the input 

            2. Different than disabled: user can still click on/interact with control 

         1. Required 

            1. Indicates form is invalid if left empty (will not submit) 

      1. Select 

         1. control that provides a menu of options 

         2. Multiple: allows multiple options to be selected by cmd/ctrl clicking 

      1. Optgroup 

         1. Group options in a select 

         2. Label displayed is not selectable 

      1. Option 

         1. Defines items contained in a select or optgroup 

         2. Value: value to be sent to the form 

         3. Selected: indicates default selected option 

            1. If none specified, defaults to first in the options list 

            2. If multiple specified, multiple can be selected 

   1. Button 

      1. Clickable button element 

      2. Can be used either inside or outside forms 

      3. Presented as same style as OS button by default with no styling 

      4. Value: initial value of the button.  

      5. Button content: enter between tags 

1\. React/JS

   1. Variables

      1. const/let

      2. Const -- value won't change

      3. Let -- value might/could change

   1. Objects

      1. Structure of key/value pairs

         1. Value can be any JS object: number, string, function, class, etc.

      1. Access objectName['foo'] or objectName.foo

      2. Used for data that doesn't need to be in a specific order when looping

      3. Loop through for...in

   1. Arrays

      1. Structure of ordered list of elements

         1. elements can be any JS object: number, string, function, class, etc.

      1. Access arrayName[index number of element]

      2. Loop through map/for each/for loop

   1. Functions

      1. Params go in, result comes out

      2. Single responsibility -- small & granular

      3. Function examples

   1. Class components

      1. Class inheritance (extends)

         1. JS object consisting of other functions, variables

         2. Can be inherited from other classes to extend functionality at more granular level

         3. Example

      1. Structure of a React class component

         1. This.props

         2. This.state

         3. Constructor

         4. Render

   1. Event handlers

      1. onClick, onChange

      2. Defining handlers as part of a class

   1. State

      1. Way of storing variables needed to display the UI in a certain way

      2. When state is the same, UI should be the same

      3. setState AddingMachine example
