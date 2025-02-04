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

Tailwind comes with a lot of functionality and all sorts of customization that can be daunting at first, but with our help we will make these new ideas fit seamlessly with your basic foundations of css.

First you should clone this repository down however you like, but we will be providing:

```bash
git clone https://github.com/johnstongrant/Tech-Demo-TailwindCSS.git
```

Next, inorder to get started we can simply navigate into our react app project, and just like any other library we invoke an npm install prompt as follows:

```bash
npm install tailwindcss@latest
```

This will start importing all of the necessary toolkits that tailwind requires to preform its amazing styling behavior.

### Task 2: Installing Dependencies

Alongside tailwind comes two other libraries that put everything together. The first library is [HeadlessUI](https://headlessui.com/) which you can read more about but in short this provides the interactivity of tailwind components. The other library is [Heroicons](https://heroicons.com/) which will give your website a cohesive, unified look.

the npm prompt to install both can be found here:

```bash
npm install @headlessui/react @heroicons/react
```

### Task 3: Config and Css

This is the last step of setup before we get into using tailwind with react!

First you will want to run the 'init' command. This will create a tailwind config file where you can fine tune tailwind to fit your exact needs. For example we will be learning about mobile and desktop specific breakpoints and will be modifying the config file for readability.

here is the command:

```bash
npx tailwindcss init
```

In this file you will see:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

We want to ensure tailwind knows where to look for our css and react components, so in the 'content: []' array add the following string:

```js
"./src/**/*.{js,jsx,ts,tsx}";
```

This will allow tailwind to search for all your related components and configure them to tailwind's css formats

Lastly, in your index.css file, at the top add these three lines:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Done! From here on you can start using tailwind specific classes to help create your perfect app. Moving forward we will be designing a simple card that will show the flexability you have when designing for multiple screens.

## Component 1: Responsive Design

Designing for mobile first is becoming more and more demanding and as we start project 2 we must all be aware of developing a web based application that looks good on our phones.

Whats incredible about Tailwind is that it follows this mobile first design, making it so every utility class is fit for mobile. However, when we want to display on a desktop we can utilize _breakpoints_ to override the utility class to fit our larger screens.

Below is the breakpoints we can apply to _any_ utility class

| Breakpoint | Minimum Width | CSS                                  |
| ---------- | ------------- | ------------------------------------ |
| `sm`       | 640px         | `@media (min-width: 640px) { ... }`  |
| `md`       | 768px         | `@media (min-width: 768px) { ... }`  |
| `lg`       | 1024px        | `@media (min-width: 1024px) { ... }` |
| `xl`       | 1280px        | `@media (min-width: 1280px) { ... }` |
| `2xl`      | 1536px        | `@media (min-width: 1536px) { ... }` |

Lets do a very simple walkthrough by utlizing these breakpoints to see how they work. Copy the following code snippet and paste it into your App.js return call:

```
<p class="text-blue-600 md:text-red-600">Testing this with text</p>
```

When you refresh your app you should see the sample text in the color red. This is because we've set our breakpoint to `md` meaning on screens 768px or bigger the text will remain red. However, if you increase the zoom of your screen (or utilize developer tools to display mobile view) you will see the text change to blue.

In conclusion unspecified utility classes like `text-blue-600` will be applied to all screen sizes, where as applying a breakpoint prefix like `md` will apply to screens that size and _larger_ .

## Component 2: Using Tailwind Components

In addition to using pre-defined Tailwind classes, we could use Tailwind components as well. A list of components could be found at this link (https://tailwindui.com/components).

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
