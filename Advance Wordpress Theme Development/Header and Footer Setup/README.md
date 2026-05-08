Then your theme is being treated as a **block theme**, so you need:

```text
templates/index.html
```

—not `templates/index.php`.

Your structure should look like:

```text
your-theme/
├── style.css
├── theme.json
├── templates/
│   └── index.html
└── parts/
    ├── header.html
    └── footer.html
```

Create `templates/index.html` with something like:

```html
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- wp:group {"layout":{"type":"constrained"}} -->
<div class="wp-block-group">

    <!-- wp:post-title /-->

    <!-- wp:post-content /-->

</div>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

Also make sure your `style.css` contains a valid theme header:

```css
/*
Theme Name: My Theme
Version: 1.0
*/
```

And keep `theme.json` in the root.

`templates/index.php` is not used in block themes, which is why WordPress says the template is missing.
