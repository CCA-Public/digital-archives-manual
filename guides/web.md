# Capturing Web Archives using Archive-It

Web archiving is the practice of using capture tools to crawl websites and save their contents. These result in web archiving (WARC) files, a container file that packages all of the code, media, and other elements of a website. WARC files are the preservation format for websites and can be played back to display the website as it appeared on the live web at the time of capture. 

CCA uses the web app [Archive-It](https://archive-it.org/) to capture certain types of web content related to our collecting interests. The web collections can be accessed through the [CCA microsite](https://archive-it.org/home/Canadian-Centre-for-Architecture). Metadata is controlled locally, and playback is mediated through the [Wayback Machine](https://archive.org/web/). 

Archive-It has a [Help Center](https://support.archive-it.org/hc/en-us), [User Guide](https://support.archive-it.org/hc/en-us/categories/201179946-Archive-It-User-Guide), and [Community Forum](https://support.archive-it.org/hc/en-us/community/topics), which should serve as primary documentation and a resource for troubleshooting. 
 
## Workflow

1. Consult web archiving seeds list to see what seeds need to be crawled. It lives here: H:\Archives\Archives numériques\Systems Development\Web Archiving. 
2. [Set scoping rules and run test and production crawls.](#scoping)
   - [Using WebRecorder to capture dynamic content.](#webrecorder)
3. [Complete QA](https://support.archive-it.org/hc/en-us/sections/115000624306-Quality-Assurance-QA-)
4. [Add metadata to each seed.](#metadata)
5. Update crawl log to reflect each SAVED crawl. It's found in the same folder as step 1. 

<a name="scoping"></a> 
## Scoping and running crawls
Add a seed to a collection and scope it using the [Archive-It Guidelines](https://support.archive-it.org/hc/en-us/sections/201864583-Scoping). Note that social media sites, like Facebook, Instagram, and Youtube, require [specific scoping rules](https://support.archive-it.org/hc/en-us/articles/208001336-Scoping-guidance-for-specific-types-of-sites).

Note that every time you add a new seed, you **MUST** run a [test crawl](https://support.archive-it.org/hc/en-us/articles/208001226-Run-monitor-and-save-a-test-crawl). This ensures that the final production crawl saved to the archive is properly scoped. Production crawls cannot be deleted, 

The CCA websites (French/English) are both scheduled to do a shallow crawl weekly. A quarterly full crawl is also recommended, but needs to be kicked off manually. As of writing, all other seeds were scheduled for a one-time crawl.

<a name="webrecorder"></a> 
### Using WebRecorder to capture dynamic content
One [known issue](https://support.archive-it.org/hc/en-us/articles/209637043-Known-Web-Archiving-Challenges#dynamic) with Archive-It is capturing dynamic content, i.e. content that requires human interaction to render properly. This includes Flash, which is used by many old CCA exhibition sites. In instances where content cannot be captured by Archive-It, [WebRecorder](https://webrecorder.io/) will be used. 

Follow the instructions in [WebRecorder's User Guide](https://guide.webrecorder.io/) to create and download a WARC file of the desired website. Upload it to Archive-It using the instructions [here](https://support.archive-it.org/hc/en-us/articles/360000651246-Integrate-external-W-ARC-files-into-Archive-It-collections). 

<a name="metadata"></a>  
## Metadata
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
