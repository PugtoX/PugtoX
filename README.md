### Yuan Kin Ho · AI Application Developer

I build AI applications end to end — **and measure them properly**.
Applied Sciences graduate (PolyU SPEED, 2026). Hong Kong resident, no visa sponsorship needed.

**Open to AI application / ML engineering roles.** Also available for freelance web work.

---

## Projects

### [hk-labour-triage](https://github.com/PugtoX/hk-labour-triage) — LoRA fine-tuning for Cantonese labour-enquiry triage

Fine-tuned **Qwen3-1.7B** with fp16 LoRA to route colloquial Cantonese labour-law questions into
`{category, urgency, escalate}`. Exported to GGUF and served through Ollama so it could be compared
against a 9B baseline **on one stack** rather than across two frameworks.

| | 9B baseline | **1.7B + LoRA** |
|---|---|---|
| Urgency accuracy | 63.2% | 63.2% (tie) |
| **Urgent-case recall** | 37.8% | **73.0%** |
| **Weighted error cost /100** | 80 | **56** |
| exact_match vs its own base | — | **3:40, p=0.000** (McNemar) |

**The part I care about:** the conclusion got reversed three times, and each reversal is logged —
a 46-item test set that ranked the models backwards, a de-duplication bug that leaked 13 duplicate
texts into the test set, and a serving bug that applied the system prompt twice, costing 24pp of
recall until the raw output exposed it. Every figure above is reproducible from the committed
per-item dumps.

`Python` · `Qwen3-1.7B` · `LoRA / PEFT` · `transformers` · `llama.cpp` · `Ollama` · `McNemar testing`

---

### [hk-law-rag](https://github.com/PugtoX/hk-law-rag) — RAG Q&A over the Hong Kong Employment Ordinance

Full pipeline: 16 official Labour Department FAQ pages → 84 structured Q&A pairs → bge-m3
embeddings → ChromaDB → cited answers from a local LLM via Ollama.

- **recall@5 93.3% on colloquially-phrased queries** (100% on the corpus's own questions — that one
  is a regression test, not a result)
- Diagnosed and fixed a real retrieval defect: encoding answers alone left short answers
  unretrievable (81/84); encoding question + answer reached 84/84
- Two independent hallucination guards, and a measurement showing **neither alone suffices** —
  a code-level distance gate that refuses without calling the model, plus a prompt constraint
- Dockerised; CI runs 10 verification scripts

`Python` · `bge-m3` · `ChromaDB` · `Ollama` · `FastAPI` · `Docker`

---

### [kin-ho-profile](https://github.com/PugtoX/kin-ho-profile) — portfolio site

React 19 + Vite + Tailwind v4, built and shipped solo. Theme persisted in `localStorage` and applied
**before first paint**; canvas backdrop that idles under `prefers-reduced-motion`; contact form with
per-field validation, honeypot and cooldown. Lint + tests in CI, auto-deploy to GitHub Pages.

→ **[pugtox.github.io/kin-ho-profile](https://pugtox.github.io/kin-ho-profile/)**

---

### Smaller experiments

| Repo | What it shows |
|---|---|
| [cookery-practice](https://github.com/PugtoX/cookery-practice) | Deployment and technical-SEO practice run on a static site |
| [palette-lab](https://github.com/PugtoX/palette-lab) | Colour palette candidates rendered side by side over one identical component skeleton |

---

## Stack

**AI / LLM** — RAG · embeddings (bge-m3) · vector search (ChromaDB) · LoRA / PEFT fine-tuning ·
GGUF export · local LLM serving (Ollama)

**Evaluation** — paired significance tests (McNemar) · Wilson intervals · per-class recall and
precision · cost-weighted metrics

**Languages & Web** — Python · TypeScript / JavaScript · SQL · React · Node.js · FastAPI · Tailwind CSS

**Tooling** — Git · Docker · GitHub Actions · Linux (WSL2)

---

## Contact

- **Email** — hugoyuan2004@gmail.com
- **Portfolio** — [pugtox.github.io/kin-ho-profile](https://pugtox.github.io/kin-ho-profile/)
- **LinkedIn** — [linkedin.com/in/pugto-yuan-48529636b/](https://www.linkedin.com/in/pugto-yuan-48529636b/)
