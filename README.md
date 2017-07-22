Jidn
======

When I ran across [Hynek Schlawack's](https://hynek.me) blog, I liked the
simplistic beauty.  When I took a look at the source, I fell in love.
Here is my homage to beautity to which I can only inspire.

This is based on the [lanyon theme](https://themes.getnikola.com/v7/lanyon/).
All of it's configurations still apply.

## Theme Highlights

* Share post on
    + Twitter
    + Facebook
    + Google+
* Author section located below post for
    + image
    + email
    + short biography
    + location information
* Author social accounts, supporting
    + Twitter
    + Facebook
    + Github
    + StackOverflow
    + Instagram
    + Pinterest

* Post license is Creative Commons Attribution-ShareAlike 4.0

## Configuration

It uses a dictionary supporting possibly different authors in the config:

```
    GLOBAL_CONTEXT = {
      "JIDN": {BLOG_AUTHOR: {   # Or "Clinton James" for alternate authors
                "image": "http://example.com/my-image.jpg",

                ## The following are all individually optional
                "bio": """I am the very model of a modern major general.""",
                "map": "Chicago, IL  USA",
                "social": (
                    "https://twitter.com/username",
                    "https://facebook.com/username",
                    "https://github.com/username,
                    # You get the idea
                    )
                }
              }
```

### Lanyon Configuration

It supports one variable set in the config:

```
    GLOBAL_CONTEXT = {
        "lanyon_subtheme": "theme-base-08"
    }
```

That changes the color scheme, replace 08 with one of 09, 0a, 0b, 0c, 0d, 0e, 0f.

## Fixes

+ Sidebar is no longer visible when printing.
