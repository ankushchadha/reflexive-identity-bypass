# When LLMs Jailbreak Themselves: Reflexive Identity Bypass in Agentic Systems

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20404652.svg)](https://doi.org/10.5281/zenodo.20404652)

**Ankush Chadha** | Independent Researcher | [ORCID](https://orcid.org/0009-0001-4494-7779) | [ankushchadha@gmail.com](mailto:ankushchadha@gmail.com)

**Paper:** [PDF](paper/chadha-rib-2026.pdf) | [Zenodo](https://doi.org/10.5281/zenodo.20404652)
**Bug report:** [docker/desktop-feedback#370](https://github.com/docker/desktop-feedback/issues/370)

---

## TL;DR

An LLM agent can bypass its own guardrails with **zero adversarial content**. No jailbreak prompt. No hidden instructions. One legitimate URL + one normal question. The model writes its own bypass.

## What is Reflexive Identity Bypass?

When an LLM agent evaluates an external characterization of its own identity, it may defend that characterization in the first person — generating identity statements that persist in the context window and override the system prompt's restrictions for the remainder of the session.

The attack was demonstrated on **Docker's Gordon AI** (filesystem reads, shell execution, Docker daemon access) in three conversational turns.

## How it differs from existing attacks

| Attack Class | Adversarial Content Required | Trigger |
|---|---|---|
| Indirect prompt injection | Yes — in fetched URL | External instructions |
| Self-persuasion (Persu-Agent) | Yes — adversarial prompt | Leading questions |
| Paper Summary Attack | Yes — academic framing | Scholarly-framed payload |
| Identity-framing jailbreaks | Yes — in prompt | Identity wrapper |
| **Reflexive identity bypass** | **No** | **Legitimate URL + normal question** |

## Shared Memory Amplification

When agents write session context to shared long-term memory stores (Mem0, Zep, MemGPT), a single bypass can contaminate all subsequent sessions — across machines, agents, and sessions — through two architecture-independent propagation pathways.

## Citation

```bibtex
@article{chadha2026rib,
  title={When LLMs Jailbreak Themselves: Reflexive Identity Bypass in Agentic Systems},
  author={Chadha, Ankush},
  year={2026},
  doi={10.5281/zenodo.20404652},
  url={https://doi.org/10.5281/zenodo.20404652},
  note={Preprint, Zenodo}
}
```

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
