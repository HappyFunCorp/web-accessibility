### Tools:

1. https://wave.webaim.org/
2. https://www.nvaccess.org
3. CSS less mode in browser
4. Screen Readers (Voice Over in Mac)

### Usability
- Avoid using technical language and many people don't understand it.
- Plain language is good usability (avoid technical Jargon if possible)
- Character sets and Fonts should be chosen so that they contain all the characters that are used in the language.
- For Audio and Video, subtitles, captions or transcripts should be provided. Use case: Noisy Places, Deaf people, people with hearing loss, people who are not fluent in the language spoken in the videos.
- All foreground and background colors should have sufficient contrast, making it easier for people with low vision to read the content.
- Keyboard/Screen Reader Navigation should be possible.


### ADA
https://webaim.org/blog/the-ada-and-the-web-concerns-and-misconceptions/

### ARIA
https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA


 
### HTML

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
- todo