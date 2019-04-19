When using Hugo pipes for SCSS/SASS, JS etc., in some cases modifying the asset file doesn't trigger a site rebuild. In other words, if I have a file in assets/scss/style.scss and I modify a CSS value, that change isn't reflected when running `hugo server`.

In order to display the CSS change, you have to run `hugo server` again. **This is not intended behavior**. Updating asset files should rebuild the asset with the changes and trigger a reload when running `hugo server`.

## Potential fixes
1. Use the --disableFastRender flag. IE `hugo server --disableFastRender`.
2. fix an errors identified when running `hugo server -v`.

### References:
* https://discourse.gohugo.io/t/pipeline-not-re-compiling-after-changes/13889
* https://discourse.gohugo.io/t/hugo-pipes-scss-not-re-compiling-on-server-or-watch/14435