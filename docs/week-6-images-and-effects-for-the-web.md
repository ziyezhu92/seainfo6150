1\. Typography

   1. Text-decoration

      1. Shorthand for text-decoration-line, text-decoration-color, and text-decoration-style

      2. Appearance of decorative lines used on text

      3. Best practice: Do not use underlining except on links

      4. Style: dashed, dotted, wavy, solid, double

      5. Line: underline, overline, line-through

      6. Eg. text-decoration: green dashed underline

      7. Example

   1. Transform

      1. https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform

      2. Takes language specific cases into account

      3. Capitalize

      4. Uppercase

      5. lowercase

   1. HTML entities

      1. special character that can't be represented as plain text in an HTML document

      2. Reserved =, left bracket, right bracket, and &

      3. Quotation marks

      4. https://dev.w3.org/html5/html-author/charref

1\. Z-index

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

   2. A value which is not specified is set to its initial value

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

1\. Images for web

   1. Vector images

      1. use lines, points, and polygons to represent an image

      2. essentially giant math equations, and each dot, line and shape is represented by its own equation

      3. ideal for images that consist of geometric shapes

      4. zoom and resolution-independent

         1. Scaling up a vector = smooth, crisp graphics

         2. ideal format for high-resolution screens and assets that need to be displayed at varying sizes

      1. What do I mean by high-resolution screens?

         1. High resolution screens have multiple device pixels per CSS pixel

            1. CSS pixel does not always equal device pixel

            2. Single CSS pixel may contain multiple device pixels

            3. The more device pixels there are, the finer the detail of the displayed content on the screen

         1. High resolution images require significantly higher number of pixels and bytes

            1. High DPI screens (dots per inch = pixels fit into an inch) 

            2. image assets need more detail in order to use higher device pixel counts

            3. vector images = rendered at any resolution with sharp results

            4. raster images = data on a per-pixel basis

               1. larger the number of pixels = the larger the filesize of a raster image

               2. photo asset displayed at 100x100 (CSS) pixels: https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization

               3. double the resolution of the physical screen = quadruples the number of required pixels

            1. high resolution screens also require high-resolution images

               1. prefer vector images whenever possible

               2. deliver and optimize multiple variants of each image (will talk about responsive images with responsive layouts)

      1. SVG

         1. Stands for Scalable Vector Graphics

         2. XML-based markup language for describing two dimensional based vector graphics

            1. essentially to graphics what HTML is to text

            2. defined in XML text files which can be searched, indexed, scripted and compressed

            3. can be created and edited with any text editor and with drawing software

            4. Designers will generally create/edit SVGs for you, but it helps to know what an SVG file looks like

         1. Example: SVG in HTML file

         2. SVG editor: https://svg-edit.github.io/svgedit/releases/latest/editor/svg-editor.html

         3. Include as img or background-image: if you don't need to modify with CSS

         4. Include as inline: if you want to access inner paths/shapes with CSS/scripting/filters

         5. Include as data uri: if you don't need to modify and you want to save additional data file download

   1. Raster images

      1. represent an image by encoding the individual values of each pixel within a 2-dimensional grid of individual "pixels"

         1. 100x100 pixel image is a sequence of 10,000 pixels

         2. each pixel stores the "RGBA" values: (R) red channel, (G) green channel, (B) blue channel, and (A) alpha (transparency) channel

      1. complex scenes with lots of irregular shapes and details

      2. Scaling up a raster image = jagged and blurry graphics

      3. Lossless vs lossy image compression

         1. For certain data like source code or executable

            1. critical that a compressor does not alter or lose any of the original information

            2. single missing or wrong bit of data could completely break it entirely

            3. "Lossless" compression = capture all of the data of your original file

               1. Nothing from the original file is lost

               2. file may still be compressed

               3. all lossless formats will be able to reconstruct file to its original state

         1. For some other types of data, such as images, audio, and video

            1. may be perfectly acceptable to deliver an "approximate" representation of the original data.

            2. can often get away with discarding some information about each pixel in order to reduce the filesize of an image

            3. "Lossy" compression = approximate what your original image looks like

               1. might reduce the amount of colors in your image or analyze the image for any unnecessary data

               2. typically reduce the file size, though they may reduce the quality of your image

         1. Lossy files typically much smaller than lossless files

         2. Each raster image file is either lossless or lossy, depending on how the format handles your image data

            1. any image can undergo a lossy compression step to reduce its size

            2. difference between various image formats GIF, PNG, JPEG, and others = combination of the specific algorithms they use or not when applying the lossy and lossless steps

            3. No optimal configuration/universal setting

               1. All depends on the image and what is acceptable to the display

      1. GIF

         1. lossless raster format

         2. stands for Graphics Interchange Format

         3. Limited to 256 colors

         4. Supports alpha channel transparency

            1. Aliased transparency

            2. "Jaggy edge", transparency does not blend nicely

      1. PNG

         1. lossless raster format

         2. stands for Portable Network Graphics

         3. "next-generation GIF"

         4. Supports anti-aliased transparency

            1. "Smooth edge", blends nicely

         1. can display higher color depths --> translates into millions of colors

         2. web standard, quickly becoming one of the most common image formats used online

      1. JPG

         1. lossy raster format

         2. stands for Joint Photographic Experts Group (technical team that developed it)

         3. have a sliding scale of compression that decreases file size tremendously, but increases artifacts or pixelation the more the image is compressed

