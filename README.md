# Wappalyzer core

[Wappalyzer](https://www.wappalyzer.com/) identifies technologies on websites. Wapalyzer Core allows you to analyze websites and identify technologies used. This package provides the core functionalities along with a set of predefined technologies and categories. However, you're free to use your own data or modify the provided one.

This is a community fork of the now removed wappalyzer-core project, initially developed by [@AliasIO](https://github.com/AliasIO).

## Installation

```shell
$ npm i wapalyzer-core
```

## Usage

```javascript
const { Wappalyzer, technologies, categories } = require("wapalyzer-core");

// Sets up Wappalyzer with necessary data.
function setupWappalyzer() {
  // You can use the provided technologies and categories data,
  // or provide your own data if needed.
  Wappalyzer.setTechnologies(technologies);
  Wappalyzer.setCategories(categories);
}

// Analyzes a website and prints the results.

async function analyzeWebsite() {
  try {
    const result = await Wappalyzer.analyze({
      url: "https://example.github.io/",
      meta: { generator: ["WordPress"] },
      headers: { server: ["Nginx"] },
      scriptSrc: ["jquery-3.0.0.js"],
      cookies: { awselb: [""] },
      html: '<div ng-app="">',
    });

    console.log(result);
  } catch (error) {
    console.error("Error analyzing website:", error);
  }
}

// This will run when the module is loaded
console.log("Setting up Wappalyzer...");
setupWappalyzer();
console.log("Analyzing website...");
analyzeWebsite();
```

You can view the latest technology JSON files [here](https://github.com/enthec/webappanalyzer) or [here](https://github.com/Lissy93/wapalyzer).
