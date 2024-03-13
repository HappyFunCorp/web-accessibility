## Web Accessibility
## Table of Contents
- [Introduction](#introduction)
- [Why Web Accessibility](#why-web-accessibility)
- [Types of Disabilities](#types-of-disabilities)
- [Tools](#tools)
- [Usability](#usability)
- [References](#references)
- [ADA](#ada)
- [ARIA](#aria)
- [HTML](#html)
  - [Lang attribute](#lang-attribute)
  - [Page Title](#page-title)
  - [Viewport Meta Tag & Low Vision](#viewport-meta-tag--low-vision)
  - [Headings](#headings)
  - [Lists](#lists)
  - [Forms](#forms)
  - [Keyboard Shortcuts](#keyboard-shortcuts)
  - [Keyboard focus vs Visual focus](#keyboard-focus-vs-visual-focus)
  - [Focus and Hover Styles](#focus-and-hover-styles)
  - [Tab Index](#tab-index)
  - [WYSIWYG Editors](#wysiwyg-editors)
  - [Web Accessibility Initiative—Accessible Rich Internet Applications (WAI-ARIA)](#web-accessibility-initiativeaccessible-rich-internet-applications-wai-aria)
    - [Roles](#roles)
    - [States and Properties](#states-and-properties)
    - [Live Regions](#live-regions)
    - [ARIA Support](#aria-support)
    - [Landmarks](#landmarks)
      - [Main Navigation Landmark Example:](#main-navigation-landmark-example)
      - [Breadcrumb Navigation Example:](#breadcrumb-navigation-example)
      - [Local Navigation Example:](#local-navigation-example)
      - [Label landmarks](#label-landmarks)

### Introduction [^](#table-of-contents)
Web Accessibility is the practice of ensuring that people with disabilities can perceive, understand, navigate, and interact with the web. It is about making the web accessible to everyone, regardless of their abilities. It is about making the web inclusive.


### Why Web Accessibility [^](#table-of-contents)
- Legal Requirement: In many countries, it is a legal requirement to make the web accessible. For example, in the United States, the Americans with Disabilities Act (ADA) requires that public and private organizations make their websites accessible to people with disabilities.
- Ethical Requirement: It is the right thing to do. The web is a public space. It should be accessible to everyone.
- Business Requirement: Making the web accessible can increase the audience for the website. It can also improve the search engine ranking of the website. It can also improve the user experience of the website. For example, making the web accessible can improve the user experience for people with low vision, people with motor disabilities, and people with cognitive disabilities.

### Types of Disabilities [^](#table-of-contents)
- Visual Impairment: People with low vision, people with color blindness, people with total blindness.
- Hearing Impairment: People with hearing loss, people who are deaf.
- Motor Disabilities: People with limited mobility, people with tremors, people with paralysis.
- Cognitive Disabilities: People with learning disabilities, people with memory loss, people with attention deficit disorder.
- Speech Disabilities: People with speech impairments, people who are mute.
- Seizure Disorders: People with epilepsy, people with photosensitive epilepsy.
- Aging: People with age related disabilities, people with age related impairments.


### Tools: [^](#table-of-contents)

1. https://wave.webaim.org/
2. https://www.nvaccess.org
3. CSS less mode in browser
4. Screen Readers (Voice Over in Mac)
5. ct.css is a little diagnostic snippet, named after Computed Tomography (CT) scans, that exposes potential performance issues in your page’s <head> tags, and will disappear as soon as you’ve fixed them. https://csswizardry.com/ct/

### Usability [^](#table-of-contents)
- Avoid using technical language/jargon in text. Keep it as simple as possible.
- Plain language is good usability (avoid technical Jargon if possible)
- Character sets and Fonts should be chosen so that they contain all the characters that are used in the language.
- For Audio and Video, subtitles, captions or transcripts should be provided. Use case: Noisy Places, Deaf people, people with hearing loss, people who are not fluent in the language spoken in the videos.
- All foreground and background colors should have sufficient contrast, making it easier for people with low vision to read the content.
- Keyboard/Screen Reader Navigation should be possible.

### References [^](#table-of-contents)
https://almanac.httparchive.org/en/2022/accessibility

### ADA [^](#table-of-contents)
https://webaim.org/blog/the-ada-and-the-web-concerns-and-misconceptions/

### ARIA [^](#table-of-contents)
https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA


 
### HTML [^](#table-of-contents)
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

#### Page Title [^](#table-of-contents)
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

#### Viewport Meta Tag & Low Vision [^](#table-of-contents)
- Viewport is the rectangular area in which root element `<html>` is contained.
- Users with low vision often use zoom to increase the size of the content. If viewport meta tag settings don't allow zooming, then it could be difficult for users with low vision to read the content.
```html
  <meta name="viewport" content="width=device-width, initial-scale=1">
```
- Avoid using restrictive viewport settings like `user-scalable=no` or `user-scalable=0`. 
- Setting `width=device-width` ensures that the content fits the screen width. Avoid using hardcoded/fixed width settings, as it could cause overflow problems if the screen width is smaller than the fixed width.
- `maximum-scale` and `minimum-scale` can be used to limit the zooming. However, it is better to avoid using these settings. Users with low vision might need to zoom in more than the maximum-scale setting.
  - https://almanac.httparchive.org/en/2022/accessibility#zooming-and-scaling


#### Headings [^](#table-of-contents)
- Sensible usage of heading tags to organise content. Heading h1,h2,h3.. describes structure of content to screen readers. Without hierarchy, it would take longer to navigate through the content or locate the desired information.

#### Lists [^](#table-of-contents)
- Use lists to organize content. It helps to divide text into smaller chunks, and easier for screen readers to skip one line item to another by just reading the first few words of each item.
  - ul - unordered list, screen readers will usually announce "bullet list" or "list of items"
  - ol - ordered list, screen readers will usually announce "numbered list" or "list of items" or the number of list item.

#### Forms [^](#table-of-contents)
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
- Important forms on page should be promoted as landmarks. This helps screen reader users to jump to the form directly. Examples: 
- Login form:
  ```html
  <form role=form"" aria-label="Login">
    <label for="username">Username (required)</label>
    <input type="text" id="username" name="username">
    <label for="password">Password (required)</label>
    <input type="password" id="password" name="password">
    <button type="submit">Login</button>
  </form>
  ```
- Search form:
  ```html
  <form role="search" aria-label="Search">
    <label for="search">Search</label>
    <input type="text" id="search" name="search">
    <button type="submit">Search</button>
  </form>
  ```
  OR
  ```html
  <search role="search">
    <form>
      <label for="search">Search</label>
      <input type="text" id="search" name="search">
      <button type="submit">Search</button>
    </form>
  </search>
  ```


#### Keyboard Shortcuts [^](#table-of-contents)
  https://www.digitaltrends.com/wp-content/uploads/2022/05/gmail-navigate-keyboard-shortcuts.jpg?fit=720%2C720&p=1

  https://twitter.com/i/keyboard_shortcuts?lang=en

#### Keyboard focus vs Visual focus [^](#table-of-contents)
- Keyboard focus is the element that is currently selected by the keyboard. Visual focus is the element that is currently highlighted on the screen. Sometimes, these are out of sync. This can be confusing for people who rely on keyboard navigation. 

#### Focus and Hover Styles [^](#table-of-contents)
- While using keyboard navigation, focus styles allow users to know which element is currently selected. For people with motor disabilities, it is difficult to use mouse. They rely on keyboard navigation. Focus styles are important for them.
- Its a quite common practice to remove focus styles as they do not generally match the design. This is a bad practice. Why not make the focus styles match the design or make them even more prominent?
- Hover styles giive visual feedback to users when they hover over an element. This is not available to keyboard users. Avoid using hover styles for non-interactive elements like div/span. It could be confusing for screen readers.s

#### Tab Index [^](#table-of-contents)
- In keyboard navigation, if tabkey is used to navigate the page, then tabindex determines the order of focus. By default, tabindex is 0. It means that the element will be focused in the order it appears in the DOM. If tabindex is set to -1, then the element will not be focused by tab key. If tabindex is set to a positive number, then the element will be focused in the order of the number.
- However, if cursor keys are used to navigate the page, then tabindex is ignored.
- Because of these inconsistencies, it is better to avoid using tabindex.
- Using tabindex on non-interactive elements like div/span is a bad practice. It could be confusing for screen readers.
- Instead of using tabindex, attempt should be made toowards a properly structured HTML. This will ensure that the tab order is logical and consistent with the visual order.

#### WYSIWYG Editors [^](#table-of-contents)
- WYSIWYG editors are used to create content. They are used to create content in a way that is visually appealing. However, they can create accessibility issues. For example, they can create nested tables, which can be difficult to navigate for screen readers. They can also create inaccessible forms. It is important to test the content created by WYSIWYG editors for accessibility.

#### Web Accessibility Initiative—Accessible Rich Internet Applications (WAI-ARIA) [^](#table-of-contents)
- Web and Markup languages were initially designed keeping document oriented design in mind. However, since then, web apps have grown complex/desktop like / more and more component based. 
- WAI-ARIA allows thesse components and widgets to be accessible to screen readers and other assistive technologies.
- ARIA roles, states and properties can be used to make custom components accessible by describing their behavior and structure to assistive technologies.
  #### Roles [^](#table-of-contents)
  - Most HTML elements have implicit roles (like button, link, etc). Browsers and assistive technologies understand these implicit roles. For example, an `<a>` tag has an implicit role of link which tells the browser and assistive technologies that this bit of HTML is not just text, but is an interactive element that can be clicked. 
  - However, there are some elements that do not have implicit roles. For example, a `<div>` tag. It is just a container. It does not have any implicit role. In such cases, ARIA roles can be used to give the element a role.
  - ```<div role="alert">``` This tells the browser and assistive technologies that this div is an alert. It should be announced as an alert and not just as a div.

  List of roles: https://www.w3.org/TR/wai-aria-1.1/#roles_categorization

  #### States and Properties [^](#table-of-contents)
  - ARIA states and properties give additional information about the widgets/components to assistive technologies. For example: aria-expanded, aria-checked, aria-disabled, aria-hidden, aria-invalid, aria-pressed, aria-selected, aria-label, aria-labelledby, aria-describedby, etc.
    - aria-describedby can tell the screen reader to read the content of the element with the id mentioned in the aria-describedby attribute and consider it as description of the element.
  
  #### Live Regions [^](#table-of-contents)
  - ARIA live regions are used to announce dynamic content changes to screen readers. For example, a chat application where new messages are added dynamically. ARIA live regions can be used to announce the new messages to screen readers.
    - aria-live="polite" - The screen reader will announce the change gracefully (without people to lose focus on their current activity). For example: when user is idle/stops typing.
    - aria-live="assertive" - The screen reader will announce the change immediately.
    - aria-live="off" - The screen reader will not announce the change.

 #### ARIA Support [^](#table-of-contents)
  - ARIA is not supported by all screen readers. It is important to test the ARIA roles, states and properties with different screen readers.
  - ARIA won't fix bad HTML. It is not a substitute for good structure. Inherent HTML semantics far outweigh the use of ARIA. ARIA should be used in conjunction with good HTML structure. 

  #### Landmarks [^](#table-of-contents)
  - Landmarks are roles that help assistive technologies to understand the role of different sections of the page and their relationship to each other. For example, a header, a footer, a main content area, a navigation area, etc.
  - Landmarks help with high level semantics of page and group common sitewide and page specific elements. It helps screen readers to understand the structure of the page.
  - Screen reader may announce landmark when user enters or leaves it. Every item of page should live inside a landmark so that it can be discovered by user.
  - Users can jump from landmark to landmark using keyboard shortcuts or gestures and skip to specific areas without interacting with rest of the page. 

    | Screen Reader            | Command          |
    |--------------------------|------------------|
    | NVDA                     | D                |
    | JAWS                     | R                |
    | Narrator                 | D                |
    | VoiceOver on iOS         | Rotor            |
    | TalkBack on Android      | Reading Controls |

  - Landmarks can be explicitly defined using `role` attribute. For example: `<div role="main">`, `<div role="navigation">`, `<div role="search">`, `<div role="complementary">`, `<div role="contentinfo">`, etc.
  - Some implicit landmarks are: `<header>`, `<footer>`, `<nav>`, `<main>`, `<aside>`, `<section>`, `<article>`, etc.

    ##### HTML Landmarks and their ARIA roles [^](#table-of-contents)
    | Element | ARIA Role     | Conditions                                                             |
    |---------|---------------|------------------------------------------------------------------------|
    | header  | banner        | Only in the context of the body element; not when a descendant of `<article>, <aside>, <main>, <nav>, or <section>`.  |
    | nav     | navigation    |                                                                        |
    | main    | main          |                                                                        |
    | section | region        | When it has an accessible name using `aria-labelledby, aria-label, or title`. |
    | form    | form          | When it has an accessible name using `aria-labelledby, aria-label, or title`. |
    | form    | search        | With `role="search"`                                                    |
    | search  | search        |                                                                        |
    | aside   | complementary |                                                                        |
    | footer  | contentinfo   | Only in the context of the body element; not when a descendant of `<article>, <aside>, <main>, <nav>, or <section>`.  |


  - `banner` - Typically the top of the page, containing the site's branding, logo, and primary navigation. Multiple `<header>` elements (if nested) can be used in a page, but only one should have the `banner` role.
  - `main` - The main content of the page. Multiple `<main>` elements can be used in a page, but only one should be visible at a time. Main represents core content of the page.
  - `contentinfo` - Footer typically contains secondary navigation, copyright info etc. Multiple nested footers are fine in a page, but there must be only one `contentinfo` role.
  
  #### Main Navigation Landmark Example: [^](#table-of-contents)
  ```html
    <header>
      <nav aria-label="Main">
        <ul>
          <li><a href="/home">Home</a></li>
          <li><a href="/products" aria-current="page">Products</a></li>
          <li><a href="/team">Team</a></li>
          <li><a href="/contact">Contact</a></li>
        </ul>
      </nav>
    </header>
  ```
  #### Breadcrumb Navigation Example: [^](#table-of-contents)
  ```html
    <nav aria-label="Breadcrumb">
      <ol>
        <li><a href="/products/">Products</a></li>
        <li><a href="/products/kitchen/">Kitchen & appliances</a></li>
        <li><a href="/products/kitchen/" aria-current="page">Kitchen worktops</a></li>
      </ol>
    </nav>
  ```
  #### Local Navigation Example: [^](#table-of-contents)
  ```html
    <nav aria-label="Contents">
      <ol>
        <li><a href="#company">Company</a></li>
        <li><a href="#licensing">Licensing</a></li>
        <li><a href="#seealso">See Also</a></li>
        <li><a href="#References">References</a></li>
        <li><a href="#externallinks">External links</a></li>
      </ol>
    </nav>
  ```
  #### Label landmarks [^](#table-of-contents)
  - TODO -


### Performance [^](#table-of-contents)
- Slow websites are inaccessible.
- HTML is parsed linearly. If something blocks rendering early in the document, then subsequent content is delayed.
- All low priority scripts that can be loaded at the end of body tag should be loaded at the end of body tag and moved out of the head tag. i.e anything that does not belong to head section should be moved oust.
- Use your own CDN to host assets instead of relying on third party CDNs. Drawbacks of using third party CDNs:
  -  https://csswizardry.com/2019/05/self-host-your-static-assets/ 
  - SlowDown/Outages: If third party CDN is slow or down, then it will slow down your website as well. If they discontinue the service, then it will break your website.
  - Security Vulnerabilities: If third party CDN or source of CDN is compromised, then it will compromise your website as well.
  - Penalty of Network negotiation:  One of the biggest and most immediate penalties we pay is the cost of opening new TCP connections. Every new origin we need to visit needs a connection opening, and that can be very costly: DNS resolution, TCP handshakes, and TLS negotiation all add up, and the story gets worse the higher the latency of the connection is.
  - Penalty of Loss of priortisation: The second penalty comes in the form of a protocol-level optimisation that we miss out on the moment we split content across domains. If you’re running over HTTP/2—which, by now, you should be—you get access to prioritisation. All streams (ergo, resources) within the same TCP connection carry a priority, and the browser and server work in tandem to build a dependency tree of all of these prioritised streams so that we can return critical assets sooner, and perhaps delay the delivery of less important ones.


- If using your own CDN is not an option then, following mitigations can be used:
  - Preconnect: It tells the browser to start the connection to the server before the request is made. This can reduce the time it takes to make the request.
  - SRI: Subresource Integrity. It is a security feature that allows you to ensure that the files you include in your page are not tampered with. It is especially useful for third party scripts.


  #### Ideal Order of elements in `<head>` tag [^](#table-of-contents)
  - Metadata about page goes first
  - Anything that blocks rendering should goo after `<title>`
  - CSS blocks the execution of subsequent script, so any synchronous javascript should come before CSS
  - Avoid using @import in CSS. It blocks the rendering of the page. Instead, use link tag to include CSS.
  - SEO tags, icons, open graphs, social meta tags, etc. should go at the end.
  ```html
  <head>
    <!-- Character encoding -->
    <meta charset="UTF-8">
    <!-- Viewport meta tag -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- CSP headers -->
    <meta http-equiv="Content-Security-Policy" content="upgrage-insecure-requests">
    <!-- Page title -->
    <title>Maya Toys</title>
    <!-- preconnect -->
    <link rel="preconnect" href="#" />
    <!-- Asynchronous JavaScript -->
    <script src="" async></script>
    <!-- CSS that includes @import -->
    <style>
      @import "file.css";
    </style>
    <!-- Synchronous JavaScript -->
    <script src=""></script>
    <!-- Synchronous CSS -->
    <link rel="stylesheet" href="#">
    <!-- preload -->
    <link rel="preload" href="#" />
    <!-- Deferred JavaScript -->
    <script src="" defer></script>
    <!-- prefetch / prerender -->
    <link rel="prefetch" href="#" />
    <link rel="prerender" href="#" />
    <!-- Everything else (meta tags, icons, open graphs, etc.) -->
    <meta name="description" content="">
  </head>
  ```