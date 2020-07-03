# Nested Jekyll Menus
> Demo of how to auto-generate Jekyll menus dynamically based on project structure


## About

This approach here makes it easy to add and rename pages in a site without having to update a config file, as the menu is generated _automatically_ based on your content. This is especially when there are nested levels and each level has a few files and folders.

The approach show the looks for pages and sections (directories) at the current level and adds those to a menu. See [listing](/_layouts/listing.html) layout.

Note that a limitation of the approach here is that the order is assumed to be alphabetical rather than manually ordered, but that okay.

It is recommended to add _breadcrumbs_ trail to your pages to help the user see where they are in the nested structure. This is not handled in this repo.

## Other approaches

While the Minima Jekyll theme handles pulling pages into a navbar automatically, the idea here is that there are _nested_ pages such as a collection and those need to appear in a nested navbar or in a table of contents menu which is appropriate for the current level.

Another approach would be to generate a menu as a config file. Or to generate a table of contents of the entire site - which can work in a nested navbar or a sidebar. But it can get overwhelming if there are many levels.


## License

Released under [MIT](/LICENSE).

Please back to this repo if you use a portion of it. Also include a copy of the original license.
