## Hello, my name is Desmond

[Website](https://desmondchoy.github.io/)

Data scientist turned applied AI researcher at Manulife. I build and evaluate LLM systems for regulated domains. Projects cover multi-agent systems, self-supervised learning, and behavioral AI. My work spans education, music, computer vision, and behavioral science, with a bias toward shipping production apps over accumulating notebooks.

## Project Highlights

**[Learning Odyssey](https://github.com/DesmondChoy/adventures)** | [Free to Play](https://learning-odyssey.up.railway.app/)

  Imagine a child choosing to explore an Underwater Kingdom — then picking "Astronomy" as their learning topic. The AI builds them a one-of-a-kind
  10-chapter adventure: they craft a magical artifact, encounter bioluminescent creatures who teach them about Jupiter's gravity, reflect on what
  they've learned inside a coral palace, and make choices that visually reshape their protagonist across AI-generated illustrations. When the story
  ends, they get a personalized learning report showing every question they answered and why the answers matter.

  That's Learning Odyssey — an AI storytelling platform where education is invisible because the story is that engaging.

  What makes it interesting technically:
  - OpenAI generates narrative and scene text; Gemini 2.5 Flash Lite handles supporting tasks such as summaries and prompt synthesis.
  - An image pipeline combines scene descriptions with tracked character visuals and generates illustrations through Gemini 3.1 Flash Image.
  - Content is validated (3 choices, retried up to 3x) before streaming word-by-word over WebSocket, with non-critical work deferred to background
  tasks
  - Eval discipline for non-deterministic AI: structural validation over content assertion, log-based error analysis across 10+ failure categories, and end-to-end simulation through the live WebSocket
  - Sessions survive disconnects with Supabase-backed state persistence and field-level corruption recovery

  Stack: FastAPI · Supabase · OpenAI API · Gemini 2.5 Flash Lite · Gemini 3.1 Flash Image · React · Tailwind · Railway

**[NANA](https://github.com/DesmondChoy/nana)** | [Live Demo](https://nana-app.up.railway.app/)

Every complex document assumes knowledge you might not have. NANA bridges that gap: upload a PDF, set your background, and get a side-by-side view — original document on the left, AI-generated study notes on the right, personalized to your expertise, math comfort, and learning goal.

An equity research report explained through a PM's lens. A technical whitepaper translated for a non-technical founder. A medical paper made accessible to a policy analyst. The same PDF produces entirely different notes for different readers — different analogies, different depth, different notation.
- Select any sentence to elaborate, simplify, or reframe with a domain-specific analogy.
- Paste your own notes and the system weaves them into the AI output.
- Notes render LaTeX, use Obsidian-style callouts, and maintain narrative flow across pages.

Under the hood: a two-phase Gemini pipeline (extract once, generate per-page) cuts API costs ~70-80% vs sending the full PDF per page — structured output guarantees, no embeddings, no vector stores, fully stateless backend. Notes cached client-side with full-text search and content-hashed Markdown export/import. BYOK, zero server-side key storage.

**[buttery_smooth_jamming](https://github.com/DesmondChoy/buttery_smooth_jamming)** | [Demo Video](https://www.linkedin.com/feed/update/urn:li:activity:7433764408931205120/)

Four LLM agents, one stage, no sheet music. They don't see each other — they hear each other. A closed-loop browser FFT pipeline turns live Strudel output back into prompt context, so every few seconds each agent decides whether to evolve its pattern, hold the groove, or carve out frequency space the others aren't using. A human bandleader can direct the whole ensemble or target individual agents via @mention syntax. Persistent memory means musical personality compounds across the set — by the third chorus, the rhythm section has developed its own relationship.

What makes it interesting technically:
- 6.2s p95 end-to-end latency, 100% directive success across 24 runs
- Closed-loop browser FFT → prompt-context pipeline for live audio reasoning
- Custom MCP server bridges the Strudel live-coding environment with agent orchestration
- Independent memory and context-window compaction per agent
- 3 architectural versions in 27 days; 243 commits, 132 issues tracked, 281 tests — the production successor to the earlier `cc_sick_beats` prototype

Stack: Next.js · TypeScript · Codex · Strudel · MCP · WebSockets

**[moodsic](https://github.com/DesmondChoy/moodsic)** | [Live Demo](https://moodsic-fe.onrender.com/) — Emotion-aware music recommendation using a dual-pathway fusion architecture. A face pathway (EmoNet) captures valence/arousal from facial expressions while a scene pathway (CLIP ViT-B/32) reads emotional context from the visual environment. Variance-weighted blending (0.6 scene / 0.4 face) outperforms face-only by ~7% and scene-only by ~19% on held-out VEATIC data. Recommended songs are matched via nearest-centroid search against a GMM-clustered DEAM music catalogue.

**[Twinkl](https://github.com/DesmondChoy/twinkl)** | [Demo](https://onboarding-production-1dd2.up.railway.app/) | [Drift Inspection](https://twinkl-drift-review-production.up.railway.app/) | [Human Annotation (local setup)](https://github.com/DesmondChoy/twinkl/blob/main/docs/readme/review_apps.md)

People can know what matters to them while repeatedly making choices that conflict with it. An AI journal can offer reassurance while leaving that pattern unexamined. Twinkl investigates evidence-grounded accountability: comparing the behavior described across Journal Entries with the Core Values a person explicitly confirmed.

Grounded in Schwartz’s Theory of Basic Human Values, Twinkl starts with a Best-Worst Scaling assessment to establish a Profile. Weekly Drift Detection examines subsequent writing for repeated Conflict, and a Coach Digest connects the evidence with an open reflective question. The user can inspect the writing and decisions behind each conclusion.

What makes it interesting technically:

- **Synthetic data treated as a research problem:** Built 1,651 longitudinal Journal Entries across 204 personas, preserving continuity within each history while controlling value-label leakage. Targeted augmentation kept validation and test personas fixed—and exposed how additional examples could improve one value while worsening another.
- **A compact model tested systematically:** A 23,454-parameter VIF Critic (Offline) explored value-alignment prediction where roughly 76% of labels were neutral. Across 133 configurations, experiments tested losses, embeddings, uncertainty, and additional history. Its limited Conflict recall, followed by unsuccessful hand-off ablations with GPT-5.4-mini, informed the decision to retain it as offline research.
- **Reasoning effort selected through measured trade-offs:** In a three-repeat development study covering 292 histories and 42 known Drifts, increasing Luna’s reasoning from low to xhigh raised median detections from 23 to 28—but also raised false alerts from four to nine. Twinkl retained low reasoning for the capstone.
- **Retrieval evaluated against the actual task:** A paired North Star Moment study across 501 synthetic weeks compared Nomic top-three retrieval with full-history review for selecting supportive quotations. Full history achieved higher precision and recall in both partitions; development Card precision was 75.5% versus 58.6%, supporting its adoption.
- **The evaluator was tested too:** A source-context diagnostic exposed chronology and causal-interpretation errors that passed automated checks. A known incorrect response still received 5/5 correctness from the same-model evaluator, demonstrating why high evaluation scores needed scrutiny against the original writing.

The responsive Experience includes five synthetic Persona demos spanning 27 replay weeks, with recorded model responses and direct access to each week's Journal Entries and Drift result. North Star Moment adds exact supportive quotations; eligible weeks compare Coach Digest responses generated with and without that context. Inspect exposes the evidence, model settings, and decisions behind the replay.

**Stack:** Python · PyTorch · React · TypeScript · Starlette · Shiny · OpenAI · Polars · Railway

*NUS-ISS capstone proof of concept. Findings use synthetic histories and AI evaluation, alongside a limited human label-agreement study; real-user usefulness remains untested.*

**[SSL ViT Models](https://github.com/DesmondChoy/ssl_wikichurches)** | [Report](https://desmondchoy.github.io/projects/ssl-vit-models)

Completed study of whether vision models attend to architectural evidence marked by human experts. Benchmarked DINOv2, DINOv3, MAE, CLIP, SigLIP, SigLIP2, and ResNet-50 on 139 church images with 631 expert boxes. DINOv3 provided the strongest frozen spatial alignment; CLIP and MAE improved after adaptation but on different architectural evidence. Attention-head analysis found that DINO models retained dominant heads while CLIP shifted toward later layers. These are descriptive alignment findings. A FastAPI and React dashboard makes the cached attention maps and metrics inspectable.

**[Aegis AI Travel Insurance Recommender](https://github.com/DesmondChoy/mtech-policy-recsys)** | [Demo](https://aegis-recsys.netlify.app/)

Academic recommender that turns policy PDFs and synthetic customer transcripts into structured requirements, insurer comparisons, and recommendations. Combined deterministic requirement scoring with transcript-aware LLM reranking. Evaluation covered 13 policy PDFs and 80 synthetic customers across four scenarios, with 85–100% scenario pass rates and 87.53% valid requirement coverage.

Stack: Python · Gemini · OpenAI · CrewAI · Pydantic · React · Vite · Netlify

## Technologies

**Languages:** Python, TypeScript, SQL, R

**AI/ML:** OpenAI/Claude/Gemini API, PyTorch, Transformers, Scikit-Learn, XGBoost

**Backend:** FastAPI, WebSockets, Pydantic, Supabase, PostgreSQL

**Frontend:** React, Next.js, Vite, Shiny

**Infrastructure:** Railway, AWS, Docker, GitHub Actions

