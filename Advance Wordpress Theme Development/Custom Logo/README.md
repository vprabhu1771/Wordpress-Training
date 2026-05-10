```
Appearance > Customize > Site Identity.
```

```
<?php 
    if (has_custom_logo()) {
      the_custom_logo();
    } else {
      echo "No logo set";
    }
?>
```
