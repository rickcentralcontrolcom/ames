# AMES: Advertising Measurement Evidence Schema

An open metadata structure for portable, interoperable advertising measurement evidence.

**Status: early conceptual development.** This repository begins the work of turning the AMES prospectus into an open specification and reference implementation. There is no released schema or validator. The hierarchy, field definitions, required information and extension model remain under development.

## Why AMES?

Advertising measurement is moving toward unified measurement, in which evidence from experiments, marketing mix modeling (MMM), attribution, quasi-experiments, brand lift, attention and other approaches is increasingly interpreted and used together. AI systems will accelerate this convergence.

Measurement results, however, generally do not travel with a consistent, machine-readable description of the context needed to interpret them. Identical-looking numbers can describe different outcomes, populations, periods, comparisons and analytical claims.

AMES proposes an open, human- and machine-readable structure for the metadata accompanying advertising measurement evidence.

**AMES provides the container. Researchers, models and AI determine how to use the evidence.**

## Scope and boundaries

AMES aims to describe what was measured, how it was measured, what was reported and the context needed to interpret it.

AMES does not:

- Prescribe how advertising measurement should be conducted.
- Define a methodology for unified measurement.
- Rank measurement methods.
- Specify how evidence should be combined or weighted.
- Replace MMM, experiments, attribution or other methodologies.
- Attempt to standardize every advertising or measurement term.
- Certify that an analytical claim is valid.

The structure should accommodate heterogeneous methods and results, including measurements that do not estimate an advertising effect.

## A shared schema, independently managed evidence

AMES defines how advertising measurement evidence is described, not where it is stored.

An **AMES evidence record** means an instance of metadata organized according to the schema. It does not imply an entry in a central database.

Organizations could create and retain records within their own systems, then selectively exchange them with relevant parties. For example, an advertiser could share experimental evidence with its MMM provider while retaining control of its own records. Records could accompany reports, travel as files or be exchanged through APIs.

Using AMES would not require a central database, common storage technology, public disclosure of evidence or contribution to a benchmark.

Benchmarking is an optional downstream use. An organization could use AMES to organize its own evidence, or participants could voluntarily contribute selected records to a separately governed shared initiative. Such an initiative would establish its own participation, confidentiality, comparability and aggregation rules.

## Developing the conceptual model

The work begins with the conceptual structure, before selecting a technical schema format or deriving fields from individual studies.

The [conceptual model](docs/conceptual-model.md) develops the proposed hierarchy, candidate metadata, applicability and necessity rules, and open design questions. It also describes the narrative summary, Measurement Facts label, external vocabulary references, and the connection between business questions and intended actions.

The model distinguishes metadata AMES can support from information needed for a particular record. AI-assisted completion should prioritize consequential gaps rather than ask contributors to fill every available field.

Areas under consideration include:

| Area | Information it could describe |
| --- | --- |
| Business question, decision and action | The question, intended decision, contemplated actions under different findings, and stated decision criteria. |
| Measurement scope | Advertiser, brand, product, campaign, media, population and geography. |
| Time and duration | Relevant campaign, exposure, intervention, outcome measurement, baseline and follow-up periods; attribution or response windows; and time granularity. |
| Method and design | How the evidence was produced, including procedures, comparisons, assumptions and method-specific details. |
| Outcomes and metrics | What was measured and how each measure was defined. |
| Results | Reported quantities, their meaning, units and relevant conditions, including effect estimates where applicable. |
| Uncertainty and limitations | Reported precision, diagnostics, assumptions and constraints on interpretation. |
| Provenance | Measurement producers, data sources, analytical systems, versions and relevant independence disclosures. |
| Record documentation | How the AMES metadata was supplied, extracted, inferred, confirmed and revised. |

These are provisional organizing areas, not settled schema categories or a comprehensive inventory of fields. Each area will be developed into subcategories and candidate fields, distinguishing shared metadata from method-specific requirements.

Several distinctions will guide development:

