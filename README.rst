.. title: JIDN: a Nikola Theme
.. slug: jidn-a-nikola-theme
.. type: text

.. raw: html

    <style>
    .menu-onclk {width: 185px; padding:0; float: right; background-color:#f8f8f8}
    .menu-onclk p { padding: .5rem 1rem; margin: 0;}
    .menu-onclk ul { margin: 0; padding: 0; list-style-type: none;}
    .menu-onclk ul li { padding: .5rem 1rem; background-color: #f0f0f0; display:block;}
    .menu-onclk ul li:hover { background-color: #d0d0d0;}
    </style> <script>
    function setLiveDemoOnClick() {
        var elms = document.getElementsByClassName("menu-onclk");
        elms = elms[0].getElementsByTagName("LI")
        for(var i = (elms.length - 1); i >= 0; i--) {
            if (elms[i].tagName == "LI"){
                var theme;
                if (elms[i].innerHTML == "None")
                    theme = "";
                else
                    theme = "theme-base-" + elms[i].innerHTML.toLowerCase();
                elms[i].setAttribute("class", theme);
                elms[i].onclick = function(t) {return function() {
                    document.body.setAttribute("class", t);
                };}(theme);
    }   }   }
    window.onload = setLiveDemoOnClick;
    </script>

.. container: menu-onclk

    `Color Themes`_

    + None
    + Red
    + Orange
    + Yellow
    + Green
    + Cyan
    + Blue
    + Magenta
    + Brown


JIDN: a Nikola Theme
============================

When I ran across Hynek Schlawack's `blog`_, I liked the simplistic beauty.
When I took a look at the source, I fell in love.
Here is my homage to beauty, to which I can only inspire.

You can view the demo, where you can change between the different colors, at http://jidn.com/jidn-a-nikola-theme/ and the code at `GitHub`_.

Theme Highlights
-----------------------------

* `Color Themes`_
* `Post Sharing`_
    + Twitter
    + Facebook
    + Google+
* `Author Information`_
    + image
    + email
    + short biography
    + location information
* `Author social accounts`_
    + Twitter
    + Facebook
    + Github
    + StackOverflow
    + Instagram
    + Pinterest
    + and more
* `Easy CSS Override`_
* Based on the `lanyon theme`_

Post Sharing
-----------------------------

What you write is worth reading.
But getting the word out about your post can be hard.
This theme tries to make it easier for your readers to share your posts on Twitter, Facebook, and Google+.
Sharing icons are seen at the end of a post.

Author Information
-----------------------------

Author information is shown at the end of a post as long as the author name associated with the post has a corresponding entry in the configuration.
While Nikola is commonly used with a single author, I figured we should allow for multiple.

First, create a dictionary in the ``GLOBAL_CONTEXT`` of your ``conf.py`` with "JIDN" as the key.
Inside this dictionary, add additional dictionaries, one for each author.
Each of these dictionaries is added to "JIDN" with the author's name as the key.
For additional authors, be sure to use the name as it appears in the post author `metadata`_.
So if the author section doesn't appear in your blog post, closely check that the author's name in ``conf.py`` to that in the post.

Each dictionary for an author can have the following fields.
All of which are optional except for ``image``:

image
    **[Required field]**
    A URL to a 120x120 image of yourself or avatar.
    If you want a different size, you can change to dimensions in the CSS (
    look for ``.author-image``).

email
    This could be BLOG_EMAIL or an alternate authors email address

bio
    A short biography of your self.

map
    A string providing your general or specific location.

.. _`Author social accounts`:

social
    A sequence of your public social accounts you want others to see.
    From the URL I try to match to something in `FontAwsome`_.

Example:

.. code:: python

    GLOBAL_CONTEXT = {
      "JIDN": {BLOG_AUTHOR: {   # Or "Given Surname" for alternate authors
               "image": "http://example.com/my-image.jpg",

               ## The following are all individually optional
               "email": BLOG_EMAIL,  # or something else for alternate authors
               "bio": """I am the very model of a modern, major general.""",
               "map": "Kahlotus, WA  USA",
               "social": (
                   "https://twitter.com/username",
                   "https://facebook.com/username",
                   "https://github.com/username",
                   # You get the idea
                   )
               }
               # Add any needed alternate authors
              }
      ...
    }

Color Themes
-----------------------------

The `lanyon theme`_ was one of my inspirations.
Thus, the JIDN theme supports all the same colored themes.
However, instead of using a hex code to reference them, I use the color name to identify the theme.
Available colors include red, orange, yellow, green, cyan, blue, magenta, and brown.

To the ``GLOBAL_CONTEXT`` in "conf.py", add the key ``"JIDN-theme"`` and the value of ``"theme-base-*color*"``, replacing *color* with one of the available colors.

Example:

.. code:: python

    GLOBAL_CONTEXT = {
        "JIDN-theme": "theme-base-blue",
        ...
        "JIDN": ...
    }

So you don't like any of these color choices and you just have to have electric lime, ``#ccff00``, as your color?
Set ``"JIDN-theme"`` to ``"theme-custom"`` 

.. code:: python

    GLOBAL_CONTEXT = {
        "JIDN-theme": "theme-custom",
        ...
        "JIDN": ...
    }

Copy the following CSS to ``assets/css/custom.css`` and you are ready to hurt your eyes.

.. code:: css

    .theme-custom .sidebar,
    .theme-custom .sidebar-toggle:active,
    .theme-custom #sidebar-checkbox:focus ~ .sidebar-toggle,
    .theme-custom #sidebar-checkbox:checked ~ .sidebar-toggle {
      background-color: #ccff00;
    }
    .theme-custom .container a,
    .theme-custom .sidebar-toggle,
    .theme-custom .related-posts li a:hover {
      color: #ccff00;
    }
    .theme-custom .sidebar-toggle:before {
      background-image: -webkit-linear-gradient(to bottom, #ccff00, #ccff00 20%, #fff 20%, #fff 40%, #ccff00 40%, #ccff00 60%, #fff 60%, #fff 80%, #ccff00 80%, #ccff00 100%);
      background-image:    -moz-linear-gradient(to bottom, #ccff00, #ccff00 20%, #fff 20%, #fff 40%, #ccff00 40%, #ccff00 60%, #fff 60%, #fff 80%, #ccff00 80%, #ccff00 100%);
      background-image:     -ms-linear-gradient(to bottom, #ccff00, #ccff00 20%, #fff 20%, #fff 40%, #ccff00 40%, #ccff00 60%, #fff 60%, #fff 80%, #ccff00 80%, #ccff00 100%);
      background-image:         linear-gradient(to bottom, #ccff00, #ccff00 20%, #fff 20%, #fff 40%, #ccff00 40%, #ccff00 60%, #fff 60%, #fff 80%, #ccff00 80%, #ccff00 100%);
    }
    .theme-custom .sidebar-toggle:active:before,
    .theme-custom #sidebar-checkbox:focus ~ .sidebar-toggle:before,
    .theme-custom #sidebar-checkbox:checked ~ .sidebar-toggle:before {
      background-image: -webkit-linear-gradient(to bottom, #fff, #fff 20%, #ccff00 20%, #ccff00 40%, #fff 40%, #fff 60%, #ccff00 60%, #ccff00 80%, #fff 80%, #fff 100%);
      background-image:    -moz-linear-gradient(to bottom, #fff, #fff 20%, #ccff00 20%, #ccff00 40%, #fff 40%, #fff 60%, #ccff00 60%, #ccff00 80%, #fff 80%, #fff 100%);
      background-image:     -ms-linear-gradient(to bottom, #fff, #fff 20%, #ccff00 20%, #ccff00 40%, #fff 40%, #fff 60%, #ccff00 60%, #ccff00 80%, #fff 80%, #fff 100%);
      background-image:         linear-gradient(to bottom, #fff, #fff 20%, #ccff00 20%, #ccff00 40%, #fff 40%, #fff 60%, #ccff00 60%, #ccff00 80%, #fff 80%, #fff 100%);
    }

Just replace ``#ccffoo`` with the color of your choice.

Easy CSS Override
-----------------------------

Place all of your CSS changes into ``custom.css`` and the theme will load it as your last word on styling.

Fixes
-----------------------------

+ Sidebar is no longer visible when printing.

.. _blog: https://hynek.me/articles
.. _GitHub: https://github.com/jidn/nikola-jidn
.. _lanyon theme: https://themes.getnikola.com/v7/lanyon/
.. _metadata: https://getnikola.com/handbook.html#extra
.. _demo: http://jidn.com/jidn-a-nikola-theme/#Live
.. _FontAwsome: http://fontawesome.io/icons/#brand


