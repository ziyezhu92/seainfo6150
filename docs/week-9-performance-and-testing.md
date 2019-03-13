1. Testing

   1. Example: creating a calculator app

   2. Unit testing

      1. Writing tests for the the individual functions you write to support your code and describe the functionality of the individual units

      2. Eg. re: calculator -- the buttons, the calculation functions, the UI are produced separately and unit tested separately

      3. Eg. if you write a helper function

         1. `Function sum(a,b) { return a+b; }`

      1. You'd want to test to make sure the return of the function 

         1. matches your expectations with regard to the inputs 

         2. Fully describes the expected behavior of the function, 

         3. Including edge cases

            1. Is it possible for this function to be passed invalid inputs? 

            2. How does the function handle them? 

            3. Does everything crash?

      1. Importance of making functions as small and granular ("single responsibility") as possible in order to make testing as easy as possible. 

      2. It's important that unit tests work truly as a unit

         1. Ie changes to other parts of your code don't make existing unit tests start failing

         2. If they do, these aren't true unit tests and you need to work on extracting/separating them further

      1. Tests are simply a series of functions that run your code and state assertions/describe expectations about the results of that code, given the inputs provided

         1. Assertions can be grouped together into a larger unit called a suite

         2. Not just for plain JS!

         3. You can write tests for React components to make sure they render as expected, assign correct CSS classes, etc. 

            1. Jest is particularly good for this

            2. Can create a "snapshot" of what a properly-rendered component looks like, and then Jest can test against that every time the tests run and validate the component still renders as expected

      1. Can and should have many unit tests to cover as many cases as possible

   1. Integration Testing

      1. Next level up from unit testing

      2. Integration testing = individual units are combined and tested as a group

         1. purpose is to expose faults in the interaction between integrated units

      1. Eg. re: calculator -- once the individual pieces are developed and tested, you put them together and test that.

         1. Does the UI show the number of the button that was pressed? 

         2. Does the reset button clear all the previous values?

      1. Integration tests allow developers to 

         1. start their applications locally

         2. Create fake implementations (mocks) for all dependencies

         3. focus specifically on the functionality they are developing/testing

      1. benefits of integration tests

         1. Reliability

         2. isolated front-end, feature-focused testing

         3. early insight into application performance

      1. Can and should have many integration tests to cover as many cases as possible

   1. End-to-end Testing

      1. test the whole application together as a user would

         1. automating whatever the user does

      1. there should not be many E2E tests

         1. If tested correctly in the unit and integration tests, probably checked everything

         2. E2E test should just check that the glue binding all units works

         3. E2E tests are slow & running lots of tests would take a long time

         4. E2E tests tend to be flaky, ie unreliable because of API calls and prone to failure

         5. Can mitigate flakiness by not having more than the minimum

            1. Does the website load?

            2. Can you navigate to the page? 

            3. Can you perform some basic tasks? 

   1. Testing frameworks

      1. There are a number of different frameworks

      2. Examples

         1. Jasmine

         2. Mocha

         3. Karma

         4. Jest

      1. All have pros & cons

      2. Just a matter of evaluating your specific needs (eg Jest is becoming standard for React testing)

   1. Performance/Stress Testing

      1. Optimizing your website's response/download time for the user

      2. http://www.frontendtesting.com

         1. A 1-second improvement correlated to a 27% increase in conversion rate

         2. Conversions (ie people who completed a call to action like a purchase or newsletter signup) were 27% higher for visitors who enjoyed a load time that was one second faster

         3. Pages that loaded in 2.4 seconds experienced a 12.8% bounce rate, while those that loaded in 3.3 seconds had a bounce rate of 20%.

      1. optimize during development:  doing as much as you can before you deploy your site

         1. https://www.dropbox.com/s/21vof23jlwf0swc/performance-checklist-1.2.pdf?dl=0

         2. Progressive enhancement

            1. Start minimal and scale up

            2. If your website is fast on a slow machine with a bad connection, it will only get faster on better machines/connections

         1. image optimization/minification

            1. Choose the right image type for the task

            2. Reduce color palettes to minimum for file size gains

         1. deferring scripts

            1. Have JS and other scripts load after important content so that the page content can load and render more quickly (not blocked) 

         1. Lazy-loading content

            1. Load only visible content and fetch additional content as needed 

         1. Identify and remove unused code (CSS & JS that might be bundled and increasing total payload unnecessarily) 

         2. Enabling compression when the web server is sending data

            1. Compress HTML, JS, CSS, images, etc.

            2. Multiple compression types: gzip, Brotli, Zopfli

      1. Optimize the site after it has been deployed

         1. Use tools such as Pagespeed, LightHouse, or Pingdom to test your site

            1. get a report on how your site is performing, and fix issues that are affecting your site's performance

         1. Lighthouse

            1. https://developers.google.com/web/tools/lighthouse/

            2. automated tool for improving the quality of web pages

            3. audits for performance, accessibility, progressive web apps, etc

            4. Dev tools > Audits > Perform audits

         1. Pagespeed

            1. https://developers.google.com/speed/pagespeed/insights/

         1. Pingdom

            1. https://www.pingdom.com/

   1. CSS & JS Linting

      1. Linting can help developers to write good quality, optimized code

         1. Code-checking process that looks for errors in the source code, and flags potential bugs

         2. can also be used during debugging to find errors that are hard to catch otherwise

      1. You can lint at multiple times

         1. in real time while you write the code

         2. when you save the file

         3. when you commit the changes

         4.  before the code goes into production

   1. Visual Regression Testing

      1. Just using the website to identify errors

      2. Most generally used to identify rendering errors like incorrect CSS that makes UI look broken

      3. Labor-intensive and not easy to automate

   1. Usability/Accessibility Testing

      1. Checking to see if the website is conducive to use by users with physical, mental or emotional challenges

   1. https://dynomapper.com/blog/27-accessibility-testing/246-top-25-awesome-accessibility-testing-tools-for-websites

