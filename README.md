# Maximizing Splunk Core: Analyzing Splunk Searches Using Audittrail and Native Splunk Telemetry

This repo is as landing page for presentation resources, information, known issues, and updates from the Splunk .Conf 2024 session *Maximizing Splunk Core: Analyzing Splunk Searches Using audittrail and Native Splunk Telemetry* given by Ryan Wood.

If you have any resources, utilities, references that you'd like to share, reach out and let me know.


**2024.06 - Presentation recording will be added here when Splunk makes it available**

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Presentation Slides - Full PDF

**Current Version of Slides: 1.0** - Link to Slides PDF: [Slide Deck](./PLA1837B%20-%20Splunk%20Audittrail%20Native%20Telemetry%20Conf%202024%20Presentation%20v1.0.pdf)


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Contact Information

Email: `ryan.wood@guidepointsecurity.com`  
Splunk UserGroups Slack: `@TheWoodRanger`  
Twitter: `@TheWoodRanger`

**Other presentation repos I've built (great technical references):**
- [Maximizing Splunk SPL: Foreach and the Power of Iterative, Templatized Evals - Presentation Resources & Information](https://github.com/TheWoodRanger/presentation-splunk_foreach)
  - Walkthrough of the `| foreach` command with lots of example SPL utilities and patterns to use.
- [What's in my Data? Field Analysis for the Advanced Engineer](https://github.com/TheWoodRanger/splunk_fields_analysis_presentation)
  - Deep dive of using `| fieldsummary` to summarize Splunk data content with lots of example SPL and utilities.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Table of Contents

- [Maximizing Splunk Core: Analyzing Splunk Searches Using Audittrail and Native Splunk Telemetry](#maximizing-splunk-core-analyzing-splunk-searches-using-audittrail-and-native-splunk-telemetry)
  - [Presentation Slides - Full PDF](#presentation-slides---full-pdf)
    - [Contact Information](#contact-information)
  - [Table of Contents](#table-of-contents)
- [Presentation Slide Deck Resources \& Materials](#presentation-slide-deck-resources--materials)
  - [*A Note on Copying SPL from the PDF*](#a-note-on-copying-spl-from-the-pdf)
  - [Changelog of PDF Slide Deck](#changelog-of-pdf-slide-deck)
- [Other Presentations/Utilities I want to Recommend](#other-presentationsutilities-i-want-to-recommend)
  - [Utilities - Apps and Other Tools Not by Me](#utilities---apps-and-other-tools-not-by-me)
    - [Utilities Not by Me - Data Source Usage](#utilities-not-by-me---data-source-usage)
    - [Utilities Not by Me - Architecture/Admin Support](#utilities-not-by-me---architectureadmin-support)
    - [Utilities Not by Me - Search Information Reporting](#utilities-not-by-me---search-information-reporting)
  - [Presentations - Ryan Wood](#presentations---ryan-wood)
  - [**Presentations - Query Writing and Optimization**](#presentations---query-writing-and-optimization)
  - [Other Presentations - Admin, Developer, Management](#other-presentations---admin-developer-management)
  - [Other Presentations - Dashboard Development](#other-presentations---dashboard-development)
  - [Conf Presentation - Utility SPL From slides](#conf-presentation---utility-spl-from-slides)
    - [Conf Presentation - Macro for Normalizing Search ID](#conf-presentation---macro-for-normalizing-search-id)
    - [Conf Presentation - Utility SPL for Parsing Audittrail](#conf-presentation---utility-spl-for-parsing-audittrail)
    - [Conf Presentation - Utility SPL Provided for Collection of Search Info \& Write to Summary](#conf-presentation---utility-spl-provided-for-collection-of-search-info--write-to-summary)
      - [Notes on Summary Collection SPL Utilities](#notes-on-summary-collection-spl-utilities)
      - [`search/jobs` Metadata Collection SPL - No search.log](#searchjobs-metadata-collection-spl---no-searchlog)
      - [`search/jobs/<search ID>/search.log` search.log Collection SPL - Both MetaData and search.log](#searchjobssearch-idsearchlog-searchlog-collection-spl---both-metadata-and-searchlog)
      - [Reporting SPL Using Collected Summary Data](#reporting-spl-using-collected-summary-data)
        - [Reporting SPL - `/search/jobs` Metadata - `sourcetype=`](#reporting-spl---searchjobs-metadata---sourcetype)
        - [Reporting SPL - `search.log` via REST - `sourcetype=search_jobs_search_log_events`](#reporting-spl---searchlog-via-rest---sourcetypesearch_jobs_search_log_events)


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Presentation Slide Deck Resources & Materials

Presentation slides will be updated as issues are identified or additional functionality is made available, see below link for latest version.

**Current Version of Slides: 1.0** - Link to Slides PDF: [Slide Deck](./PLA1837B%20-%20Splunk%20Audittrail%20Native%20Telemetry%20Conf%202024%20Presentation%20v1.0.pdf)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## *A Note on Copying SPL from the PDF*

PDFs do not preserve whitespace when copying text, so while you can copy all of the queries within these slides, they won't stay formatted.

Use the key combination `CTRL/CMD + Shift + F` within your Splunk search page to format the query automatically. Note: this may weirdly affect alignment on subsearches, multiple eval conditions, comment lines within the SPL queries.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Changelog of PDF Slide Deck

<details>
<summary>v1.0 - 2024.06.10</summary>

>  - Initial upload of slides with material presented at .Conf 2024.
</details>



------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Other Presentations/Utilities I want to Recommend

These are some other presentations that I've found particularly beneficial or filled with useful information. This is by no means exhaustive, but it's my point of perspective on some great sessions.

Past Conf sessions not currently available on the Conf website can be accessed via the Conf Archive app (shoutout to Lily Lee):
<https://splunkbase.splunk.com/app/3330>

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Utilities - Apps and Other Tools Not by Me

Apps referenced during the 2024 conf presentation here. If you'd like to share your work, reach out!


### Utilities Not by Me - Data Source Usage

- Ingestion of search.log - IUF App by David Paper
- Regex on SPL for Data/Object Usage Reporting:
  - See slides for specific objects.
  - [Sideview UI](https://splunkbase.splunk.com/app/6449)
  - [Splunk Cloud Migration Assessment](https://splunkbase.splunk.com/app/4974)
  - [Admin Pilot For Splunk](https://splunkbase.splunk.com/app/6489)
  - [Alerts for Splunk Admins](https://splunkbase.splunk.com/app/3796)


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Utilities Not by Me - Architecture/Admin Support


- [Utilities for Converting Internal Metrics to MetricStore Format by Silkyrich](https://github.com/silkyrich/splunk_internal_metrics)
  - Conversion of internal metrics data to metrics format events for better storage and search performance using mstats

- [Splunk Cluster Health Reporting Dashboards by Silkyrich](https://github.com/silkyrich/cluster_health_tools/tree/master)
  - Multiple dashboards for reporting on cluster health and metrics.

- [Dashboard for Metrics on Ingestion Blocks](https://github.com/dpaper-splunk/public/blob/master/dashboards/metrics_related_to_ingestion_blockage.xml)
  - Looks at data ingestion metrics including forwarder and indexer tiers. Designed to work with Splunk Cloud, but can be easily adapted to on prem

- [Getting Smarter about Splunk SmartStore](https://github.com/redvelociraptor/gettingsmarter/tree/main)
  - Reporting related to Splunk SmartStore activity

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Utilities Not by Me - Search Information Reporting

- [David Paper's Extended Search Reporting XML Dashboard](https://github.com/dpaper-splunk/public)
  - Looks at Search load in Splunk with a different lens than Monitoring Console. Works for both Splunk Cloud and Splunk on premise

- [Redundant & Inefficient Search Spotter App - Splunk Works](https://splunkbase.splunk.com/app/7300)
  - See PLA1457B (.conf24)

- Search Reporting Dashboards/Utilities by Nico V:
  - Bundle Push Investigator
  - High CPU Searches
  - Headroom Estimation
  - Role Quota Reducer
  - Savedsearch Analyzer
  - Search Analysis by Type
  - Search Duration Analysis
  - Search Rescheduler Tool
  - S3 Activity



------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Presentations - Ryan Wood

I've given two other technical deep dive presentations in recent years that follow the example of this talk with extreme depth and lots of examples to use:
- [Maximizing Splunk SPL: Foreach and the Power of Iterative, Templatized Evals - Presentation Resources & Information](https://github.com/TheWoodRanger/presentation-splunk_foreach)
  - Walkthrough of the `| foreach` command with lots of example SPL utilities and patterns to use.
- [What's in my Data? Field Analysis for the Advanced Engineer](https://github.com/TheWoodRanger/splunk_fields_analysis_presentation)
  - Deep dive of using `| fieldsummary` to summarize Splunk data content with lots of example SPL and utilities.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## **Presentations - Query Writing and Optimization**

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**On the topic of term efficiency, search optimization (you definitely should learn this stuff!):**

- [PLA1089C - TSTATS and PREFIX, How to get the most out of your lexicon with walklex, tstats, indexed fields, PREFIX, TERM](https://conf.splunk.com/files/2020/slides/PLA1089C.pdf)
- [PLA1466B - Fields, Indexed Tokens, and You](https://conf.splunk.com/files/2022/slides/PLA1466B.pdf)
- [PLA1258C - I Am Speed! Searching on Your Own TERMs With Simple Techniques That 99% Aren’t Using!](https://conf.splunk.com/files/2023/slides/PLA1258C.pdf)
- [TRU1133B - Clara-Fication: More Tstats for Your Buckets](https://conf.splunk.com/files/2021/slides/TRU1133B.pdf)
- [PLA1162B - Clara-Fication: Finding and Improving Expensive Searches](https://conf.splunk.com/files/2022/slides/PLA1162B.pdf)


**Docs or Blogs on Search Optimization:**

- Splunk Blog - [Splunk Clara-fication Search Best Practices](https://www.splunk.com/en_us/blog/customers/splunk-clara-fication-search-best-practices.html)
- Splunk Lantern on Optimizing searches:
  - [Lantern - Optimizing Search](https://lantern.splunk.com/Splunk_Platform/Product_Tips/Searching_and_Reporting/Optimizing_search)
  - [Lantern - Writing Better Search Queries](https://lantern.splunk.com/Splunk_Platform/Product_Tips/Searching_and_Reporting/Writing_better_queries_in_Splunk_Search_Processing_Language)
- [Whitepaper on Splunk Scheduled Search Management](https://github.com/dpaper-splunk/public/blob/master/whitepapers/Splunk%20Scheduled%20Search%20Management.pdf)


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**On the topic of understanding job performance:**
- [TRU1143C - Clara-fication: Job Inspector](https://conf.splunk.com/files/2020/slides/TRU1143C.pdf)
- [PLA1162B - Clara-Fication: Finding and Improving Expensive Searches](https://conf.splunk.com/files/2022/slides/PLA1162B.pdf)
- [YouTube - Using the Splunk job inspector](https://www.youtube.com/watch?v=n3OqaB6GVXs)


**Documentation on Job Inspector:**

- [Docs - Dispatch Directory Artifact Files, Structure, Description](https://docs.splunk.com/Documentation/SplunkCloud/latest/Search/Dispatchdirectoryandsearchartifacts)
- [Docs - Enterprise - View Search Job Properties with Job Inspector](https://docs.splunk.com/Documentation/Splunk/latest/Search/ViewsearchjobpropertieswiththeJobInspector)
- [Docs - Cloud - View Search Job Properties with Job Inspector](https://docs.splunk.com/Documentation/SplunkCloud/latest/Search/ViewsearchjobpropertieswiththeJobInspector)
- [Lantern - Troubleshooting/Investigating Searches with Job Inspector](https://lantern.splunk.com/Splunk_Platform/Product_Tips/Searching_and_Reporting/Troubleshooting_and_investigating_searches)


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**On the topic of Security Usecase/SPL Techniques:**
- [PLA1528B - Master Joining Datasets Without Using Join](https://conf.splunk.com/files/2022/slides/PLA1528B.pdf)
- [PLA1261B - Beyond REGULAR Regular Expressions v3.0](https://conf.splunk.com/files/2022/slides/PLA1261B.pdf)
- [PLA1547B - Lighter, Faster and Calmer Ways to Learn Splunk® Enterprise With | makeresults, | gentimes and Some Random()% Too!](https://conf.splunk.com/files/2023/slides/PLA1547B.pdf)
  - Note: Updated Presentation in 2024 - PLA1211B
- [TRU1192B - Getting To Know Your Data](https://conf.splunk.com/files/2021/slides/TRU1192B.pdf)
- [Turning Security Use Cases into SPL](https://static.rainfocus.com/splunk/splunkconf18/sess/1523489574149001lr6z/finalPDF/SEC1583_TurningSecurityUseCases_Final_1538510573435001VmSg.pdf)
- Security Ninjutsu Series - also available via [David Veuve's website](https://www.davidveuve.com/presentations.html)
  - Security Ninjutsu Part Four
  - Security Ninjutsu Part Five
  - Security Ninjutsu Part Six


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Other Presentations - Admin, Developer, Management

- [DEV1480C - Using Splunk® Cloud Platform ACS Through CI/CD](https://conf.splunk.com/files/2023/slides/DEV1480C.pdf)
- [DEV1387B - Deep Dive Into the Custom Search Protocol v2: How t Implement a Custom Search Command](https://conf.splunk.com/files/2021/slides/DEV1387B.pdf)
- [PLA1135B - Administrators Anonymous IV: Splunk Best Practices and Useful Tricks I Learned the Hard Way](https://conf.splunk.com/files/2022/slides/PLA1135B.pdf)
- [PLA1765C - Git Good With Splunk: Commit to Config Versioning and Deployment Automation for Your Splunk Infrastructure](https://conf.splunk.com/files/2023/slides/PLA1765C.pdf)
- [PLA1265B - Maximize Your Splunk Value With Workload Management](https://conf.splunk.com/files/2023/slides/PLA1265B.pdf)

- [Disk Diagnosis: Whitepaper walkthrough of disk performance evaluation](https://github.com/dpaper-splunk/public/blob/master/whitepapers/Digging%20Deep%20into%20Disk%20Diagnoses.pdf)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Other Presentations - Dashboard Development

- [PLA1577B - Dashboarding Wowzas! Top Tips for Making Your Dashboards Awesome! (Conf 2023)](https://conf.splunk.com/files/2023/slides/PLA1577B.pdf)
- [PLA1128C - Dashboarding Wowzas! Top Tips for Making Your Dashboards Awesome! (Conf 2023)](https://conf.splunk.com/files/2023/slides/PLA1577B.pdf)


**Docs/Blog Posts on Dashboard Development:**
- Splunk Blog - [Splunk Clara-fication Dashboarding Best Practices](https://www.splunk.com/en_us/blog/tips-and-tricks/splunk-clara-fication-dashboarding-best-practices.html)
- Splunk Blogs - All posts by Lizzy Li are focused around UI and full of great information: [Lizzy Li's Splunk Blog Posts](https://www.splunk.com/en_us/blog/author/elizabethl.html)



------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Conf Presentation - Utility SPL From slides

These SPL queries are provided in the PDF, but referenced here for easier access. **These are only a small portion of everything provided in the PDF, just highlights.**

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Conf Presentation - Macro for Normalizing Search ID

`get_normalized_search_id(1)` - Contained in Splunk Cloud Migration Assessment app as of 2024.06.10

Put in macros.conf or copy definition to Web UI

```conf
[get_normalized_search_id(1)]
description = Normalize Splunk Search ID
args = search_id
definition = rex field=$search_id$ mode=sed "s/^'|'$//g" \
| rex field=$search_id$ "_(?<search_id_normalized1>\d+[._]\d+)_" \
| rex field=$search_id$ "(?<search_id_normalized2>\d+[._]\d+$)" \
| rex field=$search_id$ "(?<search_id_normalized3>^\d+[._]\d+)" \
| eval search_id_normalized=if(isnull(search_id_normalized1),search_id_normalized2,search_id_normalized1) \
| eval search_id_normalized=if(isnull(search_id_normalized),search_id_normalized3,search_id_normalized) \
| eval search_id_normalized=if(isnull(search_id_normalized),search_id,search_id_normalized)\
| rex field=search_id_normalized mode=sed "s/\./_/g"\
| rex field=search_id_normalized mode=sed "s/^\w+;.*;|^_ACCELERATE_DM_|^_ACCELERATE_|_ACCELERATE_$//g"\
| fields - search_id_normalized1,search_id_normalized2,search_id_normalized3
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Conf Presentation - Utility SPL for Parsing Audittrail

Audittrail includes full SPL queries, so auto extraction often picks up false fields from the original search SPL. To avoid this, manually exrtract all queries you want to work with:

```spl
(index=_audit sourcetype=audittrail source="*audit.log*" action=search)
| rex field=_raw max_match=0 "sourcetype_count__(?<sourcetype_val>\w+)=(?<eventCount>\d+)"
| rex field=_raw ",\ssavedsearch_name=\"(?<savedsearch_name>[^\"]+?)\""
| rex field=_raw ",\ssearch_id='(?<search_id>[^',]+)"
| rex field=_raw ",\sapp=\"(?<app>[^\"]+)\""
| rex field=_raw ",\suser=(?<user>[^,]+)"
| rex field=_raw ",\sinfo=(?<info>[^,]+)"
| rex field=_raw ",\ssearch='(?<searchQuery>[\W\w\n]+)'((,\sautojoin=)|(\])|(,\sis_federated_search=)|(,\sincomplete_bucket_maps=)|(,\s[^\s=]+=))"
| eval searchQuery = replace(searchQuery, "',\s[^\s=]+='[^']+$", "")

```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Conf Presentation - Utility SPL Provided for Collection of Search Info & Write to Summary

SPL queries presented within .Conf 2024 presentation for collection of information from REST `/search/jobs` endpoint and collection of `search.log` files via REST.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### Notes on Summary Collection SPL Utilities


**Tuning/Configuration**

- Change `index=summary` to whatever index is desired for storing data
  - Change both `| collect` and `| search` lines to this new index location. Subsearch filter must always be the same as collect output to ensure SIDs are only captured once.
  - Ensure appropriate RBAC is applied to wherever this audit information is stored.
- Create scheduled search for this process. Ensure it has permissions to use REST endpoints.
  - Schedule should ideally be every 2 minutes, but start with every 5m and ensure no issues with dispatch directory reaping.



**Functionality Notes**
- See slides 128-133 for SPL highlights and tips for usage.
- The collection SPL uses the summary index to filter SIDs already written. Within the SPL, this is the `| search NOT []` subsearch line.
  - See slide 131 for SPL and example of this output.
- Collection SPL filters to searches dispatched in last 4 hours by default.
  - Needed to avoid long-lived artifacts from being repeatedly written due to summary index subsearch limit.
- Will only write summary events when population search job is scheduled. Ad-hoc runs will not write to summary index
  - See slide 132 for info on this.
- Uses `| foreach` to clean empty-string field values.



**Best Practice**
- Always filter out any other searches that are using `/search/jobs` endpoint to avoid recursion risk.
- See Splunk Docs for information on fields returned from REST endpoints:
  - `/search/jobs` [Documentation Link](https://docs.splunk.com/Documentation/Splunk/latest/RESTREF/RESTsearch#search.2Fjobs)
  - `/search/jobs/<sid>/search.log` Documentation Link
- Be sure to merge all important fields across all SIDs for a given primary process. 
  - Savedsearch label and keywords are merged in provided SPL, but fields can be aggregated further as desired.
- Be mindful of `dispatchState` field value


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


#### `search/jobs` Metadata Collection SPL - No search.log

Collects metadata information on searches and writes to summary index. Does not collect search.log file information.

Version 1.0 - 2024.06.10

> Example search name: `PopulateSummary - Search Jobs REST Data Collection - No search.log`

```spl
| rest /servicesNS/-/-/search/jobs splunk_server=*
   search="sid!=SummaryDirector*" search="sid!=rsa_*" search="sid!=rt_*"
| rename title AS searchQuery, sid AS search_id, label AS savedsearch_label, eai:acl.app AS appName, eai:acl.owner AS owner, eventFieldCount AS rawEventFieldsReturned
   ``` FILTER - Drop any search jobs you know you don't want - Defaults are any search/jobs query and either of the presentation collection queries ```
| search NOT searchQuery IN ("*/search/jobs*", "*search_log_events*", "*search_jobs_rest_collection*", "*search_jobs_search_log_data*")
   ``` FILTER - Drop any SIDs that have already been written to the summary location
   Subsearch passes compiled filter string: splunk_server=<host> AND search_id IN (...)```
| search NOT [search index=summary sourcetype=search_jobs_rest_collection earliest=-4h@h latest=+4h@h
   | rex field=_raw ", search_id=\"?(?<search_id>[^\",]+)\"?,"
   | rex field=_raw "orig_splunk_server=\"(?<orig_splunk_server>[^\"]+)"
   | stats values(search_id) AS search_id_list BY orig_splunk_server
   | eval "Combined Subsearch Filter for REST API Collection Job" = "( splunk_server=\"" . orig_splunk_server . "\" AND search_id IN (\"" . mvjoin(search_id_list, "\", \"") . "\") )"
   | rename "Combined Subsearch Filter for REST API Collection Job" AS search
   | table search]
   ``` FILTER - to search artifacts published within last 4h - Timerange here should be same as in the search NOT filter above/below. ```
| eval _time = strptime(published, "%Y-%m-%dT%H:%M:%S.%3N")
| where _time >= relative_time(now(), "-4h")
   ``` Output to summary index will not include original SPL, if you want the original SPL join on sourcetype=audittrail with search_id ```
| table _time, splunk_server, search_id, savedsearch_label, appName, owner, dispatchState, keywords, runDuration, searchEarliestTime, searchLatestTime, diskUsage, rawEventFieldsReturned, resultCount, eventCount, scanCount, dropCount, searchTotalEliminatedBucketsCount, searchTotalBucketsCount, performance.command.search.index.invocations, performance.command.search.kv.duration_secs, priority, provenance, dispatchAs, request.ui_dispatch_app, eventSearch, published
   ``` Handle all empty string false-null fields returned from API by explicitly setting to null if length is less than 1 ```
| foreach *
   [| eval <<FIELD>> = if( isnull('<<FIELD>>') OR len('<<FIELD>>') < 1, null(), '<<FIELD>>')]
   ``` Generate normalized SID to populate savedsearch_label value properly across search artifacts ```
| `get_normalized_search_id(search_id)`
   ``` Aggregate key fields across SIDs using normalized SID - Note: min_sid_length is used to identify primary search ```
| eventstats min(eval(len(search_id))) AS min_sid_length, values(savedsearch_label) AS savedsearch_label, values(keywords) AS all_keywords BY search_id_normalized
| eval isPrimarySID = if( len(search_id)=min_sid_length AND !match(search_id, "^(remote|subsearch)"), 1, 0 )
| fields - min_sid_length
   ``` FILTER - Do not write summary index event if the search is not DONE - wait until this point to ensure label is passed to all subsearch artifacts ```
| search dispatchState="DONE"
   ``` Clean/Modify data as needed in preparation to write to summary index ```
| eval endpoint = "/servicesNS/-/-/search/jobs"
| foreach searchEarliestTime, searchLatestTime, runDuration
   [| eval <<FIELD>> = round('<<FIELD>>', 0)]
| addinfo | fields - info_*time | rename info_sid AS population_sid
   ``` Write output from search/jobs base collection to Summary Index - use appendpipe to avoid writing summary events in ad-hoc search ```
| appendpipe
   [| where match(population_sid, "^(scheduler|_scheduler_)")
   | collect testmode=f addinfo=f index=summary sourcetype=search_jobs_rest_collection marker="search_jobs_rest_collection_job"
   | where false()]

```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### `search/jobs/<search ID>/search.log` search.log Collection SPL - Both MetaData and search.log

Collects and writes information to summary index from REST api via scheduled search:
- Metadata information on searches from `/search/jobs` base REST endpoint
- search.log information filtered to Index Usage lines identified and discussed in presentation

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Functionality Notes Specific to this Collection SPL**

- Default target: `index=summary sourcetype=search_jobs_search_log_events`
- Only Primary SIDs - all child SIDs are rolled into Primary search.log
- Filters to specific search.log lines identified during presentation
- SPL uses | map - creates new subsearch for every input SID
  - search.log vs search.log.1 requires multiple calls. SPL below covers up to search.log.2
  - Default `maxsearches` value for map command is 200,000 here
- Uses foreach to manually construct _raw output field
  - Original line and Meta fields separated by string "~~~META:"
  - Be cautious changing order of fields without updating SPL that consumes this summary data using regex patterns expecting specific sequence.



Version 1.0 - 2024.06.10

> Example Search Name: `PopulateSummary - Search Jobs REST Data Collection WITH search.log Capture`

```spl
| rest /servicesNS/-/-/search/jobs splunk_server=*
   search="sid!=SummaryDirector*" search="sid!=rsa_*" search="sid!=rt_*"
| rename title AS searchQuery, sid AS search_id, label AS savedsearch_label, eai:acl.app AS appName, eai:acl.owner AS owner, eventFieldCount AS rawEventFieldsReturned
   ``` FILTER - Drop any search jobs you know you don't want - Defaults are any search/jobs query and either of the presentation collection queries ```
| search NOT searchQuery IN ("*/search/jobs*", "*search_log_events*", "*search_jobs_rest_collection*", "*search_jobs_search_log_data*")
   ``` FILTER - Drop any SIDs that have already been written to the summary location
   Subsearch passes compiled filter string: splunk_server=<host> AND search_id IN (...)```
| search NOT [search index=summary sourcetype=search_jobs_rest_collection earliest=-4h@h latest=+4h@h
   | rex field=_raw ", search_id=\"?(?<search_id>[^\",]+)\"?," | rex field=_raw "orig_splunk_server=\"(?<orig_splunk_server>[^\"]+)"
   | stats values(search_id) AS search_id_list BY orig_splunk_server
   | eval "Combined Subsearch Filter for REST API Collection Job" = "( splunk_server=\"" . orig_splunk_server . "\" AND search_id IN (\"" . mvjoin(search_id_list, "\", \"") . "\") )"
   | rename "Combined Subsearch Filter for REST API Collection Job" AS search | table search]
   ``` FILTER - to search artifacts published within last 4h - Timerange here should be same as in the search NOT filter above/below. ```
| eval _time = strptime(published, "%Y-%m-%dT%H:%M:%S.%3N")
| where _time >= relative_time(now(), "-4h")
   ``` Output to summary index will not include original SPL, if you want the original SPL join on sourcetype=audittrail with search_id ```
| table _time, splunk_server, search_id, savedsearch_label, appName, owner, dispatchState, keywords, runDuration, searchEarliestTime, searchLatestTime, diskUsage, rawEventFieldsReturned, resultCount, eventCount, scanCount, dropCount, searchTotalEliminatedBucketsCount, searchTotalBucketsCount, performance.command.search.index.invocations, performance.command.search.kv.duration_secs, priority, provenance, dispatchAs, request.ui_dispatch_app, eventSearch, published
   ``` Handle all empty string false-null fields returned from API by explicitly setting to null if length is less than 1 ```
| foreach * [| eval <<FIELD>> = if( isnull('<<FIELD>>') OR len('<<FIELD>>') < 1, null(), '<<FIELD>>')]
   ``` Generate normalized SID to populate savedsearch_label value properly across search artifacts ```
| `get_normalized_search_id(search_id)`
   ``` Aggregate key fields across SIDs using normalized SID - Note: min_sid_length is used to identify primary search ```
| eventstats min(eval(len(search_id))) AS min_sid_length, values(savedsearch_label) AS savedsearch_label, values(keywords) AS all_keywords BY search_id_normalized
| eval isPrimarySID = if( len(search_id)=min_sid_length AND !match(search_id, "^(remote|subsearch)"), 1, 0 )
| fields - min_sid_length
   ``` FILTER - Do not write summary index event if the search is not DONE - wait until this point to ensure label is passed to all subsearch artifacts ```
| search dispatchState="DONE"
   ``` Clean/Modify data as needed in preparation to write to summary index ```
| eval endpoint = "/servicesNS/-/-/search/jobs"
| foreach searchEarliestTime, searchLatestTime, runDuration
   [| eval <<FIELD>> = round('<<FIELD>>', 0)]
| addinfo | fields - info_*time | rename info_sid AS population_sid
   ``` Write output from search/jobs base collection to Summary Index - use appendpipe to avoid writing summary events in ad-hoc search ```
| appendpipe
   [| where match(population_sid, "^(scheduler|_scheduler_)")
   | collect testmode=f addinfo=f index=summary sourcetype=search_jobs_rest_collection marker="search_jobs_rest_collection_job"
   | where false()]
   ``` END search/jobs collection - BEGIN search.log collection ```
   ``` FILTER - Only pass the primary SIDs ```
| search isPrimarySID = 1
   ``` search.log can be split into multiple files for larger searches - here we generate new rows for each search ID to ensure we capture these expanded log files if they exist.
       NOTE: This will generate many search message errors since most of these will not exist most of the time. ```
| eval search_log_counter = split("search.log, search.log.1, search.log.2", ", ")  | mvexpand search_log_counter
   ``` Set the REST url the map command will query by using the search ID and the generated counter reference ```
| eval search_job_rest_url = "/servicesNS/-/-/search/jobs/" . search_id . "/" . search_log_counter
   ``` Run a new search to collect search.log for each input row, specifying the splunk_server that returned data previously. Pass the input field values by eval'ing them within map ```
| map maxsearches=200000
   search="| rest \"$search_job_rest_url$\" splunk_server=\"$splunk_server$\" | eval search_id = \"$search_id$\" | eval endpoint = \".../$search_log_counter$\" | eval app = \"$appName$\" | eval owner = \"$owner$\" | eval savedsearch_label = \"$savedsearch_label$\"
   | rename value AS search_log_line"
   ``` Convert search.log text block into multivalue, then split into individual rows ```
| makemv search_log_line tokenizer="([^\n]+)"
| stats first(*) AS * BY search_id, search_log_line
    ``` FILTER - Only keep search.log lines that we care about ```
| search search_log_line IN ("*BatchSearch is initialized*", "*Search requires the following indexes*", "*IndexScopedsearch is called for index*")
   ``` Clean/Modify search.log data as needed in preparation to write to summary index.
   NOTE: search_log_events raw format follows schema: <original search.log line> ~~~META:, <meta fields from collection job> ```
| rename splunk_server AS log_src_server
| eval _raw = search_log_line . " ~~~META:"
   ``` Manually create the _raw for the summary event, concatenating the original search.log line and the other fields from collection job in csv key=value format
   NOTE: This ensures a consistent ordering of fields. Do not change the order of the foreach field references without updating the regular expressions in search_id extractions as well. ```
| foreach app, endpoint, search_id, log_src_server, owner, savedsearch_label
   [| eval _raw = if( isnotnull('<<FIELD>>'), _raw . ", <<FIELD>>=\"" . '<<FIELD>>' . "\"", _raw)]
   ``` Write output of search.log collection to Summary Index - use appendpipe to avoid writing summary events in ad-hoc search ```
| appendpipe
   [| addinfo | fields - info_*time | rename info_sid AS population_sid
   | where match(population_sid, "^(scheduler|_scheduler_)") | fields - population_sid
   | collect testmode=f addinfo=f index=summary sourcetype=search_jobs_search_log_events marker="search_jobs_rest_collection_search_log_data"
   | where false()]

```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### Reporting SPL Using Collected Summary Data

Reporting SPL shown in presentation that consumes summary data written by SPL utilities above for search/jobs and search.log information.

##### Reporting SPL - `/search/jobs` Metadata - `sourcetype=`

Breakout of `keywords` information captured from Metadata collection job against `/search/jobs` REST endpoint:

```spl
index=summary sourcetype=search_jobs_rest_collection isPrimarySID=1
| rex field=_raw ", search_id=\"?(?<search_id>[^\",]+)\"?,"
| rex field=_raw ", savedsearch_label=\"?(?<savedsearch_label>[^\",]+)\"?,"
| rex field=all_keywords max_match=0 "index::(?<index_keywords>[^\s\n]+)"
| rex field=all_keywords max_match=0  "sourcetype::(?<sourcetype_keywords>[^\s\n]+)"
| rex field=all_keywords max_match=0  "source::(?<source_keywords>[^\s\n]+)"
| stats dc(search_id) AS search_count, values(*_keywords) AS *_keywords 
BY savedsearch_label
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


##### Reporting SPL - `search.log` via REST - `sourcetype=search_jobs_search_log_events`

Breakout of index references based on search.log lines correlated with Index Usage insights:

```spl
index=summary sourcetype=search_jobs_search_log_events
| rex field=_raw ", search_id=\"?(?<search_id>[^\",]+)\"?,"
| rex field=_raw ", savedsearch_label=\"?(?<savedsearch_label>[^\",]+)\"?,"
| rex field=_raw "^(?<orig_search_log_line>.+?)~~~META:?,\s"
| rex field=orig_search_log_line "IndexScopedSearch is called for index = (?<index_usage_reference>[^\s,]+)"
| rex field=orig_search_log_line "Search requires the following indexes\s*=\s*\"\[(?<index_usage_array_reference>[^\]]+)"
| rex field=orig_search_log_line "BatchSearch is initialized for indexes\s*=\s*\{(?<index_usage_tuple_reference>[^\}]+)"
| eval index_usage_array_reference = split(index_usage_array_reference, ",")
| eval index_usage_tuple_reference = split(index_usage_tuple_reference, ",")
| stats dc(search_id) AS search_count, values(index_usage_*) AS index_usage_* BY savedsearch_label
```

