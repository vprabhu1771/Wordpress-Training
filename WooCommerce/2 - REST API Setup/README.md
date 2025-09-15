Got it 👍 You want to **set up the WooCommerce REST API** in WordPress so you can connect with external apps (like Flutter, React, Laravel, or Postman). I’ll guide you step by step:

---

## 🔧 Step 1: Enable WooCommerce REST API

1. Go to your **WordPress Dashboard**.
2. Navigate to **WooCommerce → Settings → Advanced → REST API**.
3. Click **Add Key**.
4. Give a **description** (example: `Flutter App`).
5. Select a **user** (must have Admin or Shop Manager role).
6. Choose **Permissions**:

   * `Read` → if you only want to fetch data.
   * `Write` → if you want to create/update products, orders, etc.
   * `Read/Write` → both.
7. Click **Generate API Key**.

✅ You’ll get:

* **Consumer Key**
* **Consumer Secret**

⚠️ Save them somewhere safe (you won’t see them again).

---

## 🔧 Step 2: Enable Permalinks

* Go to **Settings → Permalinks** in WordPress.
* Make sure **Post name** or any **non-default option** is selected.
* This ensures API routes work properly.

---

## 🔧 Step 3: Test the REST API

WooCommerce API base URL:

```
https://your-domain.com/wp-json/wc/v3/
```

### Example Endpoints:

* Products:

  ```
  GET https://your-domain.com/wp-json/wc/v3/products
  ```
* Orders:

  ```
  GET https://your-domain.com/wp-json/wc/v3/orders
  ```

### Using cURL:

```bash
curl https://your-domain.com/wp-json/wc/v3/products \
-u ck_xxxxxxxxxxxxxxxxx:cs_xxxxxxxxxxxxxxxxx
```

---

## 🔧 Step 4: Connect with External Apps

### Using Postman

1. Open **Postman**.
2. Create a new request:

   ```
   GET https://your-domain.com/wp-json/wc/v3/products
   ```
3. Go to **Auth → Basic Auth**.

   * Username = `Consumer Key`
   * Password = `Consumer Secret`
4. Send request ✅ you’ll see product JSON.

---

## 🔧 Step 5: Optional Security (JWT or OAuth)

* If you want to authenticate users (not just API keys), install **JWT Authentication for WP-API** plugin.
* For apps like Flutter, Laravel, or React, you’ll usually pass **consumer key/secret** or JWT tokens.

---

👉 Do you want me to also give you **PHP/Laravel/Flutter sample code** to connect with this WooCommerce REST API after setup?
