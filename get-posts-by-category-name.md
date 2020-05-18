# Find posts by category name

If you need to find posts by category name, you can do that quickly using the following piece of code. 

```php
$post_query = new WP_Query( array(
    'posts_per_page' => -1, //return all posts
    'category_name'  => 'your category name',
) );

echo "<ul>";
while ($post_query->have_posts()){
    $post_query->the_post();
    ?>
        <li><a href='<?php the_permalink();?>'><?php the_title();?></a></li>
    <?
}
echo "</ul>";

wp_reset_postdata();

```

If you need to find posts by multiple category names, just pass them as csv (comma separated value) and you're done!

```php
$post_query = new WP_Query( array(
    'posts_per_page' => -1, //return all posts
    'category_name'  => join(',',$categories),
) );
```

:)