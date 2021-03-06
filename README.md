# Bootstrap Confirm Delete

Bootstrap confirm delete modal dialog jquery plugin


## Installation
You can install with [bower](http://bower.io/) or [npm](https://www.npmjs.com/).

```sh
$ bower install bootstrap-confirm-delete
$ npm install --save bootstrap-confirm-delete
```

## Dependencies
This plugin depends on the following:
- jquery >= 1.9.1
- bootstrap >= 3.3.5

NOTE: This plugin has not been tested with versions prior to these.


## Basic Usage
This plugin will intercept the delete event on configured page elements. In this example it will block the deletion click
on any links or buttons that have the 'delete' class on them.

```html
<script src="jquery.js"></script>
<script src="bootstrap-confirm-delete.js"></script>
```

```html
<a href="server.php" class="delete" data-type="post">Delete</a>
```

Initialise the plugin either in <script></script> tags on the html page or in an external .js script. 

```js
$( document ).ready( function( )
{
    $( '.delete' ).bootstrap_confirm_delete( );
} );
```

Notice the 'data-type' attribute on the link. The plugin will use this attribute if set to show a custom delete message. For example,

Heading:    'Delete Post'

Message:    'Are you sure you want to delete this post?'


## Options
Bootstrap Confirm Delete plugin comes with several option settings.

### Example
This example shows all the available options:

```js
$( document ).ready( function( )
{
    $( '.delete' ).bootstrap_confirm_delete(
        {
            debug:              false,
            heading:            'My Custom Delete Heading',
            message:            'Are you sure you want to delete this item?',
            data_type:          'post',
            callback: function ( event )
            {
                // grab original clicked delete button
                var button = event.data.originalObject;
                // execute delete operation
                button.closest( 'tr' ).remove();
            },
            delete_callback:    function() { console.log( 'delete button clicked' ); },
            cancel_callback:    function() { console.log( 'cancel button clicked' ); }
        }
    );
} );
```

### debug
Debug mode will output events and information to the console.

### heading
This is for setting a custom modal heading.

### message
Setting a custom delete message/question.

### data_type
Used if heading & message are not provided

### callback
Will fire if responding to a button click that has no href attribute.

Use this callback to do any deletions from a button click.
Parameters:
* data (data.originalObject contains the originally clicked object)

### delete_callback
Will fire when the delete button is clicked and a handler is provided.
Parameters:
* data (data.originalObject contains the originally clicked object)

### cancel_callback
Will fire when the cancel button is clicked and a handler is provided.
Parameters:
* data (data.originalObject contains the originally clicked object)


## License
Copyright &copy; 2015 Tom Kaczocha <tom@rawphp.org>
Licensed under the MIT license.