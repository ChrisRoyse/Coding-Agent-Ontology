# Software Architecture Ontology - Competency Questions

This document lists example competency questions that the Software Architecture Problem Prediction Ontology is designed to answer. These questions guide the development and testing of the ontology and associated SPARQL queries.

## Technology & Versions

1.  What programming languages are defined in the ontology?
2.  List all defined frameworks.
3.  What is the homepage for the technology 'React'?
4.  What versions of 'Python' are known? (Requires populating TechnologyVersion individuals)
5.  What is the end-of-support date for Python version '3.7.0'? (Requires specific version data)
6.  Which technology versions are known to be incompatible with 'React' version '17.0.0'? (Requires relationship data)
7.  What is the latest stable version of 'Node.js'? (Requires specific version data and `isLatestStable` property)
8.  What database technology does 'Supabase' use? (Requires relationship data)
9.  Which PaaS platforms support the 'Go' programming language? (Requires relationship data)

## Problems & Vulnerabilities

10. What types of dependency issues are modeled?
11. List all known security vulnerabilities (Problems with type :SecurityVulnerability).
12. What is the CVSS score for the vulnerability with CVE ID 'CVE-2023-XXXX'? (Requires specific problem data)
13. Find problems related to 'React' version '16.8.0'. (Requires relationship data)
14. What problems are known to occur specifically in a 'Production' deployment environment? (Requires relationship data)
15. Which architectural anti-patterns can cause problems?
16. Find all 'High' severity problems. (Requires specific problem data)
17. What compatibility issues are known for the 'Chrome' browser? (Requires relationship data)

## Solutions & Mitigations

18. What solutions are suggested for 'VersionConflict' problems? (Requires relationship data)
19. Find solutions that involve updating to a specific version of 'Log4j'. (Requires relationship data and specific solution data)
20. What is the estimated effort required for the solution titled 'Migrate to Alternative Library'? (Requires specific solution data)
21. Which solutions involve architectural refactoring?
22. Find workarounds for problems affecting 'AWS Lambda'. (Requires relationship data)

## Components & Architecture

23. What software components implement the 'Microservices' architectural pattern? (Requires relationship data)
24. Which components exhibit the 'GodObject' anti-pattern? (Requires relationship data)
25. What technology versions does the 'APIGateway' component use? (Requires component and relationship data)
26. What is the defined role for the 'AuthService' component? (Requires component and relationship data)

## Context & Environment

27. What package managers are defined as part of the tooling context?
28. Find problems that occur in projects with a team size greater than 10. (Requires context and relationship data)
29. What issues are documented specifically in 'OfficialDocumentation'? (Requires relationship data)

## Combined Queries

30. Find high-severity security vulnerabilities affecting 'Java' versions released before '2022-01-01' that have a known exploit. (Requires combined data)
31. What version updates are suggested as solutions for problems caused by 'jQuery' version '1.x'? (Requires combined data)
32. List problems manifesting in 'SpringBoot' components deployed on 'AWS Elastic Beanstalk' in a 'Staging' environment. (Requires combined data)
33. Find alternatives suggested for technologies whose end-of-support date has passed. (Requires combined data)

*(Note: Answering many of these questions requires populating the ontology with specific instance data for versions, problems, solutions, components, and their relationships.)*