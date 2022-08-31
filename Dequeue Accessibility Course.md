- Type:: [[Course]]
- Subject:: [[Webdev]] [[Web Accessibility]]
- Status:: [[In Progress]]
- Abstract::
- Summary::
    - part 1
        - Types of dissabilities
            - Blindness
                - Considerations
                    - Make sure that everything is labelled correctly
                    - Use semantic html
            - On color blindness
                - Considerations
                    - The biggest takeaway is that color is not a reliable way to display information
            - Deafness
                - Web accessibility prioritizes visually impaired over auditorily impaired
                - Considerations
                    - Mostly just put transcripts (I prefer transcripts anyway)
            - Motor Dissabilities
                - Can be really impaired if a modal that doesn't focus appears on the screen
                - Stephen hawking - triggering the minimum amount of movement to make the computer do what he wants.
                - Developed the keyboard and predictive text programs to help him become the leading scientist of his generation.
                - "Without a computer, i would be little more than a vegetable"
                - Typewriter artist https://youtu.be/svzPm8lT36o
                    - Amazing tale of using the disability and creating something beautiful
                    - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2Fol9U7IOcBJ.png?alt=media&token=246e8c7f-6ea8-4e68-a033-0cb7b5577451)
                    - All done using a keyboard!
                    - Considerations
                        - **All functionality must be available using only the keyboard**.
                        - **Links, buttons, and controls must have a visible :focus state** and should have a **visible :hover state**.
                        - With session time-outs, **warn users before the time expires** (e.g. an accessible dialog or alert), and **give them the option to extend the session**. Ensure the warning itself allows for slow responses. A recommended minimum response time is 2 minutes.
                        - **Provide large click targets (links, buttons, controls)** for users who have movements that are difficult to control.
            - Speech Dissabilities
                - Considerations
                    - Don't depend on voice input
            - Cognitive Disabilities
                - People wth cognitive issues might not have the ability to navigate complicated web interfaces. This is not particularly surprising, but a good goalpost as interfaces SHOULD be accessible to people with disabilities. Generally, if you make something accessible to someone with a lower cognitive capacity it will be more intuitive for everyone. 
                    - Write software as though it is written for the user with the lowest cognitive ability. 
                    - Seems like a good UX design principle.
            - Reading Disabilities
                - Provide alternative formats to users with reading disabilities
        - WCAG Standards
            - a - minimum
            - aa - accessible
            - aaa - maximum
            - Main principles of the standard
                1. ** Perceivable:**
                    - Information and user interface components must be presentable to users in ways they can perceive. 
                    - __[Ensure content is accessible to people who are blind and/or deaf.]__****
                    - 1.1 Provide text alternatives for any non-text content so that it can be changed into other forms people need, such as large print, braille, speech, symbols or simpler language.
                    - 1.2 Provide alternatives for time-based media.
                    - 1.3 Create content that can be presented in different ways (for example simpler layout) without losing information or structure.
                    - 1.4 Make it easier for users to see and hear content including separating foreground from background.
                2.  **Operable**
                    - User interface components and navigation must be operable.
                    - __[Make sure all features are accessible by keyboard; not just by mouse.]__****
                    - 2.1 Make all functionality available from a keyboard.
                    - 2.2 Provide users enough time to read and use content.
                    - 2.3 Do not design content in a way that is known to cause seizures.
                    - 2.4 Provide ways to help users navigate, find content, and determine where they are.
                    - 2.5 Make it easier for users to operate functionality through various inputs beyond keyboard.
                3.  **Understandable**
                    - Information and the operation of user interface must be understandable.
                    - 3.1 Make text content readable and understandable.
                    - 3.2 Make Web pages appear and operate in predictable ways.
                    - 3.3 Help users avoid and correct mistakes.
                4. **Robust**
                    - Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.
                    - 4.1 Maximize compatibility with current and future user agents, including assistive technologies.
            - 
    - PART 2
        - Four main principles of accessibility[*](((vzNnYwFe3))) {{[[r/moved]]}}
            - **Perceivable **- Information and user interface components must be presentable to users in ways they can perceive.
            - **Operable** - User interface components and navigation must be operable.
            - **Understandable** - Information and the operation of user interface must be understandable.
            - **Robust** - Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.
        - ### Accessibility is the minimum
            - sure your site meets the guidelines, did you think about blind people tho?
            - Objective standards for accessibility
                - All images must have an alt attribute.
                - All form input elements must have a label.
                - The header cells of a data table must be marked as header cells using <th>.
                - The page must have a title.
                - Color cannot be used as the only visual means of conveying information.
            - Designing an alt version is the ultimate signal of this was an afterthought
        - ### 6 Principles of Accessible Design
            - Equitable use
            - Flexibility in Use
            - Simple and Intuitive Use
                - bad example
                    - A web site uses custom JavaScript widgets that are new in design and concept, and unfamiliar to users.
            - Perceptible Information
            - Tolerance for Error
            - Low Physical Effort
        - ### Exclusive Design Paterns
            - Buildings have stairs to get to the entrance
                - Viewing buildings as flawed, not people as flawed
            - Some accessibility designs start out as bad ideas even before they're built
                - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2Fy2PQan-OoA.png?alt=media&token=aeaea1db-4fa2-40fe-934e-f1db2e6768a8)
                - **Adding tabindex to focusable elements to fix bad tab order:** In theory, adding tabindex to every focusable element on a page would work to fix the tab order, but even if it is done perfectly, it will do nothing to fix bad reading order. That will put the reading order and the tab order out of sync. On a practical level, if there is any JavaScript DOM manipulation that adds new focusable elements to the DOM, or removes any from the DOM, the tabindex values may need to be completely out of order again, and may need to be altered by JavaScript, which would be costly. Plus, using tabindex (of positive numbers) has a host of other problems (values of "0" and "-1" are useful, especially when working with custom JavaScript widgets).
                - **Clunky fallback interaction patterns in widgets:** A widget designed for mouse interaction (like drag-and-drop functionality) that has accessibility features, but the accessibility features are not intuitive, and have obviously been added only for accessibility compliance, and not as the result of good interaction design.
                - **Text-only explanation of widgets that aren't accessible:** A complex widget, such as a chemistry lab simulation, that was designed for fully-able-bodied users, and which would be difficult to make accessible, so they provide a text description of what you're supposed to experience or learn, without actually letting you experience the widget itself. The information is technically accessible, but the experience is not equivalent.
                - **A lesser "accessible version:"** A link on an inaccessible site to an "accessible version" that turns out to be a stripped-down text-only version with clunky, but technically accessible, features. It is inconvenient to not be able to use the main web site in the first place, and stigmatizing because the person realizes she's getting a worse design than the rest of the population.
        - ### Affordances
            - Affirdabces are those things that an object allows a user to do
                - It is something like the way that Heidegger talks about the hammer and the nail. The outcomes that are possible through the interaction with an object
            - Donald Norman vs James J. Gibson on how to define affordances
                - Gibson:
                    - Binary
                    - Has nothing to do with the user's knowledge
                - Norman Human Computer Interaction
                    - Percievability is key
                    - Cultural
                    - Can be obfuscated or revealed through the design
                - Norman: 
                    - Objects should be designed for the right kind of affordances
        - ### Audio User Experiences
            - Audio navigation of websites relies on semantic elements
                - ```html
<main>
<nav>
<header>
<section>
<footer>```
                - Feedback for Audio
                    - **Name:** The name or label applied to the element. Screen readers will announce the name of most kinds of semantic elements when the user lists them, focuses on them, or reads through them.
                    - **Description:** Extra information about the element (via aria-describedby). Screen readers usually announce the description (if any) after announcing the element's name.
                    - **Role:** Identification of the kind of element they are interacting with (e.g. a text field, a tab panel widget, a tree view, a button, a link, a graphic, a dialog, etc.). Screen readers announce the role of most semantic elements.
                    - **Value:**
                        - **Properties:** Characteristics of elements, such as aria-valuemax (on things like sliders), aria-controls, aria-owns, etc.
                        - **States:** Changeable conditions about an element, such as aria-selected=true/false, aria-checked=true/false, aria-hidden=true/false, etc. In most cases, screen readers will read the state change automatically when the user activates a feature. For example, a screen reader will say "expanded" after the user activates a button that changes from aria-expanded="false" to aria-expanded="true". No JavaScript or live regions are required to make a screen reader announce the state change.
                    - "Live" announcements: Updates
                - 
    - Part 3 Semantic Structure and Navigation
        - Page <title>
            - The <title> is the first thing that users hear with a screen reader
            - Pages MUST contain a page title
            - Titles MUST be descriptive
                - "Keyword" - Search Results
                    - Unique information, followed by general information
                    - ![A group of tabs in a browser showing page titles on the tabs that all look identical.](https://dequeuniversity.com/assets/images/html_css/title-unique.png)
                        - Example of nothing meaningful in the title
            - Language must be explicit. It should say it in order for the screen reader to go through the page properly
                - for changes in through the docs ise the lang= atribute on the html element
                    - ```html
<p>While in Spain, my friend tried to speak Spanish, 
but she wasn't very good. Everyone kept saying 
&quot;<span lang="es">No comprendo nada de lo que dices.</span>&quot;</p>```
        - **HTML5 elements and corresponding ARIA roles**
            - {{[[table]]}}
                - **HTML5**
                    - **Aria Role**
                        - **Listed Among Landmarks by Most Screen Readers**
                - <header>
                    - role="banner"
                        - Yes
                - <nav>
                    - role="navigation"
                        - Yes
                - n/a 
                    - role="search"
                        - Yes
                - <main>
                    - role="main"
                        - Yes
                - <footer>
                    - role="contentinfo"
                        - Yes
                - <aside>
                    - role="complementary"
                        - Yes
                - <section>
                    - role="region"
                        - Mixed support: Most screen readers list it only if given a name via aria-label or aria-labelledby.
**Note** that if each section has a heading, screen reader users will be able to navigate by headings, so it is usually not necessary to give each section or region a name, and in fact it can be a bad idea to supply too many landmarks in a page, because it slows down the user's ability to sort through them all.
                - <[[Article]]>
                    - role="[[Article]]"
                        - Mixed support: JAWS lists it, but other screen readers do not
                - <form>
                    - role="form"
                        - Mixed support: Screen readers list forms only if marked as role="form" (the <form> element will be ignored in landmark lists)
                - <header>
                    - role="banner"
                        - Yes
        - Heading
            - Heading is a way to denote the content of the page
            - Banners and large text are not headings!
            - There should only be ONE h1
                - One of the main reasons that the <h1> should appear at the beginning of the main content is because screen reader users can use keyboard shortcuts to navigate directly to the first <h1>, which, in principle, should allow them to jump directly to the main content of the web page. If there is no <h1>, or if the <h1> appears somewhere other than at the start of the main content, screen reader users will have to listen to more of the web page to understand its structure, wasting valuable time.
        - Links
            - Should be descriptive, if it depends on context, then use supplemental techniques to make them descriptive again. 
                - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FV-jh_vxWYG.png?alt=media&token=0e0c2078-6905-4299-bc80-cb905b0927fd)
            - Avoid Click Here or More as link text
            - Indicate if it opens a new window
            - You can use aria-described-by to a aria-hidden attribute in the page. 
            - Visual Indicators. It is fine to overrwrite them as long as their focus state does change for people with disabilities
        - Navigation
            - DO NOT assign role="navigation" to a <ul> it strips the ul of its native functionality
            - DO indicate which nav item is the current page
                - use aria-label or hidden text to indicate current page
            - Give a chance for keyboard users to skip the navigation
                - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2FIx56hO6AMK.png?alt=media&token=c12d5fda-a2c2-4a00-8763-0a46cc5cc843)
                - Safari requires the element to be tabbable, so `[tabindex="-1"]`  helps solve this
                - The "skip link" SHOULD be the first focusable element on the page. (Can be visually hidden as long as it is focusableThe "skip link" SHOULD be the first focusable element on the page. (Can be visually hidden as long as it is focusable)
            - Screen readers ignore the css of the page. Long navigations make it difficult for people to see.
                - Dynamically loaded content can appear above a user's keyboard focus
                - tabindex makes things out of order. Use only 0 to give tabindex and -1 to make things hidden
        - Tables
            - Should have a caption. 
                - The title should not be a row that spans all cells
            - Use th for headers
                - you can use the `[headers="id-1 id-2 id-3"]` for complex tables
        - Iframes
            - Must have a title
            - Are considered part of the page by screen readers
            - The heading structure should follow the page heading
    - Part 4 Media
        - Image alt tags should be 
            - Discernible 
            - Meaningful
            - ## Concise
                - Get to the point, give relevant context. Alt tags behave different than paragraphs, navigate by word, save the place where you were don't work
        - Purely Decorative images are fine to leave blank `alt=""`
        - Form inputs can be of type image, supply an alt text
            - Because you can do this for some reason
 `<input type="image" name="submit" src="submit-button.png"  alt="Submit">`
        - Long descriptions should go in a paragraph
            - ```html
<img class="border" src="bar-chart.png" width="546" height="330" 
alt="Bar chart with percentages. Extended description below chart."
aria-describedby="description-extended">

<div id="description-extended">
    <p>Full long description goes here.</p>
</div>```
        - SVG Elements
            - SVGs should have a role="img" attribute
            - If they are inline, you can use the `<title>` element with `labelledby` and its corresponding id
                - ```html
<svg role="img" aria-labelledby="widgetSales">
  <title id="widgetSales">Total Widgets Purchased during 2016</title>```
            - There is also desc for long descriptions. (use both if needed)
                - ```html
<svg role="img" aria-labelledby="widgetSales widgetSalesDescription">
  <title id="widgetSales">Total Widgets Purchased during 2016</title>
  <desc id="widgetSalesDescription">
      The graph displays the total number of widgets...
  </desc>```
            - Have these two add up to 150 characters or less if possible
                - If more text is required to describe the image in a meaningful way, consider using one of the following techniques for complex images that makes the content available to all users:
                    - Provide the long description in the context of the HTML document itself.
                    - Provide a button that expands a collapsed region that contains the long description.
                    - Provide a button to open a dialog that contains the long description.
                    - Provide a link to a long description on another page via a normal link text.
            - High Contrast Mode on Windows
                - You can target the behavior then on Edge and IE
                    - ```css
/* Styles for all high contrast modes: */
@media screen and (-ms-high-contrast: active) { }

/* Styles for the Windows "High Contrast Black" theme: */
@media screen and (-ms-high-contrast: white-on-black) { }

/* Styles for the windows "High Contrast White" theme: */
@media screen and (-ms-high-contrast: black-on-white) { }```
                - 
    - Part X Labels
        - Labels must be meaningful, i.e., they must clearly explain the purpose of the field.
        - Labels must be programmatically associated with their control.
        - Labels must be visible at all times.
        - Labels must be in close proximity to their control.
        - **Use Labels, don't rely on placeholders, if you must use images make them self explanatory and keep all the alt label considerations**
        - ```html
<table>
<caption>Edit Program Information</caption>
  <tr>
    <th scope="col"><span id="program">Program</span></th>
    <th scope="col"><span id="now">Now</span></th>
    <th scope="col"><span id="past">Past</span></th>
    <th scope="col"><span id="date">Date</span></th>
  </tr>
  <tr>
    <th scope="row"><span id="foodstamps">Food stamps</span></th>
    <td><input type="checkbox" name="checkbox"
      aria-labelledby="now foodstamps"></td> <!-- using multiple labels per input -->
    <td><input type="checkbox" name="checkbox2"
      aria-labelledby="past foodstamps"></td>
    <td><input type="text" name="textfield"
      aria-labelledby="date foodstamps"></td>
  </tr>
</table>```
        - Fieldset gives you a label for a group of input elements
            - ```html
<fieldset>
  <legend>Contact Information</legend>
  <p><label for="name6045">Name: </label><input type="text" id="name6045"></p>
  <p><label for="phone6045">Phone: </label><input type="text" id="phone6045"></p>
  <p><label for="email6045">Email: </label><input type="text" id="email6045"></p>
  <p><label for="address6045">A`dress: </label><input type="text" id="address6045"></p>
  <p><label for="city6045">City: </label><input type="text" id="city6045"></p>
  <p><label for="state6045">State: </label><input type="text" id="state6045"></p>
  <p><label for="zip6045">Zip: </label><input type="text" id="zip6045"></p>
  <div class="mode-radio">
      <fieldset>
          <legend>Preferred mode of communication:</legend>
          <p><input type="radio" name="mode" id="mode-phone6045"> 
            <label for="mode-phone6045">Phone</label><br>
          <input type="radio" name="mode" id="mode-email6045"> 
            <label for="mode-email6045">Email</label></p>
      </fieldset>
  </div>
</fieldset>```
- Grokked::
    - Talking points
        - A web site uses custom JavaScript widgets that are new in design and concept, and unfamiliar to users.
        - Some accessibility designs start out as bad ideas even before they're built
            - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2Fy2PQan-OoA.png?alt=media&token=aeaea1db-4fa2-40fe-934e-f1db2e6768a8)
            - **Adding tabindex to focusable elements to fix bad tab order:** In theory, adding tabindex to every focusable element on a page would work to fix the tab order, but even if it is done perfectly, it will do nothing to fix bad reading order. That will put the reading order and the tab order out of sync. On a practical level, if there is any JavaScript DOM manipulation that adds new focusable elements to the DOM, or removes any from the DOM, the tabindex values may need to be completely out of order again, and may need to be altered by JavaScript, which would be costly. Plus, using tabindex (of positive numbers) has a host of other problems (values of "0" and "-1" are useful, especially when working with custom JavaScript widgets).
            - **Clunky fallback interaction patterns in widgets:** A widget designed for mouse interaction (like drag-and-drop functionality) that has accessibility features, but the accessibility features are not intuitive, and have obviously been added only for accessibility compliance, and not as the result of good interaction design.
            - **Text-only explanation of widgets that aren't accessible:** A complex widget, such as a chemistry lab simulation, that was designed for fully-able-bodied users, and which would be difficult to make accessible, so they provide a text description of what you're supposed to experience or learn, without actually letting you experience the widget itself. The information is technically accessible, but the experience is not equivalent.
            - **A lesser "accessible version:"** A link on an inaccessible site to an "accessible version" that turns out to be a stripped-down text-only version with clunky, but technically accessible, features. It is inconvenient to not be able to use the main web site in the first place, and stigmatizing because the person realizes she's getting a worse design than the rest of the population.
