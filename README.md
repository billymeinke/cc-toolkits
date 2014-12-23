The CC Toolkits project is built with HTML and Markdown pages, strung together with a static website generator called Jekyll, and hosted on the social coding website Github. The site has been set up to make it simple for anyone to suggest updates and edit to the site's pages (mostly consisting of toolkits), add new pages/toolkits to the site, or to clone/fork the site to make a CC affiliate-focused toolkit site.

##Remix this

Only basic HTML knowledge is needed to help with the CC toolkits project. For people that have web design or development skills, you're encouraged to make pull requests with your styling and functionality changes. And if your changes aren't rolled into the main CC Toolkits site, you can always use them on [your own fork](https://help.github.com/articles/fork-a-repo/).

![Imgur](http://i.imgur.com/sLOIBgCl.png)

Content (images, videos, other media) on the website is licensed as marked, and is otherwise licensed under a CC BY 4.0 International License. See http://creativecommons.org/licenses/by/4.0/ for more information. The site is based on the [Freelancer Theme](https://github.com/jeromelachaud/freelancer-theme) by Jerome Lachaud, which utilizes the [Bootstrap framework](http://getbootstrap.com/), licensed under an [MIT license](https://github.com/twbs/bootstrap/blob/master/LICENSE) .

# Painless CC Toolkit Making

## Overview:

The CC Toolkits project files can be edited in a number of ways. When you find a bug or issue with the site, you're welcome to make edits and submit them as pull requests. Hi-fives to those who find an issue and try to fix it themselves :)

[Submit a pull request here](#)<-- get link when ready

###Nontechnical help
For those with fewer tech skills, you're encouraged to submit suggestions and edits to the pages as issues in the repo. Keep in mind that issues that are submitted without a fix (pull request) included will be addressed as time allows:

[File an issue here](#)<-- get link when ready

<insert options for editing, forking>

### File organization follows this structure:

	/cc-toolkits/
		/img/ <-- the image files are in here
		/layouts/ <-- the page templates are in here
			/default.html
			/toolkit.html
			/page.html
			...
		/_includes/ <-- the common parts of the pages are in here
			/head.html
			/submenu.html
			/footer-toolkit.html
			...
		/basics/index.html <-- the 'Basics of CC' toolkit page, in English
		/basics-de/index.html <-- the 'Basics of CC' toolkit page, in German (Deutsch)
		/culture/index.html <-- The 'CC and Culture' toolkit page, in English
		/science/index.html <-- The 'Science and CC' toolkit page, in English
		...
		/collaborate/index.html <-- The collaborate page is here
		...

A 'toolkit' is just an HTML page. You can view the source of any of the toolkits, or any of the pages on the CC Toolkits site by navigating to the index.html file inside of a topic folder. To see more about how pages in the CC Toolkits site are arranged, see this [section of a guide on Jekyll](http://jekyllrb.com/docs/pages/#named-html-files).

If you were to browse to an .index.html file, or right-clicked and viewed the source of a toolkit page you are looking at, you will notice that the objects on the page (sections, divs, etc) are just HTML with some CSS for styling.

![](http://i.imgur.com/BBqoxhsl.png)

If you want to brush up on your HTML, it may be useful to download and use Mozillas [X-ray Goggles](https://goggles.webmaker.org/) browser plugin. When activated, you can see how the page sections, divs, heading levels and so on are organized. You can even play with editing a toolkit page in the browser at first, if you're unsure about jumping right in to the real project.

![](http://i.imgur.com/xAzJg28l.png)

![Imgur](http://i.imgur.com/KuEw3c5l.png)

### To fork or not to fork?

If you wish to only make edits to existing toolkit pages, you can do it right in the browser here on Github. Navigate to the index.html file for a toolkit topic and click 'edit'. You can make changes and submit them as suggestions straight away.

![Imgur](http://i.imgur.com/Z0wmmIBl.png)

### To add a translation of a toolkit page:

- Browse to an existing toolkit folder (ie /cc-toolkits/basics/)
- Make a copy of the folder, and place it next to the original
- Change the folder name to represent the translation language (ie /basics-de/)
- Open the toolkit page HTML file inside (/basics-de/index.html) with a plain text editor (ie Notepad, TextEdit)
- Edit the HTML to replace original text with translated text
- Change the front matter title (text at the top of the page) to reflect the translation language (ie 'title: Basics of CC - Deutsch')
- Replace embedded video iframes, images, and links to your preferred or language-appropriate items
- If the images you are including in your page are not hosted somewhere else (ie "https://yourwebsite.cc/picture.jpg"), then place them in the ../cc-toolkits/img/ folder

## And bam! You have a translation started.

### Translating the menu, footer

You will also want to replace the common parts of the page (header, footer, etc) with a translated version too. The header and footer may have already been translated into your desired language. This will be obvious if you see files in the _includes folder that have language extensions (ex. "de") in the file name:

	/cc-toolkits/_includes/submenu-de.html
	/cc-toolkits/_includes/footer-toolkit-de.html

If translated headers and footers do not exist, you can make them by browsing to these files:

	/cc-toolkits/_includes/submenu.html <-- the toolkit template menu (videos, case studies, etc)
	/cc-toolkits/_includes/footer-toolkit.html <-- the toolkit template footer (links, license, etc)

Make a copy of the header and footer files you need, change their file names to reference the language translation, then edit them to include the translated text/items.

### A couple more things

Now that you have a translated page menu and footer, you need to make a new toolkit page template that calls those items into your page (instead of the items in the former language).

- Browse to the toolkit page template folder at ../cc-toolkits/_layouts/toolkit.html
- Make a copy of toolkit.html and save the file name to represent the translation language (ie /toolkit-de.html)
- Edit the HTML to replace the original menu (submenu.html) and footer (footer-toolkit.html) and call for your translated items (ie /submenu-de.html and /footer-toolkit-de.html) instead.
- Browse back to your translated toolkit page (../cc-toolkits/basics-de/index.html)
- Change the front-matter (text at the top of the page) to 

Now your /basics-de/index.html toolkit is using the 'toolkit-de.html' template, which uses the 'submenu-de.html' and 'footer-toolkit.de'

### Want to make a translation of the landing page?

The landing page is located at ../cc-toolkits/index.html, which has front matter (http://jekyllrb.com/docs/frontmatter/) which says it uses the 'default' layout. The "default layout" is located at ../cc-toolkits/layouts/default.html and looks like this:

	<!DOCTYPE html>
	<html>

  	{% include head.html %}

    <body id="page-top" class="index">

    {% include header.html %}
    {% include grid.html %}
	{% include archive.html %}
	{% include collaborate.html %}
    {% include map.html %}

    <!--
      <div class="page-content">
        <div class="wrap">
        {{ content }}
        </div>
      </div>
    -->

    {% include footer.html %}
    {% include js.html %}

    </body>
	</html>

Since this template calls for multiple files (head.html, header.html, etc), translations will need to be made at those locations:

- header.html <-- where the landing page menu lives
- grid.html (topic icons)
- archive.html
- collaborate.html
- map.html
- footer.html

Name your translated landing page sections to reflect the language you translated into (ie header-de.html) and place them in the /cc-toolkits/_includes/ folder so that Jekyll knows where to find them when called.

Lastly, go back to the ../cc-toolkits/index.html file you were looking at, and make a copy of it when the appropriate filename for the language being translated to (ie ../cc-toolkits/index-de.html. Now we will have a translation of the landing page, using the new layout (template) that calls for your translated sections of the homepage (header-de.html, grid-de.html, etc).

## Not sure where to go next?
###Reply to this issue on Github, and we'll get back to you soonly:

<insert issue thread link>
