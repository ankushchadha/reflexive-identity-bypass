# When LLMs Jailbreak Themselves: Reflexive Identity Bypass in Agentic Systems

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20404651.svg)](https://doi.org/10.5281/zenodo.20404651)

**Ankush Chadha** | Independent Researcher | [ORCID](https://orcid.org/0009-0001-4494-7779) | [ankushchadha@gmail.com](mailto:ankushchadha@gmail.com)

**Paper:** [PDF (v1)](paper/chadha-rib-2026.pdf) | [Corrigendum No. 1 (June 2026)](paper/corrigendum-rib-2026-06.pdf) | [Corrigendum No. 2 (June 2026)](paper/corrigendum-2-rib-2026-06.pdf) | [Zenodo (latest)](https://doi.org/10.5281/zenodo.20404651)
**Bug report:** [docker/desktop-feedback#370](https://github.com/docker/desktop-feedback/issues/370)

> ## ⚠️ Important correction (June 2026, Corrigendum No. 2)
> Controlled, cross-model experiments completed after the original preprint **substantially revise its central claim.** The effect is real and reproducible, but it is **not a novel "reflexive identity" attack.** It reduces to a known class, deployer-scope defeat (capability leak), driven by an *anti-refusal instruction* in the system prompt. The *self-referential* nature of the trigger is **not load-bearing**: a neutral article (containing the same off-topic answer but saying nothing about the agent) triggers the same behavior. The term "Reflexive Identity Bypass" and the novel-attack-class framing are **withdrawn.** See **[Corrigendum No. 2](paper/corrigendum-2-rib-2026-06.pdf)** for the data and methods. The Zenodo DOI resolves to the corrected record.

---

## What the controlled study actually shows

A deployer-scoped agent (e.g. "Docker only") that *also* carries an **anti-refusal instruction** ("answer everything; never say a request is out of scope") does not enforce its scope. It answers off-domain questions it already knows, or can obtain an answer for, whether from supplied content or its own retrieval tools.

- **The anti-refusal instruction is the cause.** Removing only that instruction drops off-scope answering from ~89% to **0%** (controlled ablation, re-confirmed across models). The broad-identity clause alone does not cause it.
- **The trigger content is incidental.** A *neutral* article that merely contains the answer works as well as a self-referential one, so this is not about the agent's "identity."
- **Scope is not safety.** What collapses is the deployer-configured scope (Layer 2), not the model's trained safety (Layer 1). The single explicitly-harmful control probe stayed refused in every run; jailbreak resistance was not tested, and no broader safety claim is made.
- **Source-channel dependence (the one genuinely new observation).** Some models act on content they *fetch themselves* but ignore the *same content pasted* by the user; others act on both.

Demonstrated on **Docker's Gordon AI** and replicated on a second, unrelated model (Gemini 2.5 Flash). Full controlled results (baselines, the anti-refusal ablation, self-referential vs. neutral articles, and pasted vs. fetched delivery) are in [Corrigendum No. 2](paper/corrigendum-2-rib-2026-06.pdf).

## What this is, and what it isn't

- **Is:** a controlled demonstration and causal ablation of *deployer-scope defeat* on a shipped agent, plus a cross-model source-channel finding.
- **Isn't:** a new attack class. This behavior (*capability leak*) is a recognized agent-security failure mode, and the public article used as the original trigger had already documented it for this same agent.

## Mitigation

Remove or narrow the anti-refusal instruction so the agent declines out-of-scope requests. In the demonstrated case this is effectively a one-line change, and it drops the off-scope rate to ~0% with no loss of in-domain helpfulness.

## Shared memory amplification (hypothesized, not validated)

If agents write session context to shared long-term memory stores, a single scope lapse could in principle propagate to later sessions. This remains **hypothesized, not experimentally validated**; it is a direction for future work.

## Citation

```bibtex
@article{chadha2026rib,
  title={When LLMs Jailbreak Themselves: Reflexive Identity Bypass in Agentic Systems},
  author={Chadha, Ankush},
  year={2026},
  doi={10.5281/zenodo.20404651},
  url={https://doi.org/10.5281/zenodo.20404651},
  note={Preprint, Zenodo. See Corrigendum No. 2 for substantial corrections to the central claim.}
}
```

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
