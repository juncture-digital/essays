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

- **[Juncture Getting Started Guide](getting-started)**

- **[Viewer Tags](#viewer-tags)**
    - [.ve-header](#ve-header)
    - [.ve-map](#ve-map)
    - [.ve-media](#ve-media)

- **[Other Tags](#other=tags)**
    - [.ve-meta](#ve-meta)
    - [.ve-style](#ve-style)

- **[Layout](#layout)**
    - [Viewer Component Positioning](#positioning)

- **[How To's](#how-tos)**
    - [Marking text for interactions](#marking-text)
        - [Creating a **zoom to** interaction](#zoom-to)
        - [Creating a **play at** interaction](#play-at)
        - [Creating an **entity info popup** interaction](#entity-popup)

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

- **label** (_text string_):  The text to use for the essay title. 
- **subtitle** (_text string_):  The text to use for the essay subtitle.
- **height** (_height in pixels_):  The height of the header (before collapsing when in _sticky_ mode).
- **background** (_IIIF manifest URL_):  The URL to the IIIF manifest for the image to display as a banner image in the header.
- **logo** (_logo image URL_): A URL to a logo image.
- **url** (_URL associated with logo image_):  The URL that is invoked when the logo image is clicked.
- **options** (_IIIF image options_):  The _options_ attribute is used to define the [IIIF image request parameters](https://iiif.io/api/image/2.1/#image-request-parameters) for an image.  This attribute is most commonly used to define a coordinates for displaying an image region.   
- **position** ("_top_", "_center_" or "_bottom_"):  The portion of a cropped banner image to display.  The default is _center_.  Other recognized values are _top_ and _bottom_.
- **sticky** ("_true_" or "_false_"):  If set to "_true_" the header will collapse into a condensed form and remain fixed at the top of the page.

### Examples

- A sticky header defined with positional attributes and navigation menu options in a nested Markdown list.
```Markdown
.ve-header "My Essay Title" wc:Zelfportret_met_strohoed_-_s0164V1962_-_Van_Gogh_Museum.jpg "A Subtitle" pct:3,23,80,20 center true
    - [Home](/)
    - [About](/about)
```

## [⇧](#top) .ve-map {#ve-map}

The `.ve-map` tag creates a map viewer that displays a base map with optional map layers.  The map supports zooming and panning.

### .ve-map Attributes
| Syntax | Type                                   | Description                                                         |
|--------|----------------------------------------|---------------------------------------------------------------------|
| center | Geographic Coordinates or Wikidata QID | The _center_ attribute defines the center point of a displayed map. |
| zoom   | Number                                 | The _zoom_ attribute defines the zoom level of a displayed map.     |

- **center** (_Geographic Coordinates_ or _Wikidata QID_):  The _center_ attribute defines the center point of a displayed map.
- **zoom** (_number_):  The _zoom_ attribute defines the zoom level of a displayed map.

## [⇧](#top) .ve-media {#ve-media}

The `.ve-media` tag is the most commonly used essay tag.  The tag creates an IIIF viewer that is able to display images, video, and audio.  The _.ve-media_ viewer encapsulates the [Mirador](https://projectmirador.org/) ==IIIF=={Q22682088} viewer.

### .ve-media Attributes

- **alt** (_text string_):  The text to use in the _alt_ tag used by screen readers.  If not provided an _alt_ tag is automatically generated from the manifest label property.
- **compare** ("_true_" or "_false_"):  The _compare_ attribute is used compare 2 images.  In compare mode the 2 images are stacked (one is overlaid on the other) and a slider is used to show or hide portions of the bottom image.  The compared images cannot be zoomed or panned but one or both may  be cropped to align the images for comparison.
- **fit** ("_cover_" or "_contain_"):  The _fit_ attribute controls the display of an image in the viewer viewport.  In the default mode (_contain_) the entire image is shown with letter-boxing applied to the top and bottom or left and right when the image aspect ratio differs from the viewers.  When the value _cover_ is used the entire viewport is filled and the displayed portion of the image is cropped as needed to fit.
- **full** ("_true_" or "_false_"):  Use the fill width of browser viewport for the image.  Scale the image height proportional to the source image.  By default the image will be auto-sized such that its height is not more than 40% of the viewport height.
- **grid** ("_true_" or "_false_"):  Displays multiple images in a responsive grid. When clicked the images will create a popup window with full deep zoom and panning enabled. 
- **height** (_requested viewer height in pixels or as a percentage of viewing area width_):  A requested size for the  viewer height.  The default behavior is to use the full width of the available window and scale the viewer height to retain the aspect ratio of the source item (image or video).
- **left** ("_true_" or "_false_"):  Position the viewer in the left half of the viewport and scale the width proportionally.  Text will wrap around the viewer unless the _sticky_ attribute is included.
- **manifest** (_IIIF manifest URL_) :  The URL to the IIIF manifest for the item to display in the viewer.  This attribute is omitted when multiple using the viewer in multi-image mode.  This attribute may also be omitted in single image mode when QIDs are in scope.  When a _manifest_ attribute is not specified the most relevant (closest) QID to the tag is used to generate an IIIF manifest URL.  More information on QID use can be found in the [Wikidata](#wikidata) section.
- **options** (_IIIF image options_):  The _options_ attribute is used to define the [IIIF image request parameters](https://iiif.io/api/image/2.1/#image-request-parameters) for an image.  This attribute is most commonly used to define a coordinates for displaying an image region.    
- **right** ("_true_" or "_false_"):  Position the viewer in the right half of the viewport and scale the width proportionally. Text will wrap around the viewer unless the _sticky_ attribute is included.
- **seq** (_image sequence number_):  A number defining the image to use in a multi-image manifest.  If not specified the default value is _1_.
- **sticky** ("_true_" or "_false_"):  The _sticky_ attribute causes the viewer to "stick" to the top of the viewing area when the essay text is scrolled.  The viewer will stick in position until all content in the enclosing section has scrolled through the viewing area.
- **width** (_requested viewer width in pixels or as a percentage of viewing area width_):  A requested size for the  viewer width.  The default behavior is to use the full width of the available window.
- **zoom-on-scroll** ("_true_" or "_false_"):  Specifies whether the viewer will zoom the image when a scroll gesture is performed in the image viewer.  This is inhibited by default.

### Multiple images mode

To use more than one image with a `.ve-media` tag the Markdown nested list notation is used.  A Markdown list is defined by prefixing the `    - ` text to each list element on separate lines.   Each list element can include positional and/or key-value attributes for the associated image.

### Manifest URLs

The manifest URL is a URL to an IIIF presentation manifest that is compliant to version 2.x or version 3.0 of the IIIF Presentation Standard.

When referring to a manifest automatically generated by Juncture a short-form version of the auto-generated URL may be used.  The short-form version takes the form of `<SOURCE>:<SOURCE_ID>`, where `<SOURCE>` is the a site code for one of the hosting sites supporting manifest generation by Juncture.  The `<SOURCE_ID>` value is a unique resource ID applicable to the site.  For example, Juncture is able to automatically generate IIIF manifests for images and other media hosted on [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page).  A full auto-generated manifest for the image at [https://commons.wikimedia.org/wiki/File:Sunflower.jpg](https://commons.wikimedia.org/wiki/File:Sunflower.jpg){target=_blank} would be [https://iiif.juncture-digital.org/wc:Sunflow.jpg/manifest.json](https://iiif.juncture-digital.org/wc:Sunflow.jpg/manifest.json).  The short form version of this URL (**wc:Sunflower.jpg**) can be used with any Juncture tag (.ve-media, .ve-header, and others) that accept IIIF manifest attributes.

### Examples

- Using a Wikimedia Commons image using the short-form version of the manifest URL and an `alt` attribute.
```Markdown
.ve-media wc:Sunflower.jpg alt="Sunflowers in a field"
```

- Using a JSTOR Community Collections image using the short-form version of the manifest URL and `options` as positional attributes.
```Markdown
.ve-media jstor:community.24604882 pct:35,42,10,25
```

- Above example using key-value attributes rather than positional.
```Markdown
.ve-media src=jstor:community.24604882 options=pct:35,42,10,25
```

- Using a full manifest URL.
```Markdown
.ve-media https://iiif.harvardartmuseums.org/manifests/object/299843
```

- Using multiple images:
```Markdown
.ve-media
    - wc:Sunflower.jpg
    - jstor:community.24604882
```

# [⇧](#top) Other Tags {#other-tags}

## [⇧](#top) .ve-meta {#ve-meta}

The `.ve-meta` tag is used to define metadata attributes for the page.  Defining _.ve-meta_ tag in an essay enables the rendered essay to be indexed by search engines.  When the tag is not found in an essay a _noindex_ tag is added to the generated page by default.

### .ve-meta Attributes

- **title** (_text string_):  A short title for the page.  This title will be added to the browser window or tab.  When indexed by search engines this title will also appear in the search results item.   
- **description** (_text string_):  A short description of the page.  When indexed by search engines this description will appear in the search results item. 

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

# [⇧](#top) Layout {#layout}

## [⇧](#top) Viewer Component Positioning {#positioning}

This section provides information for positioning viewer components (including _.ve-media_, ._ve-video_, and _.ve-map_) in an essay in a non-mobile layout.

### Full Width

When adding a viewer component (such as _.ve-media_) to an essay, the default behavior is to position the  component in a new vertical section at the place where the component tag is defined.  The component will be sized to take the full width of the essay/.  The height for images and videos is scaled to retain the aspect ratio of the source item.  For other items, such as maps and diagrams, the height will equal the component width, both in full width and column (left or right) positioning. 

### Left or Right

An alternative to the default full-widtth positioning is to position the component in either the left or right half of the essay.  This is accomplished by adding a `left` or `right` attribute to the viewer tag, for example:

```Markdown
.ve-media wc:Sunflower.jpg right
```

When positioning a component in the left or right portion of the essay, any text following the component tag in the same section will wrap around the component unless the `sticky` attribute is included.

### Custom Width and/or Height

In both the full width and left/right column modes the width and height of a component can be explicitly set by adding `height` and/or `width` attributes.  The value of the height and width attribute may be defined in absolute pixels or as a percentage of the essay width, for example:

```Markdown
.ve-media wc:Sunflower.jpg width=80%
```

or

```Markdown
.ve-media wc:Sunflower.jpg width=800px
```

When setting only the width or the height on a _.ve-media_ or _.ve-video_ component the non-specified dimension will be calculated to retain the aspect ratio of the source item.  

If both a width and height is set on an image (using the _.ve-media_ component) and the resulting aspect ratio is different than the original items, the image `fit` will be set to `cover` unless exlicitly set to `contain`.

The `fit` attribute controls the display of an image in the viewer viewport. In the default mode (_contain_) the entire image is shown with letter-boxing applied to the top and bottom or left and right when the image aspect ratio differs from the viewers. When the value _cover_ is used the entire viewport is filled and the displayed portion of the image is cropped as needed to fit.

### Sticky

The _sticky_ attribute can be added to a component to "stick" it to the top of the essay when scrolling a section of text that is longer than can be viewed in the visible portion of the window.  This is useful when describing portions of an image or cueing video clips from text.

# [⇧](#top) How To's {#how-tos}

## [⇧](#top) Marking Text {#marking-text}

Essay text is "marked" by surrounding the applicable text with double equal signs (`==`) followed by an element attributes definition with the action to be performed.  Element attributes are defined by text enclosed with `{` and `}` characters.  For example:

```Markdown
Lorem ipsum ==dolor=={100,100,400,400} sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam
```

In the example above the text `dolor` is marked and associated with the attribute `100,100,400,400`.  This has the effect of highlighting the `dolor` text in the rendered essay and creating a `zoom` interaction when the text is selected (clicked or tapped).  The `zoom` interaction causes the closest image to zoom into the region specified by the coordinates in the  attribute.

## [⇧](#top) Marked Text Behaviors {#marked-text-behaviors}

[Marked text](marking-text) is used to create a essay interactions such as zooming into an image region or playing a specific segment of a video.  The text to trigger the interaction is marked by surrounding a word or phrase with double equal signs and enclosing a value for the desired behavior in brace characters (`{`,`}`).  Below are a few examples of some commonly used marked text behaviors.  These are explained in more detail the following sections.

- **Image region zoom** - `==click to zoom=={100,100,400,400}`
- **Play multimedia (video or audio) segment** - `==click to play=={1:30,1:45}`
- **Show entity information popup** - `==Vincent van Gogh=={Q5582}`

### [⇧](#top) Image zoom {#zoom}

.ve-media gh:juncture-digital/media/videos/Image_Zoom_Example.mp4 right

The image zoom behavior causes the `.ve-media` viewer to zoom to a specific region of an image.  The region of interest is specified using a set of 4 coordinates defining a rectangular bounding box.  The coordinates are the `x-position`, `y-position`, `width`, and `height`.  The coordinate values may be defined as absolute pixel values or as a percentage relative to the full size of the source image.[^iiif-region]

- **x,y,w,h**: The region of the full image to be returned is specified in terms of absolute pixel values. The value of x represents the number of pixels from the 0 position on the horizontal axis. The value of y represents the number of pixels from the 0 position on the vertical axis. Thus the x,y position 0,0 is the upper left-most pixel of the image. w represents the width of the region and h represents the height of the region in pixels.
- **pct:x,y,w,h**: The region to be returned is specified as a sequence of percentages of the full image’s dimensions, as reported in the image information document. Thus, x represents the number of pixels from the 0 position on the horizontal axis, calculated as a percentage of the reported width. w represents the width of the region, also calculated as a percentage of the reported width. The same applies to y and h respectively. These may be floating point numbers.

### [⇧](#top) Play video or audio segment {#play-at}

The play behavior causes the `.ve-media` viewer to play a video or audio clip starting at a specified time.  A second time value may optionally be used to define a stop time.  If a stop time is not provided the clip will play from the start time to the end.  The values for the start and end times are specified in **hh:mm:ss** notation.  The **hh** and **mm** values are optional.  For example:

- **30**: `==start playing 30 seconds into clip=={30}`
- **1:30**: `==start playing 90 seconds into clip=={1:30}`
- **15:00**: `==start playing 15 minutes into clip=={15:00}`
- **1:10:00**: `==start playing 1 hour and 10 minutes into clip=={1:10:00}`
- **5:30,6:00**: `==play from 5:30 to 6:00=={5:30,6:00}`

### [⇧](#top) Show entity info-box on hover {#entity-popup}

This behavior causes an entity information popup to be display when the cursor hovers over marked text associated with an entity (person, place, etc) identifier.  Juncture uses [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) for entity data.  Wikidata is a free and open knowledge base that can be read and edited by both humans and machines.  Wikidata acts as central storage for the structured data of its Wikimedia sister projects including Wikipedia, Wikivoyage, Wiktionary, Wikisource, and others.  The textual information displayed in a Juncture entity popup is retrieved from Wikidata and Wikipedia.  When available, thumbnail images are retrieved from Wikimedia Commons.

Wikidata entity identifiers ("Q" IDs) can be obtained by querying Wikidata or by visiting the Wikipedia page associated with the entity of interest.  When viewing a Wikipedia page the Wikidata link in the left navigation panel can be used to easily obtain the entity `QID`.  Clicking on the Wikidata link will open the associated Wikidata page where the QID can be copied from the title displayed at the top of the page.  For example, the [Wikidata page for Vincent van Gogh](https://www.wikidata.org/wiki/Q5582) reveals the QID `Q5582`.  Adding this QID to a marked text segment will cause an entity popup to appear when hovering over the text.  A working example of this can be seen in the paragraph below.

> ==Vincent Willem van Gogh=={Q5582} was a Dutch Post-Impressionist painter who posthumously became one of the most famous and influential figures in Western art history. In a decade, he created about 2,100 artworks, including around 860 oil paintings, most of which date from the last two years of his life.

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

[^iiif-region]: [IIIF Image API 2.1.1 Region Definition](https://iiif.io/api/image/2.1/#region)