`index.php`

```
<?php
$result = new WP_Query(array('post_type' => 'sliders'));
while($result->have_posts()){
    $result->the_post();

    echo get_the_title() . "<br>";
}

?>
```

`functions.php`

```php
<?php

function slider_custom_post_type() {
    register_post_type( 'sliders', array(
        'labels' => array(
            'name' => __( 'Sliders' ),
            'singular_name' => __( 'Slider' )
        ),
        'public' => true,
        'has_archive' => true,
        'rewrite' => array('slug' => 'sliders'),
        'show_in_rest' => true,
        'supports' => array(
            'title',
            'editor',
            'author',
            'thumbnail',
            'comments',
            'revisions',
            'custom-fields'
        ),
        'taxonomies' => array('category'),
    ));
}
add_action( 'init', 'slider_custom_post_type' );

?>
```
