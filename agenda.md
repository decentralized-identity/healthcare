# DIF Healthcare Special-Interest Group Running Agenda & Notes

[![hackmd-github-sync-badge](https://hackmd.io/AT6AewnkTmWkJhM2Bq8a-g/badge)](https://hackmd.io/AT6AewnkTmWkJhM2Bq8a-g)

{ [mailing list](https://lists.identity.foundation/g/healthcare-sig) | [zoom link](https://us02web.zoom.us/j/88371822694?pwd=YnZvcXduYWdPSG8zOWlJSEE4Umwwdz09) }

### February 24, 2021 - ??

### February 10, 2021 - **Note new time: 7am Pacific, 4pm CET** - FHIR and OCA (with some talk about CCI& VCI)
* Guests: Burak Serdar (Cloud Privacy Labs) and John Walker (Linux Foundation Public Health/Covid Credentials Initiative)
* [Recording](https://us02web.zoom.us/rec/share/z9ridVGc3JvKEmSJxyqB6RCJUvfLgGTCq9eYN1BgbTezdOybdH-qt039J_J_QVd-.jih7A7M72ZIIFgkh)

Topics discussed:
- Layman's history of and intro to FHIR, SMART on FHIR, and LH7 protocols
- Description of the fundamental technical problem: getting secure, trustworthy medical records out of an EHR system, via FHIR, into a maximally portable VC that's just as trustworthy (while not the system of record for that patient)
- Two approaches prototyped by the same task force at ToIP:
    - VCI: FHIR --> LD --> OCA --> VC format of choice (depicted in minutes)
    - Burak's more end-to-end solution, allowing trust authorities to specify the conversion from FHIR to VC Schemata of their design via OCA
- Useful Links:
    - Relevant ToIP task forces and WGs: [Semantic Domain](https://wiki.trustoverip.org/display/HOME/Semantic+Domain+Group) and [FHIR Focus Group](https://wiki.trustoverip.org/display/HOME/FHIR+Focus+Group), etc
    - Other references: [Kantara BIT](https://kantarainitiative.org/confluence/display/WGISI/Blinding+Identity+Taxonomy), [FHIR](http://hl7.org/fhir/), commercial tooling vendors [EPIC](https://fhir.epic.com/)     


<details>
<summary>Minutes</summary>

John's CCI/LFPH prototype:
![](https://i.imgur.com/JeBaiIq.png)

Burak's prototypes for extending OCA to specify FHIR extraction:
- [OCA projection](https://github.com/bserdar/oca-projection-prototype) and [JSON->OCA conversion prototype](https://github.com/bserdar/jsonschema2oca)

* John Walker
    * JSON --> JSON-LD --> OCA
* Burak Serdar 
    * OCA originally conceived as a data CAPTURE mechanism, but I have been involved for a while applying it to privacy use cases
* John's overview of [FHIR](http://hl7.org/fhir/)
    - protocol for HL7 (4th iteration of it)
    - JSON/JSON Schema-based
    - EPIC and Cerner (sp?) are actually more installed in the wild; FHIR still a minority 
        pipe-separated messaging structure 
    - EHR and Health Info Exchanges use it as best-practice messaging protocol
        - SMART on FHIR (boston group and Josh Mandell)- OAuth2 + JSON interface and transport for FHIR
    - Our work starts from the assumption that personal health info is accessible via SMART on FHIR
        - extracting and exchanging data in 
    - As with any open community, there's tons of development happening here; one strategy that we have decided on is to leverage validation and data structure definitions, and not reinvent any of this or create new opacity  
* VCI 
    - proposed architecture SMART on FHIR endpoint with FHIR endpoint
* Data Mechanics
    - OCA consumes the data and applies overlays and hashes and locks it to be tamperproof 
* Burak's overview of [OCA work] and [FHIR work](https://wiki.trustoverip.org/display/HOME/FHIR+Focus+Group) at ToIP
    - see also [Privacy and Risk Task Force]()
    - Overlay architecture structures FLAT data, tho-- but FHIR is very graphed, and "circularly linked"
    - Complex mapping of OCA to FHIR, that I've [been working on](https://github.com/bserdar/jsonschema2oca), reshapes this
        - This enables *transformations* and overlays onto FHIR messages
        - I've also worked on an [OCA projection protoype](/oca-projection-prototype/)
* John - LD versus JWT - We're working on FHRI --> LD --> JWTs 
* Q and A
    - Programmer could convert to and from LD the programmer could do on the server side? Does OCA enable client-side ZKP?
        - 2 use cases:
        1. EHR --> LD (apply your own schemata, apply ZKP) --> credentials (you'd need an agent before it goes to a wallet); there's value in making a generalized approach for transparently and accurately get health records into an LD format and out of "FHIRland" - tamperproofed 
        2. ??
        - Burak: 
        1. OCA can be presentation layer on extracted FHIR data
        2. But there's another use case where OCA can help translate server-to-server
        - John: I might download my own health records and put them in a POD, or a PDS-- how do I get my health records into my own controlled storage; 
    - John: Once you pull data out of EHR, it's read-only (that's the authoritative system of record)-- we just want to give people control over their own copy of that
        - what about the deltas? That's further down the roadmap
    - Burak: Complementary approach: extending OCA to "Projection" - more "end to end", allows governing authorities to define not just the LD Schema for issuance of creds but also the FHIR conversation end to end
    - Schema work - Ontology happening (early days; Mattr leading it?)
- Stephan - FHIR has no idea of doctor's DID and patient's DID
    - Stephan: Josh's VCI is poking in that direction: ISO unification of business processes could hold EHR and hospitals to best-practices of switching their ID records to SSI envelopes and identities and tooling...
    - Stephan: Vaccination might be too shiny of an object to go after-- if this isn't done by June, will it go anywhere? What about other use-cases? What about health proofs for life insurance? Do you have other use-cases in mind for self-managed health proofs?
        - John: We're not exploring them very actively, but we're open to them... (follow-up session!)
    - Contacts: bserdar at computer dot org and  johnw dot cci at lfph dot io 
</details>

### January 27, 2021 - **Note new time: 7am Pacific, 4pm CET**
 * [Recording](https://us02web.zoom.us/rec/share/0NC365kjRUrWNMqOxrMrt6V0Us4Cylb7UkQmLPKph8PsmnrXH56mZPm6krKndQQI.TLUILPB-lTFci9mr)
 * Overview of the problem space (smart contracts and trust ecosystems)
    * B2B: DSCSA (Spherity!); Allied Clinicial Access (?), Federated Learning Coordination (OpenMined?)
    * B2C/E: Vaccination Proofs; Ecosystem-Consumer; Clinician Credentialling; eligibility/proof of coverage
    * B2G: Covid19 reporting
 * What's missing?
    * Auth (whence siop?); lightweight API in a sound JS library would accelerate B2B exploration; 
 * Q&A: Tom Jones: patient matching as a blocker left off this list; [Foster bill](https://foster.house.gov/media/press-releases/foster-introduces-bipartisan-digital-identity-legislation); [CA blockchain alliance](https://www.blockadvocacy.org/); [Kantara work](https://wiki.idesg.org/wiki/index.php/State_Issued_ID_for_Healthcare) & Jim is also involved with a Medicaid group

### List of topics and guests 2020: 
Meetings
* [Recording](https://us02web.zoom.us/rec/play/V6-9D-58vNJqPTC-LgYM5qOZEeysMhNiR5N984081C3UdK3NlgZjPWIvR2-WdvVDgBJn-7o2cnKsPcPH.cpBSPLqCv_Er46_0?continueMode=true&_x_zm_rtaid=W4Gs8hpwSsSgEyR-E6WQqA.1610303195103.8c3ac711d9bc16e4b8aca9a9c607f6b4&_x_zm_rhtaid=250) 2 December - Jim St. Clair ([Lumedic](https://www.lumedic.io/)), Philipp Page ([Human Colossus](https://humancolossus.foundation/)), and Paul Knowles ([Human Colossus](https://humancolossus.foundation/), [ToIP](https://trustoverip.org/)) on Trust Frameworks and Semantic Frameworks for medical data
* [Recording](https://us02web.zoom.us/rec/share/HslRkFaYCu3JOuQDTSKQEHCe0HGUCivTASa-qdItJBMwdmZFZHBmWekgrYLLe_98.E0GRYb-RAlviCdoo) 18 November - Matthias de Bièvre ([MyData](https://mydata.org), [aNG](https://anewgovernance.org)) & Dominik Diemel ([Comuny.de](https://comuny.de)) on A New Governance and the regulatory landscape around human-centric medical data in Europe
* [Recording](https://us02web.zoom.us/rec/play/gYcNhVZ9vIgkLJE-I7MKRheQjM3ZgM6aziRT3YCpb0j7FvzDykHRpHWHXL74a9f_OdzEZjbrliKHVLfW.pMk8S3vvBkpC8POf?continueMode=true&_x_zm_rtaid=W4Gs8hpwSsSgEyR-E6WQqA.1610303195103.8c3ac711d9bc16e4b8aca9a9c607f6b4&_x_zm_rhtaid=250) 4 November 2020 - Iain Henderson ([JLinc](https://www.jlinc.com/technology), [Mydata](https://mydata.org/)) on the MyData Commons project and the MyData Operators [whitepaper](https://mydata.org/wp-content/uploads/sites/5/2020/04/Understanding-Mydata-Operators-pages.pdf) and group

<details><summary>Minutes</summary>

- Self introduction:
    - Consultant for the Scottish govt - advise startups and facilitate business thinking
    - JLinc - Business side
    - Very active in MyData -
    - IIW
- Intro - Data grabs & Surveillance Capitalism - Most but not all
    - Confidential data - there are business niches where people DON'T want as much data as possible!
- MyData Commons
    - Blog post - Covid as trial by fire for our data ecosystem - we need global citizenship management process, but we don't have the infra for that
    - Thesis early on: We need a commons, won't have it soon, but maybe in time for Covid-20
    - April-may-june - MyData team in a Covid Hackathon - Personal data store for each individual - used JLinc for SSI and a SalesForce instance (had both on hand)
    - Lessons from multiple hackathons
![](https://i.imgur.com/Qb23MhZ.png)
- Massive data problem- how can public health authorities get data about the asymptomatic, the healthy, and the mildly symptomatic? How can you get people to donate helpful data at scale?
    - Symptom-tracking apps (i.e. [DataYogi.me](http://datayogi.me),
    - Dummy data+SalesForce —> population-level analytics
    - Integration of wallets and credentials (Digital Wallet JLinc integration) - just a prototype, not taken to market
- MyData alignment/interop
    - MyData - working on shared Schema for Operators group - a dictionary that can be consumed as LD, schema.org, OCA
![](https://i.imgur.com/iHnusLc.png)
- Last 6 months have taught me that
    - 3 separate clients all coming to : current clients - 1 health, 2 in less sensitive areas
        - leave data on device
        - get ML models on depersonalized/anonymized
        - openMined - analyze data without it leaving the subject's device
![](https://i.imgur.com/LaVyHtn.png)
    - "Notice & Consent doesn't scale" —John Wunderlich (JLinc, IIW)
    - realtime co-management of data
    - multi-directional, multi-stakeholder CRUD on all data
    - "personal data logistics"
- Q and A
    - Bernard: Data quality in Covid Commons?
        - Iain: Medics designed the system (HL7/FHIR)
        - Iain: Self-Managed data tends to have lower incentive problems - individual managing own data and only-once-ing incentivizes honesty
    - Bob: How does patient control their data sharing?
        - Iain: SISA (written to ledger/immutable store!) —> contract law as enforcement rather than technical control of data
        - Iain: JLinc's early work a chain of confidentially
    - Bob: Accord project and CommonAccord? Attempting to take common legal language and standardize on it, make it more machine-readable (IEEE WG on machine-readable contracts as well)
    - Iain: Individual can come to the info-sharing counterparty as a peer ;
        - data quality and compliance are shot in status quo
        - FAANG only people making money in current system
    - Juan: PDS?
        - Iain: Covid is driving home the problem of access to and control of each patient's healthcare records; UK example: high-level summary records are owned by NHS and shared automatically to all pharmacies; My contention is that the core record should be available to patient, AT LEAST through their covid app and build a bridge between their individual records and make better data available to public health records
            - In statute, the NHS record is mine
            - Children's "blue folders" (maternity records) and "red books" (birth - 5 records) are digital and shared; when they were in paper, it was under mother's control, but in being digitized, shared data
            - MyData "DIDs for kids" didn't go very far, too scary to medical industry interlocutors
    - Bernard: I want to understand role of ML in here
        - This example was from self-asserted diet study— OpenMined was involved to help diet data be studied
    - Bob: 4% of US medications are misdirected! 
</details>

* [Recording](https://us02web.zoom.us/rec/play/5RwzuV0Bg1rlVMWAULzc3VDnXs1dZMpm92WqOQUw_mw8eCuYdyO_w1e7Kwe74OBtMeUtlYHEcf1kQ7Q4.doYJdmeIyONV7PLw?continueMode=true&_x_zm_rtaid=W4Gs8hpwSsSgEyR-E6WQqA.1610303195103.8c3ac711d9bc16e4b8aca9a9c607f6b4&_x_zm_rhtaid=250) 21 October
) 21 October 2020 - Joost Flach & Mark van der Waal ([Triall.io](https://triall.io), NL) & Maarten Boender ([Sphereon](https://sphereon.com), NL) on decentralized clinical trials
* [Recording](https://us02web.zoom.us/rec/play/b293wEn7oh7XnJeuUMBNT7VHFA5gzsogPt9R9NQ3dPoPSvrzfePtuFrrjYBSAErYNAVFCLnAIvYyXTvc.xwAjMsUbDSsw_lnE?continueMode=true&_x_zm_rtaid=W4Gs8hpwSsSgEyR-E6WQqA.1610303195103.8c3ac711d9bc16e4b8aca9a9c607f6b4&_x_zm_rhtaid=250) 7 October - Georg Jürgens ([Spherity](https://spherity.com/) GmbH) and Robert Celeste ([Center for Supply Chain Studies](https://www.c4scs.org/), USA) on VC use-cases in B2B pharmaceutical ecosystems, including Spherity's Authorized Trading Partner trial with SAP and Novartis. 

<details>
<summary>Minutes</summary>

- Attendance/ Introductions
    - Najib Rehman (??)
        - working with a data integrator to support swiss pharma clients on CTs; DLT to speed things up a bit
    - Willy (??)
    - Leah Houston
    - Bernard
    - Catherine
![](https://i.imgur.com/PBYgxGy.png)
- Robert's presentation
        - scale: billions of transactions in a 3-hour overnight crunch period
        - trial generating valuable material and guidance for industry governance processes
        - interaction of technical, operations, and compliance/governance groups
        - API and Schemata —> starting point for standardization
    - "This is an industry that runs on standards"
        - GS1 for txn info and ids,
        - Everyone obvi wants to look with the W3C standards
            - all the examples in the spec are very consumer-based; bias and mental model
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c3cd24cf-2a3c-4e0c-9ffd-ccc02ef75187/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c3cd24cf-2a3c-4e0c-9ffd-ccc02ef75187/Untitled.png)
- "Challenges"
    - **Challenge #1:** Scale
    - Standards and misfit b/w W3C as-is today and these use-cases
    - **Challenge #2:** Retention req (6 year record-keeping obligation) —> binding VCs and VPs need to be archival/auditable for 6 years!
        - VP ephemerality (in VC spec)
        - **Lesson#1** Identifier ←→ Company name binding needs to be durable/archival
    - **Challenge #3:** How does Company B know that A was handling credentials properly and according to industry and/or regulatory rules, if they just get a log or a recipt?
        - Logging of credential exchanges? reusing credentials falsely, replay attacks, etc?
        - Out of scope for now, but we're starting to look at the possibility of a third-party compliance auditor or guarantor? Do they attach additional VCs?
![](https://i.imgur.com/7GSf3rb.png)
- security risks
    - drug cartel made 25 shell corps to hide infiltration in a drug supply chain
        - mitigations of legal identity issues
        - drug cartels have a big R&D budgets for impersonation, counterfeiting, etc— way more tech savvy than many supply chain actors such as smalltown pharmacies!
- Q and A
    - Najid: FMD (I used to work for Pfizer so I know the DCSCA and serialization!); what are your thoughts on B2B2P and P identity?
    - Orphan disease area? Teaching hospital ... Therapies and vectors?
    - Volume and complex stakeholders...
    - Standards around labeling (tagging blood in loop); 200K-1.3m$ therapies! the liabilities (and stakes) are massive there
    - How do we get everybody on board? Some people are incentivized for intransparency
    - Bob: One of the pilots in the FDA program was a very expensive personalized drug: the roundtrip; temp control in transit; temperature indicator behind a bar code, so that bar code changed
    - Georg: Novartis is looking into this for Kamriah; validated (manual) process for now
    
</details>