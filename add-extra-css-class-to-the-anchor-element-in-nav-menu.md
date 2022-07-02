# Add extra css class to the anchor tag in nav menu

You may run into situations where the `<a>` tag requires some extra css class in your nav menu, but the function which renders the menu leaves you disappointed because there is no default way to do that, except using a special filter. So let's do that

```php
function set_anchor_class( $class = '', $location = 'primary', $append = false ) {
    add_filter( 'nav_menu_link_attributes', function ( $atts, $item, $args ) use ( $class, $append, $location ) {
        if ( !$append ) {
            $atts['class'] = $class;
        } else {
            $atts['class'] .= " " . $class;
        }
        return $atts;
    }, 10, 3 );
}
``` 

Instead of adding css class to every `<a>` tag found in every `theme_location` we can also restrict it to a specific location, like this, which will work only for the `primary` theme location. 

```php
function set_anchor_class( $class = '', $location = 'primary', $append = false ) {
    add_filter( 'nav_menu_link_attributes', function ( $atts, $item, $args ) use ( $class, $append, $location ) {
        if ( $args->theme_location == $location ) {
            if ( !$append ) {
                $atts['class'] = $class;
            } else {
                $atts['class'] .= " " . $class;
            }
        }
        return $atts;
    }, 10, 3 );
}
``` 

:) Nice, eh?