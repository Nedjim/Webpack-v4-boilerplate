# Webpack V4

## 1 - Webpack
```
$ yarn init
```
```
$ yarn add webpack --dev
$ yarn add webpack-cli --dev
```

Créer le point d'entrée
./scr/index.js
```js
console.log('Webpack 4 configuration')
```
**NB**: 
Nous n'avons plus besoin du fichier de configuration _webpack.config.js_ pour: 
- le point d'entrée _./src/index.js_
- le point de sortie _./dist/main.js_
- les modes de développement et de production


_package.json_
```json
"scripts": {
  "dev": "webpack --mode development",
  "build": "webpack --mode production" 
}
```
- _--mode developpement_: génère le fichier ./dist/main.js non minifié pour le développement
- _--mode production_: génère le fichier ./dist/main.js minifié pour la prod

## 2 - Babel

```
$ yarn add babel-core babel-loader babel-preset-env --dev
```
- Créer le fichier _.babelrc_
```json
{
    "presets": [
        "env"
    ]
}
```
- Configuration avec le fichier _webpack.config.js_
```js
module.exports = {
    module: {
      rules: [
        {
          test: /\.js$/,
          exclude: /node_modules/,
          use: {
            loader: "babel-loader"
          }
        }
      ]
    }
  }
```
- Configuration sans le fichier _webpack.config.js_
Modifier les scripts _dev_ et _build_ du package.json
```json
"scripts": {
    "dev": "webpack --mode development --module-bind js=babel-loader",
    "build": "webpack --mode production --module-bind js=babel-loader"
  }
```
## 3 - React

```
$ yarn add react react-dom
$ yarn add babel-preset-react
```
-  Mettre à jour le fichier _.babelrc_
```json
{
    "presets": [
        "env",
        "react"
    ]
}
```