1\. Background images

   1. applies an image or gradient to the background of an element

   2. Images

      1. Background-image: url(foo.jpg);

      2. url() --  file path to any image to use for background

         1. Relative: relative to the folder from which css is loaded

            1. if images are in another folder, use absolute path or relative to the root path (starting with /)

         1. Absolute

      1. Multiple background images: background-image: url(image-front.jpg), url(image-back.jpg)

         1. Comma separated values

      1. Image will tile horizontally and vertically by default

         1. No-repeat

         2. Repeat-x

         3. Repeat-y

         4. Comma separated values for each background image

   1. Gradients

      1. Linear -- straight line

         1. background-image: linear-gradient(red, green);

         2. Top to bottom by default

            1. "To" keyword to change direction

               1. background-image: linear-gradient(to bottom right, red, green); 

            1. Degrees

               1. background-image: linear-gradient(135deg, red, green); 

               2. 0deg = vertical gradient running bottom to top

               3. 90deg = horizontal gradient running left to right

               4. 180deg = vertical gradient running top to bottom

               5. 270deg = horizontal gradient running right to left

               6. clockwise direction

               7. negative angles run in the counterclockwise direction

         1. Color stop: change from one color to another at specific spot

            1. background-image: linear-gradient(red, green 25%);

            2. two color stops that are the same = color instantly changes to another solid color

               1. background-image: linear-gradient(red, red 25%, green 25%);

      1. Radial -- circle out from point

         1. background-image: radial-gradient(red, green);

         2. Default shape is ellipse if box is not square

            1. Force to circle: background-image: radial-gradient(circle, red, green);

         1. Location

            1. "At" keyword to change location of center

               1. background-image: radial-gradient(at top right, red, green);

         1. Supports linear concepts like color stops, multiple colors

      1. Conical

         1. similar to a radial gradient

            1. both are circular 

            2. Both use the center of the element as the source point

            3. Radial = colors emerge from the center of the circle

            4. conic = colors move around the circle

            5. Look like the shape of a cone from above

            6. Starts at top (0), moves clockwise around

         1. Supports linear concepts like color stops, multiple colors

         2. Not supported in anything but Chrome basically

