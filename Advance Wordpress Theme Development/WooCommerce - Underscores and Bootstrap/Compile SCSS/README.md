```
https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass
```

# Compile SCSS
```
Click Watch
```


`css\main.scss`

```scss
// Custom.scss
// Option A: Include all of Bootstrap

// Include any default variable overrides here (though functions won’t be available)

@import "./bootstrap/scss/bootstrap";
 
// Then add additional custom code here

```

Live Sass Compiler -> Extension Settings -> Live SASS Compile > settings:formats -> Edit in settings.json

```
"liveSassCompile.settings.formats": [
        
        {
            "format": "expanded",
            "extensionName": ".css",
            "savePath": null,
            "savePathReplacementPairs": null
        }
    ]
```

# Change To

```
"liveSassCompile.settings.formats": [
        
        {
            "format": "expanded",
            "extensionName": ".css",
            "savePath": null,
            "savePathReplacementPairs": null
        },
        {
            "format": "compressed",
            "extensionName": ".min.css",
            "savePath": null
        }
    ]
```

`functions.php`

```
function custom_scripts() {
	wp_enqueue_style( 'custom-style', get_stylesheet_uri(), array(), _S_VERSION );

	#
	wp_enqueue_style('custom-main', get_template_directory_uri() . "/css/main.css");
	#

	wp_style_add_data( 'custom-style', 'rtl', 'replace' );

	wp_enqueue_script( 'custom-navigation', get_template_directory_uri() . '/js/navigation.js', array(), _S_VERSION, true );

	if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
		wp_enqueue_script( 'comment-reply' );
	}
}
add_action( 'wp_enqueue_scripts', 'custom_scripts' );
```

```
function custom_scripts() {
	wp_enqueue_style( 'custom-style', get_stylesheet_uri(), array(), _S_VERSION );

	#
	wp_enqueue_style('custom-main', get_template_directory_uri() . "/css/main.min.css");
	#

	wp_style_add_data( 'custom-style', 'rtl', 'replace' );

	wp_enqueue_script( 'custom-navigation', get_template_directory_uri() . '/js/navigation.js', array(), _S_VERSION, true );

	if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
		wp_enqueue_script( 'comment-reply' );
	}
}
add_action( 'wp_enqueue_scripts', 'custom_scripts' );
```
