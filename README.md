# From Evaluation to Improvement: Multi-Agent Pedagogical Feedback of LLM Tutors Towards Improving Student Learning in Dialogues

Official code repository for the PRICAI 2026 paper:

**From Evaluation to Improvement: Multi-Agent Pedagogical Feedback of LLM Tutors Towards Improving Student Learning in Dialogues**

## Abstract

As Large Language Models (LLMs) increasingly power conversational AI tutors, a critical tension has emerged between technological fluency and pedagogical intentionality. Although LLMs can generate immediate responses, they often prioritize answer-giving over scaffolding, thereby failing to provide the deliberate guidance necessary for student mastery. This paper introduces an open-source, multi-agent framework designed to transform AI tutor feedback from mere evaluation into intentional pedagogical refinement. Grounded in three core educational frameworks: formative feedback theory, the Zone of Proximal Development (ZPD) and Socratic questioning, as well as a structured evaluation taxonomy, our system employs a modular architecture where specialized sub-agents evaluate tutor responses across four critical dimensions: mistake identification, mistake location, providing guidance, and actionability. Unlike traditional validation systems focused on reducing hallucinations, our framework implements an evaluation-to-improvement loop. When a response is flagged as pedagogically insufficient, a refinement agent uses the granular evaluation metrics as instructional intent to recalibrate the feedback, ensuring it remains supportive and cognitively demanding without revealing the answer. We evaluate our framework using the MRBench dataset, which comprises diverse tutoring interactions in middle school mathematics. Results demonstrate that our iterative process successfully refined 77.1\% of the tutor responses. Furthermore, an LLM-as-a-judge evaluation shows that our refinement process yields a 38.3\% improvement in pedagogical alignment compared to the original single-agent responses, achieving consistently high scores. By bridging the gap between automated response generation and evidence-based instructional design, this work contributes to the development of AI tutoring systems that are purposeful, transparent, and centered on human educational values.

## Overview

This repository contains:

- A multi-agent evaluation and refinement pipeline for tutor feedback.
- Notebook-based experiments for development and test splits.
- LLM-as-a-judge analysis for pedagogical quality comparison.
- Aggregated outputs and intermediate artifacts used in the paper.

The core idea is an **evaluation-to-improvement loop**:

1. Evaluate tutor feedback on pedagogical dimensions.
2. Detect specific weaknesses (not just pass/fail).
3. Refine feedback using dimension-level signals as instructional intent.
4. Re-evaluate up to a bounded number of iterations.

## Pedagogical Foundations

The framework is grounded in:

- **Formative feedback theory**
- **Zone of Proximal Development (ZPD)**
- **Socratic questioning**

These principles are operationalized through four evaluation dimensions:

- **Mistake identification**
- **Mistake location**
- **Providing guidance**
- **Actionability**

## Main Results

- **84.4%** of tutor responses validated within **3 iterations**.
- **+38.3%** pedagogical alignment improvement over single-agent baselines (LLM-as-a-judge).
- Consistently high refinement quality across all four dimensions.

## Repository Structure

Top-level contents:

- `Multi_Agent_System.ipynb`: End-to-end multi-agent pipeline.
- `LLM-as-a-judge_devset.ipynb`: Judge-based evaluation on development split.
- `LLM-as-a-judge_testset.ipynb`: Judge-based evaluation on test split.
- `Feedback_Statistics_devset.ipynb`: Development split statistics and analysis.
- `Feedback_Statistics_testset.ipynb`: Test split statistics and analysis.
- `Statistical_Analysis.ipynb`: Statistical analysis of the LLM-as-a-judge results.
- `outputs/`: Generated scores, refinements, and checkpoints.
- `BD/`: Model checkpoints and experiment artifacts used in comparative settings. To obtain the BD folder check the reproducibility notes.

Key output artifacts:

- `outputs/llm_judge_scores.json`
- `outputs/llm_judge_scores_testset.json`
- `outputs/mrbench_v3_devset_refinements.jsonl`
- `outputs/mrbench_v3_testset_refinements.jsonl`
- `outputs/test_checkpoint.json`

## Quick Start

This project is notebook-centric. A typical workflow is:

1. Open and run `Multi_Agent_System.ipynb` to generate/refine tutor feedback.
2. Run `LLM-as-a-judge_devset.ipynb` and/or `LLM-as-a-judge_testset.ipynb` for automatic pedagogical scoring.
3. Run `Feedback_Statistics_devset.ipynb` and `Feedback_Statistics_testset.ipynb` to reproduce summary figures and statistics.

Make sure to have Python (https://www.python.org/downloads/) and Ollama (https://docs.ollama.com/quickstart) downloaded.

## Data and Evaluation

- Benchmark: **MRBench** (middle-school mathematics tutoring interactions).
- Evaluation protocol:
  - Multi-agent dimensional assessment.
  - Iterative refinement with capped iterations.
  - LLM-as-a-judge scoring for pedagogical alignment.

## Reproducibility Notes

- The repository includes generated outputs to support result verification.
- The BD/ directory contains trained checkpoint artifacts used in experiment runs. Download the model weights from: https://uccl0-my.sharepoint.com/:u:/g/personal/snburgos_uc_cl/IQBG5piGlx-rSY8KVon7ckB6AZswWsX6uKe1B5OzP88WoTg?e=Q3gwLU
- For strict reproducibility, use the same model versions, prompts, and judge configurations as in the notebooks.

## Ethical and Educational Considerations

This framework is designed for **supportive, scaffolded learning** and avoids answer-revealing behavior when guidance is pedagogically preferable. It is intended as an assistive educational technology and should be deployed with educator oversight.

## Citation

If you use this repository, please cite:

```bibtex
@inproceedings{from_evaluation_to_improvement_pricai2026,
	title     = {From Evaluation to Improvement: Multi-Agent Pedagogical Feedback of LLM Tutors Towards Improving Student Learning in Dialogues},
	author    = {Burgos-Mart{\'\i}nez, Sebasti{\'a}n and Gan, Wenbin and Sun, Yuan},
	booktitle = {Proceedings of the 2026 Pacific Rim International Conference on Artificial Intelligence (PRICAI)},
	year      = {2026}
}
```

## License

This repository is released under the terms of the `LICENSE` file.
