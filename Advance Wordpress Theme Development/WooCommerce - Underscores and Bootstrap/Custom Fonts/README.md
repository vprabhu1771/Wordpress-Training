`functions.php`

```php
/**
 * Custom Fonts
 */
function enqueue_custom_fonts(){
	if(!is_admin()) {
		wp_register_style('source_sans_pro', 'https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap');
		wp_register_style('nunito', 'https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');
		wp_enqueue_style('source_sans_pro');
		wp_enqueue_style('nunito');
	}
}

add_action('wp_enqueue_scripts', 'enqueue_custom_fonts');
```
