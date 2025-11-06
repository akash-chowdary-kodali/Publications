# Atlas: Customizing Large Language Models for Reliable Bibliographic Retrieval and Verification

This repository contains the source code and supplementary materials for the research paper, "Atlas: Customizing Large Language Models for Reliable Bibliographic Retrieval and Verification."

## Abstract

Large Language Models (LLMs) have demonstrated remarkable capabilities in text comprehension and generation, yet their application in academic bibliographic retrieval is often hindered by a critical flaw: metadata hallucination. Standard LLMs frequently generate plausible but incorrect bibliographic details, undermining their reliability for scholarly research. This paper introduces Atlas, a novel pipeline engineered to address this challenge. Atlas employs a verification-guided prompting strategy that integrates programmatic retrieval with LLM-based validation, significantly enhancing the accuracy and completeness of metadata extraction. Our empirical evaluation demonstrates that Atlas achieves a metadata accuracy of 83.3%, a substantial improvement over standard GPT-4 (46.2%) and traditional API-based methods (0.0%). This work provides a robust framework for developing more reliable, LLM-powered tools for academic research.

## The Problem: Unreliability in LLM-based Bibliographic Retrieval

While powerful, general-purpose LLMs suffer from a key limitation known as "hallucination"—the tendency to generate factually incorrect or nonsensical information. In the context of bibliographic retrieval, this manifests as:
- **Incorrect Metadata:** Fabricating DOIs, publication dates, or author lists.
- **Incomplete Fields:** Omitting critical information like journal volume or issue numbers.
- **Mismatched Information:** Associating a real title with an incorrect author or abstract.

These errors make off-the-shelf LLMs unreliable for tasks requiring high-fidelity data extraction, such as building literature databases, conducting systematic reviews, or verifying citations.

## The Atlas System: A Verification-Guided Pipeline

To counteract these limitations, we developed Atlas, a multi-stage Python-based pipeline designed for accuracy and reliability.

### Key Components
1.  **Programmatic Retrieval:** The system first retrieves candidate bibliographic data from established academic databases using available APIs.
2.  **Verification-Guided Prompting:** Instead of merely asking an LLM to extract information, Atlas uses a targeted prompt strategy with GPT-4. The LLM is tasked with *verifying and correcting* the programmatically retrieved data against a source text (e.g., a paper's reference section). This shifts the LLM's role from a pure generator to a verifier, reducing the likelihood of hallucination.
3.  **Structured Post-Processing:** The validated metadata is normalized and structured to ensure consistency and completeness.

### Methodology
Our evaluation framework was designed to rigorously assess the performance of Atlas against baseline methods. The core of our analysis centered on:
- **Retrieval Coverage:** Measuring the proportion of unique DOI entries successfully identified by each method.
- **Field Completeness:** Assessing the percentage of essential metadata fields (e.g., title, authors, year, journal) correctly populated.
- **Metadata Accuracy:** Quantifying the correctness of the retrieved information against a ground-truth dataset.
- **Cross-Method Agreement:** Analyzing the consistency of results between different retrieval strategies to identify systematic strengths and weaknesses.

## Key Results and Findings

Our experiments confirm that the verification-guided approach is significantly more reliable than standard methods.
- **Atlas (Verification-Guided GPT-4):** 83.3% accuracy.
- **Standard GPT-4 (Direct Extraction):** 46.2% accuracy.
- **Baseline API-only Method:** 0.0% accuracy (failed to retrieve any correct metadata for the target set).

These results highlight the efficacy of designing specialized, human-in-the-loop-style pipelines for high-stakes information retrieval tasks.

## My Contributions

As a key contributor to this research, my responsibilities and achievements included:

- **Analysis and Evaluation Framework:**
  - I formatted and executed the quantitative analyses for **Field Completeness** and **Metadata Accuracy**, which were central to validating our system's performance.
  - Under the guidance of Dr. Wenlu Xu and Dr. Xin Qin, I implemented the analytical methods for assessing **Retrieval Coverage** and **Cross-Method Agreement**, primarily by processing unique DOI entries to compare the outputs of different systems.

- **System Development and Implementation:**
  - I architected and developed the **novel verification pipeline** using Python, integrating the GPT-4 API as the core verification engine.
  - A primary focus of my development work was the implementation of the **verification-guided prompt strategy**, a technique specifically designed to mitigate metadata hallucination by framing the LLM's task as a correction and validation problem.

- **Core Research Impact:**
  - My work directly addressed the fundamental challenge of LLM unreliability in academic data extraction. The pipeline I developed produced an **83.3% accuracy rate**, demonstrating a dramatic and measurable improvement over both standard LLM prompting (46.2%) and traditional programmatic approaches (0.0%).

<!-- ## Repository Contents

This repository will be populated with the following artifacts:
- Python scripts for the Atlas pipeline.
- Jupyter notebooks used for data analysis and figure generation.
- Evaluation datasets and ground-truth files.
- `requirements.txt` file for reproducing the Python environment. -->

## Citation

If you use this work, please cite the original paper:

*(A full citation will be added here once the paper is published.)*

## Acknowledgements

I extend my gratitude to Dr. Xin Qin, Dr. Hailu Xu, and Dr. Wenlu Xu for their invaluable guidance and collaboration throughout this project. Please see the full paper for a complete list of acknowledgements.

