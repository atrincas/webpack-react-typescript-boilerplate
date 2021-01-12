# webpack-react-typescript-boilerplate

## Steps

### 1.

```bash
mkdir app-name
```

### 2.

```bash
npm init -y
```

### 3.

```bash
yarn add react react-dom
```

### 4.

```bash
yarn add -D typescript @types/react @types/react-dom
```

### 5.

```bash
yarn add -D webpack webpack-cli webpack-dev-server ts-loader html-webpack-plugin
```

### 6.

```bash
tsc --init
```

### 7.

tsoncfig.js

```javascript
{
  "compilerOptions": {
    "target": "es5" /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017','ES2018' or 'ESNEXT'. */,
    "module": "commonjs" /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'. */,
    "lib": ["es6", "dom"] /* Specify library files to be included in the compilation. */,
    "jsx": "react" /* Specify JSX code generation: 'preserve', 'react-native', or 'react'. */,
    "sourceMap": true /* Generates corresponding '.map' file. */,
    "outDir": "./dist/" /* Redirect output structure to the directory. */,
    "removeComments": true /* Do not emit comments to output. */,
    "strict": true /* Enable all strict type-checking options. */,
    "allowSyntheticDefaultImports": true /* Allow default imports from modules with no default export. This does not affect code emit, just typechecking. */,
    "esModuleInterop": true /* Enables emit interoperability between CommonJS and ES Modules via creation of namespace objects for all imports. Implies 'allowSyntheticDefaultImports'. */
  },
  "include": ["./src/**/*"]
}
```

### 8.

webpack.config.js

```javascript
const path = require('path')
const HtmlWebPackPlugin = require('html-webpack-plugin')

module.exports = {
  entry: {
    app: ['./src/index.tsx'],
    vendor: ['react', 'react-dom']
  },
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'js/[name].bundle.js'
  },
  devtool: 'source-map',
  resolve: {
    extensions: ['.ts', '.tsx', '.js', '.jsx']
  },
  module: {
    rules: [
      {
        // all files with a `.ts` or `.tsx` extension will be handled by `ts-loader`
        test: /\.tsx?$/,
        loader: 'ts-loader'
      }
    ]
  },

  plugins: [
    new HtmlWebPackPlugin({
      template: './src/index.html'
    })
  ]
}
```

### 9.

src/App.tsx

```javascript
import React from 'react'

function App() {
  return <div>App Component</div>
}

export default App
```

### 10.

src/index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React App</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

### 11.

index.tsx

```javascript
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

ReactDOM.render(<App />, document.getElementById('root'))
```

### 12.

package.json

```json
 "scripts": {
    "dev": "webpack serve --mode development --port 3000",
    "build": "webpack --mode production"
  }
```
