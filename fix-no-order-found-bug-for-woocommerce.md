# Fix no orders found bug in WooCommerces + WordPress 5x

There could be many **valid** reasons for a shop owner not updating his WooCommerce to a later version. However, if he/she updates the WordPress core, he could fall into a strange situation when he will find out that no orders are displaying in his WooCommerce admin area. This is frustrating and gives a panic attack. The fix is easy though. Add the following code as a plugin, or inside the `functions.php` of your theme. 

```php
function fix_request_query_args_for_woocommerce( $query_args ) {
	if ( isset( $query_args['post_status'] ) && empty( $query_args['post_status'] ) ) {
		unset( $query_args['post_status'] );
	}
	return $query_args;
}
add_filter( 'request', 'fix_request_query_args_for_woocommerce', 1 );

```

And no more panic attack after that!