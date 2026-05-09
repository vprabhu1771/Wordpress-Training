`index.php`
```
<?php
$result = new WP_Query(array('post_type' => 'sliders'));

while($result->have_posts()){
    $result->the_post();

    echo get_the_title() . "<br>";
    echo get_the_content() . "<br>";
    echo get_the_post_thumbnail_url(get_the_ID()) . "<br>";
}

?>
```

`index.php`

```
<?php get_header(); ?>

<h1>Hello World</h1>

<?php
$result = new WP_Query(array(
    'post_type' => 'sliders'
));

if ($result->have_posts()) {
    while ($result->have_posts()) {
        $result->the_post();
        ?>

        <h2><?php the_title(); ?></h2>

        <div>
            <?php the_content(); ?>
        </div>

        <?php if (has_post_thumbnail()) { ?>
            <img src="<?php echo get_the_post_thumbnail_url(get_the_ID(), 'full'); ?>" alt="">
        <?php } ?>

        <hr>

        <?php
    }
    wp_reset_postdata();
} else {
    echo "No sliders found.";
}
?>

<?php get_footer(); ?>
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
