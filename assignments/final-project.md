# SEA INFO-6150 Final Project

We work for a small business named **VehicleMart** that offers certain kinds of vehicles that can be bought online and personalized with a number of options.

Our team has been tasked with designing, building and testing a new website for **VehicleMart**.

I have already implemented a number of pieces of the website that relate to state management, routing, injecting data into the UI, etc.

Your role is to coordinate with the other members of your team to build the UI pieces and CSS stylesheets that display the data in a usable, accessible and attractive way.

You are encouraged to do research and look at other websites that sell products to get ideas about how to present the **VehicleMart** products and order flow.

## Rubric
This project is worth 30% of your final grade.

### Final website
15% of your final grade will be the total score of the website produced based on the rubric below. The same score will be awarded identically among all team members.

Projects will be evaluated on a 0-100 scale for each of 5 sections. Each section score will be multiplied by .20 and the 5 sections will be added together to calculate the final 0-100 score.

<table>
  <thead>
    <tr>
      <th></th>
      <th>Meets expectations (100-75)</th>
      <th>Mostly meets expectations (75-50)</th>
      <th>Does not meet expectations (50-25)</th>
      <th>Incomplete (25-0)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. HTML</td>
      <td>Site validation has no errors and few warnings, HTML is semantic and well-formed</td>
      <td>Site validation has one or two errors and/or several warnings, HTML is mostly semantic and well-formed.</td>
      <td>Site validation has several errors and/or warnings, HTML is not very semantic.</td>
      <td>Site validation has many errors and/or warnings, HTML is not semantic or unfinished.</td>
    </tr>
    <tr>
      <td>2. CSS</td>
      <td>CSS shows mastery, is clearly organized using CSS modules, fully responsive and has at least 2 adaptive breakpoints</td>
      <td>CSS shows nearing mastery and/or is included globally in index.css, is mostly responsive and has at least 1 adaptive breakpoint</td>
      <td>CSS does not show mastery, is sparse and/or is included globally in index.html, is only somewhat responsive and/or has no adaptive breakpoints</td>
      <td>CSS is very crude, near non-existent and/or unfinished, is not responsive</td>
    </tr>
    <tr>
      <td>3. Usability/accessibility</td>
      <td>Project shows good principles of usability and accessibility. It is clear and easy to use/navigate.</td>
      <td>Project shows ok principles of usability and accessibility.</td>
      <td>Project shows some principles of usability and accessibility but could use much improvement.</td>
      <td>Project is difficult to use and shows little or no principles of usability/accessibility.</td>
    </tr>
    <tr>
      <td>4. Requirements</td>
      <td>Project requirements are fully or almost fully implemented</td>
      <td>Project requirements are mostly implemented</td>
      <td>Project requirements are somewhat implemented</td>
      <td>Project requirements are mostly not implemented (project is unfinished)</td>
    </tr>
    <tr>
      <td>5. Overall result/presentation</td>
      <td>Project presented in class shows good effort and refinement</td>
      <td>Project presented in class shows OK effort and refinement</td>
      <td>Project presented in class shows low effort</td>
      <td>Project was not presented in class and/or shows barely any effort</td>
    </tr>
  </tbody>
  <tfoot>
    <td colspan="5">Total: </td>
  </tfoot>
</table>

### Journal/writeup
15% of your final grade will be your individual score as determined by the level of effort/participation detailed in your project journal/writeup. You should keep this journal while your team is working on the project as a record of your individual participation.

