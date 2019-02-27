1. Viewport

   1. Mobile browsers try to optimize experience for user

      1. Tries to render the page at a desktop screen width

         1. usually about 980px, varies by device

      1. Tries to make the content look better by increasing font sizes and scaling the content to fit the screen

      2. For sites not responsive, this is good

         1. Site will be scaled down so that it's viewable

      1. For sites not responsive, this is not so good

         1. If your site is limited to eg 1024px on an ipad and you have breakpoints set for other widths, they will not be activated

      1. Background color example

   1. Using meta tag controls the width and scaling of the browser's viewport.

      1. Eg `<meta name="viewport" content="width=device-width, initial-scale=1">`

         1. The width property controls the size of the viewport

            1. can be set to a specific number of pixels like width=600 or to the special value device-width, which is the width of the screen in CSS pixels at a scale of 100%

            2. instructs the page to match the screen's width in device-independent pixels

            3. allows the page to reflow content to match different screen sizes

            4. "Reset.css" for screen size content

            5. "Device-independent": units that provide a flexible way to accommodate a design across platforms

               1. screen pixel density and resolution vary depending on the platform

               2. Eg Mac retina display=220 ppi

               3. "Normal" display usually between 100-150 ppi

         1. Initial-scale controls the zoom level when the page is first loaded

            1. establishes a 1:1 relationship between CSS pixels and device-independent pixels

               1. some browsers keep the page's width constant when rotating to landscape mode

                  1. zoom rather than reflow to fill the screen

               1. allows the page to take advantage of the full landscape width when switching orientation

      1. Other attributes

         1. minimum-scale

         2. maximum-scale

         3. user-scalable

         4. when set, can disable the user's ability to zoom the viewport

            1. potentially causing accessibility issues

            2. Best practice: don't set these

1. CSS media queries

   1. Definition

      1. simple filters that can be applied to CSS styles

      2. make it easy to change styles based on the characteristics of the device

         1. display type

         2. width

         3. height 

         4. orientation

         5. resolution

   1. What does a media query look like? 

      1. Eg `@media (min-width: 800px) { /* styles go here */ }`

      2. A media query computes to true when the media type (if specified) matches the device on which a document is being displayed and all media feature expressions compute as true

         1. If true, then all the styles nested inside the query are applied

         2. Queries involving unknown media types are always false

         3. Queries where at least one of the expressions compute as false are false

      1. Media types

         1. general category of a device

         2. If using not or only logical operators, the media type is required

         3. Otherwise, media type is implied to be all

            1. All = Suitable for all devices

            2. Print = Intended for paged material and documents viewed on a screen in print preview mode

            3. Screen = Intended primarily for screens

            4. Speech = Intended for speech synthesizers

   1. Media queries to apply styles based on device characteristics

      1. Most used

         1. min-width: browser width greater than the value defined in the query.

         2. max-width: browser width less than the value defined in the query.

         3. min-height: browser height greater than the value defined in the query.

         4. max-height: browser height less than the value defined in the query.

         5. orientation=portrait: browser where the height is greater than or equal to the width

         6. orientation=landscape        : browser where the width is greater than the height.

         7. Any filter meeting that criteria = resulting CSS block is applied (precedence rules apply)

      1. Examples

         1. Background colors example

         2. Grid content example

   1. Relative sizes for elements to avoid breaking layout

      1. Key concept of responsive design = fluidity and proportionality as opposed to fixed width layouts

      2. Relative units for measurements

         1. simplify layouts

         2. prevent accidental elements that are too big for the viewport

         3. allows browsers to render the content based on the user's zoom level

      1. Eg width 

         1. 100% on div = spans the width of the viewport

         2. never too big or too small for the viewport

         3. fits, no matter the device 

      1. Flexbox and grid are responsive by default

         1. Use these to simplify responsive layouts!

   1. Using rems/ems/px for media queries

      1. Media queries use default font size 16px for rem/em, not whatever you have declared in your css

      2. Remember when calculating media query widths

1\. Feature queries

   1. @supports 

      1. lets you specify declarations that depend on a browser's support for one or more specific CSS features

      2. Not supported in IE 11, is supported in Edge

1\. Responsive developer tools

   1. Chrome developer tools

   2. Device toggle

   3. Image widths

