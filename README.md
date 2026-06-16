# Steven Williams

**AI Infrastructure & Systems Engineer | Dallas-Fort Worth, TX**

I design and operate private AI infrastructure — the systems that make LLMs work reliably in production, not just in demos. My work sits at the intersection of hands-on systems administration and practical AI deployment: serving large language models on-premise, wiring them into applications, and building the agent architectures and governance frameworks that make AI adoption sustainable.

Background in IT infrastructure across healthcare and education. Current focus: private inference, multi-agent systems, and AI governance.

---

## Current Stack

```
┌─────────────────────────────────────────────────────────────────┐
│                     NVIDIA DGX Spark                            │
│         (GB10 Grace-Blackwell · 121 GB unified memory)          │
│                                                                 │
│  vLLM :8100  ─── Qwen3.6-35B-A3B-FP8                           │
│                  200K context · 11× concurrency · multimodal    │
│                                                                 │
│  llama.cpp :8090 ─── model playground (lazy-load, ≤2 models)   │
│  Wyoming Whisper :10300 ─── STT                                 │
│  Wyoming Piper   :10200 ─── TTS                                 │
└──────────────┬──────────────────────────────────────────────────┘
               │  OpenAI-compatible API  (shared by everything)
    ┌──────────┴───────────────────────────────────────────────┐
    │                                                           │
    ▼                                                           ▼
Voice Pipeline                                    Applications
  Wake word → HA Assist                            Open WebUI (family chat)
  → Whisper STT                                    MathSpark (AI math tutor)
  → vLLM :8100                                     FinPulse (finance AI)
  → Piper TTS                                      GutScan (FODMAP tracker)
  → Speaker                                        WebScraper + HLCC dashboard

    │
    ▼
Agent Layer  (Hermes Agent — Nous Research)
  Commander  ── orchestrates tasks, MCP tools (HLCC dashboard, rinny_ops)
  Watchtower ── read-only on-call monitor, daily 7am health briefing
  Curator    ── Obsidian vault librarian, daily triage
  Rinny      ── voice agent on Proxmox VM (de-powered, firewall-isolated)
  Rinny-ops  ── powered worker, shell tools, sandboxed
```

All AI inference is local. Zero cloud LLM calls for any homelab application.

---

## Projects

| Project                                                                        | What it does                                                                                                                                            | Stack                             |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| [AI Governance Framework](https://github.com/txkramer/ai-governance-framework) | Ready-to-deploy AI governance templates — acceptable use policies, risk matrices, HIPAA/FERPA/NIST AI RMF compliance mapping, vendor assessments        | Markdown templates                |
| [homelab-toolkit](https://github.com/txkramer/homelab-toolkit)                 | Custom Claude Code hooks, skills, Hermes agent SOUL profiles, MCP servers, and utility scripts powering the homelab AI stack                            | Python · Bash · Markdown          |
| **HLCC** (private)                                                             | Home Lab Command Center — tracks projects, token usage, resource allocation; integrates Netdata, Proxmox, Docker, Plex, Home Assistant                  | FastAPI · React · SQLite · Docker |
| **MathSpark** (private)                                                        | AI math tutor for daughters — adaptive worksheets, assessments, SmartScore progress tracking                                                            | FastAPI · React · ChromaDB · vLLM |
| **GutScan** (private)                                                          | FODMAP tracking app for IBS management — on-device AI with DGX Spark fallback                                                                           | React Native · Expo · Supabase    |
| **autoresearch**                                                               | Autonomous ML research loop — AI agent runs 150+ experiments unattended, keeps improvements by validation metric. **+10.4% improvement over baseline.** | PyTorch · NGC containers · vLLM   |

---

## Selected Achievements

- **Tuned a 200K-context LLM server** from scratch: reduced `gpu-memory-utilization` 0.80 → 0.70, simultaneously tripled context window (65K → 200K) and freed 12 GB host memory — by understanding that the KV pool is fixed, not proportional to context size
- **150+ autonomous ML experiments** across 6 weeks, unattended, with a +10.4% model improvement over baseline
- **Multi-agent security architecture** with one-way firewall between voice surface and ops worker — voice agent is structurally incapable of modifying systems, not just instructed not to
- **8 applications share one GPU** (single vLLM process) with zero scheduling conflicts at typical household load
- **Daily automated reporting** from three scheduled Hermes agents: health briefings, vault triage, and cost ledgers — filed without manual intervention

---

## Tools & Platforms

`vLLM` `NVIDIA DGX` `Hermes Agent` `MCP` `Docker` `Proxmox` `Home Assistant`
`FastAPI` `React` `Wyoming Protocol` `Whisper` `Piper` `Nginx` `Tailscale`
`Claude Code` `OpenAI-compatible APIs` `ARM64/aarch64` `HIPAA` `NIST AI RMF`

---

stevenwilliamsit26@gmail.com
