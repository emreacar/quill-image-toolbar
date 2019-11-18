# Quill ImageToolbar Module

A module for Quill rich text editor to allow images alignment and optioned size changing.

This module depends on [quill-image-resize-module](https://github.com/Etoile984816138/quill-image-resize-module), I had same changes with this module for myself.

## Usage

### Webpack/ES6

```javascript
import Quill from 'quill';
import { imageToolbar } from 'quill-image-toolbar';

Quill.register('modules/imageToolbar', imageToolbar);

const quill = new Quill(editor, {
    // ...
    modules: {
        // ...
        imageToolbar: {
            // See optional "config" below
        }
    }
});
```

### Script Tag

Copy quill-image-toolbar.min.js into your web root or include from node_modules

```html
<script src="/node_modules/quill-image-toolbar/quill-image-toolbar.js"></script>
```

```javascript
var quill = new Quill(editor, {
    // ...
    modules: {
        // ...
        imageToolbar: {
            // See optional "config" below
        }
    }
});
```

### Config

For the default experience, pass an empty object, like so:
```javascript
var quill = new Quill(editor, {
    // ...
    modules: {
        // ...
        imageToolbar: {}
    }
});
```

Functionality is broken down into modules, which can be mixed and matched as you like. For example,
the default is to include all modules:

```javascript
const quill = new Quill(editor, {
    // ...
    modules: {
        // ...
        imageToolbar: {
            modules: [ 'Toolbar' ]
        }
    }
});
```

#### `Toolbar` - Image alignment and resize tools

Displays a toolbar below the image, where the user can select an alignment for the image and change images size 100% and 50%

The look and feel can be controlled with options:

```javascript
var quill = new Quill(editor, {
    // ...
    modules: {
        // ...
        imageToolbar: {
            // ...
            toolbarStyles: {
                backgroundColor: 'black',
                border: 'none',
                color: white
                // other camelCase styles for size display
            },
            toolbarButtonStyles: {
                // ...
            }
        }
    }
});
```

#### `BaseModule` - Include your own custom module

You can write your own module by extending the `BaseModule` class, and then including it in
the module setup.

For example,

```javascript
import { Resize, BaseModule } from 'quill-image-resize-module';

class MyModule extends BaseModule {
    // See src/modules/BaseModule.js for documentation on the various lifecycle callbacks
}

var quill = new Quill(editor, {
    // ...
    modules: {
        // ...
        imageToolbar: {
            modules: [ MyModule, Resize ],
            // ...
        }
    }
});
```