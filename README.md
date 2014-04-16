Fake
====

Fake helps you building your 100% UI Web App.
Make was taken so I called it Fake instead.


# Structure

- /img
- /scripts
- /styles
- /vendor
- /views
- /module1/...
- /module2/...

The root is considered as a module ("." as the root directory). The modules have the same hierarchy as the root module.

# Compilation

After the compilation process, the files will be built in the build sub-directory and a compressed file of that build will be added in the builds sub-directory.

## makefile
This file defines two variables.

- PROJECT: the name of the project.
- MODULES: an array of the modules present in that project. It should usually contain ".". Each module should contain an "index.html" file.

## index.html
This file, besides being a standard index file, also define what will be copied, built, where and how. Here is what is supported for now.

### Copy folders (fake-dir-copy)
This will copy the directories. Usually, /img will be copied, along with the /views (for Angular for example).
    <make **fake-dir-copy**="img" src="img" />

### Compile LESS files (fake-css-pack)
    <link **fake-css-pack**="styles/style.min.css" href="css/bootstrap.css" rel="stylesheet" />

### Pack JS files (fake-js-pack)
    <script **fake-js-pack**="scripts/vendor.min.js" src="vendors/angular-1.0.5.min.js"></script>

### Copy JS or CSS files (fake-js-copy / fake-css-copy)
    <script fake-js-copy="config.js" src="config.js"></script>

### Development code to production code

In the index, the development code is encapsulated like below will be removed.

    <!-- DEV -->
    ...
    <!-- /DEV -->

On the contrary, the production code encapsulated like below will be enabled.

    <!-- PRD --><!--
    ...
    --><!-- /PRD -->
