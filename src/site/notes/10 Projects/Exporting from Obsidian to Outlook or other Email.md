---
{"dg-publish":true,"permalink":"/10-projects/exporting-from-obsidian-to-outlook-or-other-email/","tags":["project"]}
---


# Method 1 – Copy Document as HTML (Simple and preferred for small docs)

## Plugin : [Copy document as HTML]([mvdkwast/obsidian-copy-as-html: Obsidian plugin: copy document as HTML, including images (github.com)](https://github.com/mvdkwast/obsidian-copy-as-html))
Hot key set to Ctrl + C
and paste in Outlook or wherever
>[!Warning] Be sure to install Copy Document as HTML plugin as it can do images as opposed to similar sounding Copy as HTML plugin

# Method 2 – Using Pandoc plugin (Useful for longer docs with formatting, PDFs)
## Exporting from Obsidian setup
### Core setup
In Files and Links – Use Wiki links and shortest path for convenience across docs.
In Editor – Turn off strict line break (or alternatively do Linter step to add two spaces at end of line to make it hard break)

### Plugin Linter 
Enable Linter plugin to put in two spaces to convert soft line break to hard line break. **This is not needed when using Export from HTML or copy as HTML. and strict line breaks is turned off **

### Plugin Obsidian link converter
Before exporting, use Obsidian link converter to convert all links to wiki links with relative paths. If you would like you can avoid this step by choosing the relative path in Core setup, but since I export less than 1% of the document I like the cleaner look of shortest path.

### Excalidraw setup
  Use SVG or PNG for embedding
  I am using PNG- to enable PowerPoint to live update images (Insert image and link)

### Image size
[image name|300] can be used to adjust resolution if needed

### Pandoc Plugin 
#### Setup
- Enable Export from HTML
	- **Export from HTML - Transcluded Wiki link for image and relative path - Works well - Current setting**
	- Export from HTML - Transcluded Wiki link for image and shortest path - Crashes and does not export the rest of doc. 
	- Export from Markdown - Transcluded markdown link for image works for either short or relative path
	- Export from Markdown - Wikilink not understood. 
- Enable Convert Links to Text
	- Transcluded links will not get converted and the content actually get embedded as desired. 
- Does not understand spaces when parameters are passed. To work around space issue, put resource path in a separate yaml file and the path to the file into defaults arguments under "Extra Pandoc arguments"
	Save the below line,
	resource-path: [*path with spaces*]
	to a folder path without spaces and add the following to the "extra pandoc arguments"
	--defaults=C:/Users/akrish5\/obs_pandoc.yaml
> [!TIP] When you copy paste the path from WIndows to plugin the \ needs to be changed to / both for resource path and for extra pandoc arguments]

[[BUG] Pandoc cannot find image file unless full relative path is used · Issue #81 · OliverBalfour/obsidian-pandoc (github.com)](https://github.com/OliverBalfour/obsidian-pandoc/issues/81)
[feat: set the CWD for pandoc to the input dir by janLo · Pull Request #101 · OliverBalfour/obsidian-pandoc (github.com)](https://github.com/OliverBalfour/obsidian-pandoc/pull/101)
#### Output
- Formatting
	- Bolding and italics work
	- Highlights does not work
	- indenting does not work (both with tabs or spaces). If you use > at beginning it will indent but it looks wonky
- Pandoc will not export front matter
- For hiding other text you want to exclude from export use  from Obsidian comments
- You can also use html comments to hide but links will not get updated
	<!--
	-->
- Pandoc plugin does not do well with embedded attachments (word doc). Binary file is included
- Always exporting to same folder "Obsidian exports"
- Alt + W – Hotkey Setup to export to word

## Importing into Outlook

Outlook uses Word HTML rendering so it will not show the same as browser.. but if you export to word file and then copy paste to Outlook or insert as text it is fine.. (refer: [Importinghtml into outlook](https://help.chamaileon.io/en/articles/2827710-how-to-import-my-html-template-to-outlook))
Add the attach file (the one without arrow) command  into your quick access tool bar


![Attach file snapshot.excalidraw.png|600](/img/user/99%20Attachments/Attach%20file%20snapshot.excalidraw.png)


![Pasted image 20221221001121.png|undefined](/img/user/99%20Attachments/Pasted%20image%2020221221001121.png)



## To be done
- [ ] Can we automate using Autohotkey or other means to get everything done in a single command? 
- [ ] Getting check boxes to show up in Word and then Outlook. Shows up as bullet point
- [ ] Getting indenting to show up in Word doc smoothly. Does not work with tab or spaces

# Method 2A - Using Pandoc with Export from Markdown (Not using it now)

## Exporting from Obsidian setup

### Plugin Linter 
Enable Linter plugin to put in two spaces to convert soft line break to hard line break. 
Also will need to ensure headings have a space above them (not required when exporting from HTML)

### Using Obsidian link converter to convert wiki link to Markdown
This is needed only if you are using wiki links which I do since that is convenient and exporting is done only for a smaller subset. This operates on the full file and will convert all links, including non image links into Markdown link. Then they will show up in the exported doc as a link to a document, which I didn't want. Ideally, I would have preferred only images to be converted to Markdown link and rest remain as wiki link, but no such option.  It is because of this limiation I am using Method 2 over 2A.

### Another option to convert some links (manual) using pluging - wiki to md link
Enable Markdown link instead of wiki link when pasting images (in Obsidian)
	Use Ctrl +Shift + L (plugin - wiki to md link ) on each link to convert
### Using Filters to remove Wiki link
When using Markdown link plugin does not provide option to change links to text, so we will need to change the wiki link using the filter mechanism. 
![Pasted image 20221220234809.png|undefined](/img/user/99%20Attachments/Pasted%20image%2020221220234809.png)
To know more about filter see below 

## To be done
- [ ] Getting indenting to show up in Word doc smoothly. Does not work with tab or spaces
- [ ] Find a way to only format transcluded links with link converter. 

# Method 3: Running Pandoc directly (Not tested throughly)

## Using filter to remove Wikilink
pandoc "Export Test.md" --filter="removewikilink.py" -o test.docx
Python script is based on discussion [here]([Remove markdown wiki-link brackets during pandoc exports (github.com)](https://gist.github.com/maybemkl/d9be15bcabadaa19d2ca50c87b59a92e#file-remove_links-py))

### Code below 
With this code, link is removed, but closing brackets are not fully removed. An enhanced code in link above takes care of that issue, but not tested by me. 

#!/usr/bin/env python3

from pandocfilters import toJSONFilter, Str
import re

def replace(key, value, format, meta):
    if key == 'Str':
        if '[' in value:
            new_value = value.replace('[', '')
            return Str(new_value)
        if ']' in value:
            new_value = value.replace(']', '')
            return Str(new_value)
     	
if __name__ == '__main__':
    toJSONFilter(replace)




