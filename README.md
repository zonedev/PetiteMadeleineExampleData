# petite madeleine example data

This repository contains exemplary data for use with petite madeleine clients. All metadata is specified as [Property Lists](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html).

All references to other files (media as well as other Property Lists) are absolute URLs. Therefore all URLs speficied in the example Property Lists will need to be replaced with correct references to the actual location on your server.

## master list

Lists all available **issues** to the system as well as the `default_issue` which is selected on startup. The URL of this file needs to be passed to the `PetiteMadeleineCore` constructor.

## issues

An **issue** represents a printed publication. Its structure is as follows:

The `config` dictionary speficies an ID (e.g. API Key) for the image recognition service as `dataset`.

petite madeleine supports serving of different content depending on the language settings of the client. Therefore content for each supported language is referenced by a lowercase country code.

This localized content description contains the issues `name` and the `entries` dictionary which lists the content mapped to a specific image. The response from the image recogniton service for a match of the desired image is used as the key to the corresponding **entry**.

Each **entry** contains a `description` and one or more dictionaries representing attached **media**. The type of **media** is speficied by the dictionaries key. Supported keys are:

* `media` - currently only used for videos.
* `slideshow` - displays slideshow.
* `text` - used for the display of PDF files.
* `youtube` - launches YouTube App with provided url.
* `website` - launches browser with provided url.
* `safari` - launches mobile safari instead of internal browser on iOS. On Android this is synonymous with `website`

Because each **media** dictionary still needs an unique key multiple **media** entries of the same type can be suffixed like this:

* `media - 1`
* `media - 2`
* `media - 3`
* `media - 4`

Each **media** dictionary contains a `description` of the linked media as well as an `url` the linked file (in case of the slideshow another Property List)

## slideshow

Each image in a slideshow is represented as a dictionary containing:

* `name` - name/description of the image
* `url` - URL of the full resolution image
* `thumbnail` - URL of low resolution thumbnail 