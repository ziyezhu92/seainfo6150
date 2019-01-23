1\. React

   1. React is view library for generating html                

   2. Why use React? 

      1. the view is a visual representation of your application's state

         1. For a given application state, your view will always look the same way

         2. Makes it easier to reason about how your view will behave

         3. Great for repetition (reusable components)

      1. State

         1. stores a component or app's dynamic data & determines the component or app's behavior and visual representation

         2. because state is dynamic, it enables a component to keep track of changing information in between renders

         3. Examples of uses for state

            1. Which navigation item is active

            2. Whether a button is disabled or not based on external logic

            3. The value of an input

      1. Reusable components

      2. Virtual DOM

         1. memory reconciliation algorithm

         2. not invented by React, but React uses it and provides it for free

         3. abstraction of the HTML DOM

            1. Lightweight

            2. detached from the browser-specific implementation details

            3. constructs a representation of the page in a virtual memory

            4. performs the necessary updates/diffs with previous version before rendering the final into the browser

            5. Actually an abstraction of an abstraction

               1. React's local and simplified copy of the HTML DOM

               2. allows React to do computations in abstract & skip the "real" DOM operations 

         1. HTML DOM = always tree-structured

            1. Traversing trees is fairly easy but easy !== quick

            2. DOM trees are huge especially as we move to dynamic web apps/single page applications 

            3. we need to modify the DOM tree constantly

         1. DOM updates

            1. performance and development pain

            2. hard to manage

            3. Inefficient

            4. Slowness isn't actual DOM operations but layout that browsers have to do whenever the DOM changes

               1. Every time the DOM changes, browser needs to recalculate the CSS, do layout, and repaint the web page

         1. Virtual dom = strategy of reducing and batching DOM changes

            1. it tries to minimize reflow & repaint stages to gain performance

            2. React's render() method 

               1. creates a node tree from React components

               2. updates this tree in response to mutations in the data model caused by actions

               3. Once rendered, React ceases to control the elements (become normal DOM nodes)

               4. Each time the data changes, new Virtual DOM representation of UI is created

            1. Updating the browser DOM: 

               1. On data change, the entire UI is re-rendered in Virtual DOM

               2. The difference between previous Virtual DOM and the new one is calculated

                  1. https://medium.com/@gethylgeorge/how-virtual-dom-and-diffing-works-in-react-6fc805f9f84e

                  2. Reconciliation diagram

               1. The real DOM is updated with only the actual changes, like applying a patch

   1. "single source of truth"

      1. In jquery, eg, the DOM carries the application state directly

         1. "New content" list

            1. Trigger some condition when number of new content paragraphs reaches 7

            2. Business logic -- what else needs to know this condition?

            3. If app could use "isMax", not only button could use it but other components as well

            4. Only way to get text in new content #5 is

            5. $(".new-content:nth-of-type(5)").text()

               1. DOM is the only place that knows that information.

      1. React teaches us to think about that kind of logic/information as state

         1. build your HTML using pieces of that state

         2. you won't have to deal with the DOM directly at all, react will handle for you

1\. Create-react-app

   1. environment for learning React

      1. Bootstraps to start building a new single-page application in React

      2. sets up your development environment so that you can use the latest js features

      3. provides a nice developer experience

      4. optimizes your app for production

      5. doesn't handle backend logic or databases

      6. creates a frontend build pipeline, so you can use it with any backend you want

      7. uses Babel and webpack, but you don't need to know anything about them

   1. need Node >= 6, npm >= 5.2 on your machine

1\. App organization

   1. React  and similar apps usually organize components into individual files & directories

      1. /Component = Component.js, Component.module.css

      2. Component.js = HTML + JS

      3. One component per file

