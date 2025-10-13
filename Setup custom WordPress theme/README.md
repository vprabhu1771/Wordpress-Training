Here’s a **step-by-step guide** to setting up a **custom WordPress theme from scratch** — ideal for WordPress development environments.

---

## 🧩 1. Setup Your Local WordPress Environment

Before creating a theme, ensure you have a local environment.

### ✅ Option 1: Using LocalWP (Recommended for beginners)

* Download **[Local by Flywheel](https://localwp.com/)**.
* Create a new WordPress site — it sets up everything (PHP, MySQL, Apache/Nginx).

### ✅ Option 2: Using XAMPP / WAMP / MAMP / Docker

* Install **XAMPP** or similar.
* Place WordPress files inside:

  ```
  C:\xampp\htdocs\mywordpress
  ```
* Access in browser:

  ```
  http://localhost/mywordpress
  ```

---

## 🧱 2. Create Your Custom Theme Folder

Inside your WordPress project, go to:

```
wp-content/themes/
```

Create a new folder for your theme, e.g.:

```
my-custom-theme
```

---

## 🗂️ 3. Add Required Files

Every WordPress theme **must have at least** these two files:

```
my-custom-theme/
├── style.css
└── index.php
```

---

## 🧾 4. Define Your Theme in `style.css`

Create `style.css` and add this header at the top:

```css
/*
Theme Name: My Custom Theme
Theme URI: http://example.com/my-custom-theme
Author: Your Name
Author URI: http://example.com
Description: A custom theme built from scratch.
Version: 1.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: my-custom-theme
*/
```

> 💡 WordPress reads this metadata to list your theme in **Appearance → Themes**.

---

## 🧩 5. Create `index.php`

Add a simple test layout:

```php
<!DOCTYPE html>
<html <?php language_attributes(); ?>>
<head>
  <meta charset="<?php bloginfo( 'charset' ); ?>">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title><?php bloginfo( 'name' ); ?></title>
  <?php wp_head(); ?>
</head>
<body <?php body_class(); ?>>

  <header>
    <h1><?php bloginfo( 'name' ); ?></h1>
    <p><?php bloginfo( 'description' ); ?></p>
  </header>

  <main>
    <?php
      if ( have_posts() ) :
        while ( have_posts() ) : the_post();
          the_content();
        endwhile;
      else :
        echo '<p>No posts found.</p>';
      endif;
    ?>
  </main>

  <?php wp_footer(); ?>
</body>
</html>
```

---

## 🧠 6. Activate Your Theme

1. Go to **WordPress Dashboard → Appearance → Themes**
2. Find **My Custom Theme**
3. Click **Activate**

---

## ⚙️ 7. Add More Theme Files

To organize properly, add these standard files:

```
my-custom-theme/
│
├── functions.php
├── header.php
├── footer.php
├── sidebar.php
├── index.php
├── style.css
└── screenshot.png  ← (optional theme preview)
```

---

## 🧩 8. Register Styles and Scripts in `functions.php`

Example `functions.php`:

```php
<?php
function mytheme_enqueue_scripts() {
  wp_enqueue_style('mytheme-style', get_stylesheet_uri());
  wp_enqueue_script('mytheme-main', get_template_directory_uri() . '/js/main.js', [], false, true);
}
add_action('wp_enqueue_scripts', 'mytheme_enqueue_scripts');
```

Then create:

```
my-custom-theme/js/main.js
```

with:

```js
console.log("Theme JS Loaded");
```

---

## 🧱 9. Include Template Parts

In `index.php`, replace header/footer HTML with:

```php
<?php get_header(); ?>
<main>
  <!-- Content -->
</main>
<?php get_footer(); ?>
```

Create `header.php` and `footer.php` for reusable layouts.

---

## 🌈 10. Add Template Hierarchy Files (Optional but Recommended)

You can add more specialized files as your theme grows:

* `home.php` → blog posts page
* `single.php` → single post view
* `page.php` → static pages
* `archive.php` → category/tag archives
* `search.php` → search results
* `404.php` → not found page

---

## 🧰 Bonus Tips

* **Use a starter theme** like [_S (Underscores)](https://underscores.me/) if you want a clean base.
* **Enable debugging** in `wp-config.php`:

  ```php
  define( 'WP_DEBUG', true );
  ```
* **Version control**: Initialize Git inside your theme folder.
* **Child theme**: If customizing an existing theme, use a [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/).

---

Would you like me to show you a **basic folder structure with Bootstrap integrated** for a modern responsive custom theme?
