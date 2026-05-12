`wp-content\themes\your_theme\woocommerce.php`

```
<?php get_header(); ?>

<main class="container pt-5">

    <?php woocommerce_content(); ?>

</main>

<?php get_footer(); ?>
```

`wp-content\themes\your_theme\functions.php`
```
/**
 * WooCommerce
 */

add_theme_support('woocommerce');
```