1\. Components

   1. like JavaScript functions

      1. accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen

         1. Props can be strings, numbers, other React components, functions

         2. Component can also be passed special props called children

            1. Like HTML tags, component tags can surround content

            2. Eg <Foo>this is text, an image, another component</Foo>

            3. The text, img, other component would be accessed from Foo.js via props.children

      1. module-like pieces of code

      2. they're reusable and can be repeated across several web pages

      3. single responsibility principle

         1. a component should ideally only do one thing

         2. If it ends up doing a lot, it should be decomposed into smaller components

      1. Composition vs. inheritance

         1. Props and composition provide flexibility to customize

            1. components may accept arbitrary props like primitive values, other React elements/components, functions.

         1. Import additional non-ui functionality from separate JavaScript modules

            1. Can use function, object, class without extending them

   1. Kinds of React components

      1. Functional components

         1. Simply a functions that can accept props as an argument and return valid JSX

         2. Lack of state and lifecycle methods

         3. Also called "stateless components"

         4. Small and reusable

         5. simple to both read and understand

      1. Class components

         1. Class components are ES6 classes

         2. "class Foo extends Component"

         3. only required method is render()

         4. Gives you access to lifecycle hooks

            1. methods for when the component is 

               1. Rendered

               2. removed to and from the DOM

               3. updated with new state or props

            1. Internal state

   1. Working with components

      1. Components are imported from their component files into the app or component where you want to use them 

      2. Eg import Foo from 'Foo.js'

      3. Referenced with <Foo />

      4. If component can take children, then <Foo></Foo>

   1. React bundles JS & HTML together, sometimes CSS also

      1. Separation of concerns?

      2. Component acts as a unit

   1. Create a component example 

      1. Hello, world

      2. Hello [name]

      3. Looping through passed props

      4. props.children

1\. HTML

   1. https://html.spec.whatwg.org/

   2. Part of SGML (standard generalized markup language)

   3. Follows DTD format

      1. DTD = Document Type Definition

      2. set of markup declarations that define a document type,

         1. Ensures that document renders in standards mode

         2. Defines what's allowed in your document and what's not

   1. Not context-free = cannot be quantified with a series of recursive rules for describing.

      1. Allows omitting some start and ending tags (browser added)

      2. Soft syntax

      3. Popular, easy to write

   1. HTML = publishing language for web

      1. Tim Berners-Lee invents the Web

      2. CERN, the European Laboratory for Particle Physics in Geneva, Switzerland

      3. Way for researchers to organize/pool data

      4. Hypertext: link files/text from one to another (cross-referencing)

   1. HTML5

      1. Most recent version (2008)

      2. Added several semantic tags

      3. Video + audio

      4. Vector graphics (svg, canvas)

      5. Web workers (js running in background)

   1. Purpose: structural meaning to web content

1\. Viewing HTML in browser

   1. Demo in Chrome

      1. Use browser comfortable and familiar to you

      2. Things may look different

   1. Open file in browser

      1. Menu command: File > Open File

      2. Keyboard command: Cmd/Ctrl O

      3. Navigate to file location

1\. Semantic HTML

   1. https://internetingishard.com/html-and-css/semantic-html/

   2. Use of HTML markup to express meaning of the information instead of defining presentation

   3. Separation of concerns

      1. HTML: markup, content structure

      2. CSS: presentation, appearance

   1. Example: 

      1. <H1> vs big & bold

      2. <em> vs bold

   1. Important to make structure semantic

      1. Maintainability: helps you as a developer keep your site organized

      2. Accessibility

         1. Every HTML document has an "outline," which is how search engines and screen readers view the hierarchy of the content on the page

         2. Outline helps adapt the way they present information to the users according to the structure of the document

         3. The more semantic the markup, the easier it is for search engines, screen readers, and other machines to identify the different parts of your website. 

      1. Picture a series of boxes tucked away in an attic

         1. None of the boxes are labeled

         2. How do we know how to organize whatever is inside the boxes when we visit the attic? 

         3. Semantic HTML = giving the boxes relevant labels to give structure/meaning to whoever has to view the content later

            1. Browser

            2. Web crawler/robot

            3. Code maintainers

   1. Elements reference: https://developer.mozilla.org/en-US/docs/Web/HTML/Element

