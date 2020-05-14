# generate-json-webpack-plugin
Webpack plugin to generate a JSON file

## Getting Started
To begin, you'll need to install `generate-json-webpack-plugin`:

```sh
$ npm install generate-json-webpack-plugin --save-dev
```

Then add the plugin to your webpack config. For example:

`webpack.config.js`

```js
const GenerateJsonPlugin = require('generate-json-webpack-plugin');

module.exports = {
  plugins: [new GenerateJsonPlugin({
      filename: 'manifest.json',
      value: {
        short_name: 'Weather',
        name: 'Weather: Do I need an umbrella?',
        description: 'Weather forecast information',
        icons: [
            {
                src: "/images/icons-192.png",
                type: "image/png",
                sizes: "192x192"
            },
            {
                src: "/images/icons-512.png",
                type: "image/png",
                sizes: "512x512"
            }
        ],
        start_url: "/?source=pwa",
        background_color: "#3367D6",
        display: "standalone",
        scope: "/",
        theme_color: "#3367D6"
      }
  })],
};
```

That will generate a file that looks like this:

`manifest.json`

```json
{
  "short_name": "Weather",
  "name": "Weather: Do I need an umbrella?",
  "description": "Weather forecast information",
  "icons": [
    {
      "src": "/images/icons-192.png",
      "type": "image/png",
      "sizes": "192x192"
    },
    {
      "src": "/images/icons-512.png",
      "type": "image/png",
      "sizes": "512x512"
    }
  ],
  "start_url": "/?source=pwa",
  "background_color": "#3367D6",
  "display": "standalone",
  "scope": "/",
  "theme_color": "#3367D6"
}
```
### Options

| Name     | Type   | Default       | Description                                                             |
| -------- | ------ | ------------- | ----------------                                                        |
| filename | string | manifest.json | Output file name                                                        |
| source   | string | \[Optional\]  | ath to an existing JSON file to extend                                  |
| value    | object | {}            | Object to output or the properties you wish to modify                   |
| space    | number | \[Optional\]  | Insert white space into the output JSON string for readability purposes |
