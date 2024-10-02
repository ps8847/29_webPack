Webpack is a powerful and popular module bundler used primarily in modern JavaScript applications. Its main role is to bundle JavaScript files (and other assets such as stylesheets, images, and fonts) into a single file or smaller chunks for optimization, improving load times and performance. By converting files into formats that browsers can understand, Webpack helps developers manage dependencies and module interconnections more efficiently.

Key Features of Webpack:
Module Bundling: Webpack bundles multiple files (JavaScript, CSS, images) into a single or multiple output files.
Code Splitting: This allows splitting the code into chunks, which are loaded on demand. It optimizes performance by reducing the initial load time.
Loaders: Webpack can transform files like JavaScript (with Babel), CSS (Sass/SCSS), and images (PNG, JPG) using loaders before bundling them.
Plugins: Webpack uses plugins to extend its functionality. Examples include HTMLWebpackPlugin (for HTML files) and TerserWebpackPlugin (for minifying JavaScript).
Development and Production Modes: It offers different optimizations depending on whether you are in development (more features for debugging) or production mode (optimized for performance).
Basic Webpack Example:
In this example, we will set up Webpack to bundle a JavaScript file and include an image.

1. Project Structure:

bash
Copy code
/project
  /src
    index.js
    styles.css
    logo.png
  /dist
    index.html
  webpack.config.js
  package.json


2. Installing Webpack and Dependencies:
bash
Copy code
npm init -y
npm install webpack webpack-cli --save-dev
npm install css-loader style-loader file-loader --save-dev


3. Webpack Configuration (webpack.config.js):
js
Copy code
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.(png|jpg|gif)$/,
        use: ['file-loader'],
      },
    ],
  },
};


4. JavaScript File (src/index.js):
js
Copy code
import './styles.css';
import logo from './logo.png';

function addImage() {
  const img = document.createElement('img');
  img.src = logo;
  document.body.appendChild(img);
}

addImage();


5. CSS File (src/styles.css):
css
Copy code
body {
  background-color: #f0f0f0;
}


6. HTML File (dist/index.html):
html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Webpack Example</title>
</head>
<body>
  <script src="bundle.js"></script>
</body>
</html>


7. Running Webpack:
bash
Copy code
npx webpack --mode development