- **What was measured and how it was measured are separate dimensions.** Sales, awareness and attention can each be measured through different methodologies.
- **A business question is context for the evidence.** Capturing it does not mean AMES recommends a method or judges whether the evidence is sufficient for a decision.
- **Results are broader than effect estimates.** Delivery counts and other descriptive measurements also belong within scope.
- **A comparison is not necessarily a counterfactual.** Where applicable, records should describe the reference condition, its intended role, its construction and the reported assumptions.
- **Measurement provenance and metadata provenance are distinct.** AI could extract metadata from a human-led analysis, or a platform could produce both an analysis and its AMES description.
- **Missing information has different meanings.** Not reported, unknown and not applicable should remain distinguishable.

Open structural questions include:

- What should one evidence record contain, and how should related analyses and results be linked?
- Which information belongs in the common core, and which belongs in method-specific extensions?
- How should shared context relate to the context of an individual result?
- Which fields should be required, optional or conditional?
- Where are controlled vocabularies useful, and where should external definitions or free text be supported?
- How should reported facts, derived metadata, AI inferences and analyst confirmations be represented?
- How should identifiers, versions and extensions work?

## Representations of the same model

The intended representations are:

- **Machine-readable:** a structured AMES evidence object.
- **Human-readable:** a concise narrative answering “What am I looking at?” and a structured “Measurement Facts” label, analogous to a nutrition label. Plain-language explanations should accompany technical uncertainty measures where useful.
- **Developer-readable:** schema definitions, documentation, examples and eventually validation and reference tools.

These should derive from the same conceptual model.

## AI-assisted creation and consumption

A proposed workflow is:

1. An analyst supplies a measurement report, API response or other evidence artifact.
2. An AI system extracts available metadata and identifies its sources.
3. The system identifies applicable metadata and prioritizes missing or ambiguous information that could materially change interpretation; it does not request every unfilled field.
4. The analyst confirms or supplies that information.
5. The system produces a record conforming to the eventual AMES schema.

Metadata inferred by AI should be distinguishable from information explicitly reported in the source. Analyst confirmation should be documented where appropriate. Structural validity alone would not establish the truth or methodological validity of the underlying evidence.

Measurement platforms could eventually emit AMES records natively.

## Interoperability and potential uses

AMES could help evidence travel among advertisers, agencies, media companies, measurement providers, model developers and AI systems without losing its context.

Potential uses include unified measurement, experimental calibration of MMM, AI reasoning, planning, optimization, benchmarking and evidence aggregation. AMES would supply contextual metadata for those systems; the downstream systems would determine how to use it.

Relevant initiatives to investigate include the Interactive Advertising Bureau’s (IAB) Project Eidos; IAB Tech Lab’s Agentic Advertising Management Protocols (AAMP) and Agentic Real Time Framework (ARTF); and the Advertising Context Protocol (AdCP). [iab.com](https://www.iab.com/news/iab-announces-project-eidos/) AMES should reference or accommodate useful existing definitions and vocabularies where appropriate. Their current specifications should be reviewed before concrete mappings or technical dependencies are adopted.

These initiatives are identified for investigation, not as established integrations or endorsements.

## Development approach

1. Develop and document the conceptual hierarchy.
2. Resolve terminology, relationships, common metadata and method-specific needs.
3. Review relevant existing standards and vocabularies.
4. Translate the agreed model into a formal machine-readable schema.
5. Pressure-test the structure against measurement examples.
6. Develop validation tools and a human-readable Measurement Facts representation.

Development will proceed iteratively. Early proposals should remain clearly distinguished from accepted design decisions.

## Presentations

- [AMES Overview (PDF)](presentations/AMES-Overview.pdf), presented to the ARF November Attribution Working Group, November 18, 2026. The deck introduces the concept; schema examples are illustrative rather than a released specification.

## Feedback

This project was initiated by Rick Bruner. Questions and proposed changes can be discussed through GitHub Issues. Early feedback on conceptual boundaries, terminology and interoperability is welcome.

## License

A license has not yet been selected. This repository is public, but an open-source license has not yet been granted.