1. Multivariate (A/B) testing

   1. https://www.smashingmagazine.com/2010/06/the-ultimate-guide-to-a-b-testing/

   2. Method for determining the best choice between two or more versions of a website, website element, UI etc

      1. Multiple versions of an element (A and B) + metric that defines success

         1. A is usually existing design and B (C, D, etc.) are the new versions

      1. subject both versions to experimentation simultaneously by splitting your website traffic between them

      2. measure their performance using metrics that you care about (conversion rate, sales, bounce rate, etc.)

      3. select the version that performs best for real-world use

   1. every A/B test is unique but often pertain to 

      1. element's wording, size, color and placement

      2. Headline or product description

      3. Form's length and types of fields

      4. Layout and style of website

      5. Product pricing and promotional offers

      6. Images on landing and product pages

      7. Amount of text on the page (short vs. long)

1. Feature flagging

   1. A pattern that allows developers to work concurrently on new features while supporting old features safely without introducing unintended consequences

   2. Named conditionals (flags) used to control code execution

      1. If the flag is on, new code is executed, if the flag is off, the code is skipped

      2. Also could have more complex flags (eg, if a flag is on, it returns one of several possible options instead of just evaluating to true)

   1. Flags allow new features to be constantly deployed (released with the existing codebase)  but not "released" (turned on) in production

      1. can be launched with flags set to off or to a select audience to validate functionality and performance prior to releasing broadly

   1. Flags can give you the ability to change their state from outside the application

      1. let you defer decisions until you see what the real system is doing

      2. Let you place the decisions about code execution with stakeholders like product owners

         1. They can turn flags on and off based on business-decisions and not have to wait for development/release cycle

   1. Use cases

      1. release/A/B test a new feature to a subset of your users (like a group of users who opt-in to a beta tester group), gathering feedback and bug reports from real-world use cases

      2. Gradually release a feature to an increasing percentage of users, and track the effect that the feature has on key metrics

      3. turn off a feature that you realize is causing performance problems in production, without needing to re-deploy

      4. Grant access to certain features based on user attributes

      5. disable parts of your application to facilitate maintenance, without taking everything offline.
