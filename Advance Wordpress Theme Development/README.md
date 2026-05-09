```
https://developer.wordpress.org/themes/
```

```
<html lang="en">
```
Change To
```
<html <?php language_attributes(); ?>>
```

```
<meta charset="UTF-8">
```
Change To
```
<meta charset="<?php bloginfo('charset') ?>">
```
