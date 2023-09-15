# Wappalyzer core

[Wappalyzer](https://www.wappalyzer.com/) identifies technologies on websites.

This is a community fork of the now removed wappalyzer-core project, initially developed by [@AliasIO](https://github.com/AliasIO).

## Installation

```shell
$ npm i wapalyzer-core
```

## Usage

```javascript
#!/usr/bin/env node

const fs = require("fs");
const Wappalyzer = require("./wappalyzer");

// See https://github.com/wappalyzer/wappalyzer/blob/master/README.md#specification
const categories = JSON.parse(
  fs.readFileSync(path.resolve(`./categories.json`))
);

let technologies = {};

for (const index of Array(27).keys()) {
  const character = index ? String.fromCharCode(index + 96) : "_";

  technologies = {
    ...technologies,
    ...JSON.parse(
      fs.readFileSync(path.resolve(`./technologies/${character}.json`))
    ),
  };
}

Wappalyzer.setTechnologies(technologies);
Wappalyzer.setCategories(categories);

Wappalyzer.analyze({
  url: "https://example.github.io/",
  meta: { generator: ["WordPress"] },
  headers: { server: ["Nginx"] },
  scriptSrc: ["jquery-3.0.0.js"],
  cookies: { awselb: [""] },
  html: '<div ng-app="">',
}).then((detections) => {
  const results = Wappalyzer.resolve(detections);

  console.log(results);
});
```

You can view the latest technology JSON files [here](https://github.com/enthec/webappanalyzer) or [here](https://github.com/Lissy93/wapalyzer).
