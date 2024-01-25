---
title: 'Bioschemas Resource Index for Chem and Plants'
title_short: 'Bioschemas Resource Index for Chem and Plants'
tags:
  - Bioschemas
  - Structured markup
  - Schema.org
  - RDF
  - Knowledge graph
  - SPARQL
authors:
  - name: Daniel Arend
    orcid: 0000-0002-2455-5938
    affiliation: 1
  - name: Alessio Del Conte  
    orcid: 0000-0002-8052-3519
    affiliation: 2
  - name: Manuel Feser
    orcid: 0000-0001-6546-1818
    affiliation: 1
  - name: Yojana Gadiya
    affiliation: 11,12
    orcid: 0000-0002-7683-0452
  - name: Alban Gaignard
    affiliation: 1
  - name: Leyla Jael Castro
    orcid: 0000-0003-3986-0510
    affiliation: 3
  - name: Ivan Mičetić
    orcid: 0000-0003-1691-8425
    affiliation: 2
  - name: Sebastien Moretti
    orcid: 0000-0003-3947-488X
    affiliation: 6,7
  - name: Steffen Neumann
    orcid: 0000-0002-7899-7192
    affiliation: 4,5
  - name: Noura Rayya
    affiliation: 1
  - name: Claire Rioualen
    affiliation: 1
  - name: Martina Summer-Kutmon
    affiliation: 1
  - name: Ginger Tsueng
    orcid: 0000-0001-9536-9115
    affiliation: 9
  - name: Egon Willighagen
    orcid: 0000-0001-7542-0286
    affiliation: 8
  - name: Ulrike Wittig
    orcid: 0000-0002-9077-5664
    affiliation: 10
affiliations:
  - name: Leibniz Institute for Plant Genetics and Crop Plant Research (IPK) Gatersleben, Germany
    index: 1
  - name: Department of Biomedical Sciences, University of Padua
    index: 2
  - name: ZB MED Information Centre for Life Sciences
    index: 3    
  - name: Leibniz Institute of Plant Biochemistry (IPB)
    index: 4
  - name: German Centre for Integrative Biodiversity Research (iDiv) Halle-Jena-Leipzig
    index: 5
  - name: SIB Swiss Institute of Bioinformatics, Vital-IT group, Lausanne
    index: 6
  - name: Department of Ecology and Evolution, University of Lausanne
    index: 7
  - name: Department of Bioinformatics - BiGCaT, NUTRIM, Maastricht University
    index: 8
  - name: The Scripps Research Institute
    index: 9
  - name: Heidelberg Institute for Theoretical Studies, Heidelberg, Germany
    index: 10
  - name: Fraunhofer Institute for Translational Medicine and Pharmacology, Germany
    index: 11
  - name: Bonn-Aachen International Center for Information Technology (B-IT), University of Bonn, 53113 Bonn, Germany
    index: 12
date: 8 November 2023
cito-bibliography: paper.bib
event: BH23EU
biohackathon_name: "BioHackathon Europe 2023"
biohackathon_url:   "https://biohackathon-europe.org/"
biohackathon_location: "Barcelona, Spain, 2023"
group: Project 7
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/arendd/biohackathon-projects-2023
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Daniel Arend \emph{et al.} **all authors are in alphabetical order**
---
# Introduction
As part of the BioHackathon Europe 2023, we here report on the progress of the hacking team preparing a resource index and knowledge graph based on the JSON-LD Bioschemas markup from several resources in the life- and natural sciences, predominantly from the fields of plant- and (bio)chemistry research. This preliminary analysis will allow us to better understand how Bioschemas markup is currently used in these two communities, so we can take actions to improve guidelines and validation on the Bioschemas side, and markup and the data providers side. The lessons learnt will be useful for other communities as well. The ultimate goal is facilitating and improving interoperability across resources. 

<!-- Guha_2016 is doi:10.1145/2844544 -->

