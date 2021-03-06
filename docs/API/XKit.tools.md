`XKit.tools`: Utility functions for XKit.

## Methods

<a name="get_blogs" href="XKit.tools.md#get_blogs">#</a> XKit.tools.**get_blogs**()

Returns an array of the URLs of the blogs the user has.

<a name="remove_css" href="XKit.tools.md#remove_css">#</a> XKit.tools.**remove_css**(_extension_id_)

Removes the CSS added by `extension_id`.

<a name="add_css" href="XKit.tools.md#add_css">#</a> XKit.tools.**add_css**(_css_, _extension_id_)

Adds `css` to the page with id `extension_id`.

Example usage:

```javascript
run: function() {
    var hide_post = true;
    if (hide_posts) {
        // Lets hide all posts.
        XKit.tools.add_css("#posts .post { display: none; }", "my_extension_name");
    }
},

destroy: function() {
    XKit.tools.remove_css("my_extension_name");
}
```

<a name="init_css" href="XKit.tools.md#init_css">#</a> XKit.tools.**init_css**(_extension_id_)

Loads the extension's CSS into the page.

If your CSS has code that you'll be using all the time, use the Stylesheet tab on XKit Editor, then call init_css function to let XKit load it to the page. Use `XKit.tools.remove_css` to remove it.

Example usage:

```css
/* my_extension.css */
#my_fancy_div {
    background: red;
    color: yellow;
}
```

```javascript
// my_extension.js
run: function() {
    XKit.tools.init_css("my_extension_name");
    $("body").append("<div id=\"my_fancy_div\">This will be red and yellow.</div>");
},

destroy: function() {
    XKit.tools.remove_css("my_extension_name");
}
```

<a name"random_string" href="XKit.tools.md#random_string">#</a> XKit.tools.**random_string**()

Returns a random 30-character string.

<a name="add_function" href="XKit.tools.md#add_function">#</a> XKit.tools.**add_function**(_func_, _execute_, _add_t_)

Adds the function `func` to the page, and executes it if `execute` is `true`.
`add_t` contains data that is passed along with `func` to be available as the variable `add_tag` in the context of the browser page.

<a name="parse_version" href="XKit.tools.md#parse_version">#</a> XKit.tools.**parse_version**(_version_string_)

Parses `version_string` in format `<MAJOR>.<MINOR>.<PATCH>`, `<MAJOR>.<MINOR>`, or `<MAJOR>.<MINOR> REV <N>` and returns a Semver-styled object:

```
{
  major,
  minor,
  patch
}
```

## Tips

* Always remove the CSS you've added when you are done with it, and on the `destroy` function.
* Name your class names/ids with a prefix to avoid conflicts with other extensions.
  * For example, do not use `.my_div`; instead use `.my_extension_my_div`
