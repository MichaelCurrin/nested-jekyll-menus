# Nested Jekyll Menus
> Demo of how to generate Jekyll menus dynamically based on project structure

[![GitHub tag](https://img.shields.io/github/tag/MichaelCurrin/nested-jekyll-menus)](https://github.com/MichaelCurrin/nested-jekyll-menus/tags/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue)](#license)

[![Made with Jekyll](https://img.shields.io/badge/Made_with-Jekyll-blue.svg)](https://jekyllrb.com)

[![View site GH Pages](https://img.shields.io/badge/Github_Pages-Demo_site-green?style=for-the-badge)](https://MichaelCurrin.github.io/nested-jekyll-menus/)

The easy way to nest content in your Jekyll site and have menus auto-generate for you at each level.

Create directories and content pages in you Jekyll site using _any_ number of nested levels and an `index.md` file at each level. Then use the logic in the project to iterate over all pages and filter to just the pages and directories at the current level. This handled in two includes files which can be adapted to build a menu for Jekyll site.


## Sample

### Site preview

This is the homepage of this demo site - it has minimal styling.

<div align="center">
    <img src="/docs/_media/homepage.png" alt="homepage" width="400px"/>
</div>

One page doesn't really showcase the functionality of this project, so keep reading to see how this works.

### Structure

In this repo, we have the following file which is nested in a few levels of directories:

- [/animals/reptiles/snakes/rattlesnake.md](/animals/reptiles/snakes/rattlesnake.md)

The repo structure is like this. Note that the `index.md` pages are necessary to build the menu at each level.

- Sample
    ```
    animals/
        reptiles/
            snakes/
                rattlesnake.md
                index.md
            index.md
        index.md
    index.md
    ```

On the frontend, the rendered page has these breadcrumbs displayed:

<div align="center">
    <img src="/docs/_media/breadcrumbs.png" alt="breadcrumbs" width="400px"/>
</div>

Using this project, it is easy to navigate from the Homepage to that nested page using menus which are generated **dynamically** at each level. So that if you move/rename/delete a page or directory, your menus will be rebuilt to match that new setup.

See the navigation steps below.

### Level 1 - Home

Path: `/`

The Homepage knows about [animals](/animals/) and [food](/food/) directories at the top-level.

<div align="center">
    <img src="/docs/_media/home.png" alt="home" width="150px"/>
</div>

### Level 2 - Animals

Path: `/animals/`

Go into the Animals section and you'll see a listing of pages about animals and then sections (directories) to explore deeper.

<div align="center">
    <img src="/docs/_media/animals.png" alt="animals" width="300px"/>
</div>

### Level 3 - Reptiles

Path: `/animals/reptiles`

If you go in Reptiles, you see types of reptiles.

<div align="center">
    <img src="/docs/_media/reptiles.png" alt="reptiles" width="150px"/>
</div>

### Level 4 - Snakes

Path: `/animals/reptiles/snakes/`

Within Snakes, you can see these pages.

<div align="center">
    <img src="/docs/_media/snakes.png" alt="snakes" width="200px"/>
</div>

### Level 5 - Rattlesnake

Path: `/animals/reptiles/snakes/rattlesnake.html`

Follow the the Rattlesnake page and you'll end up at this page, which is the final level.

<div align="center">
    <img src="/docs/_media/rattlesnake.png" alt="rattlesnake" width="300px"/>
</div>


## How this project works

Understand how this project works then you can apply the pattern to your own project.

### List files

See the `list-` files in the [\_includes](/_includes/) directory. This is the main part of this project.

Those files are in the [listing](/_layouts/listing.html) layout file, to give the page some form and headings.

Use this project directly by forking it and setting it up yourself. Or copy any list and layout files that you need.

### Project structure

The only requirement for this pattern to build the directory structure is that there must be an `index.md` page at each level which has frontmatter that includes a page title.

Example of structure, relative to repo root:

- Minimal
    ```
    directory-1/
        index.md
    index.md
    ```
- Pages nested one level down
    ```
    directory-1/
        file-a.md
        file-b.md
        ...
        index.md
        ...
        file-z.md
    index.md
    ```
- Directory nested in a directory:
    ```
    directory-1/
        directory-2/
            file-a.md
            file-b.md
            ...
            index.md
            ...
            file-z.md
        file-a.md
        file-b.md
        ...
        index.md
        ...
        file-z.md
    index.md
    ```

Note that the nesting levels do not have to be equal - you can have some paths which are shallow and some which are deep. If you decide that a page needs multiple pages, you can split just that page into a directory of multiple pages.

On the `index.md` page at each level needs to have a menu on it from the `listing` layout. The other pages can have just a `page` layout. 

Examples:

- `directory-1/index.md`
    ```yaml
    ---
    title: Directory 1
    layout: listing
    ---
    ```
- `directory-1/file-a.md`
    ```yaml
    ---
    title: File A
    ---
    ```

Note: Avoiding setting the `listing` layout as a _default_ layout in the config - this causes memory issues and therefore a slow build on larger projects, due to looking for the `index.md` pages at multiple levels. Rather set the layout on eac file as above. 


## About

This approach here makes it easy to add and rename pages in a site without having to update a config file, as the menu is generated _automatically_ based on your content. This is especially when there are nested levels and each level has a few files and folders.

The approach show the looks for pages and sections (directories) at the current level and adds those to a menu.

Note that a limitation of the approach here is that the order is assumed to be alphabetical rather than manually ordered, but that okay.

It is recommended to add _breadcrumbs_ trail to your pages to help the user see where they are in the nested structure. See the [breadcrumbs.html](/_includes/breadcrumbs.html) includes file which is used here.

This project used the [Unsplash API](https://github.com/MichaelCurrin/learn-to-code/blob/master/en/topics/web_dev/HTML/stock_images.md) to search for and embed images, to make this project more fun.


## Other approaches

While the Minima Jekyll theme handles pulling pages into a navbar automatically, the idea here is that there are _nested_ pages such as a collection and those need to appear in a nested navbar or in a table of contents menu which is appropriate for the current level.

Another approach would be to generate a menu as a config file. Or to generate a table of contents of the entire site - which can work in a nested navbar or a sidebar. But it can get overwhelming if there are many levels.

If you don't want to use the alphabetical auto-generated menus, you can make your own like this:

```markdown
- [Foo]({% link foo/index.md %})
- [Bar]({% link bar/index.md %})
    - [Baz]({% link bar/baz.md %})
```


## Documentation

To setup and run this project locally or on Github Pages, see the [docs](/docs/#readme).


## License

Released under [MIT](/LICENSE).

Please back to this repo if you use a portion of it. Also include a copy of the original license.

Stock images provided from the [unsplash.com](https://unsplash.com/) Source API.

Breadcrumbs file is based on:

- https://jekyllcodex.org/without-plugin/breadcrumbs/
