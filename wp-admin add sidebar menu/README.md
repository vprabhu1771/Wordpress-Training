In WordPress, you can add a custom menu to the **wp-admin sidebar** using the `add_menu_page()` or `add_submenu_page()` functions.

## 1. Add a Top-Level Sidebar Menu

Add the following code to your plugin or your theme's `functions.php` file (a plugin is recommended).

```php
<?php
// Add Admin Menu
add_action('admin_menu', 'my_custom_admin_menu');

function my_custom_admin_menu() {

    add_menu_page(
        'My Plugin',                 // Page title
        'My Plugin',                 // Menu title
        'manage_options',            // Capability
        'my-plugin',                 // Menu slug
        'my_plugin_page',            // Callback function
        'dashicons-admin-generic',   // Icon
        25                           // Position
    );
}

function my_plugin_page() {
    ?>
    <div class="wrap">
        <h1>My Plugin Dashboard</h1>
        <p>Welcome to your custom admin page.</p>
    </div>
    <?php
}
```

### Result

```
Dashboard
Posts
Media
Pages
Comments
Appearance
Plugins
Users
Tools
Settings
--------------------
My Plugin
```

---

## 2. Add Submenus

```php
add_action('admin_menu', 'my_plugin_submenus');

function my_plugin_submenus() {

    add_menu_page(
        'Loan Manager',
        'Loan Manager',
        'manage_options',
        'loan-manager',
        'loan_dashboard',
        'dashicons-money-alt',
        26
    );

    add_submenu_page(
        'loan-manager',
        'Dashboard',
        'Dashboard',
        'manage_options',
        'loan-manager',
        'loan_dashboard'
    );

    add_submenu_page(
        'loan-manager',
        'Customers',
        'Customers',
        'manage_options',
        'loan-customers',
        'loan_customers'
    );

    add_submenu_page(
        'loan-manager',
        'Collections',
        'Collections',
        'manage_options',
        'loan-collections',
        'loan_collections'
    );

    add_submenu_page(
        'loan-manager',
        'Reports',
        'Reports',
        'manage_options',
        'loan-reports',
        'loan_reports'
    );
}

function loan_dashboard() {
    echo '<div class="wrap"><h1>Dashboard</h1></div>';
}

function loan_customers() {
    echo '<div class="wrap"><h1>Customers</h1></div>';
}

function loan_collections() {
    echo '<div class="wrap"><h1>Collections</h1></div>';
}

function loan_reports() {
    echo '<div class="wrap"><h1>Reports</h1></div>';
}
```

### Output

```
Loan Manager
   Dashboard
   Customers
   Collections
   Reports
```

---

## 3. Common Dashicons

| Icon        | Class                      |
| ----------- | -------------------------- |
| ⚙️ Settings | `dashicons-admin-generic`  |
| 👥 Users    | `dashicons-groups`         |
| 💰 Money    | `dashicons-money-alt`      |
| 📊 Chart    | `dashicons-chart-bar`      |
| 📄 Media    | `dashicons-media-document` |
| 🛒 Cart     | `dashicons-cart`           |
| 📦 Archive  | `dashicons-archive`        |
| 🚗 Car      | `dashicons-car`            |
| 📍 Location | `dashicons-location`       |
| ⭐ Star      | `dashicons-star-filled`    |

---

## 4. Restrict Access by User Role

Only administrators:

```php
'manage_options'
```

Editors:

```php
'edit_pages'
```

Authors:

```php
'publish_posts'
```

Custom capability:

```php
'loan_manage'
```

---

## 5. Add a Menu Under an Existing Section

Instead of creating a top-level menu, you can add your page under an existing admin menu.

Under **Settings**:

```php
add_submenu_page(
    'options-general.php',
    'Loan Settings',
    'Loan Settings',
    'manage_options',
    'loan-settings',
    'loan_settings_page'
);
```

Under **Tools**:

```php
add_submenu_page(
    'tools.php',
    'Import Loans',
    'Import Loans',
    'manage_options',
    'loan-import',
    'loan_import_page'
);
```

Under **WooCommerce** (if installed):

```php
add_submenu_page(
    'woocommerce',
    'Loan Reports',
    'Loan Reports',
    'manage_options',
    'loan-reports',
    'loan_reports'
);
```

---

## Best Practice

For production development, especially if you're building a reusable feature (such as a loan management system, ACF extension, or custom admin module), place this code in a **custom plugin** rather than in your theme's `functions.php`. This ensures the admin menu remains available even if the active theme changes.
