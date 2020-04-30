# Get a single category name of a post

A post may have multiple categories, and to pick one needs more than one line of code. Besides, there are tricky decisions you need to make how you are going to pick that particular one, a simple array_shift or a random one. Let's get things done!

### Get a name, whichever comes first
```php
function get_single_category( $post_id = null ) {
    global $post;
    $post_id = is_null( $post_id ) ? $post->ID : $post_id;
    $categories = wp_get_post_categories( $post_id, array( 'fields' => 'names' ) );
    $single_category = array_shift( $categories );

    return $single_category;
}
```

### Get a random choice
```php
function get_single_category( $post_id = null ) {
    global $post;
    $post_id = is_null( $post_id ) ? $post->ID : $post_id;
    $categories = wp_get_post_categories( $post_id, array( 'fields' => 'names' ) );
    shuffle( $categories );
    $single_category = array_shift( $categories );

    return $single_category;
}
```

### Get id, name pair
```php
function get_single_category( $post_id = null ) {
    global $post;
    $post_id = is_null( $post_id ) ? $post->ID : $post_id;
    $categories = wp_get_post_categories( $post_id, array( 'fields' => 'all' ) );
    shuffle( $categories );
    $single_category = array_shift( $categories );

    return array($single_category->term_id => $single_category->name);
}
```

And that's it! Enjoy.