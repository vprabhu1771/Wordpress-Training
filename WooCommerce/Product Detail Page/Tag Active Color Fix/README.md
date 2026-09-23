To fix the **active tab color** (the tab that's currently selected) in addition to the hover color, you need to target the `active` class that WooCommerce adds to the currently selected tab.

### 🎨 Complete Tab Color CSS

Add this to **Appearance → Customize → Additional CSS**:

```css
/* ===== TAB HOVER COLOR ===== */
.woocommerce div.product .woocommerce-tabs ul.tabs li a:hover {
    color: #ff6600 !important; /* Your brand hover color */
    background-color: #fff5eb !important; /* Optional light background on hover */
}

/* ===== ACTIVE TAB COLOR ===== */
.woocommerce div.product .woocommerce-tabs ul.tabs li.active a {
    color: #ff6600 !important; /* Your brand color for active tab */
    background-color: #ffffff !important; /* Background of active tab */
    border-bottom-color: #ff6600 !important; /* Bottom border accent */
}

/* ===== ACTIVE TAB INDICATOR (the underline) ===== */
.woocommerce div.product .woocommerce-tabs ul.tabs li.active {
    background-color: #ffffff !important;
    border-bottom: 2px solid #ff6600 !important;
}

/* ===== DEFAULT TAB COLOR (non-active, non-hover) ===== */
.woocommerce div.product .woocommerce-tabs ul.tabs li a {
    color: #333333 !important; /* Dark gray for inactive tabs */
    background-color: #f7f7f7 !important; /* Light gray background */
    transition: all 0.3s ease; /* Smooth color transition */
}

/* ===== ACTIVE TAB CONTENT PANEL BORDER ===== */
.woocommerce div.product .woocommerce-tabs .panel {
    border-top: 2px solid #ff6600 !important; /* Matches active tab accent */
}

/* ===== REMOVE DEFAULT WOOCOMMERCE TAB STYLING (if needed) ===== */
.woocommerce div.product .woocommerce-tabs ul.tabs::before {
    border-bottom: 1px solid #e0e0e0 !important;
}
```

### 🎯 How WooCommerce Tab Classes Work

| State | CSS Class | Example |
|-------|-----------|---------|
| **Default** | `li` (no special class) | `.woocommerce-tabs ul.tabs li a` |
| **Hover** | `:hover` pseudo-class | `.woocommerce-tabs ul.tabs li a:hover` |
| **Active/Selected** | `.active` class on `li` | `.woocommerce-tabs ul.tabs li.active a` |

### 💡 Why Your Active Color Might Not Change

If the active tab color still isn't changing, it's usually because:

1. **Another CSS rule has higher specificity** → Add `!important` (as shown above)
2. **Your theme overrides WooCommerce styles** → Check your theme's CSS for `.tabs` or `.woocommerce-tabs`
3. **The active class is on a different element** → Inspect the tab with browser DevTools (Right-click → Inspect) to find the exact class

### 🔍 Quick Debugging Tip

To verify the exact selector, open your product page in a browser:
1. **Right-click** on an active tab → **Inspect**
2. Look at the `<li>` element — it should have `class="active"`
3. The `<a>` inside it is what you style for text color

### 🎨 Full Custom Tab Style Example

If you want a **modern pill-style tab design**, use this:

```css
.woocommerce div.product .woocommerce-tabs ul.tabs {
    padding: 0 !important;
    display: flex;
    gap: 8px;
    border-bottom: none !important;
}

.woocommerce div.product .woocommerce-tabs ul.tabs li {
    border: none !important;
    border-radius: 6px !important;
    background: transparent !important;
    margin: 0 !important;
}

.woocommerce div.product .woocommerce-tabs ul.tabs li a {
    color: #555 !important;
    background: #f2f2f2 !important;
    border-radius: 6px !important;
    padding: 10px 20px !important;
    font-weight: 600;
    border: none !important;
}

.woocommerce div.product .woocommerce-tabs ul.tabs li a:hover {
    color: #ff6600 !important;
    background: #ffe8d6 !important;
}

.woocommerce div.product .woocommerce-tabs ul.tabs li.active a {
    color: #ffffff !important;
    background: #ff6600 !important;
}
```

This gives you a clean, modern look where the active tab is fully highlighted with your brand color.

Would you like me to help you with any other styling on this page, like the add-to-cart button or price color?
