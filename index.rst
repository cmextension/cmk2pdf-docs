.. CMK2PDF documentation master file, created by
   sphinx-quickstart on Mon Jan 25 12:10:35 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===================================
Welcome to CMK2PDF's documentation!
===================================

CMK2PDF is a plugin for `K2 component <http://www.getk2.org/>`_ to give you and your site's visitors ability to view your K2 articles in PDF format, in this way we can not only print K2 articles but also can download them for offline reading.

Conversion from HTML document to PDF document is powered by `MPDF PHP library <http://mpdf1.com/>`_.

This documention gives you instruction to install and setup CMK2PDF and MPDF on your Joomla! website.

Technical Requirements
======================

CMK2PDF is compatible with Joomla! 3.x.x. CMK2PDF is **NOT** compatible with Joomla! 1.x.x. CMK2PDF could be used on Joomla! 2.5.x, but this is not tested yet.

Please check `Joomla!'s Technical Requirements <http://www.joomla.org/technical-requirements.html>`_ for more information of Joomla!'s requirements.

CMK2PDF is built and tested on K2 2.6.9. It could be used with other older versions of K2 with no problems, but this is also not tested.

The latest version of Joomla! and K2 are always recommended for stability and security.

Install CMK2PDF
===============

Installing CMK2PDF is very easy, you just need to upload and install its package via Joomla! Extension Manager, just like you install any other Joomla! extensions.

To update CMK2PDF, you just need to install the new version's package.

Install MPDF library
====================

CMK2PDF requires MPDF library to convert HTML to PDF, you also need to install MPDF library.

By uploading the package
------------------------

Because the package of MPDF PHP library is about 47MB, so if your server allows to upload more than 47MB you can install this package via Extension Manager just like installing any other Joomla! extensions. However if you can't install by using "Upload Package File" option, you can use "Install from Directory" option. The following instruction is for installing via "Install from Directory" option.

To download MPDF Joomla! library, you go to `https://github.com/cmextension/mpdf <https://github.com/cmextension/mpdf>`_ and click "Download ZIP" button.

You log into your hosting's control panel, access file manager tool, go the "tmp" folder in your Joomla! root folder, the below screenshots are the file manager of CPanel which is popular and is used by many hosting providers.

.. image:: /images/mpdf_tmp.jpg


You upload the mPDF package into this "tmp" folder. In the below screenshots, the package is named "mpdf.zip".

.. image:: /images/mpdf_uploaded.jpg


You can use any ZIP extracting tool available in the file manager to extract the filer. In CPanel, you select the file and click "Extract" button on the toolbar. The result is "mpdf" folder.

.. image:: /images/mpdf_extracted.jpg


In Joomla!'s Extension Manager, you switch to "Install from Directory" tab and enter the path the "mpdf" folder. If your "tmp" folder is "/home/username/joomla/tmp" then the path to "mpdf" folder should be "/home/username/joomla/tmp/mpdf".

.. image:: /images/mpdf_install.jpg


Click "Install" button the library will be installed, you will get the successful message in the next page.

.. image:: /images/mpdf_success.jpg


Now mPDF library is installed, you can delete "mpdf.zip" file and "mpdf" folder in your "tmp" folder.

By installing from URL
----------------------

You can also install MPDF by using direct link to Github's archive. In Joomla! Extension Manager, you switch to "Install from URL" tab, put the link https://github.com/cmextension/mpdf/archive/master.zip into "Install URL" field and click "Install".

.. image:: /images/install_mpdf.jpg


Configure CMK2PDF
=================

In your Joomla! back-end navigate to Extensions -> Plugins, search for "pdf" to find "K2 - PDF for K2 (CMK2PDF)" plugin.

.. image:: /images/plugin_list.jpg


Edit the plugin you find 4 tabs for the plugin's configuration: Plugin, Page, Margin and Header & Footer.

Plugin tab
----------

.. image:: /images/plugin_detail.jpg

**Parameter string**

This is an important option in order to decide how your visitors can see the PDF version of your article.

If you want to replace the original print feature of K2 (in HTML format) with PDF, you can use the parameter string "print=1".

If the URL of your article is::

    http://www.yoursite.com/index.php/your-k2-article

