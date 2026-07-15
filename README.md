# FireFlow

FireFlow is an interactive, single-page schematic of a GitHub-native continuous integration and deployment system, designed around four constraints that usually trade off against each other:

- **Cognitive load** — a developer sees one required status check per pull request, not a wall of independent checks to triage.
- **Cost and scale** — the runner fleet defaults to spot capacity, bin-packs jobs, and scales toward zero when the queue is empty instead of holding a fixed pool sized for the busiest hour.
- **Security** — commits are signature-verified at intake, dependencies are scanned per diff, and every build produces a signed artifact with a software bill of materials and a provenance attestation, re-checked again at deploy time.
- **Quality and risk** — test selection, merge ordering, and rollout pacing are all driven by a risk score, so a one-line documentation change and a change to a core payment path are not held to the same gate.

The page also surfaces delivery performance using the four keys published by Google's DevOps Research and Assessment program — the standard industry framework for measuring software delivery performance. Three of the four are shown as explicit design targets; the fourth, lead time for changes, is calculated live from the page's own simulation timeline.

## What's on the page

- **Four pillar cards** stating the design principles above as concrete mechanisms, not slogans.
- **A delivery performance panel** benchmarking the system against the highest published performance tier.
- **A flow diagram** of the pipeline across six stages — trigger and intake, fast feedback, scaled build and test, merge queue, release and rollout, and observability — with every component clickable for a detailed explanation.
- **A "Run simulation" control** that replays one pull request's actual trip from the initial webhook to a production rollout, lighting up each stage in sequence with a live elapsed-time, cost, and security-gate readout.
- Every AI-assisted step is marked with a violet badge and paired, where relevant, with the human step that still has to sign off (for example, AI code review runs alongside a separate required human reviewer approval — the automation narrows what a person has to read, it doesn't replace their review).
- Every security-relevant step is marked with a teal badge: commit signature verification, secret scanning and dependency alerts, a software bill of materials export, a ruleset policy gate, a build provenance attestation, and admission-time enforcement.

## Viewing it

Open `index.html` directly in a browser — it's a single self-contained file with no build step and no external dependencies. It respects the operating system's light/dark theme preference and reduced-motion setting.

## Status

This is a design artifact and simulation, not a deployable system. The pipeline stages, timings, and cost figures are illustrative, built to be internally consistent with each other rather than pulled from a live environment.
