Here's your complete file with the **wrapped card design** implemented. I've kept your template structure and integrated the card HTML, PHP loop, and all the styling.

---

## 📄 Updated `php.txt` (Page Template)

```php
<?php
/**
 * Template Name: About Page
 */

get_header();
?>

<main id="primary" class="site-main container py-5">

    <?php
    while ( have_posts() ) :
        the_post();

        the_title('<h1 class="mb-4">', '</h1>');

        the_content();

    endwhile;
    ?>

    <!-- Product Categories -->
    <section class="container popular-categories">

        <div class="row d-flex justify-content-center text-center">
            <h1 class="pt-5">Shop by Category</h1>
            <p class="w-25">Browse our popular product categories</p>
        </div>

        <div class="pt-5 pb-5">
            <div class="container">
                <div class="row category-card-row">

                    <?php
                    // Get all product categories
                    $categories = get_terms( array(
                        'taxonomy'   => 'product_cat',
                        'hide_empty' => false, // Set true to hide empty categories
                        'orderby'    => 'name',
                        'order'      => 'ASC',
                    ) );

                    if ( ! empty( $categories ) && ! is_wp_error( $categories ) ) :
                        foreach ( $categories as $category ) :

                            // Skip the "Uncategorized" category
                            if ( $category->slug === 'uncategorized' ) {
                                continue;
                            }

                            // Get category thumbnail
                            $thumbnail_id = get_term_meta( $category->term_id, 'thumbnail_id', true );
                            $image_url    = $thumbnail_id 
                                ? wp_get_attachment_image_url( $thumbnail_id, 'woocommerce_thumbnail' ) 
                                : wc_placeholder_img_src( 'woocommerce_thumbnail' );

                            // Product count
                            $product_count = $category->count;
                    ?>

                    <div class="col-md-2 col-sm-4 col-xs-6 category-card-col">
                        <div class="single-offer">
                            <div class="all_categori_list img-full">
                                <a href="<?php echo esc_url( get_term_link( $category ) ); ?>" 
                                   title="<?php echo esc_attr( $category->name ); ?>"
                                   class="category-card-link">

                                    <!-- Card Image -->
                                    <div class="category-card-image">
                                        <img src="<?php echo esc_url( $image_url ); ?>" 
                                             alt="<?php echo esc_attr( $category->name ); ?>" 
                                             title="<?php echo esc_attr( $category->name ); ?>"
                                             loading="lazy">
                                    </div>

                                    <!-- Card Content -->
                                    <div class="category-card-content">
                                        <span class="category-card-title">
                                            <?php echo esc_html( $category->name ); ?>
                                        </span>
                                        <?php if ( $product_count > 0 ) : ?>
                                            <span class="category-card-count">
                                                <?php echo esc_html( $product_count ); ?> 
                                                <?php echo _n( 'Product', 'Products', $product_count, 'woocommerce' ); ?>
                                            </span>
                                        <?php endif; ?>
                                    </div>

                                </a>
                            </div>
                        </div>
                    </div>

                    <?php
                        endforeach;
                    endif;
                    ?>

                </div>
            </div>
        </div>
    </section>

</main>

<?php
get_footer();
```

---

## 🎨 CSS to Add (Appearance → Customize → Additional CSS)

