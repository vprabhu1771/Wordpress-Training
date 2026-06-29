```
https://wordpress.org/plugins/classic-editor/
```

If you want to **change from Gutenberg (Block Editor) to the Classic Editor** in WordPress, you have several options.

## Option 1: Install the Classic Editor plugin (Recommended)

1. Go to **Dashboard → Plugins → Add New**
2. Search for **Classic Editor**
3. Install and activate the plugin.
4. Go to **Settings → Writing**
5. Configure:

   * **Default editor for all users:** Classic Editor
   * **Allow users to switch editors:** No (or Yes if you want both)

This is the easiest and safest method.

---

## Option 2: Disable Gutenberg using a plugin

You can install plugins like:

* Classic Editor
* Disable Gutenberg

These automatically restore the old editor.

---

## Option 3: Disable Gutenberg using code

Add this to your theme's `functions.php` or a custom plugin:

```php
add_filter('use_block_editor_for_post', '__return_false', 10);
```

To disable Gutenberg for all post types:

```php
add_filter('use_block_editor_for_post_type', '__return_false', 10);
```

---

## Option 4: Disable only for specific Custom Post Types

For example, if you're using Elementor with ACF and want only a custom post type to use the Classic Editor:

```php
function disable_gutenberg_for_cpt($can_edit, $post_type) {

    if ($post_type === 'services') {
        return false;
    }

    return $can_edit;
}
add_filter('use_block_editor_for_post_type', 'disable_gutenberg_for_cpt', 10, 2);
```

Replace `services` with your custom post type.

---

## Which should you use?

Since you've recently been working with **Elementor + ACF**, I recommend:

* ✅ Install **Classic Editor**.
* ✅ Set it as the default editor.
* ✅ Build pages with Elementor and manage custom fields with ACF.
* ✅ Avoid mixing Gutenberg blocks with Elementor unless you specifically need block-based content.

This setup is stable, simple to maintain, and works well for ACF-driven websites.
