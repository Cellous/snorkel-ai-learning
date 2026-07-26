
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
# Case Studies

## Objective Ground Truth Can Still Be Scored Incorrectly

My physics-course experience represents the objective side of AI evaluation.

Physics problems normally have a reproducible solution path:

1. Identify the known values.
2. Select the appropriate formula.
3. Substitute the values.
4. Preserve units and significant figures.
5. Perform the calculation.
6. Compare the result with the expected answer.

I retained the test questions, my answers, the recorded results, and my
scratch-work calculations. This evidence allowed me to identify apparent
errors in the assessment rather than relying only on disagreement with the
score.

The scratch sheet functioned as an evaluation trace and provenance record.

### Evaluation Mapping

- Test question: benchmark task
- Official answer key: ground-truth label
- Automated scoring: evaluator
- Formula and calculations: reproducible verification procedure
- Scratch work: execution trace
- Incorrect rejection of a valid answer: false negative
- Review by other instructors: expert adjudication
- Corrected answer key: evaluator refinement

### Main Lesson

Even when ground truth is objective, the evaluator may still be wrong because
of an incorrect formula, transcription error, unit mismatch, rounding rule,
or defective scoring implementation.

Therefore, reliable evaluation requires both:

- validation of the submitted solution; and
- validation of the evaluator itself.

---

## Autocorrect as an Input-Integrity Problem

Mobile keyboards and predictive-text systems can modify a word after it has
been typed. If the user sends the message before reviewing it, the transmitted
text may not accurately represent the user's intended statement.

### Communication Trace

1. The user forms an intended message.
2. The user types the message.
3. Autocorrect or predictive text modifies part of the input.
4. The user sends the message.
5. The recipient evaluates the transmitted wording.

A failure at step 3 may later be attributed incorrectly to the user.

### Connection to AI Evaluation

The final recorded output should not always be treated as perfect evidence of
the original intent. Reliable systems should preserve enough provenance to
distinguish:

- what the user originally entered;
- what the software changed;
- what was ultimately transmitted; and
- whether the user confirmed the modification.

### Design Lesson

Systems should reduce accidental submissions by providing visible corrections,
easy undo or editing, and additional confirmation when an action has important
consequences.

Human-in-the-loop evaluation must account for urgency, excitement, stress, and
normal proofreading errors rather than assuming flawless user behavior.
