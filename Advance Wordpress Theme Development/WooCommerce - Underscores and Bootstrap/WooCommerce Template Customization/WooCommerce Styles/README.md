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

	return $enqueue_styles;
}
add_filter('woocommerce_enqueue_styles', 'remove_woocommerce_styles');

/**
 * Enqueue your own stylesheet
 */
function wp_enqueue_woocommerce_style() {
	wp_register_style('mytheme-woocommerce', get_template_directory_uri() . '/css/woocommerce/woocommerce.css');

	if( class_exists('woocommerce') ) {
		wp_enqueue_style('mytheme-woocommerce');
	}
}

add_action('wp_enqueue_scripts', 'wp_enqueue_woocommerce_style');
```
