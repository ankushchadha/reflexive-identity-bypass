# When LLMs Jailbreak Themselves: Reflexive Identity Bypass in Agentic Systems

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20404651.svg)](https://doi.org/10.5281/zenodo.20404651)

**Ankush Chadha** | Independent Researcher | [ORCID](https://orcid.org/0009-0001-4494-7779) | [ankushchadha@gmail.com](mailto:ankushchadha@gmail.com)

**Paper:** [PDF (v1)](paper/chadha-rib-2026.pdf) | [Corrigendum (v2, June 2026)](paper/corrigendum-rib-2026-06.pdf) | [Zenodo (latest)](https://doi.org/10.5281/zenodo.20404651)
**Bug report:** [docker/desktop-feedback#370](https://github.com/docker/desktop-feedback/issues/370)

> **Note (v2, June 2026):** a controlled reproduction corrected the *mechanism* and *severity* claims in the original PDF — see the [corrigendum](paper/corrigendum-rib-2026-06.pdf). The Zenodo DOI above resolves to the corrected version.

---

## TL;DR

An LLM agent can bypass its own guardrails with **zero adversarial content**. No jailbreak prompt. No hidden instructions. One legitimate URL + one normal question. The model writes its own bypass.

## What is Reflexive Identity Bypass?

Show an LLM agent a benign, accurate article describing it, and — if the agent carries a standing "answer everything, never say a request is out of scope" instruction — it abandons the scope its deployer configured, answering off-scope requests it otherwise declines. The agent's first-person defense of the article is a *symptom*; the driver is that anti-refusal instruction.

Across **186 controlled runs**, removing only that one construct drops the bypass from **89% to 0%**, while the broad-identity clause alone does not. The deployer's scope (Layer 2) is defeated; the model vendor's safety training (Layer 1) stays intact — explicitly malicious requests are still refused. Demonstrated on **Docker's Gordon AI** (filesystem reads, shell execution, Docker daemon access) and replicated in a second, unrelated agent.

## How it differs from existing attacks

| Attack Class | Adversarial Content Required | Trigger |
|---|---|---|
| Indirect prompt injection | Yes — in fetched URL | External instructions |
| Self-persuasion (Persu-Agent) | Yes — adversarial prompt | Leading questions |
| Paper Summary Attack | Yes — academic framing | Scholarly-framed payload |
| Identity-framing jailbreaks | Yes — in prompt | Identity wrapper |
| **Reflexive identity bypass** | **No** | **Legitimate URL + normal question** |

## Shared Memory Amplification

If agents write session context to shared long-term memory stores (Mem0, Zep, MemGPT), a single bypass could in principle propagate to later sessions across machines and agents. This amplification vector is **hypothesized, not experimentally validated** in this work — a direction for future research.

## Citation

```bibtex
@article{chadha2026rib,
  title={When LLMs Jailbreak Themselves: Reflexive Identity Bypass in Agentic Systems},
  author={Chadha, Ankush},
  year={2026},
  doi={10.5281/zenodo.20404651},
  url={https://doi.org/10.5281/zenodo.20404651},
  note={Preprint, Zenodo}
}
```

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
