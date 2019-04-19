# Working with JS

Embed a partial in an asset:

```
// assets/js/app.js
git
{{ partial "dashboard.js" | safeJS }}
```


```
// after </body>

// 1. Create the resource object
{{ $dashboardjs := resources.Get "js/dashboard.js" }}
// 2. Use executeAsTemplate so that the partial file is executed properly
//    Minify to compress the asset, then fingerprint for cachebusting
{{ $dashboard := $dashboardjs | resources.ExecuteAsTemplate "dashboard.js" . | resources.Minify | resources.Fingerprint }}

// 3. Reference the new resource with .Permalink, then use integrety to add cachebusting.
<script type="text/javascript" src="{{ $dashboard.Permalink }}" integrity="{{ $dashboard.Data.Integrity }}"></script>
```

## Combine Files

```
{{ $vendor := resources.Get "js/vendor/jquery.min.js" }}
{{ $customjs := resources.Get "js/main.js" }}

{{ $scripts := slice $vendor $customjs | resources.Concat "app.js" | minify | fingerprint }}
```