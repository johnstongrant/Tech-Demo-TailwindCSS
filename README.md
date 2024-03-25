# Tech-Demo-Tailwindcss

## Introduction
Welcome to team Patches' tech demo! Today we will be walking you through a CSS library called Tailwind. We wanted to share this library with you before getting into the weeds with project 2 and provide a framework that will make developing your app swift and simple.

By the end of this tutorial you will have some of the basic stepping stones for working within a React/Tailwind framework, and we will provide some useful links to branch off from so you can continue your learning.

This repo serves as a skeleton react-app that you can pull down and follow the next steps to actively learn tailwind.

## Why Use a CSS Framework

Frameworks like Tailwind provide ready-to-use CSS classes that allow you to easily implement your web app's layout and style common components without having to reinvent the wheel. This not only saves time, but also promotes reusability. Dev teams often use CSS frameworks to avoid duplication of CSS styles, maintain consistent user interfaces, and provide a common style naming schema that makes large-scale development more navigable. Open source frameworks such as Tailwind also come with the benefit of having established documentation and a large userbase which can be helpful when troubleshooting and searching for inspiration.

While there are [many CSS frameworks](https://github.com/troxler/awesome-css-frameworks) to choose from, each with their own benefits, Tailwind has [soared in popularity](https://ossinsight.io/collections/css-framework/) over the last several years.

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

### Task 3: Creating a Component