1\. Responsive images

   1. Desktop size/shape images sometimes don't work for mobile size & vice versa

   2. Simple resizing: css solutions

      1. Don't need to worry about swapping out images

      2. Width: 100%; height: auto;

         1.  image can be scaled up to be larger than its original size

         2. Ok for vector images which can zoom/resize without becoming pixelated, not so good for raster images

      1. max-width: 100%, height: auto;

         1. the image will scale down if it has to, but never scale up to be larger than its original size

      1. Background: url(foo.jpg); background-size: 100% 100%;

         1. the background image will stretch to cover the entire content area

      1. Background: url(foo.jpg); background-size: cover;

         1. the background image will scale to cover the entire content area. Notice that the "cover" value keeps the aspect ratio, and some part of the background image may be clipped

         2.    1. Resolution switching

      1. wanting to show the identical image displayed to suit different resolutions

      2. Raster images look grainy when displayed at sizes larger than original

      3. Vector images are not able to support photorealistic images

      4. Bandwidth restrictions

         1. You don't want to serve full size high resolution images to mobile

      1. Ideal situation

         1. multiple resolutions available

         2. serve the appropriate size depending upon the device

      1. HTML solutions -- same resolution

         1. Eg  `<img srcset="foo.jpg 400w, bar.jpg 600w, baz.jpg 800w" sizes="(max-width: 320px) 280px, (max-width: 600px) 440px, 800px" src="baz.jpg" alt="This is an image">`

            1. Srcset

               1. Set of images the browser can choose from to display

               2. Comma separated list of image filename  + image's actual/inherent width

               3. Eg srcset="foo.jpg 400w, bar.jpg 600w, baz.jpg 800w"

            1. Sizes

               1. Set of media conditions (eg, screen widths) + width of the slot that the image will fill when the condition is true

               2. For the slot width, absolute length (px, em) or a length relative to the viewport (vw), but not percentages

               3. Last slot width has no media condition --- this is the default chosen if no other conditions match

               4. Browser ignores everything after the first matching condition

            1. Src: older browsers that don't support these features will ignore them and load src image

         1. Browser process

            1. Look at its device width.

            2. Work out which media condition in the sizes list is the first one to be true.

            3. Look at the slot size given to that media query.

            4. Load the image referenced in the srcset list that most closely matches the chosen slot size.

      1. HTML solutions -- different resolutions (eg, retina vs. standard)

         1. Eg  `<img srcset="foo.jpg 1x, bar.jpg 1.5x, baz.jpg 2x" src="baz.jpg" alt="This is an image">`

            1. Srcset

               1. Set of images the browser can choose from to display

               2. Comma separated list of image filename  + x descriptor of image resolution as multiplier of standard (1x, 2x, etc.)

               3. Eg srcset="foo.jpg 1x, bar.jpg 1.5x, baz.jpg 2x"

            1. Sizes: none, browser just chooses appropriate resolution

            2. Src: older browsers that don't support these features will ignore them and load src image

         1. Browser process

            1. Look at its device resolution.

            2. Load the image referenced in the srcset list that most closely matches the chosen resolution

   1. Image switching

      1. wanting to change the image displayed to suit different image display sizes

      2. Images at different scale/size might look weird/less appropriate

      3. HTML solutions

         1. Eg `<picture><source media="(max-width: 799px)" srcset="foo-cropped-one-way.jpg"><source media="(max-width: 1200px)" srcset="foo-cropped-another-way.jpg"><img src="foo.jpg" alt="This is a picture"></picture>`

            1. Source

               1. Media: media conditions (eg, screen widths)

                  1. Use media attribute only when swapping completely different images

                  2. If using media, don't also include a sizes attribute

               1. Srcset: same as above (could have comma separated list)

               2. Eg `<source media="(max-width: 799px)" srcset="foo-cropped-one-way.jpg">`

            1. Img

               1. you must provide an img element, with src and alt

               2. Must be right before </picture>

               3. otherwise no images will appear

   1. Why not CSS/JS?

      1. Browser preloads images before the main parser loads CSS and JavaScript

      2. If you load the <img> element, then detect the viewport w/JS and dynamically change the source image to a smaller 

         1. the original image would already have been loaded

         2. would load the small image as well

         3. Multiple image downloads
