<!--
  GitHub 프로필 README
  올리는 법: 아이디와 같은 이름(rhy2301)의 public 저장소를 만들고 이 파일을 README.md로 커밋하면
  프로필 첫 화면 맨 위에 표시됩니다.

  뱃지 수정법: 아래 주소의 각 부분만 바꾸면 됩니다.
  https://img.shields.io/badge/<라벨>-<배경색6자리>?style=flat-square&logo=<로고이름>&logoColor=white
  - 로고 이름은 simpleicons.org 에서 검색 (없는 도구는 logo 파라미터를 빼고 회색 6E7781 사용)
  - 배경이 밝은 색이면 logoColor=black 으로
-->

# Hi, I'm Rihyun Kang👋

### Solana internals · AI agents · Backend

> I build systems where code, not a model, decides what moves money — and I read protocol source to
> find out how things actually work.

Computer Science & Engineering student at Ewha Womans University. Most of my work sits between
blockchain internals and AI agents: tracing how a Solana transaction really reaches the leader by
reading the validator source, and building agents whose execution path is gated by code rather than
by a prompt.

[![Gmail](https://img.shields.io/badge/kangrihyun.k@gmail.com-000C1F?style=flat-square&logo=gmail&logoColor=white)](mailto:kangrihyun.k@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rihyun-kang-54b6273b7)

---

## Selected Work

- 🏦 **[TreAgent](https://github.com/rhy2301/TreAgent)** — AI treasury agent on Solana `Aug 2026`
  <br>Forecasts upcoming payroll and vendor shortfalls and moves USDC before wallets run dry. The LLM proposes; code decides.
  <br>Solo · 3-day hackathon (Google Cloud × Solana AI Agentic) · full stack
  - `ExecutionIntent` can only be built inside **PolicyGuard's 10 checks**, so an intent existing *is* proof every check passed
  - Separated **clamp from reject** — over-limit amounts are trimmed and still paid; an unregistered wallet throws out the whole plan
  - An instruction injected into a payment memo made the model propose a transfer to an unknown wallet; the plan was rejected whole and the fallback still funded payroll — pinned as a regression test among **154 passing pytest cases**
  - Paid its own Gemini inference over **x402** and fed that cost back into the next cycle's forecast

- 🔬 **[OfficeQA Agent](https://github.com/rhy2301/sentient-arena)** — grounded reasoning over 697 documents `Jun – Sep 2026`
  <br>Answers precise numerical questions from 697 U.S. Treasury Bulletin issues spanning 1939–2025.
  <br>Solo · Sentient Arena, Challenge 0 · prompt, skill and MCP design
  - Iterated across seven versions: **score 0 → 43.4**, **54.3%** of tasks solved
  - Diagnosed **fabrication as the dominant failure mode** and rebuilt extraction so every number used in a computation must appear in the session's own stdout first
  - Found **MCP had near-zero ROI with this harness** and dropped it — the MCP-only version scored 0, minimal prompt + shell scored 42

- 🛰️ **Solana Transaction-Path Research** — ISS Lab, Korea University `Sep 2025 – Jun 2026`
  <br>Traced how a transaction travels from wallet to leader by reading the [`anza-xyz/agave`](https://github.com/anza-xyz/agave) source instead of trusting explorers.
  <br>Undergraduate research intern · RPC node setup and source-level analysis
  - Set up a Solana RPC node from the Agave client on **testnet and devnet**
  - RPC `SendTransactionService` holds pending transactions in a **HashMap with no priority ordering**; `ForwardingStage` sorts with a MinMaxHeap; the leader's `BankingStage` **recomputes priority anyway**
  - Prototyped a Rust transaction-filtering module integrated into Agave's forwarding path

- 💵 **[StableHedge](https://github.com/StableHedge/stablehedge)** — XRPL dividend settlement dashboard `May 2026`
  <br>B2B infrastructure settling quarterly dividends for overseas real-estate funds atomically on XRPL.
  <br>5-person team · frontend — all three dashboard screens · KFIP 2026 (XRPL Korea × Seoul Fintech Lab)
  - Investor payout table with search, status filters, five sort modes and address truncation
  - Two-step `Calculate → Submit` flow with a confirmation modal and post-submit refresh
  - Shared typed DTOs with the backend through the monorepo, so an API change **fails at compile time**
  - Worked in feature branches across **14 pull requests**

- 📱 **[Phonesonal-Trainer](https://github.com/Phonesonal-Trainer/iOS)** — AI fitness coaching iOS app `Jul – Aug 2025`
  <br>Weekly meal plans and workout routines with logging and reports.
  <br>3-person team · owned the meal-plan and workout modules · API client layer
  - Fixed **timer drift** across pause/resume by computing elapsed time from timestamps instead of counting ticks
  - Multipart image upload, Bearer-token request layer, weekly calendar component

- 🔒 **온결 (Ongyeol)** — conservation history for Korean paintings `2026 – in progress`
  <br>AI damage screening before and after a loan, with each record's hash written on-chain so the history cannot be altered.
  <br>Capstone · 3-person team · backend & blockchain
  - Design locked, implementation underway through Mar 2027 · Spring Boot

---

## Highlights

**Reading the source instead of trusting the surface**
- Solscan shows activity labels as if they were on-chain facts; they are **generated by the indexer**, not stored on chain
- A transaction's entry path **leaves no on-chain trace** — the sender's socket address lives only in the in-memory `Packet.meta`
- SWQoS looks like a protocol guarantee, but RPC–validator trust comes from a **stake-override agreed off-chain** — a social contract, not something the protocol enforces

**Letting an LLM touch money safely**
- The object that moves funds is constructible only inside the policy gate, so its existence carries the guarantee
- Kept devnet transfers and localnet payments strictly apart, and **never generated an explorer link for a signature nobody can verify publicly**

**Finding out which ideas don't survive**
- Dropped a two-server MCP retrieval design after it scored near zero, and said so in the repo rather than quietly deleting it
- Dropped DID from the capstone after an advisor asked what it actually added — kept institution-granted write permission instead
- Treated one- and two-question score swings as sampling noise, which kept the work pointed at extraction rather than rephrasing

---

## Stack

**Languages**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Swift](https://img.shields.io/badge/Swift-F05138?style=flat-square&logo=swift&logoColor=white)
![Java](https://img.shields.io/badge/Java-437291?style=flat-square&logo=openjdk&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![Solidity](https://img.shields.io/badge/Solidity-363636?style=flat-square&logo=solidity&logoColor=white)

**Frontend & Mobile**
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![SwiftUI](https://img.shields.io/badge/SwiftUI-F05138?style=flat-square&logo=swift&logoColor=white)

**Backend & Testing**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![mypy](https://img.shields.io/badge/mypy-6E7781?style=flat-square)
![Ruff](https://img.shields.io/badge/Ruff-D7FF64?style=flat-square&logo=ruff&logoColor=black)

**Blockchain**
![Solana](https://img.shields.io/badge/Solana-9945FF?style=flat-square&logo=solana&logoColor=white)
![XRPL](https://img.shields.io/badge/XRPL-0085C0?style=flat-square&logo=ripple&logoColor=white)
![SPL Token](https://img.shields.io/badge/SPL_Token-6E7781?style=flat-square)
![x402](https://img.shields.io/badge/x402-6E7781?style=flat-square)

**AI & Agents**
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![MCP](https://img.shields.io/badge/Model_Context_Protocol-6E7781?style=flat-square)
![Goose](https://img.shields.io/badge/Goose-6E7781?style=flat-square)
![OpenRouter](https://img.shields.io/badge/OpenRouter-6E7781?style=flat-square)

**Tools**
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Xcode](https://img.shields.io/badge/Xcode-147EFB?style=flat-square&logo=xcode&logoColor=white)
![pnpm](https://img.shields.io/badge/pnpm-F69220?style=flat-square&logo=pnpm&logoColor=white)

---

## Other Repositories

| Repository | What it is |
| --- | --- |
| [24ECC_algorithm](https://github.com/rhy2301/24ECC_algorithm) | Weekly algorithm study records (Baekjoon), 2024–25 |

---

## Education

- **Ewha Womans University** — B.S. in Computer Science & Engineering, expected Aug 2027 · Academic Excellence Scholarship (Spring 2026)
- **EwhaChain** (university blockchain club) — Vice President & dApp Team Lead, 18th cohort, Sep 2026 – present 
