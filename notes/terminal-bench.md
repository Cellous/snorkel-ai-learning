# Terminal-Bench 3.0

## Purpose

Terminal-Bench evaluates whether AI agents can perform valuable,
domain-specific work inside containerized terminal environments.

The benchmark evaluates more than whether an agent produces a final answer.
It observes the agent's interaction with files, tools, commands, tests,
constraints, and failure conditions.

## Current Structure

The Terminal-Bench 3.0 v0.1 release shown on the Snorkel website includes:

- 74 tasks
- 7 top-level domains
- 31 subdomains
- 35 rubric criteria per task
- A best-model pass rate of approximately 43.5%

A low pass rate is not necessarily evidence that the benchmark is defective.
It may indicate that the benchmark preserves useful model headroom and exposes
capabilities that existing agents have not yet mastered.

## Domains

### Natural Sciences and Engineering

- Biology
- Chemistry
- Physics
- Earth science
- Robotics
- Mathematics
- Linguistics

### General Software Engineering

- Algorithms
- Systems
- Databases
- Data engineering
- Frontend
- Programming languages

### Machine Learning

- Training
- Inference
- Evaluation
- Kernels

### Business and Financial Reasoning

- Finance
- Logistics
- Supply chain
- Claims
- Compliance
- Marketing

### Security

- Cryptography
- Reverse engineering
- Forensics
- Application security

### Physical and Digital Hardware

- CAD
- RTL

### Creative and Design Work

- Music
- Design

## Task Review Pipeline

Every accepted Terminal-Bench task passes through an automated and human
review process.

### 1. Static Checks

Checks may include:

- Repository and path validation
- Dockerfile sanity
- Metadata validation
- Canary checks
- Confirmation that external API keys are unnecessary

### 2. Rubric Review

The task is evaluated against detailed criteria such as:

- Verifiability
- Solvability
- Difficulty
- Resistance to cheating
- Rubric completeness

### 3. Docker, Oracle, and No-Op Validation

The environment must build successfully.

The reference solution must pass.

Doing nothing must fail.

This helps confirm that the task has a valid solution and that the verifier
does not award credit automatically.

### 4. Maintainer Review

A human maintainer reviews the task after the automated gates pass.

### 5. Agent and Cheat Trials

Multiple agents attempt the task.

Adversarial trials investigate whether an agent can exploit the tests,
rubric, files, or environment without completing the intended work.

### 6. Hacker–Fixer Loop

Reviewers repeatedly search for exploits and then harden the task against
those exploits.

### 7. Merge

A task counts toward the benchmark and becomes leaderboard-eligible only
after completing the review process.

## Relationship to the Tandem Design Principle

The Terminal-Bench pipeline maps to my diagram as follows:

| Tandem stage | Terminal-Bench implementation |
|---|---|
| Tasks + Environments | Task specification, files, Docker container and tools |
| Traces + Outputs | Agent runs, command history, modified files and deliverables |
| Rubrics + Verifiers | Detailed rubric criteria, tests, oracle and scoring |
| Quality Control + Packaging | Static checks, maintainer review and hacker–fixer loop |
| Updated Memory and Future Tasks | Community findings, hardened tasks and new subdomains |

## Core Lesson

A benchmark must test both:

1. Whether the agent completed the intended task.
2. Whether the benchmark itself is valid, reproducible, and resistant to
   accidental or deliberate exploitation.

Observability records what the agent did.

Evaluation determines whether the behavior was correct.

Adversarial benchmark review determines whether the evaluation can be trusted.

---

## CAD Model Task Study

The `cad-model` task is particularly relevant to my background in mechanical
drafting, Autodesk Inventor, AutoCAD, SolidWorks, 3D printing, and Python.

### Task Objective

The agent must interpret a non-text schematic and create a valid three-
dimensional mechanical model. The output is exported as a STEP file.

The task requires:

- Three-dimensional spatial reasoning
- Interpretation of a graphical specification
- Mechanical-design judgment
- Accurate geometric construction
- CAD-tool or programmatic-CAD knowledge
- Compliance with formal output requirements

### Programmatic CAD

The published solution uses `build123d`, a Python library for constructing
three-dimensional CAD models.

This demonstrates that a terminal agent can perform CAD work without
controlling a traditional graphical CAD application. The agent can instead
generate the model through code and export an industry-standard STEP file.

### Geometry-Based Verification

The verifier does not require an exact byte-for-byte match with a reference
STEP file.

Instead, it converts the submitted model into a triangle mesh and evaluates
physical and geometric properties such as:

- Watertightness
- Volume
- Surface area
- Principal inertia
- Convex-hull volume
- Convex-hull area
- Euler number
- Integral volume

Floating-point properties are compared with a defined tolerance.

### Evaluation Significance

This is stronger than testing whether a file merely exists.

It evaluates whether the artifact has the intended physical structure while
allowing more than one valid implementation.

A verifier should accept functionally equivalent solutions and reject:

- Empty files
- Corrupt STEP files
- Copied but unmodified example models
- Visually similar models with incorrect geometry
- Models that violate required physical properties

### Connection to the Tandem Design Principle

- **Tasks + Environments:** schematic, CAD libraries, container and STEP output
- **Traces + Outputs:** agent commands, Python source and generated STEP file
- **Rubrics + Verifiers:** geometric-property and tolerance checks
- **Quality Control + Packaging:** oracle tests, no-op tests and maintainer review
- **Updated Memory:** discovered CAD-agent failure modes and improved future tasks


## CAD Task Package Architecture

```text
instruction.md
    Defines the agent-visible assignment
            ↓
environment/
    Builds an isolated workspace and provides schematic.png
            ↓
Agent execution
    Interprets the drawing and writes /app/out.step
            ↓
Declared artifact
    /app/out.step
            ↓
tests/
    Loads and evaluates the STEP model in a separate verifier container
            ↓
Rubric and result
    Accepts valid geometry or reports specific failures
```

