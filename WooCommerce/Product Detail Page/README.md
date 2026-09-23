Based on the page content, I can see your product detail page is using the standard WooCommerce template structure. Let me show you exactly where to find and customize each section.

### 📍 Where Each Section is Located

Looking at your page, here's the mapping of what you see to the template files:

| What You See on Page | Template File Location |
|---------------------|----------------------|
| **"Description" tab content** | `wp-content/plugins/woocommerce/templates/single-product/tabs/description.php` |
| **"Additional information" tab content** | `wp-content/plugins/woocommerce/templates/single-product/tabs/additional-information.php` |
| **"Reviews" tab content** | `wp-content/plugins/woocommerce/templates/single-product/tabs/reviews.php` |
| **The tab container itself** | `wp-content/plugins/woocommerce/templates/single-product/tabs/tabs.php` |
| **Product title, price, short description** | `wp-content/plugins/woocommerce/templates/content-single-product.php` |
| **Main page wrapper** | `wp-content/plugins/woocommerce/templates/single-product.php` |

### 🎯 To Customize Your Product Page

Since you want to **hide** Description, Additional Information, Reviews, and Tags, the safest and easiest method is to add code to your child theme's `functions.php` file.

**If you don't have a child theme**, you can use the **Code Snippets** plugin (free) to add this code without touching any files.

**Step 1: Hide the Tabs**

Add this PHP code to remove all three tabs:

```php
// Remove all product tabs
add_filter( 'woocommerce_product_tabs', 'remove_all_product_tabs', 98 );

function remove_all_product_tabs( $tabs ) {
    unset( $tabs['description'] );          // Description tab
    unset( $tabs['additional_information'] ); // Additional information tab
    unset( $tabs['reviews'] );              // Reviews tab
    return $tabs;
}
```

**Step 2: Hide Tags (Product Meta)**

Add this CSS to **Appearance → Customize → Additional CSS**:

```css
/* Hide the entire product meta section (SKU, categories, tags) */
.single-product .product_meta {
    display: none !important;
}

/* Or hide ONLY tags, keep SKU and categories */
.single-product .product_meta .tagged_as {
    display: none !important;
}
```

**Step 3: Fix Hover Color**

Add this CSS to change the hover color of tabs (if you keep any) or other clickable elements:

```css
/* Tab hover color */
.woocommerce div.product .woocommerce-tabs ul.tabs li a:hover {
    color: #ff6600 !important; /* Change to your brand color */
}

/* Product title hover (if it's a link) */
.single-product .product_title a:hover {
    color: #ff6600 !important;
}

/* Button hover */
.single-product .single_add_to_cart_button:hover {
    background-color: #ff6600 !important;
    color: #ffffff !important;
}
```

### 🔧 Advanced: Override Template Files (If Needed)

If you need to change the **HTML structure** of these sections, not just hide them, you must override the template files:

1. In your **child theme**, create this folder structure:
   ```
   your-child-theme/
   └── woocommerce/
       └── single-product/
           └── tabs/
               ├── tabs.php
               ├── description.php
               ├── additional-information.php
               └── reviews.php
   ```

2. Copy the original files from:
   ```
   wp-content/plugins/woocommerce/templates/single-product/tabs/
   ```

3. Paste them into your child theme folder and edit as needed.

4. Also copy `content-single-product.php` to:
   ```
   your-child-theme/woocommerce/content-single-product.php
   ```
   This controls the overall product page layout.

### 💡 Quick Check for Your Site

Since I can't access your server files, you can verify your template structure by:

1. Going to **WooCommerce → Status → Templates**
2. This shows which template files are being used and whether any are overridden by your theme

The page you linked shows the standard WooCommerce tab structure, so the hooks and CSS above will work. Would you like me to help you with a specific customization for any of these sections?
