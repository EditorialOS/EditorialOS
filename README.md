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

### [Editorial OS](https://github.com/EditorialOS/editorial-os) — Editorial Strategy System
  `Claude plugin` `MCP` `Google Drive` `Markdown skill architecture`

  Seven commands, five specialist skills, full editorial pipeline from audit to social repurposing. Point it at a Google Drive folder and your documents become the configuration — no setup forms, no brand questionnaires.

  ### [The Gate](https://github.com/EditorialOS/The-Gate) — Editorial Quality Gate API
  `TypeScript` `Express 5` `PostgreSQL` `Drizzle ORM` `OpenAPI 3.1` `Claude`

  A REST API that evaluates any draft against a fixed eight-criterion rubric and returns a machine-readable verdict: `APPROVED`, `APPROVED_WITH_NOTES`, `REVISE`, or `BLOCKED` — with 1–5 criterion scores, evidence quotes from the draft, a weighted confidence score, and specific revision instructions when action is required. SHA-256 hashed API keys, per-key rate limiting, PostgreSQL review history.

  → The eval layer, externalized. The rubric is fixed. The model cannot freestyle.

  ### [Email Marketing Manager](https://github.com/EditorialOS/email-marketing-manager) — Newsletter Production System
  `Claude plugin` `MCP` `Google Drive` `Learning loops`

  Drafts newsletters from real documents, generates segment variants, predicts performance, and writes learnings back to Drive after every send. Institutional knowledge compounds in plain markdown any team member can read.

  ### [Pinterest Marketing Strategist](https://github.com/EditorialOS/pinterest-marketing-strategist) — Pin Production System
  `Claude plugin` `MCP` `Google Drive` `Cloudinary`

  Composed pin batches from an approved image library and brand context. Tracks performance by image type × title pattern × board, and applies learnings to every subsequent batch.

  ### [Composer](https://github.com/EditorialOS/composer) — Story Packaging System
  `Claude plugin` `Google Drive` `Rights metadata`

  Packages finished stories for publication: matched visual assets, usage rights read from embedded metadata, platform-ready crops, archival context. One brief in, one publishable package out.

    ### [Photo Editor](https://github.com/EditorialOS/photo-editor) — Post-Shoot Metadata Pipeline
    `Claude plugin` `ExifTool` `XMP/IPTC` `Deterministic CLI`

    Embeds rights, products, and shoot context into image files at ingest. Intelligence at intake, determinism at embed — the model never sits in the write path. Closes the loop with [Composer](https://github.com/EditorialOS/composer): rights written here are read at packaging.

  ---

  ## Install

  ```
  /plugin marketplace add EditorialOS/editorial-os
  /plugin install editorial-os@editorial-os

  /plugin marketplace add EditorialOS/email-marketing-manager
  /plugin install email-marketing-manager@email-marketing-manager

  /plugin marketplace add EditorialOS/pinterest-marketing-strategist
  /plugin install pinterest-marketing-strategist@pinterest-marketing-strategist
  ```

  Runs in Claude Code. After adding the marketplace, install each plugin individually.

  ---

  **Portfolio:** [signalstudio.io](https://signalstudio.io) · editorial.operating.system@gmail.com
  