`functions.php`
```
/**
 * Enqueue scripts and styles.
 */
function aangadi_scripts() {
	wp_enqueue_style( 'aangadi-style', get_stylesheet_uri(), array(), _S_VERSION );

	#
	wp_enqueue_style('custom-main', get_template_directory_uri() . "/css/main.min.css");
	wp_enqueue_style('bootstrap-icons', "https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.min.css");
	wp_enqueue_style('ionicons-icons', "https://code.ionicframework.com/ionicons/2.0.1/css/ionicons.min.css");
	#

	wp_style_add_data( 'aangadi-style', 'rtl', 'replace' );

	wp_enqueue_script( 'aangadi-navigation', get_template_directory_uri() . '/js/navigation.js', array(), _S_VERSION, true );

	#
	wp_enqueue_script( 'bootstrap-proper', "https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" , array('jquery'));
	wp_enqueue_script( 'bootstrap-script', "https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.min.js" , array('jquery'));
	wp_enqueue_script( 'custom-script', get_template_directory_uri() . "/js/script.js" , array('jquery'), '1.0.0', true);
	#

	if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
		wp_enqueue_script( 'comment-reply' );
	}
}
add_action( 'wp_enqueue_scripts', 'aangadi_scripts' );
```
