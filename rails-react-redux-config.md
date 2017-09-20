# Project Setup Checklist
Here's a Rails/React/Redux setup checklist. It should only serve as a reminder.
Ask a TA if you don't understand _why_ you're configuring something on this
list.

* [ ] `rails new`
  * Add `--database=postgresql` if using Postgres.
  * Add `--skip-turbolinks` to skip the turbolinks gem.
* [ ] Update your `Gemfile`.
  * `better_errors`
  * `binding_of_caller`
  * `pry-rails`
  * `annotate`
  * `faker`
  * `factory_girl`
* [ ] `bundle install`
* [ ] `git init`
  * Update your `.gitignore`.
    * `node_modules/`
    * `bundle.js`
    * `bundle.js.map`
* [ ] `git remote add` the proper remote.
  * `git push -u` the remote.
* [ ] `npm init --yes` to create a package.json file with the default setup.
* [ ] Create a frontend folder at the root of your project with an entry file inside of it.
* [ ] `npm install --save`
  * `webpack`
  * `react`
  * `react-dom`
  * `react-router-dom`
  * `redux`
  * `react-redux`
  * `babel-core`
  * `babel-loader`
  * `babel-preset-react`
  * `babel-preset-es2015`
  * `babel-plugin-transform-object-rest-spread`

(or use alias `npmi`)

* [ ] Create a `webpack.config.js` file.
  * The entry point should be in frontend, e.g. `entry: 'frontend/entry.jsx'`.
  * The output path should be `'app/assets/javascripts'`.
  * Configure your `module.loaders` to use Babel transpilation for:
    * JSX
    * ES6
  * Include `devtool: 'source-map'`.

  ```js
  // webpack.config.js
  var path = require('path');

  module.exports = {
    entry: "./frontend/my_app.jsx",
    output: {
        path: path.resolve(__dirname, 'app', 'assets', 'javascripts'),
        filename: "bundle.js"
    },
    module: {
      loaders: [
        {
          test: [/\.jsx?$/],
          exclude: /(node_modules)/,
          loader: 'babel-loader',
          query: {
            presets: ['es2015', 'react']
          }
        }
      ]
    },
    devtool: 'source-map',
    resolve: {
      extensions: ['.js', '.jsx', '*']
    }
  };
  ```

* [ ] add a webpack script to `webpack.json`.

* [ ] add a `.babelrc` file.

  ```js
  {
    "plugins": ["transform-object-rest-spread"]
  }
  ```

* [ ] `git commit` again (Verify that your `.gitignore` works).
  * `git push` your skeleton.
