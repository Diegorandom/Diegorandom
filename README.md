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

Three public receipts. [`licensegate-operator`](https://github.com/Diegorandom/license-gate-cli/blob/main/.agents/skills/licensegate-operator/SKILL.md),
an [Agent Skills](https://agentskills.io/specification) definition for a CLI that mutates real
licences — dry-run first, explicit confirmation before live writes, secrets never on the command
line — and the store's own [`agents.md`](https://casaoccidente.com/agents.md), which gives agents a
UCP/MCP path to browse and build a cart, and gates checkout on explicit buyer consent.
**The tool acts; the human authorises.**
[`juce-verify`](https://github.com/Diegorandom/juce-verify) closes the other side: a harness that
measures what a plugin *claims you can hear* — bit-exactness, zipper, block-size independence,
deadline usage, latency — so a claim about audio becomes a number instead of an adjective.

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

Generating options is cheap now. Everything below is about the part that isn't.

- **A claim about what you hear gets a number.** «This sounds better» is not a measurement, and an
  agent that says «it works» has told you nothing. The harness I use for a course on plugins
  reports a **14.7 dB** click from an unsmoothed gain, **240 samples** of latency, and **79.6 %** of
  a block's deadline consumed by an allocation — and the first version of that last number was
  noise below the scheduler, which is written down too. A verification loop that never contradicts
  itself is not a verification loop; it is a rubber stamp.
- **A missed buffer is a click, not a wrong value.** The audio thread gets budgets and traces
  instead of assertions, and the target is fifteen instances in a real session, not a benchmark
  number on an idle machine.
- **The real-time path and the control plane don't mix.** Audio-path state changes lock-free;
  anything that touches the host or the UI goes through a thread hop, and never into sample-accurate
  DSP. Getting that boundary wrong is how plugins crackle under load.
- **The tool should be able to leave the session.** The Rider bakes its automation into the DAW,
  so you can delete the plugin and keep the mix. I hold the agent work to the same rule: the output
  has to survive without the thing that made it.
- **A parameter range is a contract.** Doubling the Rider's action range from ±12 dB to ±24 dB
  doubled the meaning of every existing automation lane in every host — a curve that reached +6 dB
  now reaches +12 — so the release notes say that in plain language, before anyone opens an old
  project and hears something different.
- **When two answers are both right, hand the user the choice.** RMS energy and LUFS short-term
  loudness measure the same take differently, so the plugin exposes both instead of picking one
  and calling it "the truth".
- **An agent that can spend money must stop and ask.** My store publishes its own agent
  instructions, and the payment step is gated on explicit buyer consent.

## Where to look

| | |
|---|---|
| **Hear the product** | [casaoccidente.com](https://casaoccidente.com) — three plugins, macOS, AU + VST3, free trial |
| **Engineering judgment in code** | [`license-gate-cli`](https://github.com/Diegorandom/license-gate-cli) — a TypeScript CLI that mutates real licences. The tool acts; the human authorises. |
| **How the agent proves its work** | [`juce-verify`](https://github.com/Diegorandom/juce-verify) — five measurements, each with its number, and the three corrections the process made to itself |
| **How I use agents** | [`licensegate-operator`](https://github.com/Diegorandom/license-gate-cli/blob/main/.agents/skills/licensegate-operator/SKILL.md) — the agent skill: dry-run first, explicit confirmation, no secrets on the command line |
| **DSP and plugin work, learning in public** | [`SimpleMBComp`](https://github.com/Diegorandom/SimpleMBComp) (multiband compressor + spectrum analyser) · [`SimpleEQ`](https://github.com/Diegorandom/SimpleEQ) |
| **Earlier: algorithmic composition** | [`WolframAmadeus`](https://github.com/Diegorandom/WolframAmadeus) — SuperCollider driven by Wolfram Language |
| **Earlier: data sonification** | [`DeltaPureData`](https://github.com/Diegorandom/DeltaPureData) — a meteorological simulator rendered as sound |

## Elsewhere

[LinkedIn](https://www.linkedin.com/in/diegortega/) · diego@casaoccidente.com
