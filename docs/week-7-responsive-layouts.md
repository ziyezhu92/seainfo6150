1. Responsive web design

   1. Definition

      1. responds to the needs of the users and the devices they're using

      2. layout changes based on size/capabilities

      3. Examples

         1. http://www.northeastern.edu

         2. https://www.bostonglobe.com/

         3. http://www.wired.com

   1. Responsive vs. adaptive

      1. Both change appearance based on the browser environment (usually browser width)

      2. Responsive

         1. Respond to the size of the browser at any given point

         2. No matter browser width, the site adjusts its layout optimized to the screen

      1. Adaptive

         1. Adapt to the width of the browser at a specific points

            1. On phone, users might see single column view

            2. On tablet, users might see two columns

         1. Traditionally what we mean re: responsive

      1. Smooth vs. snap

         1. https://css-tricks.com/the-difference-between-responsive-and-adaptive-design/

      1. Examples

1. Mobile first philosophy

   1. Develop for the smallest mobile device first, then progressively enhance the experience as more screen real estate becomes available

      1. Mobile development = hardest, most limitations (eg screen size and bandwidth)

      2. Do mobile first!

      3. Smallest screens = only most crucial features

         1. Gives you a chance to reconsider "extraneous" features

         2. Do they need to be included on desktop?

1. Breakpoints

   1. a point that allows for the provision of the best possible layout that enables users to consume or understand your site's content for their current viewport size

   2. Mobile first: start small, work up

      1. As you expand that view, there will be a point at which the layout looks terrible

      2. that's where you add a breakpoint!

   1. Create breakpoints based on content, not devices

      1. Devices change, responsive/adaptive development should ideally work across all

      2. Breakpoints are easier to work around content than layout/design

   1. Keep lines of text to max 70-80 chars

      1. Optimize for reading

      2. As columns become too wide for comfortable reading/display, add breakpoints

      3. Adaptive font sizing (ems)

   1. Don't hide content!

      1. If content doesn't fit at certain breakpoints, is it necessary? 

      2. Data load

   1. Don't target devices!

      1. Set breakpoints wherever the presentation of the content degrades instead of specific device widths 

      2. This covers any device that comes along 

      3. Future proofing

   1. "Progressive enhancement"

      1. Build from bottom up

      2. Mobile first = content first

         1. Developing within mobile parameters forces you to prioritize content

         2. Content focus = user focus

   1. "graceful degradation"

      1. build from top down

      2. Problem w/graceful degradation

         1. Starting with the all-inclusive design = the core and supplementary elements merge

         2. Harder to distinguish and separate

         3. Treating mobile design as an afterthought -> "cutting down" the experience

1. Flexbox

   1. https://css-tricks.com/snippets/css/a-guide-to-flexbox/

   2. more efficient way to lay out, align and distribute space among items in a container especially when their size is unknown and/or dynamic

   3. give the container the ability to alter children width/height/order to best fill the available space 

      1. expands items to fill available free space

      2. shrinks items to prevent overflow

   1. Direction agnostic (can respond to direction changes, dir attribute from week 3)

   2. Most appropriate to application components and small-scale layouts

      1. grid layout is intended for larger scale layouts

   1. Flex container (parent)

      1. Display: flex

         1. Creates flex context for children (direct children only)

         2. Example + hands-on

      1. Flex-direction: 

         1. main axis, direction items are placed in container

         2. flex items mostly lay in horizontal rows or vertical columns

         3. row/row-reverse

         4. column/column-reverse

         5. Example + hands-on

      1. Flex-wrap

         1. By default, values will all try to fit along axis, but wrapping can be set

         2. Nowrap (default)

         3. Wrap/wrap-reverse

         4. Example + hands-on

      1. Flex-flow: shortcut for flex-direction + flex-wrap

         1. Eg flex-flow: row wrap;

         2. Example + hands-on

      1. Justify-content

         1. Defines alignment along the main axis

            1. Along horizontal line for row flow

            2. Along vertical line for column flow

         1. Flex-start: clustered towards beginning of axis

         2. flex-end: clustered towards end of axis

         3. Center: centered in middle of axis

         4. Space-between: items are evenly distributed

            1. first item is on the start line

            2. last item on the end line

         1. Space-around

            1. items are evenly distributed in the line with equal space around them

            2. visually the spaces aren't equal, since all the items have equal space on both sides

         1. Space-evenly

            1.  items are distributed so that the spacing between any two items (and the space to the edges) is equal

         1. Example + hands-on

      1. Align-items

         1. Defines alignment at cross axis to main axis

            1. Along vertical line for row flow

            2. Along horizontal line for column flow

         1. flex-start: cross-start margin edge of the items is placed on the cross-start line

         2. flex-end: cross-end margin edge of the items is placed on the cross-end line

         3. center: items are centered in the cross-axis

         4. baseline: items are aligned such as their text baselines align

         5. stretch (default): stretch to fill the container

         6. Example + hands-on

      1. Align-content

         1. Aligns lines within when there is extra space in the cross-axis

         2. flex-start: lines packed to the start of the container

         3. flex-end: lines packed to the end of the container

         4. center: lines packed to the center of the container

         5. space-between: lines evenly distributed; the first line is at the start of the container while the last one is at the end

         6. space-around: lines evenly distributed with equal space around each line

         7. stretch (default): lines stretch to take up the remaining space

   1. Flex children

      1. Order

         1. laid out in the source order by default

         2. Order can be specified by integer

      1. Flex-grow/flex-shrink

         1. ability for a flex item to grow/shrink if necessary

         2. takes unitless value that serves as a proportion relative to other flex children

         3. dictates what amount of the available space inside the flex container the item should take up

      1. Flex-basis

         1. Default size of element before space is distributed

         2. Length

            1. Length 0 = extra space around content isn't factored in

         1. Auto: "use my width or height property" (depending on flow)

      1. Flex

         1. Shorthand for flex-grow (+ flex-shrink + flex-basis) [shrink/basis optional]

         2. Eg flex: 1; flex: 0 1 auto (default); flex: 2 1 auto;

      1. Align-self

         1. Allows the default alignment (or the one specified by align-items) to be overridden for individual flex items

