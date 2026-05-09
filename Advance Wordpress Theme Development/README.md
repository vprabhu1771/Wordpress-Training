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


```
<title>Document</title>
```
Change To
```
<title><?php bloginfo('name'); ?> <?php wp_title(''); ?></title>
```
