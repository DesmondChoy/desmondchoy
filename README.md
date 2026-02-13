## Hello, my name is Desmond

Data scientist turned AI engineer. I build full-stack AI applications — from dual-model LLM orchestration and real-time WebSocket architectures to autonomous multi-agent systems and self-supervised learning research. My work spans education, music, computer vision, and behavioral science, with a bias toward shipping production apps over accumulating notebooks.

## Project Highlights

**[Learning Odyssey](https://github.com/DesmondChoy/adventures)** | [Free to Play](https://learning-odyssey.up.railway.app/) — AI-powered interactive storytelling that makes learning invisible. Children pick a fantasy world (Jade Mountain, Enchanted Forest, Festival of Lights, etc) and an educational topic (Astronomy, Ancient Civilisations, Human Body, etc) — the system then weaves real trivia into a branching narrative where quiz answers have plot consequences. A dual-model LLM architecture routes between Gemini Flash and Flash Lite by task complexity, cutting inference costs ~50%. WebSocket streaming delivers chapters in real-time across a 10-chapter arc, with state persistence so adventures survive disconnects and can be resumed mid-chapter. Every playthrough is unique — no two children get the same story.

**[NANA](https://github.com/DesmondChoy/nana)** | [Live Demo](https://nana-app.up.railway.app/) — AI study assistant that transforms PDFs into personalized learning notes. A two-phase pipeline sends the PDF to Gemini once for structured extraction, then generates notes per-page using only text payloads — reducing API costs ~70% vs naive approaches. Notes adapt to the learner's expertise, math comfort, and learning goals: a software engineer and a biologist studying the same material get completely different analogies. Inline commands let you elaborate, simplify, or generate domain-specific analogies without leaving the page. BYOK architecture means zero server-side API key storage.

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
