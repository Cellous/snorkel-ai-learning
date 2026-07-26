



## How Snorkel Works

Snorkel describes its workflow as:

1. **Evaluate** — Test model behavior using task-specific benchmarks and defined pass/fail criteria.
2. **Curate** — Build and improve datasets and environments with expert review.
3. **Refine** — Analyze failures, update rubrics, expand benchmarks, and repeat testing.

---

## Snorkel Expert-in-the-Loop Method

Snorkel combines programmatic scale with human expert review.

### Evaluator Development

Model-based, rule-based, and hybrid evaluators are trained or configured
using expert-reviewed examples. Evaluators may assess areas such as:

- Code quality
- Safety
- Reasoning depth
- Instruction following
- Factual accuracy

### Expert Correction and Feedback

When reviewers disagree about a model result, the disagreement is examined
and adjudicated. The rubric is then clarified or updated so future evaluations
are more consistent.

### Meta-Evaluation

Snorkel also evaluates the evaluators. Reviewer agreement and calibration are
measured rather than assumed.

### Development Loop

1. Evaluate model behavior.
2. Curate data and evaluation environments.
3. Review disagreements and failure cases.
4. Refine rubrics, datasets, and evaluators.
5. Repeat the evaluation cycle.