1\. What does HTML look like?

   1. Tag = some keyword between < > brackets

      1. <tag>

      2. <div>

      3. <strong>

      4. <img>

   1. Open tag + (USUALLY) closing tag

      1. <tag></tag>

      2. <div></div>

      3. <img /> ← does not take a closing tag, the /> is the closure

         1. Closing tags enclose content encompassed by the tag

         2. <div>Foo</div>

         3. <strong>Bar</strong>

         4. <img /> ← images don't have content to enclose

      1. Some tags don't need to be closed

         1. "Self closing tags"

         2. Closing tags are optional because it's implied that a new tag would not be able to be started without closing it 

         3. html, head, body, p, dt, dd, li, option, thead, th, tbody, tr, td, tfoot, colgroup

         4. Tags that never take an explicit close: img, input, br, hr, meta

         5. If unsure, use the HTML validator: https://validator.w3.org/

      1. HTML can be nested

         1. Inline elements are nested within block elements

            1. Eg <p><strong>This is strong</strong> while this is not</p>

         1. Block elements can be nested within block elements

            1. Eg <section><p>This is a paragraph in a section</p></section>

         1. Inline elements can be nested within inline elements, in some cases

            1. Eg <p><strong><em>This is both strong and emphasized</em></strong></p>

         1. Nesting must be closed from inside out, like parentheses

            1. Cannot cross tags while closing nesting. 

            2. Eg <p><strong><em>This is both strong and emphasized</p></strong></em> is incorrect!

1\. <!DOCTYPE html>

   1. Informs the website visitor's browser that the document being rendered HTML document

      1. Interpret document in HTML5 compliant way

      2. Ignore the new features of HTML5 if not supported

      3. https://caniuse.com/

   1. Every HTML document should begin w/ DOCTYPE declaration to be compliant with HTML standards

   2. 3 layout engine modes

      1. Full standards mode: layout behavior is behavior described by HTML5 + CSS specs

      2. Almost standard mode: layout behavior is close to specs with some deviations

      3. Quirks mode: layout behavior is nonstandard behavior from Navigator 4 and Internet Explorer 5

         1. Support websites that were built before the widespread adoption of web standards (corp. Intranets, eg.)

   1. Simplest doctype

      1. All existing browsers will interpret as full standards

1\. HTML tag

   1. the root (top-level element) of an HTML document

   2. Also called "the root element" 

   3. All elements must be descendants of this element, except doctype

   4. Lang

      1. Define the language of an element

         1. Uneditable elements = language written in

         2. Editable elements = language user should use

      1. Could tag/define every single element of a page as different language

      2. In general, defined on HTML tag

   1. Dir

      1. Directionality of language

         1. Ltr = left to right, eg. English, Spanish

         2. Rtl = right to left, eg. Hebrew, Arabic

         3. Auto = let browser decide

      1. Can be overridden by css

         1. Recommended use HTML attributes if CSS not supported for some reason

1\. Head tag

   1. provides general information about the document

      1. Title

      2. Metadata

      3. links to scripts and style sheets

   1. Meta tag

      1. https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta

      2. represents metadata that cannot be represented by other elements

      3. Charset

         1. declares the page's character encoding

         2. Always specify encoding; needed to process non-ASCII characters entered by the user in forms, in URLs generated by scripts, and so forth.

         3. Always use utf-8

            1. Unicode-based encoding

            2. Supports many languages

            3. Wide browser support

            4. Wide usage

               1. https://w3techs.com/technologies/details/en-utf8/all/all

               2. UTF-8 is used by 92.2% of all the websites whose character encoding we know

         1. Right after <head>

         2. Equivalent declarations

            1. <meta charset="utf-8">

            2. <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>

      1. Name

         1. defines the name of a piece of document-level metadata

         2. viewport

   1. Title

      1. Identify page in in browser tab

      2. Example

1\. Content sectioning

   1. Outliner: https://gsnedders.html5.org/outliner/

   2. HTML5 brings precision to how documents are broken into sections using sectioning blocks and headers

      1. Allows document outlines to be predictable and used by the browser to improve the user experience

   1. Sections

      1. https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML_sections_and_outlines

      2. All content lying inside <body> is part of a section, even if the section is the body itself

      3. sections in HTML5 can be nested

      4. Explicit sections = enclosing content in opening/closing tags like section, article, aside, etc.

         1. Example

      1. Implicit sections = dividing content with h1-h6 headers

         1. Each header causes browser to close previous section and start new

         2. Example

      1. To make your markup human-understandable, good practice to use explicit tags for opening and closing sections

      2. Exception: reusable components that may be assembled instead of top to bottom outline

         1. H1 for top level

         2. Best judgement for next level headers

         3. Outline will be generated 

   1. <Body>

      1. Content section of webpage

      2. 1 per HTML document

      3. All visible content in the viewport will be located inside the body

   1. <Main>

      1. dominant content of the <body> of a document, portion of a document or application

      2. Usually defined as being separate from document header/footer

   1. <Section>

      1. Generic sectioning block

      2. explicitly delineate block of website

   1. <Article>

      1. self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable

         1. forum post

         2. magazine or newspaper article

         3. blog entry

         4. Twitter post

   1. Sectioning blocks that don't get added to the document outline

      1. <Nav>

         1. Indicates a block of navigation links, either within the current document or to other documents

            1. Menus

            2. tables of contents

            3. Indexes

            4. Breadcrumbs

         1. Can be own block or within context of header, footer, etc.

         2. Do not need to mark individual links as nav

            1. The <a> itself is an indicator that it is navigation

      1. <Aside>

         1. portion of a document whose content is only indirectly related to the document's main content

            1. Sidebars

            2. call-out boxes

         1. Aside does not imply "to the side"! Can be located anywhere within content.

         2. Could be used to markup ad space/promoted content/affiliate info

   1. Content dividers

      1. Not sectioning blocks

         1. do not produce new sections in outline

      1. <Div>

         1. block of content

         2. hook for css

      1. <P>

         1. paragraph of text

   1. <Blockquote>

      1. Long quotation

      2. Usually rendered indented visually

      3. Cite attr: provide URL reference to where the quote comes from

