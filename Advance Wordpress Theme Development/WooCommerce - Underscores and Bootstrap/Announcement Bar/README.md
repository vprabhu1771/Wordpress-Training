`custom\css\main.scss`

```
// main.scss
$primary: rgb(129, 24, 129);
$gray: #E6E6E6;

$theme-colors: (
    "primary": $primary,
    "gray": $gray
);

// Create your own map
$custom-color: (
    "icon-background": rgba(127, 24, 127, 0.2)
);

// Merge maps
$theme-colors: map-merge($theme-colors, $custom-color);

@import "./bootstrap/scss/bootstrap";
 
// Add custom code after this

// Header
.announcement-bar {
    font-size: 0.8rem;
    border-bottom: 1px solid var(--bs-gray);
    &__list {
        padding: 0;
        margin: 0;
        list-style-type:none;
        display: inline-flex;
        margin: 0 -10px;

        li {
            margin:0 10px;
            display: flex;
            align-items: center;

            .bi {
                background-color: var(--bs-icon-background);
                display: inline-flex;
                justify-content: center;
                align-items: center;
                width: 30px;
                height: 30px;
                margin-right: 6px;
            }
        }
    }

    @include media-breakpoint-down(lg) {
        display: none;
    }
}
```

`custom\header.php`

```
<div class="announcement-bar pt-2 pb-2">
		<div class="container">
			<div class="row">
				<div class="col-md-4 col-sm-12">
					
				<ul class="announcement-bar__list">
					<li>
						<i class="bi bi-telephone rounded-circle"></i>
						<a href="tel: +91 9944177142">+91 9944177142</a>
					</li>
					<li>
						<i class="bi bi-envelope rounded-circle"></i>
						<a href="mailto:hello@gmail.com">hello@gmail.com</a>
					</li>
				</ul>

				</div>
				<div class="col-md-8 d-flex justify-content-end">
					<ul class="announcement-bar__list">
						<li>
							<i class="bi bi-truck rounded-circle"></i>FREE EU SHIPPING							
						</li>
						<li>
							<i class="bi bi-clock-history rounded-circle"></i>30 Days Moneyback
						</li>
						<li>
							<i class="bi bi-person rounded-circle"></i>24/7 Customer Support
						</li>
					</ul>
				</div>
			</div>
		</div>
	</div>
```
