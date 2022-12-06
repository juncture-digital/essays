.ve-header Documentation background=#5B152E logo=https://raw.githubusercontent.com/visual-essays/media/main/images/Juncture_Logo.png url=/ sticky

[⇧ Documentation Home](..)

# Getting Started Guide

This document provides step-by-step instructions for creating a simple Juncture essay.

## Sign-up for Github account

A Github account is required to use Juncture.  Juncture uses Github for storing and managing content files.  **Github is a free Internet hosting service** commonly used for software development projects.  It provides features for version control and workflow management for distributed teams.

For Juncture we primarly use Github as a file hosting service, similar to how one might use Dropbox or Google Drive. While Juncture is able to use some of the more advanced Github features (like website hosting) the primary use is for storing visual essay text files. Github content is organized into one or more repositories. Users unfamiliar with Github can think of a repository as a workspace, or a collection of folders. 

Juncture users have the option of manually creating and updating essay source files in Github or using the Juncture editor. When using the Juncture editor a user will not need to interact with the Github site directly as the Juncture editor will handle essay file creation and updates.

If you don't already have a Github account one can be created at [https://github.com/signup](https://github.com/signup)

## Login with Github

Logging into Github from Juncture authorizes Juncture to interact with your Github repository content from the Juncture Editor tool.  Note that this is an optional step as Github files may be edited directly in the Github web interface or by using any number of client applications running on your local computer. This getting start guide assumes the Juncture Editor is used.  The ==video below=={0} shows the basic process for logging into Github from Juncture.

.ve-media gh:juncture-digital/media/videos/Login.mp4 right

1. ==Select "Login" from the Juncture menu=={0,3}
2. ==Login to Github=={4,7} with your Github username and password.
3. ==Authorize Juncture to write Github content=={9,10}.  This will only be required on an initial login.  (Note that this authorization may be revoked using in [Github settings](https://github.com/settings/apps/authorizations))
4. ==Open the Juncture editor=={15} after logging in with Github.

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

## Creating an example essay

In this portion of the tutorial we will create an essay on Vincent van Gogh's "Bedroom in Arles" paintings.  The essay will include a number of Juncture features including:
- Use of a footnote to reference the source of the text used in the essay
- Simple Markdown formatting of section headings, quoted text, and a list
- The use of a high resolution image in an embedded media viewer
- Use the _.ve-media_ viewer in _compare_ mode to compare a painting and a sketch
- Use the _.ve-media_ viewer in _grid_ mode to display all 3 versions of the paintings (with full resolution popups)
- The use of a text interaction to zoom in on a region of the image referenced from the text
- The use of information popups that are triggered when the cursor is positioned over the relevant text
- The addition of an essay header with a title and banner image

### Create new essay file

.ve-media gh:juncture-digital/media/videos/New_Essay.mp4 right

The first step in the creation of a new essay is to create a new file for the essay text.  A new folder is created in the Github repository for the essay files.  The primary (and in many cases, the only) file needed for an essay is a Markdown file for the essay text.  Note that Juncture uses the Github convention of naming the primary Markdown file in a folder as `README.md`.

A new folder is created by selecting the parent folder from the Gitub content selection tool at the top of the editor and then clicking on the add item icon (a shaded circle with a plus sign).  A dialog is then displayed for entering the new folder (essay) name.

For our example the new folder is named `bedroom-in-arles`.  Since the folder name becomes part of the stable URL for the generated essay, the name should follow the web convention of lowercase characters, numbers, and dash characters (`-`,  used for word separators).

After entering the name of the folder to be created and selecting `Add`, the folder and `README.md` file is created.  The Juncture editor opens the `README.md` file for editing.

### Add text

In this example we will use text from the _Bedroom in Arles_ Wikipedia article.  In this video clip text is copied from various sections of the Wikipedia article and pasted into the Juncture editor window.  ==The result of this copy and paste sequence=={1:14} is the addiiton of unformatted text in our essay.  In the next portion of the tutorial we will perform some light formatting using some Markdown tags.

.ve-media gh:juncture-digital/media/videos/Add_Text.mp4

### Format text

.ve-media gh:juncture-digital/media/videos/Text_Formatting.mp4 right

- ==Add top-level section heading=={2,13}
- ==Format second-level section headings=={14,28}
- ==Format block quote=={29,32}
- ==Format list=={35,48}

### Add footnote

.ve-media gh:juncture-digital/media/videos/Add_Footnote.mp4 right

### Add image

.ve-media gh:juncture-digital/media/videos/Add_Image.mp4

In this example an image is added to the essay by ==dragging the image from the Wikipedia page=={0,3} to the Juncture editor window.  The image is dropped at the desired position in the essay text.  When adding an image using drag-n-drop a _.ve-media_ tag with the IIIF manifest URL (short form) is automatically added to the essay text.  Juncture supports the addition of media from a number of hosting sites (incouyding Wiikipedia ans Wikimedia Commons) using drag-n-drop.  For a complete list refer to **[TODO]()**.

The default behavior for the _.ve-media_ viewer is to display the image the full width of the essay.  For this example we will position the image in the right half of the essay and allow the section text to wrap around the image if needed.  Repositioning the image is accomplished by adding the `right` attribute to the _.ve-media_ tag as can be ==seen in this clip=={8}.