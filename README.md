# Biomedical Entity Characterization to Optimise NER

Code, data processing, and experiments for multidimensional biomedical entity characterization and evaluation of entity-specific named entity recognition (NER) performance in Oncology Drug Approval Notices (ODAN).

## Overview

This repository contains the code and supporting materials used for a study investigating whether measurable linguistic characteristics of biomedical entities are associated with differences in downstream NER performance.

The study focuses on two entity types extracted from Oncology Drug Approval Notices:

- **Company Name**
- **Line of Therapy (LoT)**

Company Names represent comparatively discrete and lexically consistent entities, whereas LoT expressions are typically longer, more variable, and more dependent on surrounding clinical context.

A multidimensional entity characterization (MEC) approach was used to compare the two entity types using lexical, syntactic, structural, and contextual measures. Their NER performance was then evaluated across multiple model and training configurations.

## Research Objectives

The study aimed to:

1. Characterize Company Name and LoT entities using quantitative measures of lexical, syntactic, structural, and contextual characteristics.
2. Compare entity-specific NER performance across DistilBERT and BioDistilBERT experimental configurations.
3. Evaluate whether measured linguistic differences align with differences in entity-level NER performance.
4. Examine how model choice, annotation refinement, additional training data, and hyperparameter optimization affect each entity type.

## Dataset

The corpus consists of Oncology Drug Approval Notices collected from publicly available sources including:

- FDA
- EMA
- BusinessWire

The experimental dataset contains two annotated entity types:

| Entity | Description |
|---|---|
| Company Name | The organization associated with the drug approval |
| Line of Therapy (LoT) | Text describing the treatment line, treatment history, or therapeutic stage relevant to the approval |

The repository does not necessarily redistribute all original source documents. Users should refer to the original publishers and any applicable data-use conditions.

## Multidimensional Entity Characterization

Entity characteristics were examined using measures including:

- entity token and word counts
- lexical variation
- word-frequency distributions
- n-gram patterns
- repetition across records
- part-of-speech distributions
- stop-word occurrence
- corrected type-token ratio (CTTR)
- contextual and phrase-level patterns

These measures were used comparatively rather than as a single absolute complexity score.

## NER Models

Two transformer-based token-classification models were evaluated:

- **DistilBERT**
- **BioDistilBERT**

Entities were represented using BIO tagging:

- `O`
- `B-Co`
- `I-Co`
- `B-LoT`
- `I-LoT`

Model evaluation used entity-level precision, recall, and F1-score.

## Experimental Configurations

The experiments examined combinations of:

- model architecture
- initial versus protocol-standardized annotation
- additional training data
- hyperparameter optimization

This produced 12 experimental configurations.

Each configuration was evaluated across multiple stochastic training runs.

Hyperparameter optimization was conducted using Optuna with a Tree-structured Parzen Estimator (TPE).

## Statistical Analysis

Entity-level performance differences were evaluated using paired analyses across experimental configurations and runs.

The statistical analyses include:

- paired descriptive comparisons
- Wilcoxon signed-rank tests
- linear mixed-effects modelling
- cluster-robust ordinary least squares
- within-configuration permutation testing
- bootstrap confidence intervals

The held-out test set was not used during hyperparameter optimization or model selection.

## Main Finding

Across the experimental configurations, Company Name consistently achieved higher NER F1-scores than LoT.

The linguistic characterization showed that LoT expressions were generally longer, more lexically variable, contained more function words, and appeared in more variable contexts. These findings provide evidence of an association between entity characteristics and differences in downstream NER performance.

The study is observational and does not establish that any individual linguistic characteristic directly causes changes in NER performance.

