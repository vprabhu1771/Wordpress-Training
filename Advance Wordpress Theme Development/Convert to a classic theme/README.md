That error happens because a **block theme** expects:

* `templates/index.html` → for Full Site Editing (block themes)

and not `templates/index.php`.

`templates/index.php` is ignored in block themes.

You have two possible fixes:

### Option 1 — Convert to a classic theme

Use:

* `index.php` in the theme root
* `style.css` with theme header

Structure:

```text
your-theme/
 ├── style.css
 ├── index.php
 └── functions.php
```

Example `style.css`:

```css
/*
Theme Name: My Theme
Version: 1.0
*/
```

Example `index.php`:

```php
<?php get_header(); ?>

<h1>Hello World</h1>

<?php get_footer(); ?>
```

Remove:

```text
templates/
theme.json
```

if you do not want a block theme.

---

### Option 2 — Keep it as a block theme

Then you must create:

```text
templates/index.html
```

Example:

```html
<!-- wp:template-part {"slug":"header"} /-->

<!-- wp:group -->
<div class="wp-block-group">
    <!-- wp:post-content /-->
</div>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer"} /-->
```

You should also have:

```text
theme.json
```

and usually:

```text
parts/header.html
parts/footer.html
```

---

Important distinction:

| Theme Type    | Required Main Template |
| ------------- | ---------------------- |
| Classic theme | `index.php`            |
| Block theme   | `templates/index.html` |

If you already have `theme.json`, WordPress treats your theme as a block theme, so it requires `templates/index.html`.
