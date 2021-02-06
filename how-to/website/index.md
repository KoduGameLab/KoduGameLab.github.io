---
title: Kodu Game Lab
subtitle: WebSite Notes
layout: page
show_sidebar: false
hero_height: is-small
hide_footer: true
---

Most of the website is done in markdown. For editing markdown I prefer **Markdown Edit 1.35**.  The tool is no longer being developed but is simple and functional.  You can download it [here](<https://www.softpedia.com/get/Internet/WEB-Design/HTML-Editors/Markdown-Edit.shtml>).

---
<a name="version"></a>
## Current Version Number
The current version is stored in **KoduGameLab.github.io\API\LatestVersion.xml**.<br>
To update, edit this file, and then commit/push changes.

---
<a name="newsfeed"></a>
## News Feed
The news feed entries are stored as JSON in **KoduGameLab.github.io\API\GetLatestNews**.  To create a new news feed entry just copy/paste an existing one and change the text.  Once done, commit/push changes.
### Notes:
- New entries should be inserted into the top of the list since they are not sorted by the client.
- The Twitter related entries are no longer used.  Previously we had a system that automated making Twitter posts to amplify the news posts.  While not required, I've still been filling them in with reasonable data.

---
<a name="blog"></a>
## Blog
Blog entries are handled using the standard blog capabilities of the Jekyll infrastructure used by GitHub pages.  To add a new blob post, add it to the folder **KoduGameLab.github.io\_posts** using the default naming convention.  To keep the formatting in line with existing posts it's probably easiest to copy and modify an existing post.  Once done, commit/push changes.
### Notes:
- In the header for the posts there is a "published" option.  This allows you to create and deploy a blog post without making it public until you choose.  
- The files in the _posts folder are .markdown instead of .md.  I'm not sure if this makes any difference.  May be worth experimenting.
- The index file in the blog directory is an **html** file instead of **markdown**.  This is required by the Jekyll system.  If you change this, nothing will work. 

---
<a name="localization"></a>
## Language Server / Localizations
The list of current languages is stored in **KoduGameLab.github.io\API\Languages.xml**.  This includes the languages and their most recent update date.  The localizations themselves are stored in **KoduGameLab.github.io\API\Localizations\\##** where ## is the 2 letter ISO language code.  ISO Language codes can be found [here](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).

### Adding a new langauge
> - Use [this link](<https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes>) to find the 2 letter ISO code for the language and the native version of the language name.
> - Add the entry to Languages.xml.  
> - Add a new folder with the ISO language code to the Localizations folder.
> - Add the localized Kodu files to the folder.
> - Commit/push changes.

### Updating a language
> - Edit Languages.xml to reflect the new date.  
> - Edit and/or replace the existing localization files in the Localizations\## folder.  
> - Commit/push changes.

### Notes:  
- Before adding or changing localization files, be sure to try and run them locally in debug mode.  If the XML is badly formed it will though an exception and will need some hand tweaking.
- Also add the new/modified files to the Kodu client enlistment so that they become part of the latest builds. The info from Languages.Xml goes into Locales.Xml in the build.

