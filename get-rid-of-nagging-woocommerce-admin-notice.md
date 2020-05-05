# How to Hide WooCommerce Nagging Admin Notice

If you are not a pro subscriber, you will see this nagging message "connect your woocommerce store blah blah" in your admin area, and it cannot be dismissed. Super annoying I must say. But you can easily get rid of it using the following filter

```php
add_filter( 'woocommerce_helper_suppress_admin_notices', '__return_true' );
```

Your admin panel is now clean, enjoy.