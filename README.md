# Tech-Demo-Tailwindcss

## Introduction
Welcome to team Patches' tech demo! Today we will be walking you through a CSS library called Tailwind. We wanted to share this library with you before getting into the weeds with project 2 and provide a framework that will make developing your app swift and simple.

By the end of this tutorial you will have some of the basic stepping stones for working within a React/Tailwind framework, and we will provide some useful links to branch off from so you can continue your learning.

This repo serves as a skeleton react-app that you can pull down and follow the next steps to actively learn tailwind.

## Why Use a CSS Framework

* "Don't reinvent the wheel" - save time
* Keep styles and naming consistent on large/team projects
* Reusability

CSS Framework stats (https://ossinsight.io/collections/css-framework/)

### Task 1: Installing Tailwindcss
Tailwind comes with a lot of functionality and all sorts of customization that can be daunting at first, but with our help we will make these new ideas fit seamlessly with your basic foundations of css.

First you should clone this repository down however you like, but we will be providing:
```
git clone https://github.com/johnstongrant/Tech-Demo-TailwindCSS.git
```

Next, inorder to get started we can simply navigate into our react app project, and just like any other library we invoke an npm install prompt as follows:
```
npm install tailwindcss@latest
```
This will start importing all of the necessary toolkits that tailwind requires to preform its amazing styling behavior.

### Task 2: Installing Dependencies
Alongside tailwind comes two other libraries that put everything together. The first library is [HeadlessUI](https://headlessui.com/) which you can read more about but in short this provides the interactivity of tailwind components. The other library is [Heroicons](https://heroicons.com/) which will give your website a cohesive, unified look.

the npm prompt to install both can be found here:
```
npm install @headlessui/react @heroicons/react
```

### Task 3: Config and Css
This is the last step of setup before we get into using tailwind with react!

First you will want to run the 'init' command. This will create a tailwind config file where you can fine tune tailwind to fit your exact needs. For example we will be learning about mobile and desktop specific breakpoints and will be modifying the config file for readability.

here is the command:
```
npx tailwindcss init
```

In this file you will see:
```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
We want to ensure tailwind knows where to look for our css and react components, so in the 'content: []' array add the following string:
```
"./src/**/*.{js,jsx,ts,tsx}"
```
This will allow tailwind to search for all your related components and configure them to tailwind's css formats

Lastly, in your index.css file, at the top add these three lines:
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```
Done! From here on you can start using tailwind specific classes to help create your perfect app. Moving forward we will be designing a simple card that will show the flexability you have when designing for multiple screens.

## Component 1: Responsive Design