### HTML
The HTML for your website must be semantically correct and valid to the best of your ability. I will be validating the site with the W3 HTML Validator (http://validator.w3.org).

**You are encouraged to make any changes you wish to the HTML and components here. I am happy to help you modify components to make sure the routing and logic continue to function properly.**

## Schedule

### Week 9, March 13
You will be split into teams and review project.

### Week 10, March 20
With your team, you will work on look and feel, wireframes and sitemap for the website.

The following pieces should be submitted to me **by 2pm EDT, March 27** (ie, the beginning of Week 11 class). You can email them, share them in a Google doc, etc.

#### Look and feel
Your team should give me 3 look and feel words (eg, "bold", "calm") that you want your website to convey and an explanation of how your website will convey that using concepts discussed in class.

#### Wireframes
You must have wireframes for
* Homepage
* About
* Contact
* 404
* Products
* Product Detail
* Order flow (step 1, step 2, summary, thank you)

#### Site map
You must create a sitemap showing all the pages of the site

### Week 11, March 27
With your team, you will work on project implementation

### Week 12, April 3
With your team, you will work on project implementation

### Week 13, April 10
In class, we will conduct usability testing on each others' websites and provide feedback that teams can use to finalize their projects.

### Week 14, April 17
Each team will demonstrate their final website to the rest of the class. Personal journals/writeups should be shared in a document or emailed to a.bingham@northeastern.edu **by midnight EDT, April 18**.

## Project Requirements

### Products
**VehicleMart** offers certain kinds of vehicles that can be bought online and personalized with a number of options. The current product offerings can be viewed in `src/data/products.json`

There are already some product-related components built for you to use in your project:
* `AllProducts` -- display all products available
* `CategoryProducts` -- display products available for the categoryId in the route
* `Products` -- display product information (currently displays an image and a link to the ProductDetail page). This is currently being called from both `AllProducts` and `CategoryProducts`.
* `ProductDetail` -- display a single product based on the categoryId and productId in the route

### `AllProducts` and `CategoryProducts` page
These pages **must** use grid or flex to display the products available.

### `ProductDetail` page
You must display the following pieces of data:
* large ("lg") category image (from `src/data/categories.json`) -- this is already implemented but needs styling
* ID number
* year
* price
* sale price (if available, see below)
* title
* description

This page sends the user into the first step of the order flow via an order button that has already been implemented for you.

### Sale products
Some products may be on sale. This is indicated with a `sale: [some number]` value being present in the `src/data/products.json` object. If the product is on sale, you should style the product so that it's clear to the user that it is on sale and displays both the original and sale prices.

### Unavailable products
Some products may not currently be available. This is indicated with a `available: false` value being present in the `src/data/products.json` object. If the product is not available, we still want to include it on the `AllProducts`, `CategoryProducts` and `ProductDetail` pages; however, you should style the product so that it's clear to the user that it is not available and make it so that you cannot click on the order button on the `ProductDetail` page.

### Categories
Each product belongs to a category (given by the product's categoryId).

There is already a category-related component built for you to use in your project:
`Categories` -- display a list of categories that link to the page where `CategoryProducts` are displayed.

Every product in a category will use the category image for its display image instead of an individual image.

### Routes
All of the pages of the site are available via components controlled by a router. This simplifies the process of linking the pages together and gives a straightforward mapping of which component is associated with which URL of the website.

There is already a router implemented with the following routes in place.

#### `/`
corresponds to `http://localhost:3000/` and the `Home` component; the homepage of the website.

#### `/products`
corresponds to `http://localhost:3000/products` and the `AllProducts` component; the full product listing.

#### `/products/:category`
corresponds to a route like `http://localhost:3000/products/sedan` and the `CategoryProducts` component; the product listing for a specific category. *The category must be supplied in the URL or the route will not be matched.*

#### `/products/:category/:id`
corresponds to a route like `http://localhost:3000/products/sedan/12345` and the `ProductDetail` component; the product listing for a specific product. *The category and product ids must be supplied in the URL or the route will not be matched.*

#### `/order/1`
corresponds to `http://localhost:3000/order/1` and the `Order/OrderStep1` component; screen 1 in the order flow.

#### `/order/2`
corresponds to `http://localhost:3000/order/2` and the `Order/OrderStep2` component; screen 2 in the order flow.

#### `/order/summary`
corresponds to `http://localhost:3000/order/summary` and the `Order/Summary` component; the summary screen of the order flow.

#### `/order/thank-you`
corresponds to `http://localhost:3000/order/thank-you` and the `Order/ThankYou` component; the final submit screen of the order flow.

#### `/about`
corresponds to `http://localhost:3000/about` and the `About` component; the about page of the website.

#### `/contact`
corresponds to `http://localhost:3000/contact` and the `Contact` component; the contact page of the website.

#### `/404`
corresponds to `http://localhost:3000/404` and the `NotFound` component; the 404 page of the website.


### Layout
The website should be both responsive and adaptive; you must implement at least 2 breakpoints where the layout updates in an obvious fashion.

### 404 Not found
The website should display an attractive, usable and accessible 404 page when visiting an unmatched route.

### Navigation
The website must display 2 separate navigation menus on every page.

#### Navigation 1 links:
* Homepage
* Products
* About
* Contact

#### Navigation 2 links:
The product categories displayed by using the `Categories` component

Where you choose to place these 2 navigation menus is up to you, but they should reflect good principles of usability.

### Viewed Products
The website must display a list of the images of the 5 most recent products viewed on every page.

This `ViewedProducts` component has already been implemented and is being imported in `App.js`. You shouldn't need to do anything with the logic, but it does need styling.

### Homepage
Your website must feature a homepage for **VehicleMart**. The name **VehicleMart** must appear on the homepage and in the title of every page of the website.

Your homepage (as well as the rest of the site) should use good principles of usability and accessibility discussed in class.

### About
Your website must feature an "About" page for **VehicleMart**.

Your about page should use good principles of usability and accessibility discussed in class.

### Contact
Your website must feature a "Contact" page for **VehicleMart**.

Your contact page should use good principles of usability and accessibility discussed in class.

### Order flow
The order flow has 3 screens/steps. You will collect user options and information as detailed below. The logic and routing to move from one screen to the next has already been implemented for you, but your team needs to design and implement the HTML forms where the user enters the information.

#### Options
When ordering, a user must specify values for options they want.

It is your responsibility as the UI developer to present the options in a clear and easy-to-understand manner, taking into account the option requirements as presented below and good principles of usability and accessibility.

##### Standard Options

All options can be found here:
`src/data/options.json`

Many options are required. If a user does not select one of the required options, the UI should alert them to that fact when attempting to move on in the order flow.

Some non-required options have 2 parts:
* a selection option (do they want this option?) -- these options are named hasSomething (like hasRadio)
* a corresponding value option (how many or what type of this option do they want?)

Some options have error conditions already implemented. If the value is invalid, an error will be displayed and should be styled in such a way that it alerts the user to the fact that there is a problem.

Here is the list of options/information that you must gather in the order flow with explanations and how to store the information in state:

###### Color (required)
A user must select a hex/rgb color for their vehicle, with 2 exceptions:
* Taxis can only be yellow (#ffff0)
* Fire engines can only be red (#ff0000)

This logic is already implemented. On your color input, add the following handler

`onChange={setProductOption.bind(null, 'color')}`

###### Number of seats (required)
A user must select a number of seats. The value must be a number and must be less than or equal to 10 and greater than or equal to 1, with 3 exceptions:
* Sports cars can only have 2 seats
* Limousines can only have 8 seats
* Fire engines can only have 2 seats

**If the number is greater than 10 or less than 1, an error will be displayed.**

This logic is already implemented. On your seat number input, add the following handler

`onChange={setProductOption.bind(null, 'numSeats')}`

###### Interior fabric color (required)
A user must select one of the following colors: tan, gray, black, red, maroon, green

On your interior fabric color input, add the following handler

`onChange={setProductOption.bind(null, 'interiorFabricColor')}`

###### Dashboard color (required)
A user must select one of the following colors: tan, gray, black, red, maroon, green

On your dashboard color input, add the following handler

`onChange={setProductOption.bind(null, 'dashboardColor')}`

###### Dashboard lights color (required)
A user may select any hex/rgb color for their dashboard lights.

On your color input, add the following handler

`onChange={setProductOption.bind(null, 'dashboardLightsColor')}`

###### Hubcaps material (required)
A user may select one of the following hubcaps materials: chrome, steel, plastic

On your hubcaps materials input, add the following handler

`onChange={setProductOption.bind(null, 'hubcapsMaterial')}`

###### GPS
A user may select whether they want GPS or not.

On your GPS input, add the following handler

`onChange={setProductOption.bind(null, 'hasGPS')}`

###### Number of exhausts (required)
A user must specify a number of exhausts. The value must be a number and must be less than or equal to 4 and greater than or equal to 1.

**If the number is greater than 4 or less than 1, an error will be displayed.**

This logic is already implemented. On your exhausts number input, add the following handler

`onChange={setProductOption.bind(null, 'numExhausts')}`

###### Tinted windows
A user may select if they want tinted windows or not, with 2 exceptions:
* Fire engines cannot have tinted windows.
* Jeeps cannot have tinted windows.

**If the user tries to select tinted windows for a vehicle that can't have them, an error will be displayed.**

This logic is already implemented. On your tinted windows input, add the following handler

`onChange={setProductOption.bind(null, 'hasTintedWindows')}`

###### Radio
A user may select if they want a radio or not, with 1 exception:
* Fire engines cannot have radios.

**If the user tries to select a radio for a vehicle that can't have them, an error will be displayed.**

This logic is already implemented. On your seat number input, add the following handler

`onChange={setProductOption.bind(null, 'hasRadio')}`

If a user chooses to add a radio for a vehicle that can support it, they then need to indicate the type of radio they want.

* Basic -- this option is only available for sedans and station wagons
* Medium -- this option is available for any vehicle that supports radios
* Fancy -- this option is only available for sports cars

The radio type options for the various categories can be seen in the `values` under `radioType` in `src/data/options.json`.

**If the user tries to select a radio type for a vehicle that can't support it, an error will be displayed.**

This logic is already implemented. On your radio type input, add the following handler

`onChange={setProductOption.bind(null, 'radioType')}`

###### Glove box
A user may select whether they want a glove box or not.

On your glove box input, add the following handler

`onChange={setProductOption.bind(null, 'hasGloveBox')}`

###### Cupholders
A user may select whether they want cupholders or not.

On your cupholders input, add the following handler

`onChange={setProductOption.bind(null, 'hasCupholders')}`

If a user chooses to add cupholders, they then need to indicate how many.

On your cupholders number input, add the following handler

`onChange={setProductOption.bind(null, 'numCupholders')}`

###### Cigarette lighters
A user may select if they want cigarette lighters or not, with 1 exception:
* Fire engines cannot have cigarette lighters.

**If the user tries to select cigarette lighters for a vehicle that can't have them, an error will be displayed.**

This logic is already implemented. On your cigarette lighters input, add the following handler

`onChange={setProductOption.bind(null, 'hasCigaretteLighters')}`

If a user chooses to add cigarette lighters for a vehicle that can support it, they then need to indicate how many.

On your cigarette lighters number input, add the following handler

`onChange={setProductOption.bind(null, 'numCigaretteLighters')}`

###### Spare tire (required)
A user must select one of the following spare tire sizes: S, M, L, XL

On your spare tire input, add the following handler

`onChange={setProductOption.bind(null, 'spareTire')}`

###### Engine (required)
A user must select one of the following spare tire sizes: 4-cylinder, 6-cylinder, 12-cylinder

On your engine input, add the following handler

`onChange={setProductOption.bind(null, 'engine')}`

###### Air conditioning
A user may select if they want air conditioning or not, with 1 exception:
* Jeeps cannot have air conditioning.

**If the user tries to select air conditioning for a vehicle that can't have it, an error will be displayed.**

This logic is already implemented. On your seat number input, add the following handler

`onChange={setProductOption.bind(null, 'hasAirConditioning')}`

###### Floormats color (required)
A user must select a hex/rgb color for their floormats color.

On your floormats color input, add the following handler

`onChange={setProductOption.bind(null, 'floormatsColor')}`


##### Premium options
There are 3 options that are premium and add an extra $50 to the base price of the vehicle.

The logic for implementing the additional money and calculating the total price has already been implemented and will be displayed properly if you use the `Order/TotalPrice` component that is already imported in the `Order/Summary` component.

###### Hood ornament
A user may select if they want a hood ornament or not.

On your hood ornament input, add the following handler

`onChange={setProductOption.bind(null, 'hasHoodOrnament')}`

If a user chooses to add a hood ornament, they then need to choose one of the following types: battleship, boot, cannon, horse, iron, racecar, dog, thimble, hat, wheelbarrow

**These hood ornaments can be found in `values` under `hoodOrnament` in `src/data/options.json`. Each has a corresponding image that must be displayed along with the option.**

On your hood ornament type input, add the following handler

`onChange={setProductOption.bind(null, 'hoodOrnament')}`

###### Trunk monkey
A user may select if they want a trunk monkey or not.

On your trunk monkey input, add the following handler

`onChange={setProductOption.bind(null, 'hasTrunkMonkey')}`

If a user chooses to add a trunk monkey, they then need to select one of the following types: capuchin, spider, rhesus, macaque, baboon

**These trunk monkeys can be found in `values` under `trunkMonkey` in `src/data/options.json`. Each has a corresponding image that must be displayed along with the option.**

On your hood ornament type input, add the following handler

`onChange={setProductOption.bind(null, 'trunkMonkey')}`

###### Monogrammed steering wheel cover
A user may select if they want a monogrammed steering wheel cover or not.

On your monogrammed steering wheel cover input, add the following handler

`onChange={setProductOption.bind(null, 'hasMonogrammedSteeringWheelCover')}`

If a user chooses to add a hasMonogrammedSteeringWheelCover, they then need to enter the monogram. A monogram consists of a series of 3 letters A-Z (no more, no less, and it doesn't matter if the letters are capitalized or not).

**If the user tries to enter non-letters or some number of letters that is not 3, an error will be displayed.**

On your monogram input, add the following handler

`onChange={setProductOption.bind(null, 'monogram')}`

#### Buyer information
During the order flow, you must collect following information about the buyer. Assume that the company will call them later to get payment information, so we do not have to gather credit card numbers insecurely, for example.

* Buyer’s name
* Buyer’s shipment address (street address, city, state, 5 digit zip code)
* Buyer’s billing address (street address, city, state, 5 digit zip code)
* Buyer’s phone number (10 digits - 3 digit area code + 7 digit number)
* Buyer’s cell number (10 digits - 3 digit area code + 7 digit number)
* Buyer’s date of birth (mm/dd/yyyy format)

All of this information is required. If a user does not fill in one of the required fields, the UI should alert them to that fact when attempting to move on in the order flow.

You may assume that all buyers live in the United States and all of their data can conform to formats used in the United States.

On every input you create for buyer information, add the following handler:

`onChange={setUserInfo.bind(null, [id to store info])}`.

So, for example, to store the buyer's name, you might use the handler:

`onChange={setUserInfo.bind(null, 'buyerName')}`

#### Summary page
The second-to-last step of the order flow must be a summary of all the gathered information presented in a clear, easy-to-read way.

You must create a print stylesheet for this page using print media queries as discussed in class.

#### Thank you page
The last step of the order flow must be a thank you page that thanks the user for their order.
