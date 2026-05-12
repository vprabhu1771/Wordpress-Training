# WooCommerce Styles

Copy To
```
wp-content\plugins\woocommerce\assets\css
```

```
wp-content\themes\your_theme\css\woocommerce
```

`wp-content\themes\your_theme\functions.php`

```
/**
 * Remove WooCommerce Styles
 */
function remove_woocommerce_styles($enqueue_styles) {
	unset($enqueue_styles['woocommerce-general']); // Remove the gloss

	// unset($enqueue_styles['woocommerce-layout']); // Remove the layout

	// unset($enqueue_styles['woocommerce-smallscreen']); // Remove the smallscreen optimisation
}
add_filter('woocommerce_enqueue_styles', 'remove_woocommerce_styles');
```
