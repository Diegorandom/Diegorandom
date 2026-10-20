# Diego Ortega — audio software engineer

I build audio plugins in C++/JUCE, and the agentic tooling that develops and ships them.

**Founder of [Casa Occidente](https://casaoccidente.com)** — three commercial plugins for
macOS and Windows (AU + VST3), notarized, signed, and shipped. 13,000 users in the first year.

Most of my production code is closed source, so this profile is a **route map rather than a
mirror**: the product is downloadable, the numbers are measured, and the engineering judgment
lives in the repositories below.

## What I'm building right now

A **multi-agent harness** I run in production against my own products — AI-assisted since 2024,
my own harness since 2026.

- **Orchestration.** Sub-agents in parallel sessions, each with its own skills layer and its own
  scoped tool surface, working against a shared task tracker and linter.
- **Permissions.** Agents never hold my credentials. The agent *proposes*, the backend *validates*
  against a declared scope, and irreversible operations need explicit confirmation.
- **Verification.** Agents check their own output instead of trusting a clean exit — including
  rendering an artefact and inspecting the result.

The public part of it is [`licensegate-operator`](https://github.com/Diegorandom/license-gate-cli/blob/main/.agents/skills/licensegate-operator/SKILL.md),
an [Agent Skills](https://agentskills.io/specification) definition for a CLI that mutates real
licences: dry-run first, explicit confirmation before live writes, secrets never on the command
line. **The tool acts; the human authorises.**

## Numbers I can defend

- **< 1.5 % CPU per instance**, with negligible added latency, measured on the audio thread.
- **Reported latency fixed at 5 ms — 240 samples at 48 kHz.** Always the maximum: automating a
  lookahead would force the host to re-sync the timeline, so every user pays the maximum even at
  the smallest setting. Over-reporting is the safe direction.
- **20 % more clicks associated with a user**, like-for-like, from a device-association algorithm
  I designed and shipped — measured against the existing attribution in BigQuery.
- **13,000 users** in the first year, with support and the roadmap through my own hands.

## The other half of the work

Ten years of backend and platform before this, in Java, Kotlin and TypeScript:

- **Mercado Libre, Technical Leader.** A device data platform — collection → transformation →
  BigQuery over **BigQueue** (Meli's streaming platform), with per-use-case data products behind
  an authorizer — plus a Java library for device data generation shipped inside the Meli Android app.
- **fabric.inc, via BairesDev.** v2 of the order management system in **Java**: microservices,
  event-driven on SQS/SNS, MongoDB under production load.
- **Lineage Logistics, via BairesDev.** React pages and business logic, migrating a legacy FoxPro
  codebase serving inventory management across North America.

## What I care about in this work

- **Measure on the thread that has the deadline.** A missed buffer is not a wrong value, it is a
  click, so the audio thread gets budgets and traces, not assertions.
- **A parameter range is a contract.** Widening the Rider's action range from ±12 dB to ±24 dB
  reinterprets existing automation lanes in every host, so it does not ship quietly: the release
  notes say it in plain language, before anyone opens an old project and hears something different.
- **Green is not correct.** Three tests went green on a function that was wrong in six of nine
  real cases. A test that cannot fail against the old code is decoration, not evidence.
- **You don't trust the model, you bound it.** Anything that can act on production proposes first
  and is validated before it executes — the same discipline as handing a junior engineer credentials.

## Where to look

| | |
|---|---|
| **Hear the product** | [casaoccidente.com](https://casaoccidente.com) — three plugins, macOS, AU + VST3, free trial |
| **Engineering judgment in code** | [`license-gate-cli`](https://github.com/Diegorandom/license-gate-cli) — a TypeScript CLI that mutates real licences. The tool acts; the human authorises. |
| **How I use agents** | [`licensegate-operator`](https://github.com/Diegorandom/license-gate-cli/blob/main/.agents/skills/licensegate-operator/SKILL.md) — the agent skill: dry-run first, explicit confirmation, no secrets on the command line |
| **DSP and plugin work, learning in public** | [`SimpleMBComp`](https://github.com/Diegorandom/SimpleMBComp) (multiband compressor + spectrum analyser) · [`SimpleEQ`](https://github.com/Diegorandom/SimpleEQ) |
| **Earlier: algorithmic composition** | [`WolframAmadeus`](https://github.com/Diegorandom/WolframAmadeus) — SuperCollider driven by Wolfram Language |
| **Earlier: data sonification** | [`DeltaPureData`](https://github.com/Diegorandom/DeltaPureData) — a meteorological simulator rendered as sound |

## Elsewhere

[LinkedIn](https://www.linkedin.com/in/diegortega/) · diego@casaoccidente.com
