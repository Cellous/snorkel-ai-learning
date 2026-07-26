
```
Firebase Studio
Build the AI application or agent
        ↓
Azure ML or Google Cloud
Run, train, deploy, and manage the model infrastructure
        ↓
Snorkel-style evaluation
Create realistic tasks, rubrics, tests, traces, penalties,
edge cases, and expert-reviewed benchmarks
        ↓
Improve the agent and repeat
```
## Personal Example: Detecting an Evaluation Error

During an online physics course at Georgia Northwestern Technical College,
I identified what appeared to be an incorrect answer in an online assessment.

I had preserved the relevant questions, my submitted answers, and the recorded
results. This provided an audit trail that allowed me to compare the problem,
my calculation, and the answer expected by the testing system.

This experience illustrates an important AI evaluation principle:

> An evaluator, answer key, rubric, or automated scoring system should not be
> assumed to be correct merely because it produces an official score.

### Connection to Snorkel

- **Assessment answer key:** evaluator or scoring model
- **Question and submitted answer:** evaluation input and model output
- **Saved test results:** provenance and trace data
- **Independent calculation:** validation procedure
- **Review by additional instructors:** expert adjudication
- **Correcting the answer key:** evaluator and rubric refinement
- **Rechecking other students:** benchmark-wide impact analysis

### Lesson Learned

Reliable evaluation requires evidence, reproducibility, reviewer calibration,
and a documented process for resolving disagreements. A flawed evaluator can
incorrectly mark a valid solution as wrong, just as a flawed AI benchmark can
misrepresent model performance.

---

## Snorkel Development Section
```
Evaluator development
        ↓
Expert correction and feedback
        ↓
Meta-evaluation
        ↓
Rubric or benchmark refinement
```
