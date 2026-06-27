```
https://codex.wordpress.org/Navigation_Menus
```

```
Login -> Appearance -> Menus -> Menu structure -> Menu Settings
```

`functions.php`

```php
function register_my_menus() {
  register_nav_menus(
    array(
      'header-menu' => __( 'Header Menu' ),
      'extra-menu' => __( 'Extra Menu' )
    )
  );
}
add_action( 'init', 'register_my_menus' );
```
