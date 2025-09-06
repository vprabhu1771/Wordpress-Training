```
https://help.servmask.com/2018/10/27/how-to-increase-maximum-upload-file-size-in-wordpress/
```

Do it yourself 

Edit `.htaccess` file 

```
php_value upload_max_filesize 128M
php_value post_max_size 128M
php_value memory_limit 256M
php_value max_execution_time 300
php_value max_input_time 300
```

OR


Edit `wp-config.php` file

```
@ini_set( 'upload_max_filesize' , '128M' );
@ini_set( 'post_max_size', '128M');
@ini_set( 'memory_limit', '256M' );
@ini_set( 'max_execution_time', '300' );
@ini_set( 'max_input_time', '300' );
```

`upload_max_filesize` – set this to a value > than your backup
`post_max_size` – set this to a value > than your backup
`memory_limit` – set this to a value > than your backup
`max_execution_time` – set this to 0 (infinite)