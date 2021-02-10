# DIF Healthcare Special-Interest Group Running Agenda & Notes

[![hackmd-github-sync-badge](https://hackmd.io/AT6AewnkTmWkJhM2Bq8a-g/badge)](https://hackmd.io/AT6AewnkTmWkJhM2Bq8a-g)

{ [mailing list](https://lists.identity.foundation/g/healthcare-sig) | [zoom link](https://us02web.zoom.us/j/88371822694?pwd=YnZvcXduYWdPSG8zOWlJSEE4Umwwdz09) }

### February 10, 2021 - **Note new time: 7am Pacific, 4pm CET** - FHIR and OCA (with some talk about CCI& VCI)
* Guests: Burak Serdar (Cloud Privacy Labs) and John Walker (Linux Foundation Public Health/Covid Credentials Initiative)
* Recording

Topics discussed:

<details>
<summary>Minutes</summary>

![](https://i.imgur.com/JeBaiIq.png)


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
* [Recording](https://us02web.zoom.us/rec/play/5RwzuV0Bg1rlVMWAULzc3VDnXs1dZMpm92WqOQUw_mw8eCuYdyO_w1e7Kwe74OBtMeUtlYHEcf1kQ7Q4.doYJdmeIyONV7PLw?continueMode=true&_x_zm_rtaid=W4Gs8hpwSsSgEyR-E6WQqA.1610303195103.8c3ac711d9bc16e4b8aca9a9c607f6b4&_x_zm_rhtaid=250) 21 October
) 21 October 2020 - Joost Flach & Mark van der Waal ([Triall.io](https://triall.io), NL) & Maarten Boender ([Sphereon](https://sphereon.com), NL) on decentralized clinical trials
* [Recording](https://us02web.zoom.us/rec/play/b293wEn7oh7XnJeuUMBNT7VHFA5gzsogPt9R9NQ3dPoPSvrzfePtuFrrjYBSAErYNAVFCLnAIvYyXTvc.xwAjMsUbDSsw_lnE?continueMode=true&_x_zm_rtaid=W4Gs8hpwSsSgEyR-E6WQqA.1610303195103.8c3ac711d9bc16e4b8aca9a9c607f6b4&_x_zm_rhtaid=250) 7 October - Georg Jürgens ([Spherity](https://spherity.com/) GmbH) and Robert Celeste ([Center for Supply Chain Studies](https://www.c4scs.org/), USA) on VC use-cases in B2B pharmaceutical ecosystems, including Spherity's Authorized Trading Partner trial with SAP and Novartis. 
