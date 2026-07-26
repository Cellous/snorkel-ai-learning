
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

| Physics-course element       | AI-evaluation equivalent      |
| ---------------------------- | ----------------------------- |
| Test question                | Benchmark task                |
| Official answer              | Ground-truth label            |
| Teacher’s scoring system     | Evaluator                     |
| Formula and substitutions    | Reproducible evaluation logic |
| Scratch sheet                | Trace and provenance record   |
| Incorrect marked result      | False negative                |
| Independent professor review | Expert adjudication           |
| Correcting the answer key    | Evaluator refinement          |

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

---

# Terminal-Bench–style evaluation

## Building Tasks and Environments in Tandem

Agent benchmarks should develop the task and its operating environment
together rather than treating them as separate components.

A benchmark may include:

- A task specification
- A terminal or application environment
- Input files and supporting data
- Available tools and permissions
- Hidden tests and verifiers
- Agent action traces
- Expected outputs
- Rubrics and failure labels

A change to the task can require changes to the environment, tests, rubric,
and verifier. Otherwise, the benchmark may accidentally measure an
environment defect instead of the agent's capability.

## Observability Versus Evaluation

Observability records what an agent did.

Evaluation determines whether what the agent did was correct.

A complete agent evaluation should capture:

- Commands and tool calls
- Files read and modified
- Intermediate state changes
- Errors and recovery attempts
- Final deliverables
- Compliance with task constraints
- Output quality and maintainability

## Personal Connection: Physics Scratch Work as a Trace

During an online physics course, I maintained detailed scratch work showing
the formulas, substitutions, calculations, and results used to solve the
course problems.

The instructor described the final scratch-work document as the cleanest one
he had seen. I also earned a perfect score on that submission, possibly with
bonus credit, although the exact recorded score should be verified later.

The scratch work functioned like an execution trace:

- The problem was the task specification.
- The formulas were the reasoning procedure.
- The calculations were intermediate state.
- The final value was the output.
- The answer key was the verifier.
- Disagreements exposed possible evaluator defects.

This experience demonstrates that clear technical traces help distinguish a
solver error from an incorrect answer key, formula, or evaluation system.
