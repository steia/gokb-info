# KBART introduction

KBART stands for "Knowledge Base And Related Tools".

## Goals:

+ NISO "Best Practice" for the
    * Transmission of title lists of e-resources offered by a provider in a package 
    * Transmission of inventory information / holdings data from a provider for knowledge bases of link resolvers, ERM systems or discovery interfaces.
    * Data exchange: "KBART is on data exchange among and between knowledge bases" (see [KBART: Knowledge Bases and Related Tools](https://www.uksg.org/sites/uksg.org/files/KBART_Phase_I_Recommended_Practice.pdf))
+ Improvement of data quality exchanged between providers and knowledge bases.
* Complement or replacement of existing metadata formats like ONIX-SOH.

## Links

+ [NISO specification (PDF)](https://groups.niso.org/apps/group_public/download.php/16900/RP-9-2014_KBART.pdf)
+ [KBART Style Guide (Public version)](https://docs.google.com/document/d/1jF154euh8s_RWKX0Tb0ci1W_gzziYKd5ayy5SrjyVEg/edit)
+ [KBART - a publisher'sview (PDF)](https://www.doria.fi/bitstream/handle/10024/93441/Kessler_KBART_Helsinki.pdf?sequence=2)
+ [A deep dive into KBart](https://de.slideshare.net/NASIG/deep-dive-into-kbart)

## File format

[KBART tab-separated template file](https://service-wiki.hbz-nrw.de/download/attachments/470024321/kbart_template_gokb.txt?version=1&modificationDate=1601291143438&api=v2)

## File name

```
{ProviderName}_{Region/Consortia}_{PackageName}_{YYYY-MM-DD}.txt
```

+ ProviderName: Short name of the provider, e.g. Herdt, Springer, Emerald
+ Region/Consortium: Scope of the package.
    * Region: If the package is only offered in one country or other regionally definable area, the country or region should be noted here. Example: Springer_Asia-Pacific_Medicine_2013-01-28.txt
    * Consortia: If the package is tailored for a consortia, that should be noted here. Example: IOP_NESLi2_Option1-2011_2012-05-31.txt
    * If the package is available worldwide "Global" should be added to the file name. Example: TaylorandFrancis_Global_AllTitles_2012-08-30.txt
+ PackageName: Name for the package.
    * Unique name of the package or vendor unique short name of the package.
    * For package with all titles of a provider add "AllTitles" or "AllJournals". Example: TaylorandFrancis_Global_AllTitles_2012-08-30.txt
+ YYYY-MM-DD: date of the KBART file in ISO-8601 format

## File content

+ Tab as separator
+ UTF-8 encoded
+ Date information according to ISO 8601
+ No empty line between header and content
+ Titles should be sorted alphabetically
+ A title should be listed multiple times if there is a "coverage gap" of at least 12 months


## KBART fields

See [Knowledge Bases and Related Tools (KBART)Recommended Practice, Table 5: KBART data fields](https://groups.niso.org/apps/group_public/download.php/16900/RP-9-2014_KBART.pdf) 

|Field Name|Description|Serial/Monograph|
|----------|-----------|----------------|
|publication_title|Publication title for serial or monograph. Conference proceedings series titles should be entered as serial titles, while volume titles should be entered as monograph titles.|S/M|
|print_identifier|Print-format identifier. ISSN for serials, ISBN for monographs, etc. Conference proceedings may have serial ISSNs while each proceeding volume may have its own ISBN.|S/M|
|online_identifier|Online identifier. eISSN for serials, eISBN for monographs, etc. Conference proceedings may have serial eISSNs while each proceeding volume many have its own eISBN.|S/M|
|date_first_issue_online|Date of first serial issue available online. Applicable only to serials.|S|
|num_first_vol_online|Number of first volume available online. Applicable only to serials.|S|
|num_first_issue_online|Number of first issue available online. Applicable only to serials.|S|
|date_last_issue_online|Date of last issue available online. Leave blank if coverage is to the present. Applicable only to serials.|S|
|num_last_vol_online|Number of last volume available online. Leave blank if coverage is to the present. Applicable only to serials.|S|
|num_last_issue_online|Number of last issue available online. Leave blank if coverage is to the present. Applicable only to serials.|S|
|title_url|Title-level URL. Applicable to both serials and monograph. For conference proceedings, the `title_url` for the proceedings series and the `title_url` for each volume should be different.|S/M|
|first_author|First author. Applicable only to monographs.|M|
|title_id|Title identifier. Applicable to both serials and monographs. For conference proceedings, the `title_id` for the conference proceedings series and the `title_id` for each proceeding volume should be different.|S/M|
|embargo_info|Embargo information. Describes any limitations on when resources become available online.|S/M|
|coverage_depth|Coverage depth. For example, abstracts or full text.|S/M|
|notesNotes|Free-text field to describe the specifics of the coverage policy.|S/M|
|publisher_name|Publisher name. Not to be confused with third-party platform hosting name.|S/M|
|publication_type|Serial or monograph. Use "serial" for journals and conference proceeding series. Use "monograph" for e-books and conference proceeding volumes.|S/M|
|date_monograph_published_print|Date the monograph is first published in print|M|
|date_monograph_published_online|Date the monograph is first published online|M|
|monograph_volume|Number of volume for monograph. Applicable to e-books and conference proceedings. For proceedings, use the volume within the conference proceedings series.|M|
|monograph_edition|Edition of the monograph|M|
|first_editor|First editor, Applicable to monographs, i.e., e-books or conference proceedings volumes.|M|
|parent_publication_title_id|Title identifier of the parent publication. For a conference proceeding volume, the `parent_publication_title_id` is the `title_id` of the conference proceedings series.||
|preceding_publication_title_id|Title identifier of any preceding publication title. Applicable to serials and conference proceedings series.|S|
|access_type|Access type.|S/M|

## Proprietary GOKb fields

|Field Name|Description|Serial/Monograph|
|----------|-----------|----------------|
|zdb_id|Title ID form ZDB journal database|S|
|last_changed|Date of last change|S/M|  
|access_start_date|Date when the title was added the package. Date of earliest possible access via package license|S/M|
|access_end_date|Date when title removed from the package. Date of last possible access via package license|S/M|
|medium|Detailed media type of the publication|S/M|  
|DOI of a monograph|DOI identifier or DOI link|M|
|ezb_id|Title ID form ZDB journal database|S| 
|monograph_parent_collection_title|Extension for series titles|S/M|
|subject_area|Subject classes. DDC or choose other via namespaces|S/M|
|listprice_eur|List price in Euro (without currency sign) as numerical value|S/M|
|listprice_gbp|List price in British pounds (without currency sign) as numerical value|S/M|
|listprice_usd|List price in US Dollars (without currency sign) as numerical value|S/M|
