SICP for JavaScript in EPUB 3.0
===

Introduction
---

We try to follow the [IDPF EPUB 3.0](http://www.idpf.org/epub/301/spec/epub-publications.html) specifications as closely as possible. 

The EPUB version of the textbook requires the following additional dependencies:

1. `BeautifulSoup` & `Python 2.7.3`
2. `xsltproc`
3. `PhantomJS`
4. `TeX`

Build process of EPUB
===

To build EPUB, run:
```
make epub
```

Generated EPUB file will be in `epub_javascript/sicp-epub`.

Generation of HTML pages:
---
The HTML pages for each chapter and section is first generated by xsltproc and the book's xml pages. These pages contains LaTeX which will be prerendered by MathJax in a headless browser process. The output HTML is then saved with inline SVGs.

Generation of Metadata files:
---
```epub_javascript/scripts/generate.py``` produces the following files:

1. Table of Contents: `toc.ncx`
2. Manifest file: `manifest.xhtml`

These two meta-data files are essential for the compilation of a well-formed EPUB. 

Python was chosen because of it's simplicity and effectiveness in generating small meta files. 

The IDPF standard for content is normally XHTML, however HTML is more convenient and it works fine. Therefore it is our choice of markup language for the chapter and sections contents.

----

Known Issues
---

1. Overflow of code in some `pre` tags
2. Improve code syntax highlighting
3. Automate MOBI production, currently it is required to use a software to convert the textbook into MOBI format
