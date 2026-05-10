`wp-content\themes\custom\front-page.php`

```
<?php
/**
 * The template for displaying all pages
 *
 * This is the template that displays all pages by default.
 * Please note that this is the WordPress construct of pages
 * and that other 'pages' on your WordPress site may use a
 * different template.
 *
 * @link https://developer.wordpress.org/themes/basics/template-hierarchy/
 *
 * @package CUSTOM
 */

get_header();
?>

	<main id="primary" class="site-main">
		
		<div id="carouselExampleDark" class="carousel carousel-dark slide">
			<div class="carousel-indicators">
				<button type="button" data-bs-target="#carouselExampleDark" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
				<button type="button" data-bs-target="#carouselExampleDark" data-bs-slide-to="1" aria-label="Slide 2"></button>
				<button type="button" data-bs-target="#carouselExampleDark" data-bs-slide-to="2" aria-label="Slide 3"></button>
			</div>
			<div class="carousel-inner">
				<div class="carousel-item active" data-bs-interval="10000">
				<img src="https://bootstrapstudio.io/assets/img/og.jpg" class="d-block w-100" alt="...">
				<div class="carousel-caption d-none d-md-block">
					<h5>First slide label</h5>
					<p>Some representative placeholder content for the first slide.</p>
				</div>
				</div>
				<div class="carousel-item" data-bs-interval="2000">
				<img src="https://bootstrapstudio.io/assets/img/og.jpg" class="d-block w-100" alt="...">
				<div class="carousel-caption d-none d-md-block">
					<h5>Second slide label</h5>
					<p>Some representative placeholder content for the second slide.</p>
				</div>
				</div>
				<div class="carousel-item">
				<img src="https://bootstrapstudio.io/assets/img/og.jpg" class="d-block w-100" alt="...">
				<div class="carousel-caption d-none d-md-block">
					<h5>Third slide label</h5>
					<p>Some representative placeholder content for the third slide.</p>
				</div>
				</div>
			</div>
			<button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleDark" data-bs-slide="prev">
				<span class="carousel-control-prev-icon" aria-hidden="true"></span>
				<span class="visually-hidden">Previous</span>
			</button>
			<button class="carousel-control-next" type="button" data-bs-target="#carouselExampleDark" data-bs-slide="next">
				<span class="carousel-control-next-icon" aria-hidden="true"></span>
				<span class="visually-hidden">Next</span>
			</button>
		</div>

	</main><!-- #main -->

<?php
get_footer();
```

`wp-content\themes\custom\js\script.js`
```
const myCarouselElement = document.querySelector('#carouselExampleDark')

const carousel = new bootstrap.Carousel(myCarouselElement, {
  interval: 500,
  touch: false
})
```
