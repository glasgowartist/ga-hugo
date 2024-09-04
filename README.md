Getting Started
===============

1. Create your site as a go module
----------------------------------

hugo mod init <module_name>

2. Create config.toml file and import the ga module
---------------------------------------------------

```toml
languageCode = 'en-GB'
title = 'The name of the artist'

[params]
  description = "Description of the artist"

[imaging]
  quality = "75"
  resampleFilter = "Lanczos"

[[menu.main]]
  name = "Home"
  weight = 1
  identifier = "home"
  url = "/"

[module]
[[module.imports]]
  disable = false
  ignoreConfig = false
  ignoreImports = false
  path = 'github.com/glasgowartist/ga-hugo'

  [[imports.mounts]]
    source = "archetypes"
    target = "archetypes"

  [[imports.mounts]]
    source = "assets"
    target = "assets"

  [[imports.mounts]]
    source = "content"
    target = "content"

  [[imports.mounts]]
    source = "layouts"
    target = "layouts"

  [[imports.mounts]]
    source = "static"
    target = "static"
```
4. Build the site
------------------

Run `hugo npm mod pack` to generate `package.json` and run `npm install`.

Run `hugo`.

5. Customize the index and about pages
--------------------------------------

Add `layouts/index.html` and `content/about/_index.html`.

6. Add images and galleries
---------------------------

- Create galleries/_index.md with front matter for menu
- Copy images to `assets/images`.
- Create `data/artworks.toml` database describing the images, e.g.

```toml
[[artworks]]
id = "42"
img = "01_immer_uberall-1.jpg"
title = "immer, überall 1"
year = 2009
dim = "47/67"
media = "Heliogravure überarbeitet"
[[artworks]]
id = "43"
...
```
- Add gallery files (front matter only) to content/galleries.

Gallery format should be

```toml
+++
title = "Gallery name"
date = 2004-01-01
blurb = "Some text about the gallery"
artworks = [42,43]
layout = "photoswipe"
+++

The artworks in each gallery should each correspond to an id in the `artworks.toml` file.

