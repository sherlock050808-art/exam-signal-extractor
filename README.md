> 中文版请见 [`README.zh-CN.md`](README.zh-CN.md)

# Exam Signal Extractor

> Version: v2.0 (with v3.0 preview in [`portfolio-v3/`](portfolio-v3/))  
> Core upgrade: Redefined from "how to make review materials" to "**how to extract the most predictive exam signals from massive teaching information**".  
> v3.0 preview: Separates **exam-intent processing** from **exam-content structuring** using Knowledge Nodes as queryable entry points, while reusing the proven v2.0 output templates.

This is a reusable exam-preparation methodology repository. It helps you turn fragmented information—such as classroom recordings, lecture slides, and in-class exercises—into a high-hit-rate "seven-layer exam map", and then generate exam-ready review materials for either open-book or closed-book exams.

---

## Version Roadmap

| Version | Focus | Location |
|---------|-------|----------|
| v1.0 | Information distillation SOP (historical) | [`docs/methodology/information-distillation-sop.md`](docs/methodology/information-distillation-sop.md) |
| v2.0 | Extract exam signals from classroom recordings; seven-layer exam map; open/closed-book strategies | [`docs/SKILL.md`](docs/SKILL.md) and [`docs/methodology/`](docs/methodology/) |
| **v3.0 (preview)** | Separate exam-intent and exam-content processing; Knowledge Nodes as queryable entry points; reuse v2.0 output templates | [`portfolio-v3/`](portfolio-v3/) |

v3.0 does **not** replace v2.0; it adds a structured data layer so that the same methodology can be maintained across multiple courses and exam cycles.

## Project Introduction

**This is not a question bank**, nor does it memorize specific exam questions. It distills a "signal > content" workflow for exam preparation:

- **Signal sources**: Classroom recordings / screen-capture transcripts, teacher highlights, slide titles, past exam questions.
- **Outputs**: Seven-layer exam map + term-definition list + short-answer questions + comprehensive analysis questions + index.
- **Target users**: Students who want systematic exam preparation, are willing to spend 2–4 hours on upfront organization, and want to focus review effort on the content most likely to appear on the exam.

> **Key insight**: Recordings define the exam scope; slides/courseware fill in the content. Do not treat them equally.

---

## Core Methodology

### 1. Extracting Exam Signals from Classroom Recordings

What teachers say about the exam is often far more predictive than the knowledge itself. This methodology processes raw transcripts through six steps:

```text
Raw transcript
  ├── Step 1 Hard filtering: remove deterministic noise (metadata, fillers, classroom actions)
  ├── Step 2 Topic segmentation: split into 15–20 topic segments
  ├── Step 3 Intent-unit merging + coarse classification: merge consecutive sentences into "intent units"
  ├── Step 4 Fine-grained extraction: extract knowledge points, question types, certainty, answer keys
  ├── Step 5 Courseware cross-check: promote slide-title-level content into exam scope
  └── Step 6 Output exam map: reorganize by the seven-layer structure
```

For details, see [`docs/methodology/extracting-exam-signals-from-recordings.md`](docs/methodology/extracting-exam-signals-from-recordings.md).

### 2. Seven-Layer Exam Map

The same seven-layer framework serves both open-book and closed-book exams; the difference lies in the **depth of coverage** and **weight allocation** for each layer.

| Layer | Meaning |
|-------|---------|
| 🟢 Must-appear | Points the teacher explicitly emphasized and are very likely to be tested |
| 🟡 High-probability | Repeated hints, structural highlights, or frequently tested points |
| 🟠 Possible | Slide-title-level concepts or things the teacher mentioned casually but uncertainly |
| 🔴 Excluded | Content explicitly stated as not being tested, saving review effort |
| ⚡ Traps | Easily confused concepts, common mistakes, and ways to distinguish them |
| 🔗 Fusion | Cross-chapter combinations that may appear as comprehensive analysis questions |
| ❓ To be confirmed | Insufficient information; needs confirmation before the exam or manual judgment |

Template: [`templates/exam-map-template.md`](templates/exam-map-template.md).

### 3. Open-Book vs. Closed-Book Strategy

Both exam formats share the same map, but the resulting materials differ:

| Dimension | Open-Book Exam | Closed-Book Exam |
|-----------|----------------|------------------|
| Material thickness | Thick, but must be searchable | Thin, clearly layered by the seven layers |
| Memory intensity | Recognition and location | Recitation and recall |
| Front page | Exam map + quick index | Question-type distribution (recommended) or table of contents |
| Must-appear layer | Full answers + index + quick copying | Full memorization + able to write from memory |
| High-probability layer | Full answers + index | Memorize scoring points + able to expand |

Full strategies:
- [`docs/methodology/open-book-strategy.md`](docs/methodology/open-book-strategy.md)
- [`docs/methodology/closed-book-strategy.md`](docs/methodology/closed-book-strategy.md)

---

## Usage Flow

### Option 1: Let an AI read the v3.0 Skill document (recommended for iterative use)