1\. <A> = creates hyperlink to other reference

   1. Surrounds content to be clicked on

      1. Could be simple text, image, etc.

   1. Examples

      1. Absolute link = <a href="http://www.google.com">Google</a>

      2. Relative link = <a href="/foo.html">Foo</a>

      3. Mailto: = <a href="mailto:a.bingham@northeastern.edu">April's email</a>

   1. Target attribute

      1. _self: load url into current browsing context. (default)

      2. _blank: load url into new browsing context. (tab or window)

      3. _parent: load url into parent browsing context. (same as _self if no parent)

         1. Example: page in iframe

      1. _top: load url into top browsing context (same as _self if no parent)

         1. Example: nested pages in iframes

   1. Best practice: do not capture links with javascript handlers and subvert action

      1. Ramifications for browser history and accessibility

      2. Allow user client to determine what to do with the link

      3. Target attribute for new window

      4. For javascript capturing, attach action to button and style like text link

1\. Text markup

   1. Block vs. inline elements

      1. Block

         1. block-level elements may contain inline elements or other block-level elements

         2.  block elements create "larger" structures than inline elements

      1. Inline

         1. inline elements may contain only data and other inline elements

         2. can't put block elements inside inline elements

         3.  inline elements do not force a new line to begin in the document flow

   1. <span>

      1. Generic inline text container

      2. Like div, used for css hooks

   1. <strong>

      1. Content with strong importance, seriousness, or urgency

      2. Typically rendered as bold

      3. Why not use <bold>?

         1. Possible to provide emphasis without making something bold

         2. Color, border, etc. 

         3. Bold !== strong and vice versa

   1. <em>

      1. Content to be emphasized

      2. Text that may be italicized in text

      3. Typically rendered as italic

      4. Why not use <i>?

         1. Same as strong/bold

         2. Italic !== emphasis

   1. <sub> or <sup>

      1. Subscript

         1. Footnote numbers

         2. Chemical symbols: C8 H10 N4 O2

      1. Superscript

         1. Exponents: a ^ 2 (a2)

         2. Ordinal numbers: 4th

   1. <abbr>

      1. Abbreviation

      2. Attribute title

         1. Instructs browser to give definition inline

   1. <br>

      1. Line break

      2. Equivalent to carriage return 

      3. Break up lines of text that are still related by block

   1. <address>

      1. contact information associated with the webpage itself (arbitrary addresses should use p)

      2. can be used in a variety of contexts

         1. providing a business's contact information in the page header

         2. indicating the author of an article by including an <address> element within the <article>

   1. <code>

      1. Indicate block is fragment of computer code

      2. Default display: monospace font

   1. <q>

      1. Short inline quotation

      2. Browser will render in quotation marks 

         1. Example: quotations appropriate for language! En vs. fr

   1. <s>

      1. Strikethrough

      2. Text that is no longer relevant or accurate

   1. <time>

      1. presenting dates and times in a machine readable format

      2. Datetime attribute = needs to be machine readable

         1. Valid datetimes: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time

      1. Date/time enclosed by tags can be human readable

      2. Eg <time datetime="2018-11-22">November 22, 2018</time>

   1. <var>

      1. Variable name in mathematical expressions

      2. Typically rendered as italicized

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
