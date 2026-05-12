`wp-content\themes\your_theme\footer.php`

```
<?php
/**
 * The template for displaying the footer
 *
 * Contains the closing of the #content div and all content after.
 *
 * @link https://developer.wordpress.org/themes/basics/template-files/#template-partials
 *
 * @package CUSTOM
 */

?>

	<footer id="colophon" class="site-footer">
		
		<div class="bg-primary text-white pt-5 pb-5">

			<div class="container">

				<div class="row">

					<!-- aangadi -->
					<div class="col-2">
						<?php dynamic_sidebar('footer-widget-col-one'); ?>
					</div>

					<!-- About -->
					<div class="col-2">
						<?php dynamic_sidebar('footer-widget-col-two'); ?>
					</div>

					<!-- My Account -->
					<div class="col-md-4 ms-auto">
						<?php dynamic_sidebar('footer-widget-col-three'); ?>
					</div>

				</div>

			</div>

		</div>

		<div class="container pt-2 pb-2">

			<div class="row d-flex align-items-center">

				<div class="col">					
					<p>Copyright &copy; <?php echo date('Y'); ?> <?php bloginfo('name'); ?>. All Rights Reserved.</p>					
				</div>

				<div class="col h-25 d-inline-block text-end">
					<img src="<?php echo get_template_directory_uri(); ?>/img/payment.png" class="img-fluid" loading="lazy" alt="...">
				</div>

			</div>

		</div>

	</footer><!-- #colophon -->
</div><!-- #page -->

<?php wp_footer(); ?>

</body>
</html>

```

`wp-content\themes\your_theme\functions.php`

```
/**
 * Footer Widget One
 */
function custom_footer_widget_one() {
	$args = array(
		'id'			=> 'footer-widget-col-one',
		'name'			=>	__('Footer Column One', 'text_domain'),
		'description' 	=>	__('Column One', 'text_domain'),
		'before_title'	=> '<h3 class="title">',
		'after_title'	=> '</h3>',
		'before_widget'	=> '<div id="%1$s" class="widget %2$s">',
		'after_widget'	=> '</div>',
	);
	register_sidebar($args);
}

add_action('widgets_init', 'custom_footer_widget_one');

/**
 * Footer Widget Two
 */
function custom_footer_widget_two() {
	$args = array(
		'id'			=> 'footer-widget-col-two',
		'name'			=>	__('Footer Column Two', 'text_domain'),
		'description' 	=>	__('Column Two', 'text_domain'),
		'before_title'	=> '<h3 class="title">',
		'after_title'	=> '</h3>',
		'before_widget'	=> '<div id="%1$s" class="widget %2$s">',
		'after_widget'	=> '</div>',
	);
	register_sidebar($args);
}

add_action('widgets_init', 'custom_footer_widget_two');

/**
 * Footer Widget Three
 */
function custom_footer_widget_three() {
	$args = array(
		'id'			=> 'footer-widget-col-three',
		'name'			=>	__('Footer Column Three', 'text_domain'),
		'description' 	=>	__('Column Three', 'text_domain'),
		'before_title'	=> '<h3 class="title">',
		'after_title'	=> '</h3>',
		'before_widget'	=> '<div id="%1$s" class="widget %2$s">',
		'after_widget'	=> '</div>',
	);
	register_sidebar($args);
}

add_action('widgets_init', 'custom_footer_widget_three');
```
