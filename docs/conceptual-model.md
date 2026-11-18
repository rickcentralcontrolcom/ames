# AMES Conceptual Model

**Status: early conceptual draft.**

This document develops the conceptual structure of the Advertising Measurement Evidence Schema (AMES). It begins with organizing areas and candidate metadata, before formal schema syntax, required fields or validation rules are selected.

The model builds on the AMES presentation and prospectus. Candidate fields are proposals for discussion, not an adopted specification.

## 1. Purpose and boundaries

AMES provides an open, human- and machine-readable structure for the metadata accompanying advertising measurement evidence.

**AMES provides the container. Researchers, models and AI determine how to use the evidence.**

AMES supports portability and interoperability across heterogeneous evidence. It does not prescribe measurement methods, rank them, certify their validity or determine how evidence should be combined or weighted.

AMES defines how evidence is described, not where it is stored. Organizations may retain records in their own systems and selectively exchange them. Central repositories and benchmarking initiatives are optional applications.

## 2. Decision status

This draft uses three labels:

| Status | Meaning |
| --- | --- |
| Established direction | A guiding principle of the conceptual model. Field names and technical implementation remain undecided. |
| Proposed | A structure, distinction or candidate field offered for review. |
| Open | A question requiring a substantive decision. |

The classification framework below guides prioritization. Individual candidate fields have not yet been assigned final applicability or necessity levels; this draft is not a completion checklist.

### Established directions

- AMES describes measurement evidence across methods, including descriptive measurement that does not estimate an effect.
- What was measured and how it was measured are separate dimensions.
- Results is a broader container than effect estimates.
- Time and duration deserves explicit visibility among the organizing areas.
- A record is an instance of structured metadata, not necessarily an entry in a central database.
- The conceptual structure will be developed before formal schema implementation and testing against actual measurement studies.

### Proposals still under discussion

- Capturing the business question and intended decision as explicit metadata.
- Distinguishing a reference comparison from its intended counterfactual role.
- Separately documenting production of measurement evidence and creation of its AMES description.
- Representing differences among reported, inferred and confirmed metadata.
- Distinguishing missing-information states such as not reported, unknown and not applicable.
- Grouping multiple results within one record when they share analytical context.

### 2.1 Applicability and necessity

AMES should distinguish what it can describe from what a contributor must supply. The first implementation should have a small minimum description, with richer metadata available when relevant. A long list of supported fields must not become a long mandatory questionnaire.

Each candidate field should eventually carry two classifications:

| Attribute | Categories | Purpose |
| --- | --- | --- |
| Applicability | Common; method-specific; feature-dependent | Identifies whether the field is relevant across records, to particular approaches, or only when a feature such as geographic conversion is present. |
| Necessity when applicable | Essential; recommended; supplementary | Identifies how important the information is to interpreting the evidence. |

Essential information prevents a material ambiguity about the evidence. Recommended information improves interpretation or reuse. Supplementary information supports specialized uses. These classifications concern metadata needs, not a rating of measurement quality.

Applicability conditions must be explicit. Counterfactual construction may be essential to interpreting a causal claim but inapplicable to a descriptive impressions report. Geographic conversion details matter when such a conversion affects the evidence; they are not a universal requirement.

Unknown essential information should be explicitly marked and its interpretive consequence identified. An incomplete source can still be documented. Missing-information status must remain distinguishable from a known value, and structural validity must remain distinguishable from completeness for a particular use. The eventual schema will specify the minimum structural requirements.

Each candidate should be assessed against two questions: What misunderstanding would this information prevent? Under what circumstances does it matter? Related candidates should be consolidated where they describe parts of one concept. Specialized detail may belong in extensions.

### 2.2 Proportionate AI-assisted completion

An extraction system should first identify the evidence and applicable metadata, then extract what is available with source references. It should ask targeted questions about missing or ambiguous information that could materially change interpretation, in small prioritized batches. It should explain why those answers matter.

It should not present every unused schema field as missing information requiring a response. Supplementary omissions may remain unfilled. Unavailable answers should be recorded without repeated requests or invented values. Additional requirements for a particular downstream use should be identified separately from the basic AMES record.

The schema describes information and its applicability. Completion tools manage the questioning workflow. A large inventory of supported metadata does not imply a large manual form.

## 3. Provisional organizing areas

These areas provide a working outline. Their boundaries, names and eventual hierarchy remain open.

