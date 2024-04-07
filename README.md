# Tech Demo of Tailwind CSS

![Tailwindcss logo](/tailwind/public/tailwindcss-logotype-white.svg)

## Introduction

Welcome to team Patches' tech demo! Today we will be walking you through a CSS library called Tailwind. We wanted to share this library with you before getting into the weeds with project 2 and provide a framework that will make developing your app swift and simple.

By the end of this tutorial you will have some of the basic stepping stones for working within a React/Tailwind framework, and we will provide some useful links to branch off from so you can continue your learning.

This repo serves as a skeleton react-app that you can pull down and follow the next steps to actively learn tailwind.

## Why Use a CSS Framework

Frameworks like Tailwind provide ready-to-use CSS classes that allow you to easily implement your web app's layout and style common components without having to reinvent the wheel. This not only saves time, but also promotes reusability. Dev teams often use CSS frameworks to avoid duplication of CSS styles, maintain consistent user interfaces, and provide a common style naming schema that makes large-scale development more navigable. Open source frameworks such as Tailwind also come with the benefit of having established documentation and a large userbase which can be helpful when troubleshooting and searching for inspiration.

While there are [many CSS frameworks](https://github.com/troxler/awesome-css-frameworks) to choose from, each with their own benefits, Tailwind has [soared in popularity](https://ossinsight.io/collections/css-framework/) over the last several years.

## Utility Classes

Tailwind is a utility class based CSS framework. Utility classes give you the flexibility to build custom components and fine-tune your layout without having to write additional CSS. Here's an example of a utility class in Tailwind:

```html
<div class="rounded-md ring-orange-400">
  <span>Text</span>
</div>
```

While the same effect could be accomplished by inlining the styles using the [HTML style attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/style), utility classes provide the benefit of coming directly from a CSS stylesheet. In CSS parlance, this means we're applying "rules" rather than "styles" to elements, which allows us to access the entire CSS toolbox and use CSS [preprocessors](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor), among [many other benefits](https://frontstuff.io/no-utility-classes-arent-the-same-as-inline-styles).

### Task 1: Installing Tailwindcss

_please note that all credit and attribution for setup process belongs to [tailwind](https://v2.tailwindcss.com/docs/guides/create-react-app)_

Tailwind comes with a lot of functionality and all sorts of customization that can be daunting at first, but with our help we will make these new ideas fit seamlessly with your basic foundations of css.

First you should clone this repository down however you like, but we will be providing:

```bash
git clone https://github.com/johnstongrant/Tech-Demo-TailwindCSS.git
```

Next, inorder to get started we can simply navigate into our react app project, and just like any other library we invoke an npm install prompt as follows:

```bash
npm install -D tailwindcss
```

This will start importing all of the necessary toolkits for us to start using tailwind in our project.

### Task 3: Config and Css

Next we will be creating a config file specifically for tailwind so that it can know our specified settings if we wish to change them.

```bash
npx tailwindcss init
```


In this file you will see:

```/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

We want to ensure tailwind knows where to look for our templates and react components, so in the 'content: []' array add the following string:

```js
"./src/**/*.{js,jsx,ts,tsx}"
```

I know a lot of this feels like magic, and it kind of is in a sense. Just know that these configurations are essential for tailwind to know where to look to style our website.

This will allow tailwind to search for all your related components and configure them to tailwind's css formats and get rid of unecessary component styling when we host our website.

Lastly, in your index.css file, at the top add these three lines:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

You will also want to navigate to `index.js` and ensure you see `import './index.css'` somewhere at the top of the file.

Whew. We know that was a lot of setup and some of it can seem confusing. However we are all done! Now we can start discussing why all this setup is worth doing.

## Component 1: Tailwind Utility classes and States in action

Tailwind can be used to to create interactions with elements by applying states using utility classes as discussed prior and modifiers like from the responsive design section. Take for example this line of code:

```html
<button class="bg-blue-400 rounded-full"> A Cool Button </button>
```

We can apply a hover state within the class definition to define behavior for when the user hovers their cursor over the button. Let's have it so the button gets darker when we hover over it by modifying the line of code to following:

```html
<button class="bg-blue-400 hover:bg-blue-700 rounded-full"> A Cool Button </button>
```

By adding an active state and focus state, we can have the button become even darker when clicked and give it a red ring when it's right clicked like so:

```html
<button class="bg-blue-400 hover:bg-blue-700 active:bg-blue-800 focus:ring focus:ring-red-400 rounded-full"> A Cool Button </button>
```

Using states, we can easily add conditionality to our element's appearence with using these psuedo classes modifiers. A list of available psuedo-classes modifiers to use can be found within the [Tailwind CSS docs](https://tailwindcss.com/docs/hover-focus-and-other-states#pseudo-class-reference).

## Component 2: Using Tailwind's out-of-the-box Examples

During homework and project 1 we were told to utilize PureCss which came with it a lot of pre-defined templates for us to work with. Tailwind also provides some sample templates for us to utilize and the list of them can be found in [Tailwind's component documentation](https://tailwindui.com/components).

For now, we will demonstrate using a Tailwind Avatar component. This is the code for Avatar component from the abovementioned Tailwind website:

```jsx
<div className="flex -space-x-1 overflow-hidden">
  <img
    className="inline-block h-6 w-6 rounded-full ring-2 ring-white"
    src={
      "https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
    }
    alt=""
  ></img>
</div>
```

which would work perfectly fine, but for usuability we will demonstrate converting this component into reusable React component.

Firstly, you will want the component to be wrapped in a React component and export it.

```js
export function Avatar() {
  return (
    <>
      //the avatar component
    <>
  )
}
```

Next, we want this component to have some props rather than some static values. For now, we will replace the source of the image as a prop. Remember that you can also replace other properties as prop such as the className.

```js
export function Avatar({ src, className }) {
  return (
    <>
      <div className="flex -space-x-1 overflow-hidden">
        <img
          className="inline-block h-6 w-6 rounded-full ring-2 ring-white"
          src={src}
          alt=""
        ></img>
      </div>
    </>
  );
}
```

This is it! Now you can call the new Avatar component how many times you want with appropriate props. We have just created a reusable React component with props.

```js
<Avatar src="src1"></Avatar>
<Avatar src="src2"></Avatar>
<Avatar src="..."></Avatar>
```

## Component 3: Responsive Design

Designing for mobile first is becoming more and more demanding and as we start project 2 we must all be aware of developing a web based application that looks good on our phones.

Tailwind, like many other modern css libraries, focuses on a 'mobile-first' approach to styling. This makes it so all [utility](https://v2.tailwindcss.com/docs/utility-first) classes are fit for mobile right out of the gate. However, when we want to display our information in a different way on different sized screens we can utilize _breakpoints_ to override the utility classes to fit our larger screens.

Below are the breakpoints we can apply to _any_ utility class

| Breakpoint | Minimum Width | CSS                                  |
| ---------- | ------------- | ------------------------------------ |
| `sm`       | 640px         | `@media (min-width: 640px) { ... }`  |
| `md`       | 768px         | `@media (min-width: 768px) { ... }`  |
| `lg`       | 1024px        | `@media (min-width: 1024px) { ... }` |
| `xl`       | 1280px        | `@media (min-width: 1280px) { ... }` |
| `2xl`      | 1536px        | `@media (min-width: 1536px) { ... }` |

Lets do a very simple walkthrough by utlizing these breakpoints to see how they work. Copy the following code snippet and paste it into your App.js return call:

```html
<p class="text-blue-600 md:text-red-600">Testing this with text</p>
```

When you refresh your app you should see the sample text in the color red. This is because we've set our breakpoint to `md` meaning on screens 768px or bigger the text will remain red. However, if you increase the zoom of your screen (or utilize developer tools to display mobile view) you will see the text change to blue.

## Tailwind Config customization: Dark Mode

Tailwind CSS provides low-level utility classes to build custom designs. This feature enables us to create dark mode theme for users' who prefer this theme over others. To start the dark mode implementation, we need to apply some changes to Tailwind's `configuration` file. These changes can be seen in the following:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  darkMode: 'selector',
  // ...
}
```

The configuration above will enable the developer to use "dark:" variant in order to distinguish between classes that will be used for dark mode and those of that will be used for light mode. The following is an example of how to use dark mode class assignment:

```html
<!-- Dark mode not enabled -->
<html>
<body>
  <!-- Will be white -->
  <div class="bg-white dark:bg-black">
    <!-- ... -->
  </div>
</body>
</html>
```

In this example, dark mode is not enabled, therefore `dark:bg-black` would not work. On the contrary, the following is an example of correct implementation of dark mode:

```html
<!-- Dark mode enabled -->
<html class="dark">
<body>
  <!-- Will be black -->
  <div class="bg-white dark:bg-black">
    <!-- ... -->
  </div>
</body>
</html>
```

Furthermore, Tailwind provides some strategies that enable the developers to use user's system prefernces in order to change the default theme of the website by `window.matchMedia()` API. Here's a simple example of how to use operating system prefernces while defining different themes for the website:

```js
// On page load or when changing themes, best to add inline in `head` to avoid FOUC
if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

// Whenever the user explicitly chooses light mode
localStorage.theme = 'light'

// Whenever the user explicitly chooses dark mode
localStorage.theme = 'dark'

// Whenever the user explicitly chooses to respect the OS preference
localStorage.removeItem('theme')
```

## Review and Discussion
To conclude, we've shared a lot of information to you about the use cases and inner components of tailwind CSS. Although we only scratch the surface of what tailwind can do for you and your web app, we wanted to give you several different topics that you can now delve deeper into seeing if tailwind will work for you and your team. We hope that one of these topics will be enough to show you that tailwind is worht including and can make your css lifecyle something to look forward to!
