<style>
  .codehilite { margin: 12px 46px; .background-color: unset; }
  pre {padding: 12px;}
  li {margin: 6px;}
  #quick-links > ul {list-style: none; padding-left: 1rem;}
  #quick-links li {margin: 0;}
  #quick-links li > p {margin: 6px 0 3px 0;}
  .section1 {padding: 0 18px;}
</style>
  
.ve-meta title="Juncture Documentation"

.ve-header Documentation background=#5B152E logo=https://raw.githubusercontent.com/visual-essays/media/main/images/Juncture_Logo.png url=/ sticky

# Juncture Help {#top}

### Quick links {#quick-links}

- **[Juncture Quick Start](#quick-start)**

- **[Viewer Tags](#viewer-tags)**
    - [.ve-header](#ve-header)
    - [.ve-image](#ve-image)
    - [.ve-image-grid](#ve-image-grid)
    - [.ve-meta](#ve-meta)
    - [.ve-style](#ve-style)

- **[How To's](#how-tos)**
    - [Marking text for interactions](#marking-text)
    - [Creating a **zoom to** interaction](#zoom-to)

- **[Tools](#tools)**
    - [Editor](#editor)
    - [Media tool](#media-tool)
    - [Annotator](#annotator)

- **[Useful Background](#background)**
    - [Juncture Architecture](#juncture-architecture)
    - [Github](#github)
    - [IIIF](#iiif)
    - [Self-hosted Media Collections](#self-hosted-media)
    - [Wikidata](#wikidata)

- **[Hosting Options](#hosting)**
    - [Github Pages](#github-pages)
    - [Custom Domain](#custom-domain)

- **[Resources](#resources)**
    - [Finding IIIF Images](#finding-iiif)

# Juncture Quick Start {#quick-start}

## Sign-up for a Github account

In this version of Juncture a Github account must be used for storing and managing content files.  At its core Github is a free Internet hosting service commonly used for software development projects.  It provides sophisticated features for version control and workflow management for distributed teams.  

For Juncture we primarly use Github as a file hosting service, similar to how one might use Dropbox or Google Drive.  While Juncture is able to use some of the more advanced Github features (like website hosting) the primary use is for storing visual essay text files.  Github content is organized into one or more repositories.  Users unfamiliar with Github can think of a repository a workspace, or a collection of folders.  Github allows the creation and use of multiple repositories.

Juncture users have the option of manually creating and updating essay source files in Github or using the Juncture editor.  When using the Juncture editor a user will not need to interact with the Github site directly as the Juncture editor will handle essay file creation and updates.  

All that Juncture requires is read access to the Github repository storing the visual essay files.

## Create a Github repository to store essay source files

After a new Github account has been established, a Github repository must be created to manage the essay text files.  For existing accounts any repository may be used or one may be optionally created for Juncture essay files.  By default Juncture looks for a repository named `essays` when first launching the editor but any repository may be selected.  Juncture essays may be created in multiple repositories.  When using the Juncture editor it will create an `essays` repository if a repository has not yet been created for a new Github account. 

## Log in to Github from Juncture (optional)

Logging into Github from Juncture authorizes Juncture to update your Github repository from the Juncture Editor tool.  Note that this is an optional step as Github files may be edited directly in the Github web interface or by using any number of client applications running on your local computer.  This quick start guide assumes the Juncture Editor is used.

## Create your first Visual Essay

Select the `Editor` option from the Juncture Editor.

# [⇧](#top) Viewer Tags {#viewer-tags}

Custom tags are added to essay text to define viewers that are inserted into the generated page.  Each viewer tag includes a **.ve-** prefix and must appear at the beginning of a new line.  Viewer tags accept one or more positional and/or key-value attributes.  

- A `positional attribute` is a text string that follows the tag.  Some viewers can accept multiple positional attributes, in which case the ordering is important.
- `Key-value attributes` take the form of `<KEY>`=`<VALUE>`, explicitly defining the attribute name and value.  Key-value attributes must follow any positional arguments used.  For both positional and key-value attributes a value with a space must be enclosed in quotes.  
- Key-value attributes that use a value of "_true_" or "_false_" are also known as `boolean attributes`.  Boolean attributes may be specified with the attribute name only or as a key-value attribute with a _true_ or _false_ value.  When the attribute is present without the value the attribute value resolves to _true_, otherwise it is assumed to be _false_.

## [⇧](#top) .ve-header {#ve-header}

The `.ve-header` tag is used to define an optional header that appears at the start of the essay.  The header can be used to:

- Define a title and subtitle for the essay
- Display a banner image
- Create a navigation menu for linking to sections within the current essay, to other essays, or to arbitrary web pages

As with the images displayed by the `.ve-image` tag, the banner image used by the `.ve-header` tag is a IIIF image and can be cropped or otherwise manipulated when displayed in the header.

### .ve-header Attributes

- `label` (_text string_):  The text to use for the essay title. 
- `subtitle` (_text string_):  The text to use for the essay subtitle.
- `height` (_height in pixels_):  The height of the header (before collapsing when in _sticky_ mode).
- `background` (_IIIF manifest URL_):  The URL to the IIIF manifest for the image to display as a banner image in the header.
- `logo` (_logo image URL_): A URL to a logo image.
- `url` (_URL associated with logo image_):  The URL that is invoked when the logo image is clicked.
- `options` (_IIIF image options_):  The _options_ attribute is used to define the [IIIF image request parameters](https://iiif.io/api/image/2.1/#image-request-parameters) for an image.  This attribute is most commonly used to define a coordinates for displaying an image region.   
- `position` ("_top_", "_center_" or "_bottom_"):  The portion of a cropped banner image to display.  The default is _center_.  Other recognized values are _top_ and _bottom_.
- `sticky` ("_true_" or "_false_"):  If set to "_true_" the header will collapse into a condensed form and remain fixed at the top of the page.

### Examples

- A sticky header defined with positional attributes and navigation menu options in a nested Markdown list.
```Markdown
.ve-header "My Essay Title" wc:Zelfportret_met_strohoed_-_s0164V1962_-_Van_Gogh_Museum.jpg "A Subtitle" pct:3,23,80,20 center true
    - [Home](/)
    - [About](/about)
```

## [⇧](#top) .ve-image {#ve-image}

The `.ve-image` tag is the most commonly used essay tag.  The tag creates an IIIF image viewer that is able to display one or more images.

### .ve-image Attributes

- `alt` (_text string_):  The text to use in the _alt_ tag used by screen readers.  If not provided an _alt_ tag is automatically generated from the manifest label property.\
- `compare` ("_true_" or "_false_"):  The _compare_ attribute is used in multi-image mode to compare 2 or 3 images.  When not combined with either the _curtain_ or _sync_ attribute the default compare mode is invoked.  In the default mode comparisons are limited to 2 images.   2 or 3 images may be compared when _curtain_ or _sync_ attributes are included.  In the default mode the 2 images are stacked (one is overlaid on the other) and a slider is used to show or hide portions of the bottom image.  The compared images cannot be zoomed or panned but one or both may  be cropped to align the images for comparison.
- `curtain` ("_true_" or "_false_"):  The _curtain_ attribute is used in combination with the _compare_ attribute.  When comparing images in _curtain_ mode up to 3 images may be compared and deep zoom and panning is enabled.  Image cropping is currently not supported in _curtain_ mode.
- `fit` ("_cover_" or "_contain_"):  The _fit_ attribute controls the display of an image in the viewer viewport.  In the default mode (_contain_) the entire image is show with letter-boxing applied to the top and bottom or left and right when the image aspect ratio differs from the viewers.  When the value _cover_ is used the entire viewport is filled and the displayed portion of the image is cropped as needed to fit.
- `full` ("_true_" or "_false_"):  Use the fill width of browser viewport for the image.  Scale the image height proportional to the source image.  By default the image will be auto-sized such that its height is not more than 40% of the viewport height.
- `grid` ("_true_" or "_false_"):  Displays multiple images in a responsive grid. When clicked the images will create a popup window with full deep zoom and panning enabled. 
- `left` ("_true_" or "_false_"):  Position the image in the left half of the viewport and scale the width proportionally.  Text will wrap around the image unless the _sticky_ attribute is included.
- `options` (_IIIF image options_):  The _options_ attribute is used to define the [IIIF image request parameters](https://iiif.io/api/image/2.1/#image-request-parameters) for an image.  This attribute is most commonly used to define a coordinates for displaying an image region.    
- `right` ("_true_" or "_false_"):  Position the image in the right half of the viewport and scale the width proportionally. Text will wrap around the image unless the _sticky_ attribute is included.
- `seq` (_image sequence number_):  A number defining the image to use in a multi-image manifest.  If not specified the default value is _1_.
- `src` (_IIIF image manifest URL_) :  The URL to the IIIF manifest for the image to display in the viewer.  This attribute is omitted when multiple using the viewer in multi-image mode.  This attribute may also be omitted in single image mode when QIDs are in scope.  When a _src_ attribute is not specified the most relevant (closest) QID to the tag is used to generate an IIIF manifest URL.  More information on QID use can be found in the [Wikidata](#wikidata) section.
- `sticky` ("_true_" or "_false_"):  The _sticky_ attribute causes the image viewer to "stick" to the top of the viewing area when the essay text is scrolled.  The viewer will stick in position until all content in the enclosing section has scrolled through the viewing area.
- `sync` ("_true_" or "_false_"):  The _sync_ attribute is used in combination with the _compare_ attribute.  When comparing images in _sync_ mode up to 3 images may be compared and deep zoom and panning is enabled.  Image cropping is currently not supported in _sync_ mode. In _sync_ mode the images to compare are displayed side-by-side with zoom and panning actions applied to each simultaneously.
- `width` (_requested viewer width in pixels or as a percentage of viewing area width_):  A requested size for the image viewer window.
- `zoom-on-scroll` ("_true_" or "_false_"):  Specifies whether the image viewer will zoom the image when a scroll gesture is performed in the image viewer.  This is inhibited by default.

### Multiple images mode

To use more than one image with a `.ve-image` viewer the Markdown nested list notation is used.  A Markdown list is defined by prefixing the `    - ` text to each list element on separate lines.   Each list element can include positional and/or key-value attributes for the associated image.

### Manifest URLs

The manifest URL is a URL to an IIIF presentation manifest that is compliant to version 2.x or version 3.0 of the IIIF Presentation Standard.

When referring to a manifest automatically generated by Juncture a short-form version of the auto-generated URL may be used.  The short-form version takes the form of `<SOURCE>:<SOURCE_ID>`, where `<SOURCE>` is the a site code for one of the image hosting sites supporting manifest generation by Juncture.  The `<SOURCE_ID>` value is a unique resource ID applicable to the site.  For example, Juncture is able to automatically generate IIIF manifests for images hosted on [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page).  A full auto-generated manifest for the image at [https://commons.wikimedia.org/wiki/File:Sunflower.jpg](https://commons.wikimedia.org/wiki/File:Sunflower.jpg){target=_blank} would be [https://iiif.juncture-digital.org/wc:Sunflow.jpg/manifest.json](https://iiif.juncture-digital.org/wc:Sunflow.jpg/manifest.json).  The short form version of this URL (**wc:Sunflower.jpg**) can be used with any Juncture tag (.ve-image, .ve-header, .ve-image-grid, and others) that accept IIIF manifest attributes.

### Examples

- Using a Wikimedia Commons image using the short-form version of the manifest URL and an `alt` attribute.
```Markdown
.ve-image wc:Sunflower.jpg alt="Sunflowers in a field"
```

- Using a JSTOR Community Collections image using the short-form version of the manifest URL and `options` as positional attributes.
```Markdown
.ve-image jstor:community.24604882 pct:35,42,10,25
```

- Above example using key-value attributes rather than positional.
```Markdown
.ve-image src=jstor:community.24604882 options=pct:35,42,10,25
```

- Using a full manifest URL.
```Markdown
.ve-image https://iiif.harvardartmuseums.org/manifests/object/299843
```

- Using multiple images:
```Markdown
.ve-image
    - wc:Sunflower.jpg
    - jstor:community.24604882
```

## [⇧](#top) .ve-meta {#ve-meta}

The `.ve-meta` tag is used to define metadata attributes for the page.  Defining _.ve-meta_ tag in an essay enables the rendered essay to be indexed by search engines.  When the tag is not found in an essay a _noindex_ tag is added to the generated page by default.

### .ve-meta Attributes

- `title` (_text string_):  A short title for the page.  This title will be added to the browser window or tab.  When indexed by search engines this title will also appear in the search results item.   
- `description` (_text string_):  A short description of the page.  When indexed by search engines this description will appear in the search results item. 

###  Example

```Markdown
.ve-meta title="The Page Title" description="A brief description of the page. This will appear in Google search results."
```

## [⇧](#top) .ve-style {#ve-style}

The `.ve-style` tag is used to replace the default stylesheet with a custom one loaded from the URL defined in the tags `href` attribute.

###  Example

```Markdown
.ve-style href=https://www.example.com/my/custom/stylesheet.css
```

# [⇧](#top) How To's {#how-tos}

## [⇧](#top) Marking Text {#marking-text}

Essay text is "marked" by surrounding the applicable text with double equal signs (`==`) followed by an element attributes definition with the action to be performed.  Element attributes are defined by text enclosed with `{` and `}` characters.  For example:

```Markdown
Lorem ipsum ==dolor=={100,100,400,400} sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam
```

In the example above the text `dolor` is marked and associated with the attribute `100,100,400,400`.  This has the effect of highlighting the `dolor` text in the rendered essay and creating a `zoom to` interaction when the text is selected (clicked or tapped).  The `zoom to` interaction causes the closest image zoom to the region specified by the coordinates in the  attribute.  More information about the `zoom to` interaction, including how to define the coordinates, is provided below.

## [⇧](#top) Zoom To {#zoom-to}

TODO


# [⇧](#top) Tools {#tools}

## [⇧](#top) Editor {#editor}

## [⇧](#top) Media Tool {#media-tool}

## [⇧](#top) Annotator {#annotator}


# [⇧](#top) Useful Background {#background}

## [⇧](#top) Juncture Architecture {#juncture-architecture}

## [⇧](#top) Github {#github}

## [⇧](#top) IIIF {#iiif}

## [⇧](#top) Self-Hosted Media Collections {#self-hosted-media}

## [⇧](#top) Wikidata {#wikidata}


# [⇧](#top) Hosting Options {#hosting}

## [⇧](#top) Github Pages {#github-pages}

## [⇧](#top) Custom Domain {#custom-domain}


# [⇧](#top) Resources {#resources}

## [⇧](#top) Finding IIIF Images {#finding-iiif}