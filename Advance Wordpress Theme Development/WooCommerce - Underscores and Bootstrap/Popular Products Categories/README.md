Use WooCommerce product categories shortcode instead of products shortcode.

Example:

```php id="4vbq14"
<!-- Product Categories -->
<section class="container popular-categories">

	<div class="row d-flex justify-content-center text-center">
		<h1 class="pt-5">Shop by Category</h1>
		<p class="w-25">Browse our popular product categories</p>
	</div>

	<div class="pt-5 pb-5">
		<?php echo do_shortcode('[product_categories columns="4" limit="4"]'); ?>
	</div>

</section>
```

---

Useful shortcode options:

```php id="8a0msp"
[product_categories columns="4"]
```

```php id="3wvj1t"
[product_categories parent="0"]
```

only top-level categories.

```php id="frw8n4"
[product_categories ids="12,15,18"]
```

specific categories.

```php id="6c0x74"
[product_categories hide_empty="0"]
```

show empty categories too.

---

Recommended version:

```php id="kjceah"
<?php echo do_shortcode(
	'[product_categories columns="4" parent="0" hide_empty="0"]'
); ?>
```

---

You can style category cards using:

```css id="j6k9ho"
.woocommerce ul.products li.product-category {
    text-align: center;
}

.woocommerce ul.products li.product-category img {
    border-radius: 10px;
}

.woocommerce ul.products li.product-category h2 {
    margin-top: 15px;
    font-size: 20px;
}
```

WooCommerce treats category grid similar to product grid.
