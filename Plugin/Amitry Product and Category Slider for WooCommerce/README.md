```
https://wordpress.org/plugins/amitry-product-category-slider/
```

### Implementation Approach

Replace your existing code:

```php
<?php echo do_shortcode('[product_categories columns="4"]'); ?>
```

With the shortcode from a slider plugin, for example using Amitry:

```php
<?php echo do_shortcode('[amitry_slider type="categories" sort="count"]'); ?>
```

Or if you're using Elementor, simply drag the corresponding category carousel widget into the page.

### Selection Suggestions

- **Elementor user** → Prioritize **Arboleda Category List** or **Amitry** (both have dedicated widgets)
- **Gutenberg user** → **CatCraft** or **Amitry** (native block support)
- **Want to display all categories + product counts** → **Dynamic Product Category Grid** or **Amitry**
