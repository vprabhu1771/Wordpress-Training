`wp-content\themes\custom\css\main.scss`

```
// Main Menu
.main-navigation {
    font-weight: 600;

    .current-menu-item {
        background-color: rgb(149, 33, 149) 
    }

    a {
        color: var(--bs-white);
        padding: 1rem 1.4rem;
    }

    a:hover {
        background-color: rgb(149, 33, 149);
    }

    .menu-toggle {
        background-color: $primary;
        color: var(--bs-white);
        border: none;
    }
}
```

`wp-content\themes\custom\header.php`
```
<header>
  <nav id="site-navigation" class="main-navigation bg-primary">

			<div class="container d-flex justify-content-center">

				<div class="row">

					<div class="col-12 d-flex justify-content-center">
						<button class="menu-toggle" aria-controls="primary-menu" aria-expanded="false">
						<i class="bi bi-list"></i>	
						<?php esc_html_e( 'Primary Menu', 'custom' ); ?>
						</button>
					</div>

					<div class="col-12 text-center">
						<?php
							wp_nav_menu(
								array(
									'theme_location' => 'menu-1',
									'menu_id'        => 'primary-menu',
								)
							);
						?>
					</div>
				</div>

				
			</div>
			
			
		</nav><!-- #site-navigation -->
</header><!-- #masthead -->
```
