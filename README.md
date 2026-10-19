# Diego Ortega — audio software engineer

I build audio plugins in C++/JUCE, and the platform that sells them.

**Founder of [Casa Occidente](https://casaoccidente.com)** — three commercial plugins for
macOS and Windows (AU + VST3), notarized, signed, and shipped. 13,000 users in the first year.

Most of my production code is closed source, so this profile is a **route map rather than a
mirror**: the product is downloadable, the numbers are measured, and the engineering judgment
lives in the repositories below.

## Numbers I can defend

- **< 1.5 % CPU per instance**, with negligible added latency, measured on the audio thread.
- **Reported latency fixed at 5 ms — 240 samples at 48 kHz.** Always the maximum: automating a
  lookahead would force the host to re-sync the timeline, so every user pays the maximum even at
  the smallest setting. Over-reporting is the safe direction.
- **13,000 users** in the first year, with support and the roadmap through my own hands.

## What I care about in this work

- **Real-time budgets instead of feature lists.** A missed deadline is not a wrong value, so the
  audio thread gets budgets and measurement, not assertions.
- **A parameter range is a contract.** When I widened the action range from ±12 dB to ±24 dB,
  existing automation lanes were reinterpreted by the host — so the release notes say so, in
  plain language, before anyone opens an old project and hears something different.
- **Boundaries are where the bugs live.** The end of a region is exclusive; the first and the
  last gap are the ones implementations forget.

## Where to look

| | |
|---|---|
| **Hear the product** | [casaoccidente.com](https://casaoccidente.com) — three plugins, macOS, AU + VST3, free trial |
| **Engineering judgment in code** | [`license-gate-cli`](https://github.com/Diegorandom/license-gate-cli) — a TypeScript CLI that mutates real licences, with an [agent skill](https://github.com/Diegorandom/license-gate-cli/blob/main/.agents/skills/licensegate-operator/SKILL.md) that specifies dry-run-first and explicit confirmation. The tool acts; the human authorises. |
| **DSP and plugin work, learning in public** | [`SimpleMBComp`](https://github.com/Diegorandom/SimpleMBComp) (multiband compressor + spectrum analyser) · [`SimpleEQ`](https://github.com/Diegorandom/SimpleEQ) |
| **Earlier: algorithmic composition** | [`WolframAmadeus`](https://github.com/Diegorandom/WolframAmadeus) — SuperCollider driven by Wolfram Language |
| **Earlier: data sonification** | [`DeltaPureData`](https://github.com/Diegorandom/DeltaPureData) — a meteorological simulator rendered as sound |

## Elsewhere

[LinkedIn](https://www.linkedin.com/in/diegortega/) · diego@casaoccidente.com
