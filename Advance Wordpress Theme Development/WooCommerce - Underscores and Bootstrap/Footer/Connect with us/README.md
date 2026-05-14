```
<!-- Connect with us -->
<div class="col-md-4 col-sm-12 ms-auto">
  <h3>Connect with us</h3>
  <?php dynamic_sidebar('footer-widget-col-four'); ?>
</div>
```

```html
<!-- Facebook -->
<a href="https://www.linkedin.com/in/aangadishop/" target="_blank" title="Facebook">
  <i class="bi bi-facebook"></i>
</a>

<!-- Twitter (X) -->
<a href="https://x.com/aangadishop" target="_blank" title="Twitter">
  <i class="bi bi-twitter-x"></i>
</a>

<!-- Instagram -->
<a href="https://www.instagram.com/aangadishop/" target="_blank" title="Instagram">
  <i class="bi bi-instagram"></i>
</a>

<!-- YouTube -->
<a href="https://www.youtube.com/@aangadishop" target="_blank" title="YouTube">
  <i class="bi bi-youtube"></i>
</a>
```

### Important ⚠️

Make sure you have Bootstrap Icons included:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css" rel="stylesheet">
```

---

### Small Fix Suggestion

Your first link is actually **LinkedIn**, but icon is Facebook. If you want it correct:

```html
<i class="bi bi-linkedin"></i>
```

---

If you want hover effects, colors, or rounded icon buttons, tell me 👍

You don’t need anything complicated—just target the `<i>` inside your links and style it with SCSS.

### ✅ Basic SCSS (white color + bigger size)

```scss
a {
  i {
    color: #fff;        // white color
    font-size: 22px;    // increase icon size
    transition: 0.3s;
  }

  &:hover i {
    opacity: 0.7;       // simple hover effect
  }
}
```

---

### ✅ Better (recommended – scoped for social icons)

If these are social icons, give them a class like `.social-icons`:

```html
<div class="social-icons">
  <!-- your links -->
</div>
```

```scss
.social-icons {
  a {
    margin-right: 12px;

    i {
      color: #fff;
      font-size: 24px;
      transition: all 0.3s ease;
    }

    &:hover i {
      transform: scale(1.2); // nice zoom effect
      opacity: 0.8;
    }
  }
}
```

---

### ✅ Optional: Circle background style (modern look)

```scss
.social-icons {
  a {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    background: #000;
    border-radius: 50%;

    i {
      color: #fff;
      font-size: 18px;
    }

    &:hover {
      background: #333;
    }
  }
}
```

---

If you want brand colors on hover (Facebook blue, Instagram gradient, etc.), I can add that too.

