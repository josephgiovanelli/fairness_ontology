# The Fairness Ontology

A comprehensive and extensible ontology for systematically modeling fairness notions, metrics, biases, evaluation methods, and scientific provenance in machine learning. This ontology provides researchers, developers, and practitioners with a unified, machine-readable framework to guide the design and assessment of fair ML systems.

## Table of Contents

- [Overview](#overview)
- [Scoping Areas](#scoping-areas)
  - [Evaluation Process](#evaluation-process)
  - [AI Pipelines](#ai-pipelines)
  - [Fairness Concerns and Guidelines](#fairness-concerns-and-guidelines)
  - [Fairness Metrics, Notions, and Biases](#fairness-metrics-notions-and-biases)
- [Core Concepts](#core-concepts)
- [Provenance and Scientific Content](#provenance-and-scientific-content)
- [Usage and Examples](#usage-and-examples)
- [Getting Started](#getting-started)
- [License](#license)

---

## Overview

This ontology was developed to structurally encode, analyze, and reason over fairness-related concepts, metrics, and scientific artefacts relevant to ML systems. It enables structured modeling for specific use cases, supports evaluation, and assists in inferring suitable fairness interventions for any scenario. Built using OWL (Web Ontology Language), the ontology is machine-readable, interoperable, and compliant with semantic web standards.

## Scoping Areas

### Evaluation Process

- **Purpose:** Model the evaluation of ML models with respect to fairness, labelling which metrics and notions are satisfied and why.
- **Main Classes:**
  - `Evaluation`: Holds the measurement value of a specific fairness metric on an ML model or dataset.
  - `MachineLearningModelEvaluation`: Specialized evaluation with explicit metric values and pipeline context.
  - `Dataset` and its specializations: Explicit modeling of train/test splits and their roles in fairness evaluation.
- **Utility:** Supports reproducible, provenance-aware documentation of model assessments using the ontology.

### AI Pipelines

- **Purpose:** Describe and analyze ML pipelines with explicit representation of each processing step in relation to fairness.
- **Main Classes:**
  - `PipelineStep`: Represents each stage (preprocessing, learning, mitigation, postprocessing).
  - `LearningAlgorithm`: Categorized by paradigm (eager, lazy, rule-based, probabilistic, margin-based, etc.).
  - `MitigationTechnique`: Encodes taxonomies of fairness-aware interventions (pre-processing, in-processing, post-processing).
- **Utility:** Enables traceability of fairness interventions, supporting documentation and comparison of various mitigation strategies.

### Fairness Concerns and Guidelines

- **Purpose:** Explicitly encode fairness risks, the biases they expose, mitigation guidelines, and relevant contexts/domains.
- **Main Properties:**
  - `exposesTo`: Connects a concern to specific biases.
  - `mitigatedBy`: States which technique is used for mitigation.
  - `enforcedBy`: Specifies the fairness notion/requirement being optimized.
  - `measuredBy`: Details the fairness metric(s) used in evaluation.
  - `testedOn`: Binds the concern to empirical context/datasets.
  - `isProposedBy` / `isUsedBy`: Links to scientific artefacts and papers.
- **Utility:** Provides a structured framework for mapping fairness issues to actionable remediation pathways and benchmarks.

### Fairness Metrics, Notions, and Biases

- **Purpose:** Formalize the taxonomy and interrelationship of fairness concepts and quantification methods.
- **Main Classes:**
  - `FairnessNotion`: High-level fairness property (procedural or outcome).
  - `FairnessMetric`: Quantitative measures enforcing notions (`ParityBasedMetric`, `ScoreBasedMetric`, etc).
  - `Bias`: Hierarchy including historical, representation, algorithmic, sampling, and intersectional biases.
  - `SocialPrinciple`: Foundational values (equity, equality) guiding fairness notions.
- **Utility:** Enables detailed evaluation of ML systems with distinctions between what is measured, how, and why.

## Core Concepts

- **Unified Definitions:** Each fairness notion and metric is precisely defined, disambiguating terminology from the literature.
- **Hierarchical Taxonomies:** Supports reasoning across fairness types (procedural/outcome, group/individual, observational/causal).
- **Interlinked Entities:** Provenance, domain suitability, and usage are captured with explicit links.

## Provenance and Scientific Content

- The ontology links every notion, metric, and artefact to relevant scientific papers and domains, enabling knowledge tracing and research contextualization.
- Includes classes for scientific papers, tasks (e.g., classification, clustering, NLP), and real-world application domains (health, law, finance, etc).

## Usage and Examples

### Example: Capturing Metric Relationships

```turtle
:DisparateImpact a :ScientificArtifact, :ParityBasedFairnessMetric ;
    :hasDefinition """This fairness metric computes the ratio between the probabilities of positively classifying unprivileged and privileged groups.""" ;
    :enforces :StatisticalParity ;
    :hasBeenAppliedTo :CensusIncomePrediction ;
    :isSuitableFor :Classification ;
    :isProposedBy :2015_Feldman ;
    :isUsedBy :2017_Chouldechova ;
.
```

- See full ontology, class diagrams, and usage notes in the [`/docs`](docs/) directory and the latest [`fairness_ontology.ttl`](https://liveunibo.sharepoint.com/:u:/r/sites/Huawei-Fairness-Project/Shared%20Documents/General/Working%20Documents/fairness_ontology.ttl?csf=1&web=1&e=yxcaKX).  

## Getting Started

1. **Download the Ontology**: [`fairness_ontology.ttl`](https://liveunibo.sharepoint.com/:u:/r/sites/Huawei-Fairness-Project/Shared%20Documents/General/Working%20Documents/fairness_ontology.ttl?csf=1&web=1&e=yxcaKX)
2. **Open with Protégé** or any OWL-compatible ontology editor.
3. **Explore classes, individuals, and relationships:** Query, visualize, and extend the ontology for your tasks.
