# Capturing Web Archives using Archive-It

Web archiving is the practice of using capture tools to crawl websites and save their contents. These result in web archiving (WARC) files, a container file that packages all of the code, media, and other elements of a website. WARC files are the preservation format for websites and can be played back to display the website as it appeared on the live web at the time of capture. 

CCA uses the web app [Archive-It](https://archive-it.org/) to capture certain types of web content related to our collecting interests. The web collections can be accessed through the [CCA microsite](https://archive-it.org/home/Canadian-Centre-for-Architecture). Metadata is controlled locally, and playback is mediated through the [Wayback Machine](https://archive.org/web/). 

Archive-It has a [Help Center](https://support.archive-it.org/hc/en-us), [User Guide](https://support.archive-it.org/hc/en-us/categories/201179946-Archive-It-User-Guide), and [Community Forum](https://support.archive-it.org/hc/en-us/community/topics), which should serve as primary documentation and a resource for troubleshooting. 
 
## Workflow

- consult web archiving seeds list 
- run crawls
- complete QA
- [Add metadata to each seed.](#metadata)
- update crawl log

<a name="metadata"></a>  
### Metadata
Metadata can be added to individual seeds by clicking a seed URL and navigating to the "Metadata" tab. Click "Edit" to begin entering metadata in fields; you must click "Add" for the changes to save. The following fields are required for all seeds: 
- **Title:** Use the "Grab title" feature when possible. Feel free to edit the "Grab title" results if they are especially long or do not represent an appropriate title. If the "Grab title" feature does not work for a particular seed, generate the title of the website using your best judgment. 
- **Creator:** The organizition or individual behind a particular website. This will frequently be "Canadian Centre for Architecture."
- **Date:** Year values related to the website. This minimally should include the year of the crawl, and can also include exhibition dates. Each year should be entered seperately (e.g. "2012" and "2013", not "2012-2013").
- **Language:** Major language(s) represented on a website. Each language should be entered seperately (e.g. "English" "French", not "English and French" 
- **Relation (required if applicable):** If the website relates to another archival fonds at CCA, provide the title of the fonds with a link to the finding aid.

The following fields are optional: 
- **Subjects (recommended):** 1-3 subjects related to the website available in [searchFAST](http://fast.oclc.org/searchfast/), including the Creator. While subject analysis is typically outside of typical CCA archival description, it will make our seeds more discoverable within the Archive-It and Wayback environments. 
- **Description (recommended):** A 3-5 sentence summary of the website's contents. This can be copy-and-pasted directly from the website's "About" page (or similar).
- **Publisher (if needed):** To be used only if the Publisher differs from the Creator.
- **Contributors (if needed):** To be used only if there are other important contributors not covered by Creator or Publisher.
- **Coverage (recommended):** A place name available in [searchFAST](http://fast.oclc.org/searchfast/).

The following fields are not used: type, format, identifier, source, rights, collector, related archival materials. (The last element involves ArchiveSpace integration, not yet possible at CCA.)
