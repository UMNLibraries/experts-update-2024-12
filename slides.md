## Experts@Minnesota Project Update
### David Naughton
#### Application Development
#### Libraries/Minitex IT meeting, December 2024
---
## What is Experts@Minnesota?

> [Experts@Minnesota](https://experts.umn.edu) is the research information management tool for the 
> University of Minnesota. It uses University records and publication data
> harvested from Scopus to create public profiles for University of Minnesota
> faculty and researchers.

-- [https://libguides.umn.edu/experts-at-mn](https://libguides.umn.edu/experts-at-mn)
---
## University-wide project

* Provost's office uses it to collect information on all centers/institutes
  * Centers/institutes must be in Experts to receive funding
* Colleges, departments,and other organizations use it for reporting and faculty profiles
  * Especially useful for centers/institutes that are not represented in PeopleSoft
* Researchers use it to advertize their research to the public
---
## How does it work?

* [experts.umn.edu](https://experts.umn.edu) runs [Pure](https://www.elsevier.com/products/pure) (PUblished REsearch) by Elsevier
* Pure matches research output metadata to UMN researcher demographic, grant, & project data
* Most research output metadata comes from [Scopus](https://www.elsevier.com/products/scopus)
---
### Etymology

Fun fact: Experts@Minnesota orginally used yet another Elsevier product, SciVal Experts
---
## AppDev: data engineering

* Provide UMN researcher demographics, grant, and project data to Pure
* Download Pure data, using the Pure API, into a local database for custom reporting
---
## Updates
---
## Collections Analysis Report

* Tells us what journals UMN researchers use
  * i.e., what journals are publishing articles authored by UMN researchers, and the articles cited by UMN researchers
* Helps us decide which journals to add to or remove from our collections
* Combines data from Pure, Scopus, and UMN systems
---
## Collections Analysis Report: Problems

* No caching. Re-downloads all data for every run
* Takes at least three days to run
* Can be run only on a librarian’s laptop
* So painful, we rarely run it
---
## Collections Analysis Report: Solutions

* Continuously update the data, in a remote database
* Publish the report on the web, using Tableau
* Automate everything
---
## CAR: Solution details

* Process multiple records at a time
  * Bulk operations and mathematical set operations
  * Parallelism/concurrency/asynchrony
* ELT instead of ETL
  * Extract > Load > Transform instead of Extract > Transform > Load
  * Delay data transformation until needed, and transform only what is needed
  * Similar to Medallion Architecture
---
## CAR: More solution details

* We use the [Oracle JSON API](https://docs.oracle.com/en/database/oracle/oracle-database/21/adjsn/intro-to-json-data-and-oracle-database.html), which was not even available in UMN databases when we started Experts@Minnesota
  * Though the documentation does not say so, querying uses [JSONPath](https://datatracker.ietf.org/doc/html/rfc9535), which is [based on XPath for XML](https://goessner.net/articles/JsonPath/)
* Presented on [Oracle JSON API and ELT vs ETL for Code People](https://umnlibraries.github.io/oracle-json-api-2021-04/)
---
## Manifold for the Medical School

The Libraries is ending support for this custom reporting application at the end of FY 24-25.
---
## Automate everything!

Still fighting to fix problems that prevent full automation, since the beginning of the project.
---
## Thank you!
---
## Questions?