```css
/* =========================================================
   CATEGORY CARD GRID
   ========================================================= */
.category-card-row {
    display: flex;
    flex-wrap: wrap;
    margin-left: -8px;
    margin-right: -8px;
}

.category-card-col {
    padding: 8px;
    margin-bottom: 16px;
}

/* =========================================================
   CARD WRAPPER
   ========================================================= */
.single-offer {
    height: 100%;
    transition: transform 0.3s ease;
}

.single-offer:hover {
    transform: translateY(-6px);
}

/* =========================================================
   CARD LINK (the visible card)
   ========================================================= */
.category-card-link {
    display: flex;
    flex-direction: column;
    height: 100%;
    background: #ffffff;
    border: 1px solid #eaeaea;
    border-radius: 12px;
    overflow: hidden;
    text-decoration: none !important;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
    transition: box-shadow 0.3s ease, border-color 0.3s ease;
}

.category-card-link:hover {
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
    border-color: #ff6600;
}

/* =========================================================
   CARD IMAGE
   ========================================================= */
.category-card-image {
    position: relative;
    width: 100%;
    padding-top: 62%; /* 270:162 aspect ratio */
    overflow: hidden;
    background: #f7f7f7;
}

.category-card-image img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.4s ease;
}

.category-card-link:hover .category-card-image img {
    transform: scale(1.08);
}

/* =========================================================
   CARD CONTENT
   ========================================================= */
.category-card-content {
    padding: 12px 10px 14px;
    text-align: center;
    display: flex;
    flex-direction: column;
    gap: 4px;
    flex-grow: 1;
    justify-content: center;
}

/* =========================================================
   CARD TITLE
   ========================================================= */
.category-card-title {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    font-size: 13px;
    font-weight: 600;
    color: #222222;
    line-height: 1.35;
    min-height: 36px;
    transition: color 0.3s ease;
}

.category-card-link:hover .category-card-title {
    color: #ff6600;
}

/* =========================================================
   CARD PRODUCT COUNT
   ========================================================= */
.category-card-count {
    display: inline-block;
    font-size: 11px;
    color: #888888;
    font-weight: 400;
    letter-spacing: 0.3px;
}

/* =========================================================
   RESPONSIVE BREAKPOINTS
   ========================================================= */
@media (max-width: 1199px) {
    .category-card-col {
        flex: 0 0 25%;
        max-width: 25%;
    }
}

@media (max-width: 991px) {
    .category-card-col {
        flex: 0 0 33.333%;
        max-width: 33.333%;
    }
}

@media (max-width: 767px) {
    .category-card-col {
        flex: 0 0 33.333%;
        max-width: 33.333%;
    }

    .category-card-title {
        font-size: 12px;
        min-height: 32px;
    }
}

@media (max-width: 480px) {
    .category-card-col {
        flex: 0 0 50%;
        max-width: 50%;
        padding: 6px;
    }

    .category-card-image {
        padding-top: 70%;
    }

    .category-card-content {
        padding: 10px 8px 12px;
    }

    .category-card-title {
        font-size: 12px;
    }

    .category-card-count {
        font-size: 10px;
    }
}
```

---

## ✅ What Changed From Your Original Code

| Original | Updated |
|----------|---------|
| `<div class="row">` | `<div class="row category-card-row">` |
| `<div class="col-md-2 col-sm-4 col-xs-6">` | `<div class="col-md-2 col-sm-4 col-xs-6 category-card-col">` |
| `<a>` with only `<img>` + `<span>` | `<a class="category-card-link">` with image wrapper + content wrapper |
| No product count | ✅ Product count added below title |
| Plain `<img>` | ✅ Wrapped in `.category-card-image` for aspect ratio + zoom effect |
| Plain `<span>` | ✅ Wrapped in `.category-card-content` with title + count |

---

## 🎯 Result Features

- ✅ **Wrapped card** with rounded corners and border
- ✅ **Soft shadow** that deepens on hover
- ✅ **Card lifts up** on hover (`translateY(-6px)`)
- ✅ **Image zooms** on hover (`scale(1.08)`)
- ✅ **Brand color border** (`#ff6600`) on hover
- ✅ **Title changes color** on hover
- ✅ **Product count** displayed under title
- ✅ **Consistent card heights** (2-line title truncation)
- ✅ **Fully responsive** — 6/4/3/2 columns based on screen
- ✅ **Lazy loading** images for performance

---

## 🔧 Optional Tweaks

**Change brand color** — Replace every `#ff6600` with your brand color (e.g., `#2e7d32` for green, `#c62828` for red).

**Show 4 per row on desktop** — Change `col-md-2` to `col-md-3` in the PHP.

**Remove product count** — Delete this block in PHP:
```php
<?php if ( $product_count > 0 ) : ?>
    <span class="category-card-count">...</span>
<?php endif; ?>
```

**Hide empty categories** — Change `'hide_empty' => false` to `'hide_empty' => true` in the PHP.

Would you like me to add a **"Shop Now" button** inside each card, or turn this into a **slider/carousel**?
