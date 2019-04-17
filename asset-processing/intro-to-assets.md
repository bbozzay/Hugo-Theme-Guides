# Intro to resources and assets
If you need to resize an image programatically, bundle JS/CSS files, or use SASS/SCSS, you need to create a resource. Resources can be global or page-level. Assets are files that are added by the user and later turned into resources. 

## Global resources and assets
To create a global resource, create a folder called "assets" in either your root directory or your theme directory:

```
// In root
assets/

// In your theme directory
themes/YOURTHEME/assets
```

Hugo will prioritize the assets folder in your root directory first, then your theme directory.

You'll probably use a few different types of global resources, such as images, JS, and SCSS. You should create directories in your asset folder for each type.

We'll use `resources.Get PATH` to create a resource from our source asset.
`.Permalink` is used to reference that newly generated path.

### When to use global assets
It's best to use global assets when the same resource needs to be referenced on many different pages. For example, we might need to generate a favcon from a larger source image. The same favcon will be used on every generated page on our website, so this should be a global resource.

## Page resources
Page resources are assets that are relative to a specific page. In order to use page resources, we need to create a folder for our page (instead of just a markdown file).

Your content directory might look like this:
```
_index.md
about.md
services.md
```

If we want to add image page resources for our services page, we need to create a directory in place of services.md. We'll move services.md into our new directory (we'll name it services still), then our markdown file to index.md, and we'll create an images folder.

Now our content directory looks like this:
```
_index.md
about.md
services
  |----- images
  |----- index.md
```

We'll use `{{ .Resources.Match PATTERN }}` to return a list of resources. We'll iterate over those resources using `range`, then reference each resource using `.Permalink`. 

### When to use page resources
Page resources should be used when an asset is used only on one specific page. For example, an image for a blog post.