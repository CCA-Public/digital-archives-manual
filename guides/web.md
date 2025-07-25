# Capturing Web Archives using Archive-It

Web archiving is the practice of using capture tools to crawl websites and save their contents. These result in web archiving (WARC) files, a container file that packages all of the code, media, and other elements of a website. WARC files are the preservation format for websites and can be played back to display the website as it appeared on the live web at the time of capture. 

CCA uses the web app [Archive-It](https://archive-it.org/) to capture certain types of web content related to our collecting interests. The web collections can be accessed through the [CCA microsite](https://archive-it.org/home/Canadian-Centre-for-Architecture). Metadata is controlled locally, and playback is mediated through the [Wayback Machine](https://archive.org/web/). 

Archive-It has a [Help Center](https://support.archive-it.org/hc/en-us), [User Guide](https://support.archive-it.org/hc/en-us/articles/360041250172-Guide-for-new-Archive-It-users), and [Community Forum](https://support.archive-it.org/hc/en-us/community/topics), which should serve as primary documentation and a resource for troubleshooting. 
 
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

Note that every time you add a new seed, you **MUST** run a [test crawl](https://support.archive-it.org/hc/en-us/articles/208001226-Run-monitor-and-save-a-test-crawl). This ensures that the final production crawl saved to the archive is properly scoped. Production crawls cannot be deleted, meaning that an incorrectly scoped crawl can eat up a large amount of the data budget. However, test crawls can be saved, and this is the preferred starting point, especially for seeds being crawled for the first time. 

The CCA websites (French/English) are both scheduled to do a shallow crawl weekly. A quarterly full crawl is also recommended, but needs to be kicked off manually. As of writing, all other seeds were scheduled for a one-time crawl.

<a name="webrecorder"></a> 
### Using WebRecorder to capture dynamic content
One [known issue](https://support.archive-it.org/hc/en-us/articles/209637043-Known-Web-Archiving-Challenges#dynamic) with Archive-It is capturing dynamic content, i.e. content that requires human interaction to render properly. This includes Flash, which is used by many old CCA exhibition sites. In instances where content cannot be captured by Archive-It, [WebRecorder](https://webrecorder.io/) will be used. 

Follow the instructions in [WebRecorder's User Guide](https://guide.webrecorder.io/) to create and download a WARC file of the desired website. Upload it to Archive-It using the instructions [here](https://support.archive-it.org/hc/en-us/articles/360000651246-Integrate-external-W-ARC-files-into-Archive-It-collections). 

<a name="metadata"></a>  

## Metadata
Description should live in three places: seed-level metadata should be in Archive-It and CCA's library catalog, and fonds-level metadata should be in TMS.

### Archive-It description
Metadata can be added to individual seeds by clicking a seed URL and navigating to the "Metadata" tab. Click "Edit" to begin entering metadata in fields; you must click "Add" for the changes to save. The following fields are required for all seeds: 
- **Title:** Use the "Grab title" feature when possible. Feel free to edit the "Grab title" results if they are especially long or do not represent an appropriate title. If the "Grab title" feature does not work for a particular seed, generate the title of the website using your best judgment. 
- **Creator:** The organizition or individual responsible for the creating the content of a website.
- **Contributor:** Includes any "meaningful but secondary" contributors to a resource not covered by other fields. 
- **Date:** Year values related to the website. This minimally should include the year of the crawl, and can also include exhibition dates. Each year should be entered seperately and contextualized. Examples:
  -2012-2016 (published)
  -2013-2014 (exhibition dates)
  -2018 (captured)
 -Captured 2018
 - **Type:** This will always be "web archives" for archived content (i.e. one-time crawls) and "websites" for lives sites (i.e. ongoing, scheduled crawls). 
- **Format:** Entered in the "Format" field. This will always be "1 archived website." 
- **Relation (required if applicable):** If the website relates to another archival fonds at CCA, provide the title of the fonds with a link to the finding aid.
- **Source:** This will always be "Description based on archived web page captured (date of capture). Last updated (date)." 
- **Collector:** This will always be "Canadian Centre for Architecture". 
- **Language:** Major language(s) represented on a website. Each language should be entered seperately (e.g. "English" "French", not "English and French"). 

The following fields are optional: 
- **Subjects (recommended):** 1-3 subjects related to the website available in [searchFAST](http://fast.oclc.org/searchfast/), including the Creator. While subject analysis is typically outside of typical CCA archival description, it will make our seeds more discoverable within the Archive-It and Wayback environments. 
- **Description (recommended):** A 3-5 sentence summary of the website's contents. This can be copy-and-pasted directly from the website's "About" page (or similar). It is also recommended that this include provenance information (i.e. why a particular site was chosen for capture) where relevant.
- **Publisher (if needed):** To be used only if the Publisher differs from the Creator.
- **Coverage (recommended):** A place name available in [searchFAST](http://fast.oclc.org/searchfast/).

All other fields are not used.

### Catalog description
There should one record in the library catalog for each seed. These will map exactly to the descriptions in Archive-It; see the [OCLC Descriptive Metadata for Web Archiving](https://www.oclc.org/content/dam/research/publications/2018/oclcresearch-wam-recommendations.pdf) for a MARC-Archive-It crosswalk. Access will be available with the URL of the landing page of each seed ([for example](https://wayback.archive-it.org/10908/*/http://we-aggregate.org/)).

Send the cataloger (Mary) a spreadsheet once a month with new seeds to catalog. Seeds with recurring, scheduled crawls only need to be updated after the first crawl of a new year to reflect the new date.

### TMS description and ingest into Archivematica
At the end of every Archive-It subscription period, CCA will accession a hard drive of all of the WARCs captured during that year. A fonds-level record will need to be created, and accessions should be nested underneath it. Appropriate metadata standards should follow the [OCLC Descriptive Metadata for Web Archiving](https://www.oclc.org/content/dam/research/publications/2018/oclcresearch-wam-recommendations.pdf) and will be developed at the time of the first accession. Once the TMS metadata is completed, the WARCs should be ingested into Archivematica. 
