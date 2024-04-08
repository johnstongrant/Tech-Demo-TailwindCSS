# Tech Demo of Tailwind CSS

![Tailwindcss logo](/tailwind/public/tailwindcss-logotype-white.svg)

## Introduction

Welcome to team Patches' tech demo! Today we will be walking you through a CSS library called Tailwind. We wanted to share this library with you before getting into the weeds with project 2 to provide a framework that will make developing your app front-end swift and simple.

By the end of this tutorial, you will have some of the basic stepping stones for working within a React/Tailwind framework. We will also provide some useful links for you to dive deeper into Tailwind CSS if you choose.

This repo serves as a skeleton react-app that you can pull down to follow the next steps and actively learn Tailwind.

## Why Use a CSS Framework

Frameworks like Tailwind provide ready-to-use CSS classes that allow you to easily implement your web app's layout and style common components without having to reinvent the wheel. This not only saves time, but also promotes reusability. Dev teams often use CSS frameworks to avoid duplication of CSS styles, maintain consistent user interfaces, and provide a common style naming schema that makes large-scale development more navigable. Open source frameworks such as Tailwind also come with the benefit of having established documentation and a large user base which can be helpful when troubleshooting and searching for inspiration.

While there are [many CSS frameworks](https://github.com/troxler/awesome-css-frameworks) to choose from, each with their own benefits, Tailwind has [soared in popularity](https://ossinsight.io/collections/css-framework/) over the last several years.

## Utility Classes

Tailwind is a utility class based CSS framework. Utility classes give you the flexibility to build custom components and fine-tune your layout without having to write additional CSS. Here's an example of a utility class in Tailwind:

```html
<div class="rounded-md ring-orange-400">
  <span>Text</span>
</div>
```

While the same effect could be accomplished by inlining the styles using the [HTML style attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/style), utility classes provide the benefit of coming directly from a CSS stylesheet, which allows us to access the entire CSS toolbox and use CSS [preprocessors](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor), among [many other benefits](https://frontstuff.io/no-utility-classes-arent-the-same-as-inline-styles).

### Task 1: Installing Tailwind

_please note that all credit and attribution for setup process belongs to [Tailwind CSS](https://v2.tailwindcss.com/docs/guides/create-react-app)._

Tailwind comes with a lot of functionality and all sorts of customization that can be daunting at first, but with our help we will make these new ideas fit seamlessly with your basic foundations of CSS.

First, if you want to learn Tailwind using this repo, you should clone this repository:

```bash
git clone https://github.com/johnstongrant/Tech-Demo-TailwindCSS.git
```

Once you have a React project, navigate into the React app project and install Tailwind using npm:

```bash
cd <react app root directory>
npm install -D tailwindcss
```

This will import all of the packages and dependencies for us to start using Tailwind in our project.

### Task 2: Configuration

Next we will create a config file specifically for Tailwind, so Tailwind can properly integrate with our React app, and so we can configure Tailwind beyond the default configuration if needed. The config file can be created automatically by running:

```bash
npx tailwindcss init
```

Once this command has been run, it will create a file called `tailwind.config.js` in your project's root directory. In this file, you will see the following default contents:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

We want to ensure Tailwind knows where to look for our templates and react components. We need to change the contents of the `tailwind.config.js` file in order for Tailwind to know this:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

I know a lot of this feels like magic, and it kind of is in a sense. Just know that these configurations are essential for Tailwind to know where to look to style our website.

This will allow Tailwind to search for all your related components, configure the components to use Tailwind's CSS formatting, and get rid of uneccessary component styling when we host our website.

#### Themes

Tailwind makes customization easy. While many CSS frameworks' default themes are customizable, often through the use of [CSS preprocessors](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor), Tailwind makes customization a focus and provides customization directly in the `tailwind.config.js` file.

Within your config file's "theme" section, you can set the colors, fonts, spacing variables, and even breakpoints used by Tailwind. As an example, let's set some default colors, add a font, and change the border radius used by Tailwind:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    colors: {
      'yellow': '#ffcc99',
      'gray': '#333333',
    },
    fontFamily: {
      sans: ['Bungee Spice', 'sans-serif'],
      serif: ['Merriweather', 'serif'],
    },
    extend: {},
  },
  plugins: [],
}
```

Without writing a single line of CSS, we can use Tailwind's config settings and utility classes to quickly change to look and feel of a web app. Using the above config, we can quickly build out a distinct design (_note: this example requires the import of the "Bugnee Spice" and "Merriweather" fonts from Google fonts_):

```js
import './App.css';

function App() {
  return (
    <div className="App bg-gray min-h-screen text-center pt-10">
      <header className="App-header">
        <h1 className="font-sans text-6xl">With Tailwind CSS</h1>
        <p className="font-serif text-2xl text-yellow">This didn't even require writing CSS - just Tailwind config and Google fonts.</p>
      </header>
    </div>
  );
}

export default App;
```

![Before Tailwind config](/demo-resources/config-before.png)
![After Tailwind config](/demo-resources/config-after.png)

For in-depth documentation of custom theming in Tailwind, see Tailwind's [official documentation](https://tailwindcss.com/docs/theme).

#### Configuration Wrap-Up

Finally, in your index.css file, add these three lines to the top of the file:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

You should also check in your `index.js` file and ensure you see `import './index.css'` somewhere at the top of the file. Without this line, styles from `index.css` won't be applied!

Whew. We know that was a lot of setup and some of it can seem confusing. However we are all done! Now we can start discussing why all this setup is worth doing.

## Component 1: Tailwind Utility Classes and States in Action

Tailwind can be used to create interactions with elements by applying states using utility classes, as discussed previously, and modifiers - which will be discussed in the responsive design section. Take for example this line of code:

```html
<button class="bg-blue-400 rounded-full p-3"> A Cool Button </button>
```

![A cool button](/demo-resources/button.png)

We can apply a hover state within the class definition to define behavior for when the user hovers their cursor over the button. Let's have it so the button gets darker when we hover over it by modifying the line of code to following:

```html
<button class="bg-blue-400 hover:bg-blue-700 rounded-full p-3"> A Cool Button </button>
```

![A cool button with hover state](/demo-resources/hover.gif)

By adding an active state and focus state, we can have the button become even darker when clicked and give it a red ring when it's right clicked like so:

```html
<button class="bg-blue-400 hover:bg-blue-700 active:bg-blue-800 focus:ring focus:ring-red-400 rounded-full p-3"> A Cool Button </button>
```

![A cool button with focus and active states](/demo-resources/focus.gif)

Using states, we can easily add conditionality to our element's appearance with using these pseudo-class modifiers. A list of available pseudo-class modifiers to use can be found within the [Tailwind CSS docs](https://tailwindcss.com/docs/hover-focus-and-other-states#pseudo-class-reference).

## Component 2: Using Tailwind's Out-of-the-Box Examples

Homework 1 and Project 1 utilized PureCss, which came with a lot of pre-defined templates for us to work with. Tailwind also provides some sample templates for us to utilize and the list of them can be found in [Tailwind's component documentation](https://tailwindui.com/components).

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Please note: If you intend on using Tailwind's predefined templates you will need to import the following dependencies with this command:**

```bash
npm install @heroicons/react @headlessui/react
```

This is due to most of Tailwind's templates utilizing heroicon imports and headless ui functionality to get responsive behavior. By all means delete their imports and calls, but this is here to remove headaches with your implementations using Tailwind.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

For now, we will demonstrate using a Tailwind Avatar component. This is the code for Avatar component from the abovementioned Tailwind website:

```jsx
<div className="flex-space-x-1 overflow-hidden">
  <img
    className="inline-block h-32 w-32 rounded-full ring-2 ring-white"
    src={
      "https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
    }
    alt=""
  ></img>
</div>
```

![Avatar of a happy Tailwind CSS user](/demo-resources/avatar.png)

The HTML version of this avatar works perfectly fine as standalone HTML, but let's add some reusability by converting this avatar into a reusable React component.

First, you will want the component to be wrapped in a React component and export it:

```js
export function Avatar() {
  return (
    <>
      //the avatar component
    <>
  )
}
```

Next, we want this component to have some props rather than use static values. For now, we will replace the source of the image as a prop. Remember that you can also replace other properties as prop such as the className.

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

Mobile-first design is becoming more and more in demand, and as we build project 2 we must all be aware of developing a web based application that looks good not only on desktops, but also on mobile devices.

Tailwind, like many other modern CSS libraries, focuses on a 'mobile-first' approach to styling. This makes it so all [utility](https://v2.tailwindcss.com/docs/utility-first) classes are fit for mobile right out of the gate. However, when we want to display our information in a different way on different sized screens we can utilize _breakpoints_ to override the utility classes to fit our larger screens.

Below are the breakpoints we can apply to _any_ utility class

| Breakpoint | Minimum Width | CSS                                  |
| ---------- | ------------- | ------------------------------------ |
| `sm`       | 640px         | `@media (min-width: 640px) { ... }`  |
| `md`       | 768px         | `@media (min-width: 768px) { ... }`  |
| `lg`       | 1024px        | `@media (min-width: 1024px) { ... }` |
| `xl`       | 1280px        | `@media (min-width: 1280px) { ... }` |
| `2xl`      | 1536px        | `@media (min-width: 1536px) { ... }` |

Let's do a very simple walkthrough of breakpoints to see how they work. Copy the following code snippet and paste it into your `App.js` return call:

```html
<p class="text-blue-600 md:text-red-600">Testing this with text</p>
```

When you refresh your app, you should see the sample text in the color red. This is because we've set our breakpoint to `md`, meaning on "medium" screens - displays 768px wide or larger - the text will remain red. However, if you increase the zoom of your screen (or utilize developer tools to display mobile view) you will see the text change to blue.

[Larger Screen](redtxt.png)
[Smaller Screen](bluetxt.png)

## Tailwind Config Customization: Dark Mode

Tailwind provides low-level utility classes to build custom designs. This feature enables us to create a dark mode theme for users who prefer an alternative color scheme. To start the dark mode implementation, we need to apply some changes to the `tailwind.config.js` file we created while setting up Tailwind. This file is found in your react project's root directory.

To add dark mode theming, add a "darkMode" key to the `tailwind.config.js` file, as shown here:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  darkMode: 'selector',
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

The configuration above will enable you and your team to use a "dark:" CSS selector in order to distinguish between classes that will be used for dark mode and those that will be used for light mode. The following is an example of how to use dark mode class assignment:

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

In this example, dark mode is not enabled, therefore `dark:bg-black` would not work. In contrast, the following is an example of correct implementation of dark mode:

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

Furthermore, Tailwind provides some strategies that enable developers to use a user's system preferences in order to change the default theme of the website by `window.matchMedia()` API. Here's a simple example of how to use operating system prefernces while defining different themes for the website. Note that it's best to add this JavaScript inline the the HTML Head element in order to avoid a ["flash of unstyled content"](https://en.wikipedia.org/wiki/Flash_of_unstyled_content):

```js
// On page load or when changing themes
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

To conclude, we've shared a lot of information about the use cases and components of Tailwind CSS. Although we only scratch the surface of what Tailwind can do for you and your web app, we wanted to give you a brief peek into several different topics that you can now delve deeper into, and see if Tailwind will work for you and your team. We hope that one of these topics will be enough to show you that Tailwind is worth using in your projects, and can make designing your app something to look forward to!
