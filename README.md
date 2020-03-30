# Photo Stream

A theme to showcase your photo albums, powered by [Hugo](https://gohugo.io).
A live demo is available [at photo-stream.netlify.com](https://photo-stream.netlify.com/).

## Features

This theme is basically a port of [maxvoltar's photo-stream theme](https://github.com/maxvoltar/photo-stream).
Thanks to him for this nice creation!

This theme features:

* Lazy loading of photos (a photo is downloaded when it appears in the viewport)
* Albums containing photos
* Photos thumbnail are resized to fit 800x800
* The large version is resized to fit 2048x2048
* The background is filled with a tint matching the photo
* Keyboard shortcuts for previous / next / back to list

## Installation

You can install the theme either as a clone or submodule.

I recommend the latter. From the root of your Hugo site, type the following:

```sh
git submodule add https://github.com/nmasse-itix/photo-stream.git themes/photo-stream
git submodule init
git submodule update
```

Now you can get updates of this theme in the future by updating the submodule:

```sh
git submodule update --remote themes/photo-stream
```

## Configuration

After installation, take a look at the `exampleSite` folder inside `themes/photo-stream`.

To get started, copy the `config.toml` file inside `exampleSite` to the root of your Hugo site:

```sh
cp themes/photo-stream/exampleSite/config.toml .
```

Now edit this file and add your own information. Note that some fields can be omitted.

## Demo Website

A live demo is available [at photo-stream.netlify.com](https://photo-stream.netlify.com/) but you can have a look by yourself at the example site.

```sh
cd themes/photo-stream
./fetch-photos.sh
hugo serve
```

## How to create an album

The theme provides an **archetype** named `album`.
Create a new album with the `hugo new` command.

```sh
hugo new my-album/index.md -k album
```

## How to add photos

To add photos to an album, simply copy your JPEG files in the album directory, **under content, NOT static!**

```sh
cp path/to/DCIM_*.jpeg content/my-album/
```

## How to customize an album

A minimal `index.md` looks like this:

```yaml
---
date: "2016-01-01"
title: Animals
- src: '**.jpeg'
---
```

This index file defines an album with a date, a title and instructs to add all JPEG files to the album.

But a usual `index.md` would include more customization:

```yaml
---
date: "2016-01-01"
title: Animals
sort_by: "Exif.Date"
resources:
- src: 'camel.jpeg'
  params:
    cover: true
- src: '**.jpeg'
- src: '**.jpg'
---
```

This index also specifies:

* To sort photos by date (specified in the EXIF metadata).
* To also include files with `.jpg` extension.
* To set `camel.jpeg` as the cover photo for the album.

## Global configuration

The Date format for the album can be set in your `config.toml`.

```toml
[params]
album_date_format = "01/2006"
```

Check the Go documentation for possible formats: [time.Format](https://golang.org/pkg/time/#Time.Format).