Then the URL to print the article is::

    http://www.yoursite.com/index.php/your-k2-article?tmpl=component&print=1

You can see this URL when clicking on "Print" link on the top of your article.

The below screenshot is the default style of a K2 article. You can see the "Print" link on the top of the article.

.. image:: /images/article.jpg


By default, if you click "Print" a new popup appears, it is an HTML document for printing. It doesn't only inlucde the article but also includes some other parts of K2 features like rating, font size control, social network buttons, etc...

.. image:: /images/article_popup.jpg


When you enable CMK2PDF, this popup is no longer an HTML document, it is now a PDF document which only contains your K2 article's content.

.. image:: /images/print.jpg


You can use your own parameter string if you need, however you will need to override K2 item's layout in order to show a link or a button to print K2 article.

Example: If your parameter string is "printme" then the URL of your article could look like this::

    http://www.yoursite.com/index.php/your-k2-article?printme

Example: If your parameter string is "pdf=true" then the URL of your article could look like this::

    http://www.yoursite.com/index.php/your-k2-article?pdf=true

**Additional CSS files**

Your K2 article often doesn't inlude any CSS styles, the PDF version of it is also created from plain HTML. So if you want your PDF version looks the same or similar to your HTML version, you may need to include some CSS files to decorate your article. These CSS files often come from your template or your own custom CSS files.

Not all CSS attributes are supported by MPDF library, you can see what MPDF supports at `http://mpdf1.com/manual/index.php?tid=34 <http://mpdf1.com/manual/index.php?tid=34/>`_.

To include these files, you enter their paths into "Additional CSS files" field, one path per line.

If your files come from your current template, their paths often starts with "templates/". If they are in the folders of other components, their paths starts with "components/".

For example, if you want to include the CSS file of Protostart template (the default template of Joomla!), you enter "templates/protostar/css/template.css".

In order to know what CSS you need to include, you can check your template's documentation, ask the template's author or contact us for support.

**Force Download**

Force user to download PDF file instead of viewing it on browser.

**Include Intro Text**

Include article's intro text in PDF, it is showed before the main content of article.

**Include Article's Ttile**

By default your article's title is included in its content. If you want to display the article's title on the top of your PDF document, you switch this option to "Yes".

**Article Title's Heading**

This option give you ability to choose the heading style of your article's title if you set"Include article's ttile" to "Yes". You can wrap your title with <h1>, <h2>, <h3> or <h4> HTML element.

**Include Extra Fields**

If you include extra fields, they are shown after article's content.

The HTML code of extra fields is the same to the default code of K2 with the CSS classes like 
itemExtraFields, itemExtraFieldsHeader, itemExtraFieldsLabel, itemExtraFieldsValue... So you just need to include your CSS file then the output of extra fields could be the same to article's HTML version.

**Wrap Document With A Locale**

If the content of your article is not English and requires special font to show (for example Russian, Korean, Hebrew,...), you should select your language in this option.

If your article have many languages which have UTF-8 characters, you should wrap the paragraphs with "lang" attribute and their 2 letter language code (ISO 639-1). For example "ru" for Russian, "ko" for Korean. You can find the list of language code at `https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes <https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes>`_. If your languages only use Latin characters, you don't need to set any language code.

Example: <p lang="ru">This text is in Russian</p>

.. image:: /images/article_language.jpg

Page tab
--------

.. image:: /images/plugin_detail_page.jpg

**Format**

You configure the page format of your PDF document. The popular format is A4.

**Orientation**

The PDF documentation is in portrait or landscape orientation.

Margin tab
----------

.. image:: /images/plugin_detail_margin.jpg

In this tab you can configure the left, right, top and bottom margin of your document. The values are in millimetres.

Header & Footer tab
-------------------

.. image:: /images/plugin_detail_header_footer.jpg

With these options you can configure to show or hide the header and footer of your documentation. The header and footer can have title and/or page number, they can be shown on the left side, right side or in the middle.  The values of header and footer margins of are in millimetres.

Customize PDF output
====================

CMK2PDF has a default layout, to customize this layout to build your own PDF output, you create this file

    plugins/k2/cmk2pdf/layouts/override.php

Copy the content of default.php in the same folder into override.php. Now you can modify override.php to build our own output. Your changes will not be lost when you update CMK2PDF.