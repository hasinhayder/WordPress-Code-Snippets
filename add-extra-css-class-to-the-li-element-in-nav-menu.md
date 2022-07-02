# Add extra css class to the li tag in nav menu

You may run into situations where the `<li>` tag requires some extra css class in your nav menu, but the function which renders the menu leaves you disappointed because there is no default way to do that, except using a special filter. So let's do that

```php
function set_li_class( $class = '', $location = 'primary' ) {
    add_filter( 'nav_menu_css_class', function ( $classes, $item, $args ) use ( $class, $location ) {
        $classes[] = $class;
        return $classes;
    }, 10, 3 );
}
``` 

Instead of adding css class to every `<li>` tag found in every `theme_location` we can also restrict it to a specific location, like this, which will work only for the `primary` theme location. 

```php
function set_li_class( $class = '', $location = 'primary' ) {
    add_filter( 'nav_menu_css_class', function ( $classes, $item, $args ) use ( $class, $location ) {
        if ( $args->theme_location == $location ) {
            $classes[] = $class;
        }
        return $classes;
    }, 10, 3 );
}
``` 

That was not tough, or was it?