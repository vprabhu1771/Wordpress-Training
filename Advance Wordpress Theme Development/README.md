```
https://developer.wordpress.org/themes/
```
# WordPress WooCommerce Custom Theme Development
```
https://www.youtube.com/playlist?list=PLHKO87MLJx2mabc8n9CR_Cb00juQrDfHM
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
