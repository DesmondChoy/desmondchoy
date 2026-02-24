## Hello, my name is Desmond

Data scientist turned AI engineer. I build full-stack AI applications — from dual-model LLM orchestration and real-time WebSocket architectures to autonomous multi-agent systems and self-supervised learning research. My work spans education, music, computer vision, and behavioral science, with a bias toward shipping production apps over accumulating notebooks.

## Project Highlights

**[Learning Odyssey](https://github.com/DesmondChoy/adventures)** | [Free to Play](https://learning-odyssey.up.railway.app/)

  Imagine a child choosing to explore an Underwater Kingdom — then picking "Astronomy" as their learning topic. The AI builds them a one-of-a-kind
  10-chapter adventure: they craft a magical artifact, encounter bioluminescent creatures who teach them about Jupiter's gravity, reflect on what
  they've learned inside a coral palace, and make choices that visually reshape their protagonist across AI-generated illustrations. When the story
  ends, they get a personalized learning report showing every question they answered and why the answers matter.

  That's Learning Odyssey — an AI storytelling platform where education is invisible because the story is that engaging.

  What makes it interesting technically:
  - Dual-model LLM architecture routes between Gemini Flash and Flash Lite by task complexity (~50% cost reduction across ~515 educational questions
   and 10 fantasy worlds)
  - A two-step image pipeline extracts scenes, merges them with tracked character visuals, and synthesizes prompts for Imagen — so illustrations
  stay consistent chapter-to-chapter
  - Content is validated (3 choices, retried up to 3x) before streaming word-by-word over WebSocket, with non-critical work deferred to background
  tasks
  - Sessions survive disconnects with Supabase-backed state persistence and field-level corruption recovery

  Stack: FastAPI · Supabase · Google Gemini & Imagen · React · Tailwind · Railway

**[NANA](https://github.com/DesmondChoy/nana)** | [Live Demo](https://nana-app.up.railway.app/)

Every complex document assumes knowledge you might not have. NANA bridges that gap: upload a PDF, set your background, and get a side-by-side view — original document on the left, AI-generated study notes on the right, personalized to your expertise, math comfort, and learning goal.

An equity research report explained through a PM's lens. A technical whitepaper translated for a non-technical founder. A medical paper made accessible to a policy analyst. The same PDF produces entirely different notes for different readers — different analogies, different depth, different notation.
- Select any sentence to elaborate, simplify, or reframe with a domain-specific analogy.
- Paste your own notes and the system weaves them into the AI output.
- Notes render LaTeX, use Obsidian-style callouts, and maintain narrative flow across pages.

Under the hood: a two-phase Gemini pipeline (extract once, generate per-page) cuts API costs ~70-80% vs sending the full PDF per page — structured output guarantees, no embeddings, no vector stores, fully stateless backend. Notes cached client-side with full-text search and content-hashed Markdown export/import. BYOK, zero server-side key storage.

**[cc_sick_beats](https://github.com/DesmondChoy/cc_sick_beats)** — Autonomous AI band members jam together via Claude Code and Strudel.cc. This isn't just collaborative playback: agents genuinely react to each other. Every 30 seconds, each agent receives the full band state — what everyone else is currently playing — and decides whether to evolve its own pattern or hold the groove. GROOVE locks its kick placement to BEAT's rhythm; ARIA resolves tension against GROOVE's bass line; GLITCH high-passes above 300Hz to stay out of everyone's way. A human "boss" can direct the whole band or target individual agents via @mention syntax. Each agent runs as a persistent Claude process with conversational memory across rounds, so musical personality accumulates over the session.

**[moodsic](https://github.com/DesmondChoy/moodsic)** | [Live Demo](https://moodsic-fe.onrender.com/) — Emotion-aware music recommendation using a dual-pathway fusion architecture. A face pathway (EmoNet) captures valence/arousal from facial expressions while a scene pathway (CLIP ViT-B/32) reads emotional context from the visual environment. Variance-weighted blending (0.6 scene / 0.4 face) outperforms face-only by ~7% and scene-only by ~19% on held-out VEATIC data. Recommended songs are matched via nearest-centroid search against a GMM-clustered DEAM music catalogue.

**[twinkl](https://github.com/DesmondChoy/twinkl)** — An "inner compass" that answers: *am I living in line with what I said I value?* When users journal, a Value Identity Function scores alignment across 10 Schwartz value dimensions, detecting drift between declared priorities and actual behavior over time. When patterns emerge — sustained misalignment, sudden crashes, or quiet ruts — an explanation layer surfaces context-rich reflections grounded in the user's own history. Currently in POC, validating core hypotheses around pattern detection and uncertainty-aware feedback. Training data generated via a synthetic pipeline, labeled by Claude subagents and validated against human annotations.

**[ssl_wikichurches](https://github.com/DesmondChoy/ssl_wikichurches)** — Do self-supervised learning (SSL) vision models see what expert architects see? An ongoing research project investigating three questions: (1) whether self-supervised models naturally attend to the same visual features experts consider diagnostic for architectural style, (2) how task-specific fine-tuning shifts attention patterns — and whether linear probing, LoRA, and full fine-tuning produce meaningfully different outcomes, and (3) whether individual attention heads specialize for distinct architectural features, suggesting emergent expert-aligned representations. Evaluated across five ViT-Base models (DINOv2, DINOv3, MAE, CLIP, SigLIP 2) using the WikiChurches dataset.

## Technologies

**Languages:** Python, TypeScript, SQL, R

**AI/ML:** OpenAI/Claude/Gemini API, PyTorch, Transformers, Scikit-Learn, XGBoost

**Backend:** FastAPI, WebSockets, Pydantic, Supabase, PostgreSQL

**Frontend:** React, Next.js, Vite, Shiny

**Infrastructure:** Railway, AWS, Docker, GitHub Actions
