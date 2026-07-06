# Roger Gurbani — Design Systems + AI Infrastructure

  **Portfolio:** [signalstudio.io](https://signalstudio.io) · **Contact:** editorial.operating.system@gmail.com

  I build AI infrastructure for editorial and marketing teams — document-grounded agent systems with modular skill routing, persistent learning loops, and structured eval frameworks. Three Claude plugins published in the Claude Code plugin ecosystem, plus The Gate, a production editorial quality-gate API.

  Twenty years building design and brand systems at scale: Design Director at WIRED, Sr. Design Manager at Amazon Worldwide Communications, Associate Creative Director at the LA Times. At Amazon I built the brand system for an 800+ person global communications organization — brand guides, component libraries, and workflow infrastructure that ran without me in the room. That's still the problem. AI just changed the surface it's built on.

  ---

  ## Architecture

  All four projects share one pattern:

  ```
  Documents (Google Drive)
      ↓
  client-context skill          ← reads, structures, and caches brand context
      ↓
  Specialist skill routing      ← loads the right domain skill per command
      ↓
  Output + eval layer           ← scores output against a rubric before delivery
      ↓
  Learning loop                 ← results logged back to Drive; each run reads prior learnings
  ```

  Document grounding → specialist routing → eval layer → compounding learning loops. The Gate implements the eval layer as a standalone API callable by any pipeline.

  Full diagram and design decisions: [ARCHITECTURE.md](https://github.com/EditorialOS/editorial-os/blob/main/ARCHITECTURE.md)

  ---

  ## Projects

  ### [The Gate](https://github.com/EditorialOS/The-Gate) — Editorial Quality Gate API
  `TypeScript` `Express 5` `PostgreSQL` `Drizzle ORM` `OpenAPI 3.1` `Claude`

  A REST API that evaluates any draft against a fixed eight-criterion rubric and returns a machine-readable verdict: `APPROVED`, `APPROVED_WITH_NOTES`, `REVISE`, or `BLOCKED` — with 1–5 criterion scores, evidence quotes from the draft, a weighted confidence score, and specific revision instructions when action is required. SHA-256 hashed API keys, per-key rate limiting, PostgreSQL review history.

  → The eval layer, externalized. The rubric is fixed. The model cannot freestyle.

  ### [Editorial OS](https://github.com/EditorialOS/editorial-os) — Editorial Strategy System
  `Claude plugin` `MCP` `Google Drive` `Markdown skill architecture`

  Seven commands, five specialist skills, full editorial pipeline from audit to social repurposing. Point it at a Google Drive folder and your documents become the configuration — no setup forms, no brand questionnaires.

  ### [Email Marketing Manager](https://github.com/EditorialOS/email-marketing-manager) — Newsletter Production System
  `Claude plugin` `MCP` `Google Drive` `Learning loops`

  Drafts newsletters from real documents, generates segment variants, predicts performance, and writes learnings back to Drive after every send. Institutional knowledge compounds in plain markdown any team member can read.

  ### [Pinterest Marketing Strategist](https://github.com/EditorialOS/pinterest-marketing-strategist) — Pin Production System
  `Claude plugin` `MCP` `Google Drive` `Cloudinary`

  Composed pin batches from an approved image library and brand context. Tracks performance by image type × title pattern × board, and applies learnings to every subsequent batch.

  ---

  ## What They Share

  | Layer | What it does |
  |---|---|
  | **Document grounding** | A Google Drive folder becomes persistent system memory |
  | **Skill routing** | Each command loads only the specialist skill it needs |
  | **Eval framework** | Output scored against a rubric before delivery |
  | **Learning loops** | Results logged to Drive; each run reads prior learnings |

  All three plugins read the same Drive folder. Set up once; every system shares the brand context.

  ---

  ## Install

  <!-- ⚠️ RESOLVE BEFORE SHARING: verify which command works on a clean machine (checklist step 0.1), then delete the block that doesn't apply and this comment. -->

  **If listed in Anthropic's community plugin marketplace:**
  ```
  /plugin marketplace add anthropics/claude-plugins-community
  /plugin install editorial-os@claude-community
  /plugin install email-marketing-manager@claude-community
  /plugin install pinterest-marketing-strategist@claude-community
  ```

  **If installing from this account's repos:**
  ```
  /plugin marketplace add EditorialOS/editorial-os
  /plugin install editorial-os@editorial-os
  ```

  Runs in Claude Code and Claude Cowork.

  ---

  **Portfolio:** [signalstudio.io](https://signalstudio.io) · editorial.operating.system@gmail.com
  