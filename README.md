### Tools:

1. https://wave.webaim.org/
2. https://www.nvaccess.org
3. CSS less mode in browser
4. Screen Readers (Voice Over in Mac)

### Usability
- Avoid using technical language/jargon in text. Keep it as simple as possible.
- Plain language is good usability (avoid technical Jargon if possible)
- Character sets and Fonts should be chosen so that they contain all the characters that are used in the language.
- For Audio and Video, subtitles, captions or transcripts should be provided. Use case: Noisy Places, Deaf people, people with hearing loss, people who are not fluent in the language spoken in the videos.
- All foreground and background colors should have sufficient contrast, making it easier for people with low vision to read the content.
- Keyboard/Screen Reader Navigation should be possible.

### References
https://almanac.httparchive.org/en/2022/accessibility

### ADA
https://webaim.org/blog/the-ada-and-the-web-concerns-and-misconceptions/

### ARIA
https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA


 
### HTML
#### Lang attribute
```<html lang="en">```
- The lang attribute is used to specify the primary language for the document. It is important for screen readers to announce the content in the correct language. Lacking the lang attribute, screen readers will assume the language based on the user's settings. This can lead to incorrect pronunciation of words and phrases, bad translations, and other formatting issues.
- Lang attribute can be used on the html tag, or on the specific elements like p, h1, etc.

```
  <p lang="en">
    The Alchemist is a novel written by Brazilian author <span lang="es">
    Paulo Coelho</span>, originally published in Portuguese in 1988.
  </p>
```
  - Screen readers that support multiple languages adapt their pronounciation and accent based on the lang attribute. A page with German content but lang set to "en" could end up being pronounced in English accent which could result into hard to understand pronounciation (or even wrong).
  - Certain tags like `<q>` behave differently based on the lang attribute. For example, in English, quotes are represented by double quotes. In French, quotes are represented by guillemets. The lang attribute helps the browser to render the quotes correctly.
  ```html
    <p lang="en">
      <q>quotes are represented as</q>
    </p>
  <!-- Results in: “quotes are represented as” -->
  ```
  ```html
    <p lang="en">
      <q>les citations sont représentées comme</q>
    </p>
    <!-- Results in: „les citations sont représentées comme“ -->
  ```
  - Browser may select language specific fonts based on the lang attribute. 
  - SEO: lang attribute could also help search engines understand content better. 

#### Page Title
- `<title>` of page must be unique and should describe the content of the page. It is the first thing that screen readers announce when the page is loaded. It is also used by search engines to understand the content of the page.
- Additionally, opengraph meta tag can be used to include catchier title for social media previews.
```html
  <head>
    <title>Web Accessibility</title>
    <meta property="og:title" content="Web Accessibility - A Comprehensive Guide">
  </head>
```
- Screen reader users often use shortcut keys to anounce the title of the page. So, even for SPA's where the title does not change, it is important to update the title when the content changes.
- Titles becomes labels for bookmarks.
- Titles should be unique, concise and should contain relevant information first. For ex: "Website Name: Page Name" is a bad practice. "Page Name - Website Name" is a better practice.
- Titles should be less than 60 characters. This is because search engines truncate titles longer than 60 characters.
- Additional context can be provided for example if a page is part of flow, then title could include step number and step description.

#### Viewport Meta Tag & Low Vision
- Viewport is the rectangular area in which root element `<html>` is contained.
- Users with low vision often use zoom to increase the size of the content. If viewport meta tag settings don't allow zooming, then it could be difficult for users with low vision to read the content.
```html
  <meta name="viewport" content="width=device-width, initial-scale=1">
```
- Avoid using restrictive viewport settings like `user-scalable=no` or `user-scalable=0`. 
- Setting `width=device-width` ensures that the content fits the screen width. Avoid using hardcoded/fixed width settings, as it could cause overflow problems if the screen width is smaller than the fixed width.
- `maximum-scale` and `minimum-scale` can be used to limit the zooming. However, it is better to avoid using these settings. Users with low vision might need to zoom in more than the maximum-scale setting.
  - https://almanac.httparchive.org/en/2022/accessibility#zooming-and-scaling


#### Headings
- Sensible usage of heading tags to organise content. Heading h1,h2,h3.. describes structure of content to screen readers. Without hierarchy, it would take longer to navigate through the content or locate the desired information.

#### Lists
- Use lists to organize content. It helps to divide text into smaller chunks, and easier for screen readers to skip one line item to another by just reading the first few words of each item.
  - ul - unordered list, screen readers will usually announce "bullet list" or "list of items"
  - ol - ordered list, screen readers will usually announce "numbered list" or "list of items" or the number of list item.

#### Forms
- Avoid using Spans and Divs in place of interactive elements like  buttons, links, form elements. Interactive elements carry default accessibility features, which are lost when replaced with non-interactive elements.
- **Input elements** like text fields, radio buttons, checkboxes, and select menus carry default accessibility features. For example: When a radio button is focused, screen readers will announce the radio button's label and its state (checked or unchecked).
- **Labels** are important for screen readers. They provide context to the form element. When a form element is focused, screen readers will announce the label. If the label is missing, screen readers will announce the placeholder attribute value. 
- **Required fields** If an input field is required, then label should clearly indicate that the field is required. Simply putting an asterisks (*) might not be enough for screen readers.
- Label and Input should be associated using `for` attribute in label and `id` attribute in input. This helps screen readers to announce the label when input is focused. Example:
  ```html
  <label for="username">Username (required)</label>
  <input type="text" id="username" name="username">
  ```
