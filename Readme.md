# Abdlmu'tii Portfolio Translation

Thank you for your interest in translating my portfolio! I welcome contributions in any language, including dialects. Here's how you can celebrate and contribute:

1. Fork this repository.
2. Create a new branch for your translation work.
3. Create a file includes your language using the [templete.json](templete.json) as a templete..
4. Test your translation to make sure it is accurate and reads well.
5. Commit your changes and push them to your forked repository.
6. Create a pull request to merge your changes into the main repository.
7. Celebrate your contribution to making my portfolio accessible to more people around the globe! 🥳

Thank you for taking the time to contribute to my portfolio translation. Your translation work is greatly appreciated!

## List of contributors:
[@Abdlmu'tii](https://github.com/abdlmitii) - amde english language fallbacks and templete example.
<br>
**More soon...**
<br>
# Creating your own multi-language website
> If you want to collaborate with translating my portfolio. You can ignore this section. that's an tutorial about how to create your own.

Are you interested in creating a website that can be viewed in multiple languages? This tutorial will guide you through the process of setting up a translations repository on GitHub and implementing translation functionality into your website.

## Step 1: Create a GitHub Account and Repository

If you don't already have a GitHub account ( which i suspect, how are you seeing this? ), head over to https://github.com/signup to create one. Once you have an account, create a new repository called "translations" or a name of your choice. This repository will contain all your translations JSON files.

## Step 2: Create JSON Files for Each Language

For each language you want to support, create a new JSON file in your translations repository. The file name should be in the format of `{LANG}.json`, where `{LANG}` is the ISO code of the language. For example, if you want to support Arabic, the file name should be `ar.json`.

In each JSON file, create key-value pairs for each translated string you want to use on your website. For example:
```json
{
"welcome": "مرحبا",
"contact": "تواصل",
"about": "من انا"
}
```


## Step 3: Implement Translation Functionality in Your Website

In your HTML, add the attribute `tr` to any element you want to translate, and set its value to the key of the translated string. For example:
```html
<h1 tr="welcome">Welcome to our website!</h1> <!-- "Welcome to our website!" is the fallback text. In case something didn't work or the user didn't have another language.. -->
<p tr="about">About us</p> <!-- "About us" is the fallback text. In case something didn't work or the user didn't have another language.. -->
<a href="/contact" tr="contact">Contact us</a> <!-- "Contact us" is the fallback text. In case something didn't work or the user didn't have another language.. -->
```

In your JavaScript, define a variable translations to hold your translated strings and specify the `repo` and `username` variables to match your translations repository and GitHub username. Then, define a function `loadTranslation` to fetch the JSON file for the desired language and parse its content. Define a function `translateElement` to update the text content of an element with its translated string. Finally, define a function `translatePage` to load the translation for the current language and apply the translation to all elements with the `tr` attribute:
```js
let translations = {};
let repo = "translations"; // your translations repository.
let username = "your-github-username"; // your GitHub username.

function loadTranslation(language, callback) {
  fetch(`https://api.github.com/repos/${username}/${repo}/contents/${language}.json`)
    .then(response => response.json())
    .then(data => {
      let translation = JSON.parse(atob(data.content));
      callback(translation);
    });
}

function translateElement(element, translation) {
  let key = element.getAttribute('tr');
  if (translation.hasOwnProperty(key)) {
    element.textContent = translation[key];
  }
}

function translatePage(language) {
  loadTranslation(language, function(translation) {
    translations[language] = translation;
    let elements = document.querySelectorAll('[tr]');
    for (let i = 0; i < elements.length; i++) {
      translateElement(elements[i], translation);
    }
  });
}

if(navigator.language || navigator.userLanguage) translatePage(navigator.language || navigator.userLanguage);
```

## Step 4: Test and Celebrate!
Test your website by changing the language in your browser settings or using a browser extension to switch languages. If everything works as expected, you now have a website that can be viewed in multiple languages! Celebrate your accomplishment and enjoy reaching a wider audience..


## Credits
By the way. Would be awesome if i got an credit in your next website using this. **You are not required to give creadits**
but would be polite to do.