Feed [`portfolio-v3/SKILL.md`](portfolio-v3/SKILL.md) to a long-context assistant such as Kimi or Claude, then say:

> "Help me prepare for the [XXX] exam using this. Here is the classroom recording transcript, the courseware, and the syllabus."

The AI will separate exam-intent processing from exam-content structuring, build a Knowledge Node tree, and generate closed-book or open-book materials.

### Option 2: Let an AI read the v2.0 Skill document (recommended for one-off quick preparation)

Feed [`docs/SKILL.md`](docs/SKILL.md) to a long-context assistant such as Kimi or Claude, then say:

> "Help me prepare for the [XXX] exam using this. Here is the classroom recording transcript and the courseware."

The AI will confirm the exam format, execute the six-step workflow, and generate the exam map and review materials.

### Option 3: Execute the workflow manually

1. Prepare materials: classroom recording transcript, courseware PDF/PPT, past exam questions if available.
2. Read [`docs/methodology/extracting-exam-signals-from-recordings.md`](docs/methodology/extracting-exam-signals-from-recordings.md).
3. Extract signals by following the six steps and fill in [`templates/exam-map-template.md`](templates/exam-map-template.md).
4. Based on open-book/closed-book strategy, apply templates under [`templates/`](templates/) to generate exam materials.
5. Before the exam, use [`checklists/pre-exam-checklist.md`](checklists/pre-exam-checklist.md).
6. After the exam, fill in [`checklists/post-exam-checklist.md`](checklists/post-exam-checklist.md) to accumulate few-shot samples.

### Option 4: Quick start with templates only

If you only need a format reference, open [`templates/`](templates/) and [`examples/`](examples/) directly and follow the patterns.

---

## Directory Structure

```text
exam-signal-extractor/
├── README.md                                    # This file
├── README.zh-CN.md                              # Chinese version
├── LICENSE                                      # MIT License
├── .gitignore                                   # Git ignore rules
├── portfolio-v3/                                # v3.0 skill preview: intent/content separation + Knowledge Nodes
│   ├── README.md                                # v3.0 overview
│   ├── SKILL.md                                 # v3.0 skill document for AI assistants
│   ├── references/                              # v3.0 methodology and v2.0/v1.0 references
│   ├── templates/                               # v3.0 node schema and closed-book workflow templates
│   ├── examples/                                # v3.0 worked example (CNC technology)
│   └── checklists/                              # Pre-exam and post-exam checklists (v2.0)
├── docs/
│   ├── SKILL.md                                 # Skill document for AI assistants
│   └── methodology/
│       ├── extracting-exam-signals-from-recordings.md  # v2.0 core methodology
│       ├── information-distillation-sop.md             # v1.0 historical SOP
│       ├── open-book-strategy.md                       # Open-book strategy
│       ├── closed-book-strategy.md                     # Closed-book strategy
│       └── post-exam-review-checklist.md               # Post-exam review checklist (reference)
├── examples/
│   └── consumer-goods-intelligent-equipment/
│       ├── exam-map-example.md                  # Seven-layer exam map example
│       └── post-exam-review.md                  # Real post-exam review
├── templates/
│   ├── exam-map-template.md                     # Blank seven-layer exam map template
│   ├── term-definition-template.md              # Term-definition list template
│   ├── short-answer-template.md                 # Short-answer question template
│   └── comprehensive-analysis-template.md       # Comprehensive analysis question template
└── checklists/
    ├── pre-exam-checklist.md                    # Pre-exam checklist
    └── post-exam-checklist.md                   # Post-exam review checklist
```

---

## Contributing

Contributions of exam maps, post-exam reviews, template improvements, or translations are welcome!

1. **Fork this repository**.
2. Add your subject case under `examples/` (use lowercase English directory names, e.g., `advanced-mathematics/`).
3. If a certain question type or teacher pattern appears repeatedly, update `templates/` or `checklists/`.
4. Submit a Pull Request describing your improvement and validation results (e.g., "This exam hit 8/10 predicted points").

When contributing, please:
- Do not upload original exam questions to avoid copyright issues.
- Share **methodologies, templates, and structured reviews**, not raw exam papers.
- Keep Chinese content as needed; file paths should use lowercase English with hyphens.

---

## License

This project is open-sourced under the [MIT License](LICENSE). You are free to use, modify, and distribute it, provided that the copyright notice is retained.

---

## Quick Start

If this is your first time, read in this order:

1. [`docs/methodology/extracting-exam-signals-from-recordings.md`](docs/methodology/extracting-exam-signals-from-recordings.md)
2. [`examples/consumer-goods-intelligent-equipment/post-exam-review.md`](examples/consumer-goods-intelligent-equipment/post-exam-review.md)
3. [`templates/exam-map-template.md`](templates/exam-map-template.md)
4. [`checklists/pre-exam-checklist.md`](checklists/pre-exam-checklist.md)

Good luck on your exams—may your hit rate be high!