- Certain inputs like radio buttons have very small interaction area. Pairing the input with the label increases the interaction area. It reduces the chances of selecting the wrong input. Increasing the interactive area helps people with motor disabilities, where they might have difficulty in clicking on small areas.

#### Keyboard Shortcuts
  https://www.digitaltrends.com/wp-content/uploads/2022/05/gmail-navigate-keyboard-shortcuts.jpg?fit=720%2C720&p=1

  https://twitter.com/i/keyboard_shortcuts?lang=en

#### Keyboard focus vs Visual focus
- Keyboard focus is the element that is currently selected by the keyboard. Visual focus is the element that is currently highlighted on the screen. Sometimes, these are out of sync. This can be confusing for people who rely on keyboard navigation. 

#### Focus and Hover Styles
- While using keyboard navigation, focus styles allow users to know which element is currently selected. For people with motor disabilities, it is difficult to use mouse. They rely on keyboard navigation. Focus styles are important for them.
- Its a quite common practice to remove focus styles as they do not generally match the design. This is a bad practice. Why not make the focus styles match the design or make them even more prominent?
- Hover styles giive visual feedback to users when they hover over an element. This is not available to keyboard users. Avoid using hover styles for non-interactive elements like div/span. It could be confusing for screen readers.s

#### Tab Index
- In keyboard navigation, if tabkey is used to navigate the page, then tabindex determines the order of focus. By default, tabindex is 0. It means that the element will be focused in the order it appears in the DOM. If tabindex is set to -1, then the element will not be focused by tab key. If tabindex is set to a positive number, then the element will be focused in the order of the number.
- However, if cursor keys are used to navigate the page, then tabindex is ignored.
- Because of these inconsistencies, it is better to avoid using tabindex.
- Using tabindex on non-interactive elements like div/span is a bad practice. It could be confusing for screen readers.
- Instead of using tabindex, attempt should be made toowards a properly structured HTML. This will ensure that the tab order is logical and consistent with the visual order.

#### WYSIWYG Editors
- WYSIWYG editors are used to create content. They are used to create content in a way that is visually appealing. However, they can create accessibility issues. For example, they can create nested tables, which can be difficult to navigate for screen readers. They can also create inaccessible forms. It is important to test the content created by WYSIWYG editors for accessibility.

#### Web Accessibility Initiative—Accessible Rich Internet Applications (WAI-ARIA)
- Web and Markup languages were initially designed keeping document oriented design in mind. However, since then, web apps have grown complex/desktop like / more and more component based. 
- WAI-ARIA allows thesse components and widgets to be accessible to screen readers and other assistive technologies.
- ARIA roles, states and properties can be used to make custom components accessible by describing their behavior and structure to assistive technologies.
  #### Roles
  - Most HTML elements have implicit roles (like button, link, etc). Browsers and assistive technologies understand these implicit roles. For example, an `<a>` tag has an implicit role of link which tells the browser and assistive technologies that this bit of HTML is not just text, but is an interactive element that can be clicked. 
  - However, there are some elements that do not have implicit roles. For example, a `<div>` tag. It is just a container. It does not have any implicit role. In such cases, ARIA roles can be used to give the element a role.
  - ```<div role="alert">``` This tells the browser and assistive technologies that this div is an alert. It should be announced as an alert and not just as a div.

  List of roles: https://www.w3.org/TR/wai-aria-1.1/#roles_categorization

  #### Landmarks
  - Landmarks are roles that help assistive technologies to understand the role of different sections of the page and their relationship to each other. For example, a header, a footer, a main content area, a navigation area, etc.
  - If you already using HTML5 semantic elements like `<header>`, `<footer>`, `<main>`, `<nav>`, `<aside>`, `<section>`, then you do not need to use ARIA landmarks. These elements already have implicit roles.
  
  #### States and Properties
  - ARIA states and properties give additional information about the widgets/components to assistive technologies. For example: aria-expanded, aria-checked, aria-disabled, aria-hidden, aria-invalid, aria-pressed, aria-selected, aria-label, aria-labelledby, aria-describedby, etc.
    - aria-describedby can tell the screen reader to read the content of the element with the id mentioned in the aria-describedby attribute and consider it as description of the element.
  
  #### Live Regions
  - ARIA live regions are used to announce dynamic content changes to screen readers. For example, a chat application where new messages are added dynamically. ARIA live regions can be used to announce the new messages to screen readers.
    - aria-live="polite" - The screen reader will announce the change gracefully (without people to lose focus on their current activity). For example: when user is idle/stops typing.
    - aria-live="assertive" - The screen reader will announce the change immediately.
    - aria-live="off" - The screen reader will not announce the change.

 #### ARIA Support
  - ARIA is not supported by all screen readers. It is important to test the ARIA roles, states and properties with different screen readers.
  - ARIA won't fix bad HTML. It is not a substitute for good structure. Inherent HTML semantics far outweigh the use of ARIA. ARIA should be used in conjunction with good HTML structure. 