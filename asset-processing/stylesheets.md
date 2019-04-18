# CSS/SCSS Resources
As of Hugo version 0.43, we can use Hugo's asset pipelines to process CSS. This means we can use SASS/SCSS, combine files into one stylesheet, cachebust our stylesheets automatically, and minify CSS without installing any additional build tools. This means we really only have to run `hugo` or `hugo server` to process these resources.

{{ $s := resources.Get "scss/style.scss" | toCSS | postCSS | minify }}

postCSS needs to be installed first:

1. In root, run `npm install postcss-cli`
2. `npm install autoprefixer`
3. add postcss.config.js to root. [Example](https://github.com/pancakes-builder/pancakesStarter/blob/master/postcss.config.js)
4. Add package.json to root. [Example](https://github.com/pancakes-builder/pancakesStarter/blob/master/package.json)
5. Add `/node_modules` to .gitignore

Read more about [asset processing with Hugo](https://blog.fullstackdigital.com/how-to-cache-bust-and-concatenate-js-and-sass-files-with-hugo-in-2018-9266fd3c411e).