.ve-header Documentation background=#5B152E logo=https://raw.githubusercontent.com/visual-essays/media/main/images/Juncture_Logo.png url=/ sticky

[⇧ Documentation Home](..)

# Juncture Getting Started Guide {#top}

This tutorial provides step-by-step instructions for creating a Juncture essay.  The created essay will incorporate a number of Juncture features including the use of an embedded media viewer for viewing a high-resolution image and the use of the media viewer for displaying an image grid and comparing two images.  The tutorial provides detailed instructions with accompanying videos and/or interactive images for each step.  

Most of the tutorial sections include a short video clip demonstrating the actions that need to be accomplished.  Some sections also include links in the text for starting the video at specific points.

---

# Prerequisites
The only true prerequisite for using Juncture is a Github account.  **Github is a free Internet hosting service** commonly used for software development projects.  It provides features for version control and work flow management for distributed teams.  Juncture uses Github for storing and managing essay files.  In addition to a Github account, some familiarity with Markdown and IIIF would be beneficial.

#### Sign-up for Github account

If you don't already have a Github account one can be created at [https://github.com/signup](https://github.com/signup)

For more information on the following topics, please click on the internal link.
* [Markdown](#markdown)
* [IIIF (International Image Interoperability Framework)](#iiif)
* [Github](#github)

### Markdown {#markdown}

Markdown is a lightweight markup language for creating formatted text using a plain-text editor.   Behind the scenes the Markdown text is converted into HTML for display in web browsers.  Juncture extends the core Markdown language with a few simple tags and conventions enabling rich essays to be created by anyone.

- [Markdown Guide](https://www.markdownguide.org/)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Short (12min) Markdown tutorial on YouTube](https://www.youtube.com/watch?v=6A5EpqqDOdk)
            
### IIIF (International Image Interoperability Framework) {#iiif}

IIIF is a set of open standards for delivering high-quality, attributed digital objects online at scale. It’s also an international community developing and implementing the IIIF APIs. IIIF is backed by a consortium of leading cultural institutions.  Juncture makes extensive use of IIIF, using existing IIIF resources when available, and converting non-IIIF images, videos, and audio into IIIF when used in Juncture essays.  

- [IIIF Home Page](https://iiif.io/)
- [Introduction to IIIF](https://www.youtube.com/watch?v=K4i7YlZEMGA), a presentation by Josh Hadro given at the 2021 IIIF Annual Conference

### Github {#github}

Juncture primarily uses Github as a file hosting service, similar to how one might use Dropbox or Google Drive. While Juncture is able to use some of the more advanced Github features (like website hosting) the primary use is  storing visual essay text files. Github content is organized into one or more repositories. Users unfamiliar with Github can think of a repository as a workspace or a collection of folders. 

Juncture users have the option of manually creating and updating essay source files in Github or using the Juncture editor. When using the Juncture editor a user will not need to interact with the Github site directly as the Juncture editor will handle essay file creation and updates.

### Sign-up for Github account

If you don't already have a Github account one can be created at [https://github.com/signup](https://github.com/signup)

---

## Login with Github and open Juncture editor

Logging into Github from Juncture authorizes Juncture to interact with your Github repository content from the editor.  Note that this is an optional step as Github files may be edited directly in the Github web interface or by using any number of client applications running on your local computer. This getting started guide assumes the Juncture Editor is used.  The ==video below=={0} shows the basic process for logging into Github from Juncture.

.ve-media gh:juncture-digital/media/videos/Login.mp4 right

1. ==Select "Login" from the Juncture menu=={0,3}
2. ==Login to Github=={4,7} with your Github username and password.
3. ==Authorize Juncture to write Github content=={9,10}.  This will only be required on an initial login.  (Note that this authorization may be revoked using in [Github settings](https://github.com/settings/apps/authorizations))
4. ==Open the Juncture editor=={15} after logging in with Github.

---

## The Juncture Editor

Juncture provides a web-based editor for authoring visual essays.  The editor handles Github content management and includes a convenient preview option for viewing working versions of essays.  The Juncture editor also supports the automatic creation of viewer tags by simply dragging images and other media (including YouTube videos) into the browser window.

.ve-media gh:juncture-digital/media/images/Juncture_Editor.png right

This section provides an overview of the Juncture editor sections.  Video clips in this document show many of the typical uses of the editor.

1. ==Github content tool=={0,0,751,1098|7cc4f0fb}.  The Github content tool provides basic content mangement support for interacting with Github.  By default the content tool reads and writes files from the `essays` repository in a users primary Github account.  Other accounts and repositories may be used if desired.  The content tool provides drop down menus for selecting other Github accounts and repositories.  For many users the default `essays` repository is probably a good option changing Github accounts and/or repositories will not be required.
2. ==Markdown toolbar=={0,0,751,1098|79479e74}
3. ==Juncture toolbar=={560,0,522,762|44cc3619}
    - ==Preview=={560,0,522,762|de7c7af6} - The preview button will toggle the Juncture editor between edit and preview modes.
    - ==Help=={560,0,522,762|48618266} - Opens a new Help window with Juncture documentation
    - ==Save=={560,0,522,762|fbb24f5a} - The save button will write the essay text to Github
    - ==Copy=={560,0,522,762|c12e1ee4} - Copies the essay text onto the clipboard
    - ==Launch=={560,0,522,762|59ecd40f} - The launch button will display the essay in a new tab
5. ==The main editor window=={0,0,1081,1602|9d0bf556}
6. A sample ==Viewer tag=={58,148,626,927|2ca0f199}

---

## Creating an essay {#create-essay}

In this portion of the tutorial we will create an essay on Vincent van Gogh's =="Bedroom in Arles"=={Q724377} paintings.  The tutorial will demonstrate the use of a number of Juncture features including:
- [Creating a new essay file](#new-essay)
- [Adding text to the essay](#adding-text)
- [Some basic Markdown formatting](#simple-formatting), including the creation and formatting of section headings, quoted text, and a list
- [Adding a citation](#add-citation) (footnote) to reference the source of the text used in the essay
- [Adding a high resolution image](#add-image) in an embedded media viewer
- [Using the media viewer in compare mode](#add-image-compare) to compare the first version of the "Bedroom in Arles" painting and an early sketch 
- [Using the media viewer in grid mode](#add-image-grid) to display all 3 versions of the paintings with full resolution popups
- [Creating a text interaction to zoom](#create-zoomto) in on a region of an image referenced from the text
- [Creating an information popup](#create-infobox) that is opened when the cursor is positioned over the relevant text
- [Adding an essay header](#add-essay-header) with a title, subtitle and banner image
- [Sharing the essay](#save-and-share)

**A version of a completed essay from this tutorial can be seen at [https://beta.juncture-digital.org/snagsby/essays/bedroom-in-arles](https://beta.juncture-digital.org/snagsby/essays/bedroom-in-arles)**

### [⇧](#create-essay) Creating a new essay file {#new-essay}

.ve-media gh:juncture-digital/media/videos/New_Essay.mp4 right

The first step in the creation of a new essay is to create a new file for the essay text.  A new folder is created in the Github repository for the essay files.  The primary (and in many cases, the only) file needed for an essay is a Markdown file for the essay text.  Note that Juncture uses the Github convention of naming the primary Markdown file in a folder as `README.md`.

A new folder is created by selecting the parent folder from the Gitub content selection tool at the top of the editor and then clicking on the add item icon (a shaded circle with a plus sign).  A dialog is then displayed for entering the new folder (essay) name.

For our example the new folder is named `bedroom-in-arles`.  Since the folder name becomes part of the stable URL for the generated essay, the name should follow the web convention of lowercase characters, numbers, and dash characters (`-`,  used for word separators).

After entering the name of the folder to be created and selecting `Add`, the folder and `README.md` file is created.  The Juncture editor opens the `README.md` file for editing.

### [⇧](#create-essay) Add essay text {#adding-text}

In this example we will use text from the _Bedroom in Arles_ Wikipedia article.  In this video clip, text is copied from various sections of the Wikipedia article and pasted into the Juncture editor window.  ==The result of this copy and paste sequence=={1:14} is the addition of unformatted text in our essay.  In the next portion of the tutorial we will perform some light formatting using some Markdown tags.

.ve-media gh:juncture-digital/media/videos/Add_Text.mp4 width=80%

### [⇧](#create-essay) Format essay text {#simple-formatting}

.ve-media gh:juncture-digital/media/videos/Text_Formatting.mp4 right

After adding the plain text some formatting is applied.

- ==Add top-level section heading=={2,13} - A top-level section heading is defined by adding a single hash character to the start of the line with the heading text.
- ==Format second-level section headings=={14,28} - Second-level sections and headings are similarly defined using double hash characters.
- ==Format block quote=={29,32} - A block quote is defined by adding a greater-than symbol (`>`) at the beginning of the quoted passage.
- ==Format list=={35,48} - The _Provenance_ section is an unordered list of text.  This is formatted by adding a dash (`-`) and space character at the start of the line for each list item.

### [⇧](#create-essay) Add citation {#add-citation}

.ve-media gh:juncture-digital/media/videos/Add_Footnote.mp4 right

Here we add a citation to our essay to identify the source of the text used in the essay.  Normally a separate citation is used for each distinct instance of cited text.  However, in our essay all of the text has been copied and thus will be cited using a blanket citation that is added at the beginning of the essay.   A citation is made by appending a citation reference to the cited text.  This is then used to connect to citation text located in a footnote (or endnote) section.

In Juncture, a citation reference consists of an ID enclosed in brackets.  The citation ID is an alphanumeric string prefixed with the caret symbol, for example `[^1]`.  The citation reference is also added to the end of the essay where a references section will be included in the rendered essay.  The citation reference used in the references section includes a colon (`:`) suffix and a space between the citation reference and start of the reference text, for example `[^1]: Reference text...`

Our blanket citation at the start of the essay is also italicized (by enclosing text with underscore characters) and is separated from the essay text with a horizontal rule.  This is only done for stylistic purposes to demonstrate some Markdown formatting.

### [⇧](#create-essay) Add image {#add-image}

.ve-media gh:juncture-digital/media/videos/Add_Image.mp4 width=80%

In this example an image is added to the essay by ==dragging the image from the Wikipedia page=={0,3} to the Juncture editor window.  The image is dropped at the desired position in the essay text.  When adding an image using drag-n-drop a _.ve-media_ tag with the IIIF manifest URL (short form) is automatically added to the essay text.  Juncture supports the addition of media from a number of hosting sites (including Wikipedia and Wikimedia Commons) using drag-n-drop.  For a complete list refer to **[TODO]()**.

The default behavior for the _.ve-media_ viewer is to display the image the full width of the essay.  For this example we will position the image in the right half of the essay and allow the section text to wrap around the image if needed.  Repositioning the image is accomplished by adding the `right` attribute to the _.ve-media_ tag as can be ==seen in this clip=={8}.

### [⇧](#create-essay) Add image zoom interaction {#add-zoomto}

.ve-media gh:juncture-digital/media/videos/Add_Image_Zoom_Interaction.mp4 right

A key feature of Juncture is its ability to create interactions between the text narrative and visualizations.  In this essay we will add an interaction that causes the media viewer to zoom in on a region of the image mentioned in the essay text.  Specifically, we will link a mention of wall pictures to a zoomed-in close-up of one of the pictures above the bed in the painting.

For this interaction the bounding-box coordinates of the image region of interest must be obtained.  This is accomplished by zooming and panning in the media viewer while the editor is in preview mode.  After the viewer has been positioned at the right location hovering the cursor over the bottom right corner of the media viewer will reveal the bounding-box coordinates.  Clicking on the coordinates copies them to the clipboard.

After the coordinates have been copied they can be associated with the relevant text in the editor (when in edit mode).  This can accomplished manually or by selecting the text and clicking on the code icon ('</>') in the Markdown toolbar.  The linked text is enclosed with double equal signs and the coordinates are added as a value in the attributes attached to the linked text.

When in preview mode,  notice that the marked text is now clickable.  Clicking on the text will cause the media viewer to zoom in on the image region of interest.

### [⇧](#create-essay) Add media viewer for comparing two images {#add-image-compare}

The _.ve-media_ viewer has two modes for viewing multiple images, `compare` and `grid` mode.  In `compare` mode 2 images are stacked and a slider is used to show/hide relevant sections of each image.  To use the _.ve-media_ viewer in one of the multi-image modes the IIIF manifest URLs for each image are defined in an indented Markdown list following the _.ve-media_ tag.  The mode is specified by adding the _compare_ or _grid_ attribute to the tag.  

.ve-media gh:juncture-digital/media/videos/Add_Image_Compare.mp4 width=80%

In this sample essay both the viewer mode attribute (_compare_) and a positioning attribute (_right_) are specified.  The 2 images to be compared are defined in the Markdown list immediately following the tag.  In this essay one of van Gogh's sketches and first version finished painting are compared.  The image list can be created manually or using the drag-n-drop gesture used to add the first image.   When using the drag-n-drop approach the second image is dropped over the _.ve-media_ tag created by the drag-n-drop of the first image.

### [⇧](#create-essay) Add media viewer for displaying the 3 paintings {#add-image-grid}

In this portion of the tutorial a _.ve-media_ viewer instance is added in _grid_ mode to display the 3 versions of the painting side-by-side.  Each painting is displayed as a clickable thumbnail.  When clicked, a popup is displayed with image in a full media viewer enabling deep-zoom and panning of the painting image.

.ve-media gh:juncture-digital/media/videos/Add_Image_Grid.mp4 width=80%

Similar to how the _.ve-media_ tag was created for comparing the original painting and sketch, the image list in _grid_ mode is created by dragging and dropping the image for each of the painting versions into the Juncture editor window.

### [⇧](#create-essay) Add an information popup {#create-infobox}

Information popups are useful for providing a quick definition and overview of a term.  The information popup appears when a users cursor is positioned over the term.  Information popups are typically used to provide background on entities such as people, places, organizations, creative works, etc.  The data used in the creation of the information popup is retrieved from Wikidata and Wikipedia.  Wikidata is an open knowledge base hosted by the Wikimedia Foundation that can be read and edited by both humans and machines. Wikidata acts as the central source of common, open structured data used by Wikipedia, Wiktionary, Wikisource, and others. It is used in a variety of academic and industrial applications.

Wikidata currently contains data for more than 100 million entities.  Each of these entities is associated with a unique Wikidata Identifier (or "Q" ID).  To create an information popup a term is associated with a QID obtained from Wikidata.  Finding a QID can be accomplished in a couple of ways.
- Using the search interface on the [Wikidata home page](https://www.wikidata.org/wiki/Wikidata:Main_Page) site
- Using general web search tools (Google, Bing, etc) to locate the Wikipedia page associated with the entity of interest and then using the Wikidata link found in the left sidebar to navigate to the associated Wikdata page.  When on a Wikidata page the QID for the entity can be found in the top header and page URL.

After a QID has been found for the text to be linked to the information box, the text is wrapped with double equal signs (`==`) and the QID is added in an attribute set attached to the marked text.  For example, to create an information popup for Vincent van Gogh.

```Markdown
this snippet creates an information popup for ==Vincent van Gogh=={Q5582} by wrapping the text and associating it with the Wikidata QID.
```

.ve-media gh:juncture-digital/media/videos/Add_Entity_Infobox.mp4 width=80%

A live version of an information popup for ==van Gogh=={Q5582} can be seen in this paragraph.  Hover over the  "van Gogh" text to see the popup in action.

### [⇧](#create-essay) Add essay header with title and banner image {#add-essay-header}

Our last addition to the sample essay is the addition of a header for the displaying the essay title and subtitle.  In this header we are also including a banner image that is obtained from the Wikimedia Commons site.

.ve-media gh:juncture-digital/media/videos/Add_Header.mp4 width=80%

The _.ve-header_ tag provides a few configuration options, including the definition of a navigation menu with an email contact form.  That is not used in this example, but we do configure the header title/nav bar to "stick" to the top of the browser window when content is scrolled.

### [⇧](#create-essay) Save and share essay {#save-and-share}

.ve-media gh:juncture-digital/media/videos/Save_and_Share.mp4 right

While creating an essay Juncture will periodically save a version of the essay with the browser.  Because of this a user may navigate away from the Juncture Editor page or close the browser.  Upon returning to the Juncture editor the user is able to resume editing the essay text.  These automatic saves are only performed within the browser, the contents are not automatically saved to Github.  Saves to Github must be explicitly performed by pressing the `save` button in the Juncture toolbar at the top right of the editor window.

If is recommended that intermediate versions of an essay be saved to Github periodically.  Once an essay has been completed it will need to be saved to Github to share with others.  Again, this is accomplished by clicking the save button in the Juncture toolbar.  Clicking the `launch` button in the toolbar will open the most recently saved version of the essay in Github in a new browser tab.  The URL in this new tab is the stable URL for the essay and can be used by others to view the essay.