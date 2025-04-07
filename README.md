# Software Architecture Problem Prediction Ontology

## Introduction

This repository contains a modular OWL/RDF ontology designed to model knowledge about software technologies, architectural concepts, potential problems (like dependency issues, vulnerabilities, compatibility errors), and their solutions within specific contexts. The primary goal is to build a knowledge graph that can be used to predict potential problems in software architecture designs based on the chosen technology stack, versions, and architectural patterns.

The ontology is defined using the Turtle (.ttl) syntax and adheres to OWL 2 DL principles where possible.

## Base URI and Prefixes

*   **Base URI:** `http://example.org/software-architecture-ontology#`
*   **Default Prefix:** `:`
*   **Standard Prefixes:** `owl`, `rdf`, `rdfs`, `xsd` are used throughout.

## Modular Structure

To maintain clarity and adhere to best practices (including line limits), the ontology is split into several modules, each focusing on a specific aspect of the domain. Modules import others as needed.

*   **Core Definition:**
    *   `ontology_core.ttl`: Defines the top-level abstract classes (`SoftwareEntity`, `Problem`, `Solution`, `Context`, `DataSource`, `ArchitecturalConcept`) and the ontology IRI.
*   **Class Hierarchies:**
    *   `ontology_technologies.ttl`: Defines the hierarchy for `:Technology`, `:TechnologyVersion`, `:SoftwareComponent`, and specific technology types (e.g., `:ProgrammingLanguage`, `:Platform`, `:DatabaseTechnology`). Imports `ontology_core.ttl`, `ontology_architecture.ttl`.
    *   `ontology_problems.ttl`: Defines the hierarchy for `:Problem` subclasses (e.g., `:DependencyIssue`, `:SecurityVulnerability`). Imports `ontology_core.ttl`, `ontology_architecture.ttl`.
    *   `ontology_solutions.ttl`: Defines the hierarchy for `:Solution` subclasses (e.g., `:VersionUpdate`, `:Workaround`). Imports `ontology_core.ttl`, `ontology_technologies.ttl`.
    *   `ontology_context.ttl`: Defines the hierarchy for `:Context` subclasses (e.g., `:ProjectContext`, `:EnvironmentContext`). Imports `ontology_core.ttl`.
    *   `ontology_datasources.ttl`: Defines the hierarchy for `:DataSource` subclasses (e.g., `:GitHubIssue`, `:OfficialDocumentation`). Imports `ontology_core.ttl`.
    *   `ontology_architecture.ttl`: Defines the hierarchy for `:ArchitecturalConcept` subclasses (e.g., `:ArchitecturalPattern`, `:ComponentRole`). Imports `ontology_core.ttl`.
*   **Property Definitions:**
    *   `ontology_object_properties.ttl`: Defines all `owl:ObjectProperty` instances (relationships between classes/individuals). Imports all class definition modules.
    *   `ontology_datatype_properties.ttl`: Defines all `owl:DatatypeProperty` instances (relationships between individuals and literal values). Imports relevant class definition modules.
*   **Individual Definitions (Examples/Base):**
    *   `ontology_individuals_languages.ttl`: Defines individuals for programming languages. Imports `ontology_technologies.ttl`, `ontology_datatype_properties.ttl`.
    *   `ontology_individuals_platforms.ttl`: Defines individuals for platforms and cloud services. Imports `ontology_technologies.ttl`, `ontology_datatype_properties.ttl`, `ontology_object_properties.ttl`.
    *   `ontology_individuals_databases.ttl`: Defines individuals for database technologies. Imports `ontology_technologies.ttl`, `ontology_datatype_properties.ttl`.
    *   `ontology_individuals_devops_tools.ttl`: Defines individuals for DevOps and development tools. Imports `ontology_technologies.ttl`, `ontology_datatype_properties.ttl`.
    *   `ontology_individuals_frameworks_libs_misc.ttl`: Defines individuals for frameworks, libraries, OS, and browsers. Imports `ontology_technologies.ttl`, `ontology_datatype_properties.ttl`.

## Loading in Protégé

To load this modular ontology correctly in Protégé (version 5.5.0 or later recommended):

1.  Ensure all `.ttl` files and the `catalog-v001.xml` file are in the same directory.
2.  Open Protégé.
3.  Go to `File` -> `Open...` and select the `ontology_core.ttl` file.
4.  Protégé should automatically use the `catalog-v001.xml` file in the same directory to resolve the `owl:imports` statements and load all modules correctly. Alternatively, you can configure Protégé to use the catalog file explicitly via `File` -> `Preferences` -> `Ontology Libraries`.

## Competency Questions and SPARQL Examples

*   `competency_questions.md`: Lists key questions the ontology aims to answer, demonstrating its scope.
*   `sparql_examples.rq`: Provides example SPARQL queries corresponding to the competency questions, showing how to query the ontology structure. Note that these queries will only return meaningful results once the ontology is populated with substantial instance data representing real-world relationships.

## Populating the Ontology

The provided files define the schema (TBox) and a basic set of individuals (ABox) for common technologies. To make the ontology useful for prediction, it needs to be populated with extensive instance data, including:

*   Specific `TechnologyVersion` individuals with release dates, EOS dates, etc.
*   Instances of `Problem` linked to specific `TechnologyVersion`s or `SoftwareComponent`s.
*   Instances of `Solution` linked to `Problem`s.
*   Relationships like `dependsOn`, `compatibleWith`, `incompatibleWith` between `TechnologyVersion`s.
*   Instances of `SoftwareComponent` representing parts of actual applications, linked to technologies, patterns, and potentially problems.
*   `DataSource` instances documenting the evidence for problems and solutions.

This population process is ongoing and can be done manually or via automated scripts extracting information from sources like package managers, CVE databases, issue trackers, and documentation.