# Working with CSS Site and Page Resources

{{ $s := resources.Get "scss/style.scss" | toCSS | postCSS | minify }}

postCSS needs to be installed first:

1. In root, run `npm install postcss-cli`
2. `npm install autoprefixer`
3. add postcss.config.js to root. [Example](https://github.com/pancakes-builder/pancakesStarter/blob/master/postcss.config.js)
4. Add package.json to root. [Example](https://github.com/pancakes-builder/pancakesStarter/blob/master/package.json)
5. Add `/node_modules` to .gitignore

Read more about [asset processing with Hugo](https://blog.fullstackdigital.com/how-to-cache-bust-and-concatenate-js-and-sass-files-with-hugo-in-2018-9266fd3c411e).