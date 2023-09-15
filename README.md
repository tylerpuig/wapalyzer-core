# Wappalyzer core

[Wappalyzer](https://www.wappalyzer.com/) identifies technologies on websites.

This is a community fork of the now removed wappalyzer-core project, initially developed by [@AliasIO](https://github.com/AliasIO).

## Installation

```shell
$ npm i wapalyzer-core
```

## Usage

```javascript
const Wappalyzer = require("wapalyzer-core");

// Loading data files
const categories = require("./categories.json");
const technologies = require("./technologies.json");

/**
 * Sets up Wappalyzer with necessary data.
 */
function setupWappalyzer() {
  Wappalyzer.setTechnologies(technologies);
  Wappalyzer.setCategories(categories);
}

/**
 * Analyzes a website and prints the results.
 */
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