1. Grid

   1. https://css-tricks.com/snippets/css/complete-guide-grid/

   2. two-dimensional grid-based layout system

   3. Good for dividing a page into major regions or defining the relationship in terms of size, position, and layer, between parts of a control built from HTML tags

   4. Picture newspaper layout with rows and columns

   5. grid layout enables an author to align elements into columns and rows

      1. NOT table 

      2. Remember table is for tabular data that corresponds to the intersection of a row and column

   1. Definitions

      1. Grid container (parent)

         1. display: grid

            1. direct parent of all the grid items

            2. Creates grid context for children (direct children only)

            3. Grids can be nested by making children grid containers w/ display: grid

      1. grid line

         1. https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout#Grid_lines

         2. dividing lines that make up the structure of the grid

         3. vertical ("column grid lines") or horizontal ("row grid lines")

         4. Located in between rows or columns, or around the outside

         5. numbered according to the writing mode of the document

            1. In a left-to-right language, line 1 is on the left-hand side of the grid, in r-t-l, line 1 is on the right-hand side

      1. grid track

         1. space between two adjacent grid lines

         2. the columns or rows of the grid

         3. Tracks can be defined using any length unit (ie, rem, em, px, %, etc. 

         4. New unit = fr

            1. fraction of the available space in the grid container

            2. Eg = 1fr 1fr 1fr

            3. each track = 3 equal width tracks that fill available space

      1. Grid area

         1. elements spanning one or more cells by row or by column

            1. must be rectangular -- can't create an L-shaped area, for example

      1. Grid cell

         1. single "unit" box of the grid

         2. smallest unit on a grid

   1. Explicit vs. implicit grid

      1. Rows and columns defined with grid-template-columns = explicit grid

      2. Rows and columns created when content goes beyond bounds of explicit = implicit grid

      3. Eg  defined our column tracks with the grid-template-columns property, but the grid also created rows on its own

   1. repeat()

      1. grids with many tracks can use repeat() 

      2. repeat all or a section of the track listing

         1. Eg 1fr 1fr 1fr = repeat(3, 1fr)

   1. minmax()

      1. Way of defining how tracks (rows or columns can expand/collapse and never go under/over a certain size. 

         1. Eg. may want to give tracks a minimum size, but also ensure they expand to fit any content that is added

      1. minmax(100, auto) = may want my rows to never collapse smaller than 100 pixels, but if my content stretches to 300 pixels in height, then I would like the row to stretch to that height

         1. Auto = the size will look at the content size and will stretch to give space for the tallest item in a cell, in this row

   1. Gutters

      1. Spaces between grid cells

      2. Created with column-gap & row-gap properties

1. Difference between flexbox and grid

   1. flexbox was designed for layout in one dimension - either a row or a column

      1. works from the content out.

      2. Good use case for flexbox is when you have a set of items and want to space them out evenly in a container

      3. let the size of the content decide how much individual space each item takes up

      4. If the items wrap onto a new line, they will work out their spacing based on their size and the available space on that line

   1. grid was designed for two-dimensional layout - rows and columns at the same time

      1. works from the layout in

      2. create a layout and then you place items into it, or you allow the auto-placement rules to place the items into the grid cells according to that strict grid
