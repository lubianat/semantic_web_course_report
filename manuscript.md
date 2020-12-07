---
author-meta:
- Tiago Lubiana
bibliography:
- content/manual-references.json
date-meta: '2020-12-07'
header-includes: "<!--\nManubot generated metadata rendered from header-includes-template.html.\nSuggest improvements at https://github.com/manubot/manubot/blob/master/manubot/process/header-includes-template.html\n-->\n<meta name=\"dc.format\" content=\"text/html\" />\n<meta name=\"dc.title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta name=\"citation_title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta property=\"og:title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta property=\"twitter:title\" content=\"Releasing PanglaoDB human cell-type markers to Wikidata\" />\n<meta name=\"dc.date\" content=\"2020-12-07\" />\n<meta name=\"citation_publication_date\" content=\"2020-12-07\" />\n<meta name=\"dc.language\" content=\"en-US\" />\n<meta name=\"citation_language\" content=\"en-US\" />\n<meta name=\"dc.relation.ispartof\" content=\"Manubot\" />\n<meta name=\"dc.publisher\" content=\"Manubot\" />\n<meta name=\"citation_journal_title\" content=\"Manubot\" />\n<meta name=\"citation_technical_report_institution\" content=\"Manubot\" />\n<meta name=\"citation_author\" content=\"Tiago Lubiana\" />\n<meta name=\"citation_author_institution\" content=\"Department of Clinical and Toxicological Analyses, School of Pharmaceutical Sciences, University of S\xE3o Paulo, S\xE3o Paulo, Brazil\" />\n<meta name=\"citation_author_orcid\" content=\"0000-0003-2473-2313\" />\n<link rel=\"canonical\" href=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta property=\"og:url\" content=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta property=\"twitter:url\" content=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta name=\"citation_fulltext_html_url\" content=\"https://lubianat.github.io/semantic_web_course_report/\" />\n<meta name=\"citation_pdf_url\" content=\"https://lubianat.github.io/semantic_web_course_report/manuscript.pdf\" />\n<link rel=\"alternate\" type=\"application/pdf\" href=\"https://lubianat.github.io/semantic_web_course_report/manuscript.pdf\" />\n<link rel=\"alternate\" type=\"text/html\" href=\"https://lubianat.github.io/semantic_web_course_report/v/3dedc0985b6a66f27c7732a51b51a68afa77f56a/\" />\n<meta name=\"manubot_html_url_versioned\" content=\"https://lubianat.github.io/semantic_web_course_report/v/3dedc0985b6a66f27c7732a51b51a68afa77f56a/\" />\n<meta name=\"manubot_pdf_url_versioned\" content=\"https://lubianat.github.io/semantic_web_course_report/v/3dedc0985b6a66f27c7732a51b51a68afa77f56a/manuscript.pdf\" />\n<meta property=\"og:type\" content=\"article\" />\n<meta property=\"twitter:card\" content=\"summary_large_image\" />\n<link rel=\"icon\" type=\"image/png\" sizes=\"192x192\" href=\"https://manubot.org/favicon-192x192.png\" />\n<link rel=\"mask-icon\" href=\"https://manubot.org/safari-pinned-tab.svg\" color=\"#ad1457\" />\n<meta name=\"theme-color\" content=\"#ad1457\" />\n<!-- end Manubot generated metadata -->"
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
([permalink](https://lubianat.github.io/semantic_web_course_report/v/3dedc0985b6a66f27c7732a51b51a68afa77f56a/))
was automatically generated
from [lubianat/semantic_web_course_report@3dedc09](https://github.com/lubianat/semantic_web_course_report/tree/3dedc0985b6a66f27c7732a51b51a68afa77f56a)
on December 7, 2020.
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

PanglaoDB [@https://panglaodb.se/index.html] [@doi:10.1093/database/baz046] is a public database that contains data and metadata on different types of cells. The types of cells are associated with marker genes, which are used to identify the classes that best fit cells observed in biomedical experiments. PanglaoDB, especifically, derives its marker genes from the curation of several single-cell RNA sequencing experience.

The database is used for scientists when analyzing RNA-sequencing data to help in identification of the cells in a sample. 
Despite its usefulness for the community, the database is only on a 3-star category for Linked Open Data [@url:https://www.w3.org/DesignIssues/LinkedData.html] as it does not use open standards from W3C (RDF and SPARQL). To make it 5-star, it needs to be also linked to external data via common identifiers. 

The OBO Foundry provides a rich collection of linked biological identifiers [@url:http://www.obofoundry.org/]. However, reconciliation to OBO is challenging, as there are many ontologies, each with slightly different contribution guidelines. For that reason, we decided to reconcile PanglaoDB to Wikidata, which allows simple creation of new terms, provided they follow Wikidata`s notability criteria[@url:https://www.wikidata.org/wiki/Wikidata:Notability]. 

In this work, I created classes on Wikidata for human-specific cell types, as well as an object property for linking cell type classes to gene classes. Then, I proceeded to reconciled the human cell-type / marker relations on PanglaoDB to Wikidata , and uploaded the PanglaoDB dataset as Linked Open Data directly to Wikidata via its Application Programming Interface. Finally, I show how this upload now enables SPARQL queries to Wikidata's endpoint that extend the usefulness of the Panglao database. 
 

# Data source

The markers dataset was dowloaded manually from PanglaoDB's website (https://panglaodb.se/markers/PanglaoDB_markers_27_Mar_2020.tsv.gz). It contains 15 columns and 8256 rows. 

For the scope of this work, only the columns `species`, `official gene symbol` and 	`cell type` were used. 

# Property creation on Wikidata

To represent the cell-type --> marker property, I proposed a property for the Wikidata community. In Wikidata:Property proposal (https://www.wikidata.org/wiki/Wikidata:Property_proposal/has_positive_marker), I posted a message in 17th of November presenting the property, domain and range constraints, as well as additional comments. The html of the property proposal is reproduced below:

<div class="property-navibox" dir="ltr"><style data-mw-deduplicate="TemplateStyles:r1021077283">.mw-parser-output .property-navibox{background-color:#dff;border:3px solid #cddddd}.mw-parser-output .property-navibox-header{background-color:#dff;outline:3px solid #cddddd;padding:4px}.mw-parser-output .property-navibox-links{float:right;margin:0}.mw-parser-output .property-navibox-links li{display:inline;margin:0}.mw-parser-output .property-navibox-links li:after{display:inline;content:" – "}.mw-parser-output .property-navibox-links li:last-child:after{content:none}.mw-parser-output .property-navibox-main{overflow-x:auto}.mw-parser-output .property-navibox table{display:table;overflow-x:visible}.mw-parser-output .property-navibox-main tr{vertical-align:text-top}.mw-parser-output .property-navibox-main th{width:20%}.mw-parser-output .property-navibox[dir="ltr"] .property-navibox-main th{text-align:left}.mw-parser-output .property-navibox[dir="rtl"] .property-navibox-main th{text-align:right}</style><div class="property-navibox-header"><ul class="property-navibox-links plainlinks"><li class="mw-empty-elt"></li></ul><div><span style="background-color:#0C0;">  </span> <span id="P8872"></span>Done: <a href="/wiki/Property:P8872" title="Property:P8872">has marker</a> <small>(P8872)</small> (<a href="/wiki/Property_talk:P8872" title="Property talk:P8872">Talk and documentation</a>)</div></div><div class="property-navibox-main"><table><tbody><tr><th>Description</th><td><span lang="en">a gene or a protein published as a marker of a species-specific cell type</span></td></tr><tr><th>Represents</th><td><a href="/wiki/Q2776413" title="Q2776413">Marker gene <small>(Q2776413)</small></a> (partially)</td></tr><tr><th>Data type</th><td><a href="/wiki/Special:MyLanguage/Help:Data_type#wikibase-item" title="Special:MyLanguage/Help:Data type">Item</a></td></tr><tr><th>Domain</th><td>?subject <a href="/wiki/Property:P31" title="Property:P31">instance of <small>(P31)</small></a> <a href="/wiki/Q189118" title="Q189118">cell type <small>(Q189118)</small></a> . 
<p>?subject <a href="/wiki/Property:P703" title="Property:P703">found in taxon <small>(P703)</small></a> ?taxon . 
</p>
?taxon <a href="/wiki/Property:P105" title="Property:P105">taxon rank <small>(P105)</small></a> <a href="/wiki/Q7432" title="Q7432">species <small>(Q7432)</small></a>.</td></tr><tr><th>Allowed values</th><td>{?object <a href="/wiki/Property:P31" title="Property:P31">instance of <small>(P31)</small></a> <a href="/wiki/Q8054" title="Q8054">protein <small>(Q8054)</small></a> .}
<p>UNION {?object <a href="/wiki/Property:P31" title="Property:P31">instance of <small>(P31)</small></a> <a href="/wiki/Q7187" title="Q7187">gene <small>(Q7187)</small></a> .}
</p>
UNION {?object <a href="/wiki/Property:P31" title="Property:P31">instance of <small>(P31)</small></a> <a href="/wiki/Q22325163" title="Q22325163">macromolecular complex <small>(Q22325163)</small></a> .}</td></tr><tr><th>Example 1</th><td><a href="/wiki/Q67801129" title="Q67801129">human astrocyte <small>(Q67801129)</small></a> → <a href="/wiki/Q14864879" title="Q14864879">GFAP <small>(Q14864879)</small></a>
<p>referenced by:
</p>
<ul><li><a href="/wiki/Property:P248" title="Property:P248">stated in <small>(P248)</small></a> <a href="/wiki/Q99936939" title="Q99936939">PanglaoDB <small>(Q99936939)</small></a></li>
<li><a href="/wiki/Property:P813" title="Property:P813">retrieved <small>(P813)</small></a> 08 of November 2020</li>
<li><a href="/wiki/Property:P854" title="Property:P854">reference URL <small>(P854)</small></a> <a rel="nofollow" class="external free" href="https://panglaodb.se/markers.html">https://panglaodb.se/markers.html</a></li></ul></td></tr><tr><th>Example 2</th><td><a href="/wiki/Q101423166" title="Q101423166">human cytotoxic t cell <small>(Q101423166)</small></a> → <a href="/wiki/Q50260473" title="Q50260473">CD8 [plasma membrane] <small>(Q50260473)</small></a>
<p>referenced by:
</p>
<ul><li><a href="/wiki/Property:P813" title="Property:P813">retrieved <small>(P813)</small></a> 09 of November 2020</li>
<li><a href="/wiki/Property:P854" title="Property:P854">reference URL <small>(P854)</small></a> <a rel="nofollow" class="external free" href="https://www.niaid.nih.gov/research/immune-cells">https://www.niaid.nih.gov/research/immune-cells</a></li></ul></td></tr><tr><th>Example 3</th><td><a href="/wiki/Q101423298" class="mw-redirect" title="Q101423298">human t helper cell <small>(Q101423298)</small></a> → <a href="/wiki/Q412587" title="Q412587">CD4 molecule <small>(Q412587)</small></a>
<p>referenced by:
</p>
<ul><li><a href="/wiki/Property:P813" title="Property:P813">retrieved <small>(P813)</small></a> 09 of November 2020</li>
<li><a href="/wiki/Property:P854" title="Property:P854">reference URL <small>(P854)</small></a> <a rel="nofollow" class="external free" href="https://www.niaid.nih.gov/research/immune-cells">https://www.niaid.nih.gov/research/immune-cells</a></li></ul></td></tr><tr><th>Source</th><td>- <a rel="nofollow" class="external text" href="https://panglaodb.se/">PanglaoDB</a> marker database: <a href="/wiki/Q99936939" title="Q99936939">PanglaoDB <small>(Q99936939)</small></a> and <a href="/wiki/Q63664483" title="Q63664483">PanglaoDB: a web server for exploration of mouse and human single-cell RNA sequencing data <small>(Q63664483)</small></a>
<p>- <a rel="nofollow" class="external text" href="http://biocc.hrbmu.edu.cn/CellMarker/">CellMarker</a> marker database: <a href="/wiki/Q64371987" title="Q64371987">CellMarker <small>(Q64371987)</small></a> and <a href="/wiki/Q56984510" title="Q56984510">CellMarker: a manually curated resource of cell markers in human and mouse <small>(Q56984510)</small></a>
</p>
- <a rel="nofollow" class="external text" href="https://stemcellinformatics.org/">CellPedia-SHOGoiN</a> marker database: <a href="/wiki/Q35482351" title="Q35482351">CELLPEDIA: a repository for human cell information for cell studies and differentiation analyses. <small>(Q35482351)</small></a></td></tr><tr><th>Planned use</th><td>Reconcile knowledge from the PanglaoDB marker database to Wikidata. In the future, expand to other trusted sources of cell type marker information.</td></tr></tbody></table></div></div>


It was accompanied by the following motivation statement: 

"Even though the concept of a marker gene/protein is not clear cut, it is very important, and widely used in databases and scientific articles.
This property will help us to represent that a gene/protein has been reported as a marker by a credible source, and should always contain a reference.
Some markers are reported as proteins and some as genes. Some genes don`t encode proteins, and some protein markers are actually protein complexes.
The property would be inclusive to these slightly different markers.
Some cell types are marked by absence of expression of genes/proteins/protein expression. As these seem to be less common than positive markers (no organized databases, for example) they are left outside the value range for this property"

In the same day, the property received 3 "Support" tags by different members of the community:

<ul><li><img alt="" src="//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/15px-Symbol_support_vote.svg.png" decoding="async" width="15" height="15" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/23px-Symbol_support_vote.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/30px-Symbol_support_vote.svg.png 2x" data-file-width="180" data-file-height="185">&nbsp;<b>Support</b> — <a href="/wiki/User:Jvcavv" title="User:Jvcavv">Jvcavv</a> (<a href="/wiki/User_talk:Jvcavv" title="User talk:Jvcavv"><span class="signature-talk">talk</span></a>) 14:51, 17 November 2020 (UTC)</li>
<li><img alt="" src="//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/15px-Symbol_support_vote.svg.png" decoding="async" width="15" height="15" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/23px-Symbol_support_vote.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/30px-Symbol_support_vote.svg.png 2x" data-file-width="180" data-file-height="185">&nbsp;<b>Support</b> <a href="/w/index.php?title=User:Bmeldal&amp;action=edit&amp;redlink=1" class="new" title="User:Bmeldal (page does not exist)">Bmeldal</a> (<a href="/w/index.php?title=User_talk:Bmeldal&amp;action=edit&amp;redlink=1" class="new" title="User talk:Bmeldal (page does not exist)"><span class="signature-talk">talk</span></a>) 20:00, 17 November 2020 (UTC)</li>
<li><img alt="" src="//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/15px-Symbol_support_vote.svg.png" decoding="async" width="15" height="15" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/23px-Symbol_support_vote.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/9/94/Symbol_support_vote.svg/30px-Symbol_support_vote.svg.png 2x" data-file-width="180" data-file-height="185">&nbsp;<b>Support</b> <small>&nbsp;– <i>The preceding <a href="/wiki/Q4663253" title="Q4663253">unsigned</a> comment was added by</i> <a href="/wiki/User:Tinker_Bell" title="User:Tinker Bell">Tinker Bell</a> (<a href="/wiki/User_talk:Tinker_Bell" title="User talk:Tinker Bell">talk</a>&nbsp;•&nbsp;<a href="/wiki/Special:Contributions/Tinker_Bell" title="Special:Contributions/Tinker Bell">contribs</a>)&nbsp;at 20:07, November 17, 2020‎ (UTC).</small></li></ul>

As there were 3 approvals and no objections, 10 days later one Wikidata Property Administrator created the property: 

<dd>@<a href="/wiki/User:TiagoLubiana" title="User:TiagoLubiana"><bdi>TiagoLubiana</bdi></a>, <a href="/wiki/User:Jvcavv" title="User:Jvcavv"><bdi>Jvcavv</bdi></a>, <a href="/w/index.php?title=User:Bmeldal&amp;action=edit&amp;redlink=1" class="new" title="User:Bmeldal (page does not exist)"><bdi>Bmeldal</bdi></a>, <a href="/wiki/User:Tinker_Bell" title="User:Tinker Bell"><bdi>Tinker Bell</bdi></a>: <img alt="✓" src="//upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Yes_check.svg/15px-Yes_check.svg.png" decoding="async" title="✓" width="15" height="15" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Yes_check.svg/23px-Yes_check.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Yes_check.svg/30px-Yes_check.svg.png 2x" data-file-width="600" data-file-height="600"><b>&nbsp;Done</b> <a href="/wiki/Property:P8872" title="Property:P8872">has marker <small>(P8872)</small></a> <a href="/wiki/User:Pamputt" title="User:Pamputt">Pamputt<span class="adminMark"> (A)</span></a> (<a href="/wiki/User_talk:Pamputt" title="User talk:Pamputt"><span class="signature-talk">talk</span></a>) 07:24, 27 November 2020 (UTC)</dd>

# Class creation on Wikidata

Different from property creation, class creation on Wikidata does not require community approval, and any user can create new classes and add statements. 

Species-neutral cell types were already mostly present on Wikidata. Human-specific cell types were created for each human-specific cell type mentioned in PanglaoDB. Class labels and subclass of statements(https://www.wikidata.org/wiki/Q21514624) were added to a spreadsheet and uploaded to Wikidata via the batch edition tool Quickstatements (https://quickstatements.toolforge.org/#/)

# Integration to Wikidata 

The reconciled dataset was uploaded to Wikidata via the Wikidata Integrator python package (https://github.com/SuLab/WikidataIntegrator), a wrapper for the Wikidata Application Programming Interface. The details of the integration can be seen in the accompanying Jupyter notebook. 

# Access to reconciled data

## Wikidata dumps

Wikidata provides regular dumps in a variety of formats, including RDF dumps: https://www.wikidata.org/wiki/Wikidata:Database_download. It is possible to also download partial dumps of the database with reduced size (ex: https://wdumps.toolforge.org/dump/987 for all cell types with the has_marker property)   

## SPARQL queries

Besides the Wikidata Dumps, Wikidata provides an SPARQL endpoint with a Graphical User Interface (https://query.wikidata.org/). Updated data was immediately accessible via this endpoint, enabling integrative queries integrated with other database statements.

# Results of the integration

As explained in the method session


## SPARQL query for cell types related to neurogenesis


Linking biological with Wikidata allows out-of-the-box integrative SPARQL queries, as many biomedical ontologies and datasets have been already integrated to Wikidata, and are available in Wikidata's graph. Besides the well-known advantages of having data linked to the Linked Open Data cloud, the Wikidata integration provides user-friendly interfaces for the data. That includes both navigable html pages of classes and properties (e.g. https://www.wikidata.org/wiki/Q67801129) as well as an SPARQL Query Service with user-friendly modifications to ease queries for beginners (https://query.wikidata.org/) with helper pages for learning SPARQL (https://www.wikidata.org/wiki/Wikidata:SPARQL_tutorial) or even requesting queries (https://www.wikidata.org/wiki/Wikidata:Request_a_query).   


In addition to user-friendly data access systems, Wikidata makes it easy for users to contribute. This user-friendliness is specially important in the case of the biomedical sciences, where database curation is becoming increasingly challenging with the growth of scientific publications. Wikidata allows editions directly in the Graphical User Interface, which makes it acessible for domain experts with little to no experience with programming and formal ontological representations. The Wikidata community has developed wrappers for the API in web applications that further facilitate contribution, such as the Quickstatements tool (https://quickstatements.toolforge.org/#/) for general purpose statements. The python module Wikidata Integrator facilitates for python users to reconcile databases to Wikidata, and it has been used to build bots for several different biological databases [wikidata:Q87830400].


This work exemplifies the power of releasing Linked Open Data via Wikidata, and provides the biomedical community with the first (to my knowledge) semantically accessible, 5-star LOD dataset. I hope that community will keep improving marker content on Wikidata, and that the interlinked marker information will be useful for researchers all over the world.  

# Acknowledgements

This work has been done within the scope of a slightly larger ongoing project in a collaboration with João Vitor Ferreira Cavalcante available at https://github.com/jvfe/wikidata_panglaodb/. 

This work has been supported by grant #2019/26284-1, São Paulo Research Foundation (FAPESP).


## References {.page_break_before}

<!-- Explicitly insert bibliography here -->
<div id="refs"></div>