1\. Effects

   1. Shadows

      1. Box-shadow: Used in casting shadows (drop shadows)

         1. Eg: box-shadow: 5px 5px 10px 10px red;

         2. 5 elements

         3. The horizontal offset (required)

            1. positive = the shadow will be on the right of the box

            2. negative = the shadow on the left of the box

         1. The vertical offset (required)

            1. negative = the shadow will be above the box

            2. positive = the shadow will be below the box

         1. The blur radius (required),

            1. 0 the shadow will be sharp

            2. the higher the number, the more blurred it will be, and the further out the shadow will extend

         1. The spread radius (optional)

            1. positive = increase the size of the shadow

            2. negative = decrease the size of the shadow

            3. Default is 0 (the shadow is same size as its blur)

         1. Color (required)

            1. If color is omitted, shadow will use are drawn in the foreground text color

            2. Can take any named value, hex, rgb, rgba

         1. Shadow can be inset into the box as well

            1. "Inset" keyword

            2. Box-shadow: inset 5px 5px 10px 10px red;

         1. Can comma separate box shadows to apply multiple shadows around box

   1. Animations

      1. Ability to animate transitions from one CSS style configuration to another

      2. consist of two components

         1. style describing the CSS animation

         2. set of keyframes that indicate the start and end states of the animation's style + possible intermediate points

      1. Advantages to CSS animations:

         1. easy to use for simple animations (does not require knowing JS)

         2. the animations run well

            1. browser can use frame-skipping and other techniques to keep the performance as smooth as possible

         1. the browser optimizes performance and efficiency

      1. Animation sub properties:

         1. Animation-name: the name of the @keyframes describing the animation's keyframes

         2. Animation-duration:  length of time that an animation should take to complete one cycle

         3. Animation-timing-function: how the animation transitions through keyframes, by establishing acceleration curves (linear, ease-in, ease out, etc.)

            1. https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function

         1. Animation-delay: delay between the time the element is loaded and the beginning of the animation sequence

         2. Animation-iteration-count: number of times the animation should repeat

            1. Use "infinite" to repeat forever

         1. Animation-direction: should the animation alternate direction on each run through the sequence or reset to the start point and repeat itself

         2. Animation-fill-mode: what values are applied by the animation before and after it is executing

            1. Does it retain the last css styles to persist the change? Does it reset itself?

            2. https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode

         1. Animation-play-state: pause and resume the animation sequence.

      1. Example

1\. Optimizing images

   1. Do you need an image at all? 

      1. Eliminate unnecessary image resources

         1. Every image downloaded = extra data load on your user

      1. Select the right image format

         1.  three universally supported image formats: GIF, PNG, and JPEG

         2. Need small file sizes for simple graphics? 

            1. Use GIF

            2. compression techniques in the GIF format allow image files to shrink tremendously

         1. need animation?

            1. GIF is the only universal choice

            2. GIF limits the color palette to at most 256 colors

         1. Need transparency?

            1. PNG = alpha transparency

            2. GIF = aliased transparency

         1. need to preserve fine detail with highest resolution? 

            1. Use PNG

               1. does not apply any lossy compression algorithms beyond size of the color palette

               2. highest quality image, but at a cost of significantly higher filesize than other formats -- use wisely!

         1. Image is a photo, screenshot, or similar? 

            1. Use JPEG

            2. JPEG uses a combination of lossy and lossless optimization to reduce file size of the image asset

            3. Try different JPEG quality levels to find the best quality vs. filesize tradeoff for your asset

         1. image contains imagery composed of geometric shapes?

            1. consider converting it to SVG format

         1. Image contains text?

            1. Use web fonts instead of encoding text in images

            2. Still selectable, searchable, resizeable, easily translatable -- usability!

      1. SVG files should be minified/optimized to reduce their size

         1. https://jakearchibald.github.io/svgomg/

         2. Illustrator SVG → optimized

      1. Compress raster images

         1. Bit depth

            1. number of memory bits used to store color data for each pixel in a raster image

               1. 1 bit = 2 colors (black and white) "bit map"

               2. 2 bits = 4 colors

               3. 4 bits = 16 colors

               4. 8 bits = 256 colors

               5. 16 bits = "thousands"

               6. 32 bits = "millions"

            1. reduce the "bit-depth" of the image from 8 bits per channel to a smaller color palette

               1. 8 bits per channel = 256 values per channel = 16,777,216 (256 ^ 3) colors in total

               2. Reducing to 256 colors = 8 bits in total for the RGB channels and immediately save two bytes per pixel

            1. Complex scenes with gradual color transitions (gradients, sky, etc.) require larger color palettes to avoid visual artifacts

            2. if the image only uses a few colors, then a large palette is simply inflating bits for no reason

         1. Leverage CSS3 effects (shadows, gradients, etc.) where possible

         2. Already being loaded along with your css

         3. CSS effects/animations

            1. produce resolution-independent assets 

            2. always look sharp at every resolution and zoom level

            3. fraction of the bytes required by an image file
