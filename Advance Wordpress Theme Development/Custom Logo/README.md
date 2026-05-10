```
Appearance > Customize > Site Identity.
```

```
<?php 
    if (has_custom_logo()) {
      the_custom_logo();
    } else {
      echo "No logo set";
    }
?>
```

```
<header id="masthead" class="site-header">

    <div class="container pt-2 pb-2">

        <div class="row align-items-center">

            <div class="col site-header__logo">					
                <?php 
                    if (has_custom_logo()) {
                        the_custom_logo();
                    } else {
                        echo "No logo set";
                    }
                ?>
								
            </div>

            <!-- Search -->
            <div class="col-md-5">					
                <?php aws_get_search_form( true ); ?>
            </div>

            <!-- Cart -->
            <div class="col cart d-flex justify-content-end align-items-center">
                <a href="<?php echo wc_get_cart_url(); ?>">
                    <i class="bi bi-bag-dash p-2"></i>
                </a>

                <a class="cart-customlocation" href="<?php echo wc_get_cart_url(); ?>" title="<?php _e( 'View your shopping cart' ); ?>"><?php echo sprintf ( _n( '%d item', '%d items', WC()->cart->get_cart_contents_count() ), WC()->cart->get_cart_contents_count() ); ?> – <?php echo WC()->cart->get_cart_total(); ?></a>
            </div>

        </div>

    </div>
</header>
```