| Area | Purpose | Development status |
| --- | --- | --- |
| Business question, decision and action | Describe the question, intended decision, contingent actions and any stated decision criteria. | Initial proposal in Section 5.1 |
| Measurement scope | Describe the advertiser, brand, product, campaign, media, population and geography covered by the evidence. | Initial proposal below |
| Time and duration | Describe when activities occur, how long they last and how their timing relates; specify the time intervals used to aggregate data. Link each description to the relevant activity, study arm, outcome or result. | Outline only |
| Method and design | Describe the measurement approach, such as experiments, quasi-experiments, MMM, attribution or delivery reporting; specify applicable design features, analytical procedures, comparisons and assumptions. | Outline only |
| Outcomes and metrics | Define what was measured, such as sales, conversions, awareness, attention, reach or frequency; specify units and counting rules where applicable. | Outline only |
| Results | Describe the reported findings, such as $250,000 in estimated incremental revenue, 35% unaided awareness or 12 million recorded impressions; connect each finding to its metric, method and relevant context. | Outline only |
| Uncertainty and limitations | Describe statistical uncertainty, such as confidence or credible intervals, confidence levels, standard errors and p-values; include reported diagnostics and limitations, such as sensitivity checks, incomplete data or a short observation period. | Outline only |
| Provenance | Describe measurement producers, data sources, analytical systems, versions and independence disclosures. | Outline only |
| Record documentation | Describe how AMES metadata was supplied, extracted, inferred, confirmed and revised. | Outline only |
| Human-readable representations | Provide a concise narrative summary and a Measurement Facts label derived from the same evidence record. | Initial proposal in Section 5.9 |

## 4. Measurement scope: initial proposal

**Status: proposed.**

### 4.1 Purpose

Measurement scope describes the business, brands, products, campaigns, media, populations, audiences and geographic areas covered by the evidence. Population and audience metadata describes groups and their inclusion criteria. It does not include personally identifiable information about individual audience members.

It should help a recipient determine whether two results concern the same subject or materially different subjects. It should also make boundaries and exclusions visible.

The scope of an analysis can differ from the scope of its underlying campaign. For example, evidence may concern a defined population within a broader campaign audience. AMES should be able to express that difference without assuming the result applies to everyone the campaign targeted.

### 4.2 Proposed subcategories

| Subcategory | What it describes |
| --- | --- |
| Business and product context | The advertiser or other business subject, brands, products and categories covered. |
| Campaign and activity context | Campaigns or other advertising activity covered by the evidence. |
| Media context | Channels, platforms, properties, ad product, formats and other relevant media boundaries. |
| Population and audience context | The people, households, businesses or other units the evidence concerns, and how they relate to the campaign audience. |
| Geographic context | Geographic coverage, resolution and relevant exclusions. |

These five subcategories are the initial proposed coverage of Measurement scope. Their completeness and boundaries remain open for review. Where they intersect, the model should preserve explicit relationships, such as connecting a campaign to its products, media and audiences.

### 4.3 Business and product context

Candidate fields are conceptual descriptions, not proposed machine-readable keys.

| Candidate information | Working meaning | Applicability and unresolved points |
| --- | --- | --- |
| Advertiser or business subject | The organization whose advertising, business activity or outcomes the evidence concerns. | May involve one organization, several organizations or an aggregate. Distinct from the measurement provider. |
| Brand | The brand or brands covered by the evidence. | A result may concern a parent brand, sub-brand or portfolio. |
| Product or service | The products, services, product lines or assortments covered. | Needs a way to describe both named items and broader groupings. |
| Business or product category | A classification relevant to interpreting the evidence. | The classification system and version should be identifiable where supplied. External vocabularies should be investigated before adopting a taxonomy. |
| Coverage boundaries | Relevant inclusions and exclusions within the business, brand or product scope. | Could include particular divisions, retailers, sales channels or product lines. Placement remains open. |
| Source identifiers | Identifiers used by the contributing organization or another named system. | An identifier needs its issuing system or namespace; a code alone may be ambiguous. |

**Open questions**

1. Is "advertiser" sufficient as the general label, or should AMES use a broader business-subject concept?
2. How much brand and product hierarchy is necessary for interpretation?
3. Should retail and sales-channel coverage sit here or with outcome definitions?
4. How should an unnamed or anonymized business be described while preserving useful context?

