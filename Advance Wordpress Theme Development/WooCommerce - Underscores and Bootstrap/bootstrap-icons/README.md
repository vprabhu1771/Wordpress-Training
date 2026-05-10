`custom\functions.php`

```php
/**
 * Enqueue scripts and styles.
 */
function custom_scripts() {
	wp_enqueue_style( 'custom-style', get_stylesheet_uri(), array(), _S_VERSION );

	#
	wp_enqueue_style('custom-main', get_template_directory_uri() . "/css/main.min.css");
	wp_enqueue_style('bootstrap-icons', "https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.min.css");
	#

	wp_style_add_data( 'custom-style', 'rtl', 'replace' );

	wp_enqueue_script( 'custom-navigation', get_template_directory_uri() . '/js/navigation.js', array(), _S_VERSION, true );

	if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
		wp_enqueue_script( 'comment-reply' );
	}
}

add_action( 'wp_enqueue_scripts', 'custom_scripts' );
```
