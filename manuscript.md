---
author-meta:
- Tiago Lubiana
bibliography:
- content/manual-references.json
date-meta: '2020-11-30'
header-includes: "<!--\nManubot generated metadata rendered from header-includes-template.html.\nSuggest improvements at https://github.com/manubot/manubot/blob/master/manubot/process/header-includes-template.html\n-->\n<meta name=\"dc.format\" content=\"text/html\" />\n<meta name=\"dc.title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta name=\"citation_title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta property=\"og:title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta property=\"twitter:title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta name=\"dc.date\" content=\"2020-11-30\" />\n<meta name=\"citation_publication_date\" content=\"2020-11-30\" />\n<meta name=\"dc.language\" content=\"en-US\" />\n<meta name=\"citation_language\" content=\"en-US\" />\n<meta name=\"dc.relation.ispartof\" content=\"Manubot\" />\n<meta name=\"dc.publisher\" content=\"Manubot\" />\n<meta name=\"citation_journal_title\" content=\"Manubot\" />\n<meta name=\"citation_technical_report_institution\" content=\"Manubot\" />\n<meta name=\"citation_author\" content=\"Tiago Lubiana\" />\n<meta name=\"citation_author_institution\" content=\"Department of Clinical and Toxicological Analyses, School of Pharmaceutical Sciences, University of S\xE3o Paulo, S\xE3o Paulo, Brazil\" />\n<meta name=\"citation_author_orcid\" content=\"0000-0003-2473-2313\" />\n<link rel=\"canonical\" href=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta property=\"og:url\" content=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta property=\"twitter:url\" content=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta name=\"citation_fulltext_html_url\" content=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta name=\"citation_pdf_url\" content=\"https://lubianat.github.io/semantic_web_course_report/manuscript.pdf\" />\n<link rel=\"alternate\" type=\"application/pdf\" href=\"https://lubianat.github.io/semantic_web_course_report/manuscript.pdf\" />\n<link rel=\"alternate\" type=\"text/html\" href=\"https://lubianat.github.io/semantic_web_course_report/v/73f41d9e8f576ca841ebf4a1a8d525325a7dafe6/\" />\n<meta name=\"manubot_html_url_versioned\" content=\"https://lubianat.github.io/semantic_web_course_report/v/73f41d9e8f576ca841ebf4a1a8d525325a7dafe6/\" />\n<meta name=\"manubot_pdf_url_versioned\" content=\"https://lubianat.github.io/semantic_web_course_report/v/73f41d9e8f576ca841ebf4a1a8d525325a7dafe6/manuscript.pdf\" />\n<meta property=\"og:type\" content=\"article\" />\n<meta property=\"twitter:card\" content=\"summary_large_image\" />\n<link rel=\"icon\" type=\"image/png\" sizes=\"192x192\" href=\"https://manubot.org/favicon-192x192.png\" />\n<link rel=\"mask-icon\" href=\"https://manubot.org/safari-pinned-tab.svg\" color=\"#ad1457\" />\n<meta name=\"theme-color\" content=\"#ad1457\" />\n<!-- end Manubot generated metadata -->"
keywords:
- cell type
- nomenclature
- classification
lang: en-US
manubot-clear-requests-cache: false
manubot-output-bibliography: output/references.json
manubot-output-citekeys: output/citations.tsv
manubot-requests-cache-path: ci/cache/requests-cache
title: Releasing PanglaoDB human cell-type markers to Wikidata
...






<small><em>
This manuscript
([permalink](https://lubianat.github.io/semantic_web_course_report/v/73f41d9e8f576ca841ebf4a1a8d525325a7dafe6/))
was automatically generated
from [lubianat/semantic_web_course_report@73f41d9](https://github.com/lubianat/semantic_web_course_report/tree/73f41d9e8f576ca841ebf4a1a8d525325a7dafe6)
on November 30, 2020.
</em></small>

## Authors



+ **Tiago Lubiana**<br>
    ![ORCID icon](images/orcid.svg){.inline_icon}
    [0000-0003-2473-2313](https://orcid.org/0000-0003-2473-2313)
    · ![GitHub icon](images/github.svg){.inline_icon}
    [lubianat](https://github.com/lubianat)<br>
  <small>
     Department of Clinical and Toxicological Analyses, School of Pharmaceutical Sciences, University of São Paulo, São Paulo, Brazil
  </small>



## Abstract {.page_break_before}




# Introduction

PanglaoDB [@https://panglaodb.se/index.html] [@doi:10.1093/database/baz046] is a public database that contains data and metadata on different types of cells. The types of cells are associated with marker genes, which are used to identify the classes that best fit cells observed in biomedical experiments.

Despite its usefulness for the community, the database is on a 3-star category for Linked Open Data [@url:https://www.w3.org/DesignIssues/LinkedData.html] as it does not use open standards from W3C (RDF and SPARQL). To make it 5-star, it needs to be also linked to external data via common identifiers. 


The OBO Foundry provides a rich collection of linked biological identifiers [@url:http://www.obofoundry.org/]. However, reconciliation to OBO is challenging, as there are many ontologies, each with slightly different contribution guidelines. For that reason, we decided to reconcile PanglaoDB to Wikidata, which allows simple creation of new terms, provided they follow Wikidata`s notability criteria[@url:https://www.wikidata.org/wiki/Wikidata:Notability]. 

# Data source

- Panglao

# Property creation on Wikidata

- Process of creating a property on Wikidata

# Class creation on Wikidata

- Process of creating species-specific cell types on Wikidata.

# RDF preparation

- Use of rdflib

# Integration to Wikidata 

- Use of Wikidata Integrator

# SPARQL queries in Wikidata endpoint

# Results of the integration

## SPARQL query for cell types related to neurogenesis


- Linking with Wikidata allows out-of-the-box integrative SPARQL queries (thanks to Gene Wiki and the Gene Ontology integration)
- Dataset on Wikidata can be updated by the community and improved through time


# Acknowledgements

This work has been done within the scope of a slightly larger ongoing project in a collaboration with João Vitor Ferreira Cavalcante available at https://github.com/jvfe/wikidata_panglaodb/. 

This work has been supported by grant #2019/26284-1, São Paulo Research Foundation (FAPESP).


## References {.page_break_before}

<!-- Explicitly insert bibliography here -->
<div id="refs"></div>
