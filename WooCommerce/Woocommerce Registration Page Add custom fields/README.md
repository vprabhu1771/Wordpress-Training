There are three common ways to add custom fields to the **WooCommerce registration page**.

## Method 1: Add fields using code (Recommended)

Add the following code to your theme's `functions.php` or a custom plugin.

### Add custom fields to the registration form

```php
/**
 * Add custom registration fields
 */
add_action('woocommerce_register_form', 'custom_woocommerce_register_fields');

function custom_woocommerce_register_fields() {
    ?>

    <p class="form-row form-row-wide">
        <label for="reg_phone">Phone Number <span class="required">*</span></label>
        <input type="text"
               class="input-text"
               name="phone"
               id="reg_phone"
               value="<?php if (!empty($_POST['phone'])) echo esc_attr(wp_unslash($_POST['phone'])); ?>" />
    </p>

    <p class="form-row form-row-wide">
        <label for="reg_company">Company Name</label>
        <input type="text"
               class="input-text"
               name="company"
               id="reg_company"
               value="<?php if (!empty($_POST['company'])) echo esc_attr(wp_unslash($_POST['company'])); ?>" />
    </p>

    <?php
}
```

---

## Validate required fields

```php
add_filter('woocommerce_registration_errors', 'custom_registration_validation', 10, 3);

function custom_registration_validation($errors, $username, $email) {

    if (empty($_POST['phone'])) {
        $errors->add('phone_error', __('Phone Number is required.', 'woocommerce'));
    }

    return $errors;
}
```

---

## Save the custom fields

```php
add_action('woocommerce_created_customer', 'save_custom_registration_fields');

function save_custom_registration_fields($customer_id) {

    if (isset($_POST['phone'])) {
        update_user_meta($customer_id, 'phone', sanitize_text_field($_POST['phone']));
    }

    if (isset($_POST['company'])) {
        update_user_meta($customer_id, 'company', sanitize_text_field($_POST['company']));
    }

}
```

---

## Display in Admin User Profile

```php
add_action('show_user_profile', 'show_custom_user_fields');
add_action('edit_user_profile', 'show_custom_user_fields');

function show_custom_user_fields($user) {
?>

<h3>Extra Information</h3>

<table class="form-table">

<tr>
<th>Phone</th>
<td><?php echo esc_html(get_user_meta($user->ID,'phone',true)); ?></td>
</tr>

<tr>
<th>Company</th>
<td><?php echo esc_html(get_user_meta($user->ID,'company',true)); ?></td>
</tr>

</table>

<?php
}
```

---

# Method 2: Use ACF (Advanced Custom Fields)

If you already use **Advanced Custom Fields**:

1. Create a Field Group.
2. Set Location:

   * **User Form = Add/Edit**
3. Add fields like:

   * Phone
   * GST Number
   * Address
   * Company Name

ACF fields appear on the WordPress user profile, but **they do not automatically appear on the WooCommerce registration page**. To show them during registration, you still need custom code or an ACF extension.

---

# Method 3: Plugin (No Coding)

You can use plugins such as:

* Registration Fields for WooCommerce
* ThemeHigh Checkout Field Editor (supports registration fields in some versions)
* User Registration plugins with WooCommerce integration

These let you add fields using a drag-and-drop interface.

---

## Example Registration Form

```
First Name *
Last Name *
Email *
Phone Number *
Company Name
GST Number
Password *
Confirm Password *
```

Each field can be saved as user meta:

```php
first_name
last_name
phone
company
gst_number
```

---

If you're building a **B2B or dealer registration** form, I can also provide a complete example with fields like:

* First Name
* Last Name
* Mobile Number (OTP-ready)
* Company Name
* GST Number
* PAN Number
* Address
* City
* State
* Pincode
* Dealer Type
* File Upload (GST Certificate)
* Terms & Conditions checkbox