### 4.4 Campaign and activity context

| Candidate information | Working meaning | Applicability and unresolved points |
| --- | --- | --- |
| Campaign or activity name | A human-readable description of the advertising activity covered. | A named campaign may not exist; evidence may cover ongoing activity or a portfolio. |
| Campaign or activity identifiers | References to campaigns or activity in source systems. | Several platforms may assign different identifiers to related activity. |
| Activity coverage | Whether the evidence concerns an entire campaign, a component, several campaigns or broader ongoing activity. | Candidate distinction, not a settled vocabulary. |
| Campaign relationships | Connections among parent campaigns, components or related activity. | The minimum useful relationship structure remains open. |
| Creative coverage | The creatives, messages or variants included, where relevant to interpretation. | Creative attributes may eventually need an extension; a full creative taxonomy is outside this draft. |
| Campaign type or advertising product | A platform-defined campaign type or advertising offering, such as Google Ads Performance Max. | May span multiple channels and formats; identify the platform and preserve its terminology without treating the offering as a single channel. |
| Relevant boundaries and exclusions | Which components of the activity are included or excluded. | Should support explicit statements without requiring disclosure of proprietary campaign detail. |

Campaign dates belong in Time and duration. Campaign identifiers connect that timing to the relevant activity.

**Open questions**

1. Should campaigns and ongoing activity use the same structure?
2. What level of creative detail belongs in the common core?
3. Where should planned activity be distinguished from delivered activity?
4. How should a record describe broad coverage without listing every underlying campaign?

### 4.5 Media context

| Candidate information | Working meaning | Applicability and unresolved points |
| --- | --- | --- |
| Channel or media type | The media category covered by the evidence. | Labels can overlap across classification systems. A chosen taxonomy should not be assumed at this stage. |
| Platform, publisher or media owner | The organizations or services through which the relevant advertising was delivered. | These roles differ and should not be collapsed automatically. |
| Property or environment | A particular site, app, service, network or other delivery environment. | Appropriate detail depends on the evidence and disclosure constraints. |
| Ad format | The format or formats covered. | Existing definitions should be investigated before developing an AMES vocabulary. |
| Placement or inventory coverage | The relevant portions of inventory included or excluded. | The structure should allow broad descriptions and source references. |
| Buying or delivery context | Buying arrangements or delivery characteristics material to interpretation. | Whether this belongs in the common core or an extension remains open. |
| Media relationships | Connections among channels, platforms, properties, formats and campaign components. | Simple independent lists may falsely imply that every listed format ran on every listed platform. |

Media context identifies what media the evidence covers. Delivered impressions, reach, frequency and spend may also be inputs or results. Their placement and references will be resolved alongside Outcomes and metrics, Results, and Method and design.

**Open questions**

1. Which media descriptors are sufficiently universal for the common core?
2. How should multi-channel scope preserve relationships among its components?
3. How should planned media scope be distinguished from actual delivery and analyzed media scope?
4. What information should be referenced from external campaign standards rather than repeated?

### 4.6 Population and audience context

| Candidate information | Working meaning | Applicability and unresolved points |
| --- | --- | --- |
| Population the result concerns | The defined group to which a result refers or is intended to apply. | This may differ from the population directly observed. |
| Observed or analyzed population | The group represented in the data used for the analysis. | Coverage and exclusions may affect interpretation. |
| Campaign target audience | The audience the campaign intended to reach. | Applicable where reported; does not establish actual exposure. |
| Audience definition and source | The segment label, provider, source-system identifier, definition and version or effective date where available. | A label such as “Car Intenders” is not a universal definition; identify the DMP, media company or other source. Document undisclosed proprietary criteria rather than inferring them. |
| Reached or exposed population | The audience reported as reached or exposed under a stated definition. | Exposure definitions and ascertainment connect to Method and design. |
| Population unit | The kind of entity described, such as a person, household, business or device. | Different roles may use different units; one record-wide unit may be insufficient. |
| Eligibility and exclusions | Criteria determining inclusion in the relevant population. | Method-specific details may be described under Method and design. |
| Segments or subpopulations | Defined subsets for which evidence is reported. | Each result needs an unambiguous connection to its applicable population. |

These are distinct roles that populations can play, not a requirement that every record contain five separate audience descriptions. The representation should allow a contributor to state when roles refer to the same population.