[Bioschemas](https://bioschemas.org/)[@citesAsAuthority:Gray_2017] is a community-based effort providing specifications, tools and training on how to add structured markup on webpages in Life Sciences. It builds on top of [schema.org](https://schema.org/) [@usesMethodIn:Guha_2016] by providing new types and profiles relevant for Life Sciences, i.e., type usage recommendations, useful to describe Life Sciences concepts (e.g., taxa or chemicals) but also and research outcomes in general (e.g., datasets or software). Although Bioschemas main aim is to facilitate findability, it also provides an initial interoperability layer. 

The JSON-LD from multiple resources can be imported into either central or distributed SPARQL endpoints to provide queries against multiple data sources. While incorporating Bioschemas markup to a resource is fairly lightweight, adding and maintaining a SPARQL endpoint to a resource can be challenging. 

This project builds upon previous work done by the [Intrinsically Disordered Protein (IDP)](https://elixir-europe.org/communities/intrinsically-disordered-proteins) Community in aggregating Bioschemas markup and constructing the IDP knowledge graph, which served as the basis for the IDPcentral registry ([@citesAsAuthority:Gray_2022;@citesAsAuthority:Gray_2021;@citesAsAuthority:Ammar_2022]). During these efforts, we used different approaches for data integration, but always based on Bioschemas implementation from one provider. In the project reported here, we are using the JSON-LD from different providers with their own Bioschemas implementations.

# Material and Methods

The following is a brief introduction of the components, linked data sources and analysis approaches we used. 

## Knowledge Graphs

We used both local developer instances and a publicly accessible demo site hosted in a cloud-based virtual machine. A public instance of GraphDB with the Chem and Plants knowledge graph is available at knowledge.ipk-gatersleben.de (login/password: demo/demo).

## Data Sources

We initially agreed on extracting reduced file dumps containing Bioschemas markup formatted as JSON-LD for six selected repositories or databases. During the week at the BioHackathon we were able to get in touch with other people interested in this project and add an additional resource to our set. Subsequently, the seven different resource are shortly described. 

### Coconut

### e!DAL-PGP
The e!DAL-PGP (Plant Genomics and Phenomics Research Data Repository) is an infrastructure to comprehensively publish plant research data. This covers in particular cross-domain datasets that are not being published in central repositories because of its volume or unsupported data scope, like image collections from plant phenotyping and microscopy, unfinished genomes, genotyping data, visualizations of morphological plant models, data from mass spectrometry as well as software and documents. All published datasets are accessible via a DOI linking to a dedicated content page, which embeds a schema.org and BioSchema markup in the HTML code. Currently, it supports the `Dataset` and `Taxon` profiles.

### MassBank
MassBank [@citesAsAuthority:Horai_2010] is an open spectral database that provides mass spectral data records. Bioschemas markup is embedded in the rendered HTML pages of individual records. MassBank has been supporting Bioschemas markup for the individual records as `Dataset` and `MolecularEntity` since 2018, and recently switched to use `ChemicalSubstance`. The records are hosted on GitHub and released regularly [https://github.com/MassBank/MassBank-data/releases]. A datadump of the JSON-LD information is part of the data releases. 

### MetaNetX
MetaNetX [@citesAsAuthority:Moretti_2021] is an open resource unifying metabolites and biochemical reactions, in the context of metabolic models, in a common namespace. MetaNetX provides bioschemas markup for each metabolite record as `MolecularEntity` with structural information (i.e. InChI, SMILES and InChIKey) and cross-references. A SPARQL endpoint is also available. A datadump of the JSON-LD information is part of the data releases.

### nmrXiv

### WikiPathways
WikiPathways already used Bioschemas on their website and modelled each pathway as a `Dataset` [@citesAsDataSource:citesAsAuthority:Agrawal_2023]. Genes, proteins, and metabolites 
were added as keywords. Here, we extended the new `libGPML` library (https://github.com/PathVisio/libGPML) with a Java-based method to convert a WikiPathways GPML file into
Bioschemas, taking advantage of the `org.json` library. This generated JSON-LD adds a `Taxon` resource, as well as `BioChemEntity`
resources for genes, `Protein` for proteins, and `MolecularEntity` for the small molecules. The code is made available at
https://github.com/BiGCAT-UM/org.pathvisio.io.bioschemas.

### SABIO-RK
SABIO-RK [@citesAsDataSource:citesAsAuthority:Wittig_2018] is a manually curated database for biochemical reactions and their kinetic properties. Each database entry represents kinetic parameters for a biochemical reaction including reaction participants (e.g. substrates, products, enzymes) in a biological source (e.g. organism, tissue, cell location) under specific experimental conditions (e.g. pH, temperature). SABIO-RK provides Bioschemas markup for each database entry. 

# Results
## JSON-LD datadumps
JSON-LD datadumps were prepared for a selection of databases from the plant science and (bio-)chemistry domains. 

 | Resource     | Description                                                               | Import as named graph            | File                                 |
|--------------|---------------------------------------------------------------------------|----------------------------------|--------------------------------------|
| [Coconut](https://coconut.naturalproducts.net/)      | Database of natural products                                              | https://biohack2023/coconut      | [coconut.ttl](coconut.ttl)           |
| [e!DAL-PGP](https://edal-pgp.ipk-gatersleben.de/)     | e!DAL - Plant Genomics & Phenomics Research Data Repository               | https://biohack2023/edal         | [edal.ttl](edal.ttl)                 |
| [MassBank](https://massbank.eu/)     | Mass spectra database                                                     | https://biohack2023/massbank     | [massbank.ttl](massbank.ttl)         |
| [MetaNetX](https://www.metanetx.org/)     | Platform for genome annotation and large-scale metabolic network analysis | https://biohack2023/metanetx     | [metanetx.ttl](metanetx.ttl)         |
| [nmrXiv](https://nmrxiv.org/)       | NMR spectroscopy data repository                                          | https://biohack2023/nmrxiv       | [nmrxiv.ttl](nmrxiv.ttl)             |
| [WikiPathways](https://www.wikipathways.org/)| Platform for biological pathways                                          | https://biohack2023/wikipathways | [wikipathways.ttl](wikipathways.ttl) |
| [SABIO-RK](https://sabiork.h-its.org/) | Biochemical Reaction Kinetics Database | https://biohack2023/sabio-rk | [sabio-rk.ttl](sabio-rk.ttl) |

## Example SPARQL queries for Chem and Plants KG:

Here there are some examples queries to the chem and plants knowledge graph making use of the connection between both data domains.

### Which resources mention the compound caffeine?
```sparql
PREFIX schema: <http://schema.org/>
SELECT ?resource WHERE {
  GRAPH ?resource {
    ?entry schema:inChIKey ?key .
  }
  BIND("RYYVLZVUVIJVGH-UHFFFAOYSA-N" as ?caffeineChIKey)
  FILTER (?key = ?caffeineChIKey)
} 
LIMIT 100 
```
### Count the number of entries per resource talking about caffeine:
```sparql
PREFIX schema: <http://schema.org/>
SELECT ?resource (COUNT(?entry) as ?entriesAboutCoffe) WHERE {
  GRAPH ?resource {
    ?entry schema:inChIKey ?key .
  }
  BIND("RYYVLZVUVIJVGH-UHFFFAOYSA-N" as ?caffeineChIKey)
  FILTER (?key = ?caffeineChIKey)
} 
GROUP BY ?resource
LIMIT 100
```
### List chemical pathways in plants:
```sparql
PREFIX biohack23: <https://biohack2023/>
PREFIX schema: <http://schema.org/>
PREFIX up: <http://purl.uniprot.org/core/>
PREFIX taxon: <http://purl.uniprot.org/taxonomy/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
SELECT DISTINCT  ?pathway ?organismName 
WHERE {
  GRAPH biohack23:wikipathways {
    ?pathway a schema:Dataset ;
      schema:taxonomicRange ?taxon .
  }
  {
    SELECT DISTINCT ?taxon ?organismName ?commonName ?ncbiURI
    WHERE {
      {
        SELECT distinct ?taxon ?ncbiURI
        WHERE {
          GRAPH biohack23:wikipathways {
            ?x schema:taxonomicRange ?taxon .
            BIND(STRAFTER(STR(?taxon), "_") AS ?ncbi)
            BIND(URI(CONCAT(
              "http://purl.uniprot.org/taxonomy/" ,?ncbi))
              AS ?ncbiURI)
          }
        } 
      }
      SERVICE <https://sparql.uniprot.org/sparql> {
        ?ncbiURI up:scientificName ?organismName ;
          up:commonName ?commonName .
        # Taxon subclasses are materialized, do not use rdfs:subClassOf+
        FILTER EXISTS {
          ?ncbiURI rdfs:subClassOf taxon:33090 .
        }
      }
    }
  }
}
```
### List compounds per plant pathway:
```sparql
PREFIX biohack23: <https://biohack2023/>
PREFIX schema: <http://schema.org/>
PREFIX up: <http://purl.uniprot.org/core/>
PREFIX taxon: <http://purl.uniprot.org/taxonomy/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
SELECT DISTINCT ?pathway ?organismName ?molecule 
WHERE {
  GRAPH biohack23:wikipathways {
    ?pathway a schema:Dataset ;
      schema:taxonomicRange ?taxon .
    ?molecule a schema:MolecularEntity ;
      schema:includedInDataset ?pathway .
  }
  {
    SELECT DISTINCT ?taxon ?organismName ?commonName ?ncbiURI
    WHERE {
      {
        SELECT distinct ?taxon ?ncbiURI
        WHERE {
          GRAPH biohack23:wikipathways {
            ?x schema:taxonomicRange ?taxon .
            BIND(STRAFTER(STR(?taxon), "_") AS ?ncbi)
            BIND(URI(CONCAT(
              "http://purl.uniprot.org/taxonomy/" ,?ncbi))
              AS ?ncbiURI)
          }
        } 
      }
      SERVICE <https://sparql.uniprot.org/sparql> {
        ?ncbiURI up:scientificName ?organismName ;
          up:commonName ?commonName .
        # Taxon subclasses are materialized, do not use rdfs:subClassOf+
        FILTER EXISTS {
          ?ncbiURI rdfs:subClassOf taxon:33090 .
        }
      }
   }
  }
}
```
### Molecular entities in pathways of plant resources:
```sparql
PREFIX biohack23: <https://biohack2023/>
PREFIX schema: <http://schema.org/>
PREFIX up: <http://purl.uniprot.org/core/>
PREFIX taxon: <http://purl.uniprot.org/taxonomy/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
SELECT DISTINCT ?pathway ?organismName ?molecule ?resource ?property ?object
WHERE {
  GRAPH biohack23:wikipathways {
    ?pathway a schema:Dataset ;
      schema:taxonomicRange ?taxon .
    ?molecule a schema:MolecularEntity ;
      schema:inChIKey ?key ;
      schema:includedInDataset ?pathway .
  }
  {
    SELECT DISTINCT ?taxon ?organismName ?commonName ?ncbiURI
    WHERE {
      {
        SELECT distinct ?taxon ?ncbiURI
        WHERE {
          GRAPH biohack23:wikipathways {
            ?x schema:taxonomicRange ?taxon .
            BIND(STRAFTER(STR(?taxon), "_") AS ?ncbi)
            BIND(URI(CONCAT(
              "http://purl.uniprot.org/taxonomy/" ,?ncbi))
              AS ?ncbiURI)
          }
        } 
      }
      SERVICE <https://sparql.uniprot.org/sparql> {
        ?ncbiURI up:scientificName ?organismName ;
          up:commonName ?commonName .
        FILTER EXISTS {
          ?ncbiURI rdfs:subClassOf taxon:33090 .
        }
      }
    }
  }
  {
    {
      GRAPH ?resource {
        ?x schema:inChIKey ?key ;
          ?property ?object .
      }
    } MINUS {
      GRAPH biohack23:wikipathways {
        ?x schema:inChIKey ?key .
      }
    }
  }
}
```

## Capturing information from Controlled Vocabularies

Some of the resources we indexed and imported into the knowledge graph make use of the `DefinedTerm` schema.org type to reference and re-use controlled vocabulary and ontology terms. While technically it is sufficient to include `"@type": "DefinedTerm"` and an IRI as `@id`, presenting any human readable information requires to visit or import possibly multiple controlled vocabulary lists or ontologies. 

We conducted surveys based on the list of `exampleURL` on the Bioschemas Live-deploys page (https://bioschemas.org/developer/liveDeploys). Based on the results of the survey, we proposed two new profiles to help normalize and enable proper capture for this field, i.e., in future endeavors. 

Additionally, there may be controlled vocabularies in use that are not formalized into an ontology. In such cases, there may not be a suitable IRI and additional information would be needed. For example, the ClinicalTrials.gov's Protocol Registration and Results System (PRS) Schema has controlled vocabulary used as values for many properties in their own codebook, but these terms are not necessarily in a formal ontology. In this case, it is important to leverage the `DefinedTermSet` profile to ensure sufficient information is included for provenance.

# Howto

A working demo of the plant and chemistry knowledge graph can be replicated by importing a selection of [data dumps](https://github.com/elixir-europe/biohackathon-projects-2023/tree/main/7/Chem-Plants-KG) directly in a running instance of GraphDB. A Docker Compose file is provided in appendix A for convenience. Upon instantiation of GraphDB a new repository must be generated. In the repository, datadumps in turtle format should be imported as named graphs with URIs in the form `https://biohack2023/<resource>`. After the import of RDF data, SPARQL queries can be run directly with the SPARQL Query & Update interface through the UI or programmatically at the SPARQL endpoint `http://localhost:7200/repositories/<repository name>`.

# Discussion

After the first sessions during the hackathon, it was quite early clear, that the initial idea of extracting datadumps with schema.org and BioSchema markup and feed them into a graph database was very optimistic. It became visible, that the specifications are interpreted in many different ways, which results in low or even no interoperability between actual connected datasets. 

We spend a lot of time in curating the datadumps and add additional properties or modify existing one to create connections between datasets otherwise it is not possible to show an initial level of interoperability. As a general recommendation that can be derived from this is to always use the proper `@id` attributes and complement with `@sameAs` attributes to all other possible identifiers. In fact, `@id` attribute is considered a minimum attribute while `@sameAs` a recommended one in Bioschemas profiles.

# Outlook

Beside the extraction and curation of the resource datadumps, we also drafted a howto explaining the set-up of a local instance of a graph database and how to equip it with datadumps based on schema.org / Bioschemas. We will get in touch with the editors of RDMKit and FAIR Cookbook to evaluate if this is valuable for writing an entry [@citesAsPotentialSolution:Rocca2023FAIR]. Another interesting idea for future work and to get more out of the developed knowledge graphs is using synergies from the combining it with frameworks for Large Language Models (LLMs) e.g. BioCypher [@citesAsPotentialSolution:Lobentanzer_2023] to create a user friendly chat client and provide the end user an intuitive platform to get access to the explored connections and the contained knowledge.

# Acknowledgements

This work was performed during the ELIXIR BioHackathon Europe 2023 organized by ELIXIR in November 2023. 
This work was supported by the German Research Foundation (DFG) within the project “Establishment of the National Research Data Infrastructure (NFDI)” in the consortium FAIRagro (www.fairagro.net, project number 501899475) and NFDI4Biodiversity (www.nfdi4biodiversity.org, project number 442032008).


# References

# Appendix A

A docker-compose setup to spin-up a local Knowledge Graph instance.

docker-compose.yml
```yml
version: '1.0'
services:
  graphdb:
    image: ontotext/graphdb:10.4.0
    ports:
      - 7200:7200
      - 7300:7300
    restart: unless-stopped
    command:
      - -Dgraphdb.home=/opt/graphdb/home
      - -Dgraphdb.workbench.cors.enable=true
      - -Dgraphdb.workbench.cors.origin=*
      - -Dgraphdb.append.request.id.headers=true
      - -Dgraphdb.workbench.importDirectory=/opt/graphdb/home/graphdb-import
      - -Dhealth.max.query.time.seconds=60
      - -Dreuse.vars.in.subselects=true
    volumes:
      - ./graphdb-home:/opt/graphdb/home
```