Units should be described according to their roles. The population unit identifies the entities the evidence concerns, such as people, households, accounts, devices or geographic areas. Observation units, assignment units where applicable, and analysis units belong under Method and design; reporting units belong with Results. These units may differ within the same analysis and should be explicitly connected. For example, an experiment might assign treatment by DMA, observe daily household purchases, analyze DMA-level weekly totals and report a national effect estimate.

**Open questions**

1. Which population distinctions are essential across evidence types?
2. Is "population" broad enough to cover all relevant units, including inventory or advertising events?
3. How should a result's intended population be distinguished from a provider's broader generalization?
4. How should identities, audience definitions and source systems be referenced without importing individual-level data?

### 4.7 Geographic context

| Candidate information | Working meaning | Applicability and unresolved points |
| --- | --- | --- |
| Geographic coverage | The geographic area or areas covered by the evidence. | Can be national, regional, local, multinational or another defined area. |
| Geographic identifiers and system | Codes or names together with the system that defines them. | Different systems can assign different meanings to similar labels. |
| Geographic representation | How an area is defined, such as an administrative boundary, polygon, radius around a point or set of grid cells. | Supports named areas and custom definitions without requiring one geographic system. |
| Grid system and resolution | The geographic grid system, cell identifiers, resolution and version, such as H3 hexagonal cells, S2 cells or geohash. | Cell resolution describes geographic granularity; it does not establish the accuracy of location assignment. |
| Coordinates and radius definitions | Coordinates and their reference system; where applicable, a center point, radius, distance units and boundary rule. | Describes geographic definitions, not individual audience members' locations. |
| Geographic role | Whether a definition describes intended targeting, treatment assignment, exclusions, actual delivery, outcome coverage or reporting. | These areas may differ within the same analysis and should be explicitly connected. |
| Positional accuracy and uncertainty | The reported accuracy of location assignment, including its source, definition and any stated confidence or error radius. | Distinguishes uncertainty about location from the size of the geographic unit. |
| Geographic conversions | How geographic representations were translated or aggregated, including the source and destination systems, rules and versions. | Examples include converting a radius or polygon to grid cells, or mapping cells to ZIP codes. Preserve material changes in coverage. |
| Geographic resolution | The spatial level at which scope or data is described. | Campaign targeting, data collection and analysis may use different resolutions. |
| Boundary version or effective date | The boundary definition applicable to the evidence. | Relevant when geographic definitions change. |
| Geographic inclusions and exclusions | Areas included or omitted within broader coverage. | Should allow exceptions to a broad scope statement. |
| Basis for locating units | How geography was assigned, such as residence, store location or exposure location. | These interpretations can differ even when geographic labels match. |

Geographic coverage, targeting, treatment assignment, exclusions, delivery and outcome reporting may use different areas or units and should be explicitly connected. For example, a study covering the United States might assign treatment by DMA and analyze outcomes using another geographic unit. Geographic definitions belong here; their assignment and analytical roles are described under Method and design. Conversions between representations should document the rules used, such as including cells whose centers fall within a boundary versus cells that intersect it. Changes in resolution or representation should preserve any reported location uncertainty and disclose resulting changes in coverage.

**Open questions**

1. How should geographic roles be represented when targeting, exposure, outcomes and analysis differ?
2. Should custom geographic definitions be embedded, referenced or both?
3. How should geographic coverage be stated when individual areas cannot be disclosed?
4. Which geographic reference systems should be accommodated initially?

### 4.8 Relationships within Measurement scope

Proposed principles:

- A scope description may involve multiple brands, products, campaigns, media components, populations or geographies.
- The model should preserve relevant connections among those entities. Independent lists alone can create false combinations.
- Shared scope may apply to several results, but differences must be attached to the relevant result explicitly.
- Being part of the same campaign does not establish that two results share a methodology, outcome definition, population or period.
- An identifier should be interpretable within its issuing system.
- Confidentiality should not force a contributor to invent a public name. Anonymized descriptions and withheld information need explicit treatment.

The technical mechanism for shared context, references and result-specific differences remains undecided.

### 4.9 Proposed scope boundary

Measurement scope describes the subject and coverage of the evidence. Other areas would describe related information as follows:

| Information | Provisional primary area |
| --- | --- |
| Campaign, exposure and outcome periods | Time and duration |
| Intervention, comparison, assignment and analytical procedures | Method and design |
| Definition of revenue, conversions, awareness or another measure | Outcomes and metrics |
| Reported values, including delivery measures and effect estimates | Results |
| Precision, diagnostics and interpretive limitations | Uncertainty and limitations |
| Data suppliers, measurement producers and analytical systems | Provenance |
| Extraction, inference, confirmation and revision of metadata | Record documentation |

These boundaries are provisional. Information may need to be connected across areas without being independently redefined in each.

## 5. Remaining areas: development outline

The remaining areas are outlined below. Detailed subcategories and candidate fields have not yet been developed.

### 5.1 Business question, decision and action

AMES should document the connection between measurement and the action it was intended to inform.

| Candidate information | Working meaning |
| --- | --- |
| Business question | What the organization wants to learn. |
| Intended decision | The choice the evidence is intended to inform. |
| Contingent actions | Actions contemplated under different findings, including an inconclusive result. |
| Decision criteria | Stated thresholds, uncertainty requirements, practical constraints or other conditions governing the choice. |
| Timing and source of the plan | Who stated the intended decision and action, and whether the plan preceded the results or was developed afterward. |

For example, an organization might intend to increase spending if estimated incremental returns exceed a stated threshold, retain spending if the evidence is inconclusive, and reduce spending under a specified unfavorable finding. AMES records those intentions; it does not choose the threshold or recommend the action.

A pre-existing action plan, a subsequent recommendation and an action actually taken are distinct. Any recorded recommendation or action should identify its source and timing. Historical evidence without a documented decision or action plan remains within scope; absence of that context should be explicit rather than reconstructed as fact.

To resolve: field applicability and necessity; how contingent actions relate to multiple results; how to distinguish original intent from later uses of the evidence.

### 5.2 Time and duration

Describe the timing necessary to interpret the evidence, potentially including campaign, exposure, intervention, baseline, outcome measurement and follow-up periods; attribution or response windows; and time granularity.

To resolve: how periods relate to particular activities and results; how overlapping or discontinuous periods are represented; how lag and carryover are described; where analysis and publication dates belong.

### 5.3 Method and design

Describe how the evidence was produced, with a common structure and additional metadata appropriate to particular approaches.

To resolve: method descriptors; comparison and counterfactual roles; units; assumptions; analytical procedures; combinations of methods; the division between common metadata and extensions.

### 5.4 Outcomes and metrics

Define what was measured, including units, counting rules and other conditions needed to understand the measure.

To resolve: the distinction between an outcome and a metric; measures with no business outcome claim; definitions shared across results; external vocabulary references; proxy measures.

### 5.5 Results

Describe reported quantities and their interpretation, including descriptive measurements, attributed quantities and effect estimates where applicable.

To resolve: result types; denominators and reference values; units and scales; derived quantities; connections to scope, time, methods and uncertainty; the meaning of the quantity an analysis seeks to estimate.

### 5.6 Uncertainty and limitations

Describe reported precision, diagnostics and limitations relevant to interpreting the evidence.

To resolve: result-specific versus analysis-wide information; statistical and other sources of uncertainty; planned power and MDE versus realized precision; placement of assumptions; descriptions of diagnostics without AMES-issued quality ratings.

### 5.7 Provenance

Describe the origin and production of the underlying evidence.

To resolve: organizational roles; data sources and transformations; analytical software, models and versions; AI and human roles; sponsorship and independence disclosures; dependencies on other evidence.

### 5.8 Record documentation

Describe the creation and maintenance of the AMES metadata.

To resolve: source artifact references; field-level versus record-level provenance; extraction and inference; analyst confirmation; revisions; missing-information states; distinction between confidence in extraction and statistical uncertainty.

### 5.9 Human-readable representations

Every AMES record should include a concise narrative summary answering “What am I looking at?” A separate Measurement Facts label should provide a consistent, scannable presentation of key metadata. Both should derive from the same conceptual model and remain consistent with the structured record, rather than introduce independent claims.

#### Narrative summary

The summary should normally take one or two short paragraphs. It should identify the type of analysis, the campaign or activity, its purpose, population and period, principal findings, and material uncertainty or caveats affecting use. It should state when important information is unavailable rather than fill gaps through unsupported inference.

Use plain language first, followed by technical detail where useful. For example:

> The analysis estimated that the campaign increased sales by 3%, but the data are also compatible with no increase or a small decline. The estimate is uncertain (95% confidence interval: −1% to +7%). Outcomes were observed only during the campaign, so the analysis does not establish whether effects persisted afterward.

This example describes uncertainty without equating a confidence interval with a probability that the true effect lies inside it. Summaries should preserve units, denominators and distinctions such as relative percentage change versus percentage-point change.

Descriptions of evidentiary strength should explain relevant design features, uncertainty and limitations. Provider or reviewer assessments may be included with attribution and their stated basis. AMES does not issue a universal evidence grade, certify validity or determine whether evidence is sufficient for an action. A summary should not claim that a causal method establishes causality merely because of its name.

AI-generated summaries should follow the metadata provenance and confirmation rules. An interpretation added during summarization should remain distinguishable from a conclusion reported in the underlying analysis.

#### Measurement Facts label

The label is a structured human-readable view, analogous to a nutrition label. Candidate elements include the measurement approach, question and intended decision, scope and period, outcome definition, principal results, uncertainty, major limitations, measurement provider and source references.

The label should show applicable information and important gaps rather than every possible field. Method-specific detail can be available in an expanded view. The narrative provides orientation; the label provides a consistent reference. Neither replaces the full structured metadata.

To resolve: the minimum label content, rules for selecting principal results, handling multiple results and methods, and keeping generated representations synchronized with record revisions.

### 5.10 External taxonomies, reference systems and definitions

AMES should support multiple established taxonomies and reference systems rather than require one universal product, media, geographic or audience vocabulary. It should standardize how a definition is referenced and preserve its source terminology.

| Candidate information | Purpose |
| --- | --- |
| System name and publisher | Identifies the taxonomy, reference system or proprietary definition and its responsible source. |
| System identifier or namespace | Distinguishes systems whose names or codes might overlap. |
| Version or effective date | Preserves the definition used for the evidence. If unknown, that gap should be explicit. |
| Entry code and label | Identifies the particular category, cell, segment or other entry. |
| Reference link | Points to authoritative documentation or a definition where available. |
| Local definition | Preserves relevant meaning when no accessible external definition exists. |

For example, “Car Intenders” should identify the audience provider and segment identifier, with qualification criteria, version or effective date where supplied. Identical labels from different providers do not establish equivalent populations. Proprietary definitions can be referenced without requiring their disclosure or individual-level data.

The project should maintain a directory of external vocabularies and reference systems, with authoritative links, versions where available, access conditions and review dates. Inclusion in the directory would not imply endorsement, verified integration or equivalence to another system. The directory would reference external resources rather than attempt to duplicate and maintain all their contents.

Living documentation and historical interpretation serve different needs. Records should preserve the version used when the evidence was produced; changes to a linked resource must not silently redefine an existing record. Crosswalks should identify their source, version and any lossy or approximate mappings. New categories should not be silently substituted for source categories.

Specific systems and mappings will be investigated before inclusion. A required network lookup is not proposed as a condition for reading a record.

## 6. Cross-cutting questions

These questions affect the whole model and remain open:

1. **Record boundaries:** What should one record contain, and when should analyses be separate but linked?
2. **Shared context:** How should common information be associated with multiple results?
3. **Identity and versioning:** How are records, analyses, results and referenced entities identified and revised?
4. **Applicability:** Which concepts are universal, method-specific or conditional?
5. **Missing information:** How should unknown, unreported, withheld, unavailable and inapplicable information be distinguished?
6. **Extensibility:** How can future evidence types and proprietary descriptions be accommodated without undermining interoperability?
7. **External definitions:** How should an external vocabulary, identifier or standard be referenced, including its version?
8. **Confidentiality:** How can a useful record be exchanged with appropriate omissions or anonymization?
9. **Dependencies:** How should records disclose shared data or reliance on other evidence, including experimental calibration of a model?
10. **Representations:** How will the narrative summary and Measurement Facts label derive from the same model and remain synchronized?

Existing industry specifications will be researched before concrete mappings, vocabularies or dependencies are adopted. This draft does not assert compatibility with any external standard.

## 7. Further development

Measurement scope is the first area developed in detail. Its proposed subcategories, candidate information and relationships remain open for discussion. Initial proposals also address prioritization, completion workflows, the connection to action, human-readable representations and external definitions. The remaining areas will be expanded to comparable conceptual depth before further specialized detail is added.

Formal field names, data types, requiredness, technical syntax and validation rules will follow conceptual decisions.
