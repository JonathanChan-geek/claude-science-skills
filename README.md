# Claude Science Skills

Anthropic **Claude Science** 桌面客户端（v0.1.56, windows-x64, build 2026-10-02）内置的全部 **29 个 Agent Skill** 原文，从客户端二进制中提取。

每个技能都是一个自包含的目录：`SKILL.md`（frontmatter + 指令正文）加上可选的 `references/`（按需加载的二级文档）、`kernel.py`（注入宿主内核的辅助函数）、`envs/*.py`（远程 GPU 环境构建脚本）与 `provider.py`（算力提供方适配层）。共 **80 个文件 / 808 KB**。

---

## 结构预测与生物学基础模型

| 技能 | 说明 | 许可 | 文件 |
|---|---|---|---|
| [`alphafold2`](skills/alphafold2/) | Predict protein structure for monomers and multimers with AlphaFold2 via the ColabFold runner (Mirdita et al. 2022, github.com/sokrypton/ColabFold;… | Apache-2.0 | 1 |
| [`boltz`](skills/boltz/) | Structure prediction for protein, nucleic-acid, and small-molecule complexes with Boltz-2 (Passaro & Wohlwend et al. 2025,… | Apache-2.0 | 1 |
| [`chai1`](skills/chai1/) | Structure prediction for protein, nucleic-acid, and small-molecule complexes with the Chai-1 foundation model (Chai Discovery 2024,… | Apache-2.0 | 1 |
| [`openfold3`](skills/openfold3/) | Structure prediction using OpenFold3, an open-weights PyTorch reproduction of AlphaFold3 from the AlQuraishi Lab. Use this skill when predicting… | Apache-2.0 | 1 |
| [`esmfold2`](skills/esmfold2/) | Biohub ESMFold2 / ESMFold2-Fast all-atom co-folding (Candido et al. 2026, github.com/Biohub/esm). Single-sequence and MSA modes; protein, DNA, RNA,… | Apache-2.0 | 3 |
| [`fair-esm2`](skills/fair-esm2/) | Embed proteins with Meta AI's ESM-2 (`fair-esm` package). Use this skill when: (1) Extracting per-residue or per-sequence embeddings for downstream… | Apache-2.0 | 1 |
| [`borzoi`](skills/borzoi/) | Predict genome-wide functional tracks (RNA-seq, CAGE, DNase, ChIP) from DNA sequence with Borzoi. Use this skill when: (1) Scoring the regulatory… | Apache-2.0 | 1 |
| [`evo2`](skills/evo2/) | Score, embed, and generate DNA sequences with Evo 2, a long-context genomic foundation model. Use this skill when: (1) Computing per-nucleotide or… | Apache-2.0 | 1 |
| [`proteinmpnn`](skills/proteinmpnn/) | Inverse-fold a protein backbone (PDB structure) into amino-acid sequence with ProteinMPNN (Dauparas et al. 2022, github.com/dauparas/ProteinMPNN).… | Apache-2.0 | 1 |
| [`ligandmpnn`](skills/ligandmpnn/) | Inverse-fold a backbone with ligand, nucleic-acid, and metal context using LigandMPNN (Dauparas et al. 2023, github.com/dauparas/LigandMPNN). Reach… | Apache-2.0 | 1 |
| [`solublempnn`](skills/solublempnn/) | Inverse-fold a backbone with SolubleMPNN — ProteinMPNN retrained on a soluble-PDB subset (Dauparas et al. 2022) — for sequences biased toward… | Apache-2.0 | 1 |
| [`diffdock`](skills/diffdock/) | Predict small-molecule binding poses with DiffDock-L (Corso et al. 2023/2024, github.com/gcorso/DiffDock) — blind diffusion docking that places a… | Apache-2.0 | 2 |
| [`scgpt`](skills/scgpt/) | Embed and annotate single-cell expression data with scGPT, a foundation model for single-cell biology. Use this skill when: (1) Producing cell… | Apache-2.0 | 1 |
| [`scvi-tools`](skills/scvi-tools/) | Probabilistic single-cell RNA-seq with scvi-tools — scVI for a batch-corrected latent space, scANVI for semi-supervised label transfer, and Bayesian… | Apache-2.0 | 2 |

## 文献、调研与科研写作

| 技能 | 说明 | 许可 | 文件 |
|---|---|---|---|
| [`indication-dossier`](skills/indication-dossier/) | Generate a therapeutic indication dossier. Covers the patient population, epidemiology, disease biology, standard of care, regulatory precedent, and… | Apache-2.0 | 9 |
| [`literature-review`](skills/literature-review/) | Find, verify, and synthesize scientific literature — from "what's the seminal paper for X" through full multi-source reviews. Covers grounding claims… | Apache-2.0 | 2 |
| [`paper-narrative`](skills/paper-narrative/) | Judge and reshape the STORY a paper's figures tell. Input is the work itself — manuscript (or abstract) + figure deck — no hand-written brief.… | Apache-2.0 | 2 |
| [`pdf-explore`](skills/pdf-explore/) | Use this skill when the user has attached a PDF, paper, report, or other document and the answer needs content from more than one place in it:… | Apache-2.0 | 2 |

## 图表

| 技能 | 说明 | 许可 | 文件 |
|---|---|---|---|
| [`figure-composer`](skills/figure-composer/) | Compose one publication-grade multi-panel figure. Entry from a one-line claim + data refs, OR from an existing figure via `derive_outline(png)`. Runs… | Apache-2.0 | 2 |
| [`figure-style`](skills/figure-style/) | Publication-grade figure correctness and legibility rules for final-deliverable figures — not every plot. Quick look or iterating on the analysis… | Apache-2.0 | 2 |

## 计算环境与模型端点

| 技能 | 说明 | 许可 | 文件 |
|---|---|---|---|
| [`compute-env-setup`](skills/compute-env-setup/) | Set up a compute environment on a remote provider so Claude Science jobs can run there. Covers direct SSH/conda hosts, Slurm clusters,… | Apache-2.0 | 2 |
| [`remote-compute-modal`](skills/remote-compute-modal/) | Run GPU jobs on the user's own Modal account via host.compute.create('modal', provider_params={...}) — the create→submit→wait_for_notification flow,… | Apache-2.0 | 15 |
| [`remote-compute-ssh`](skills/remote-compute-ssh/) | Submit→wait_for_notification→collect-outputs workflow for the user's SSH/SLURM hosts. Load once you've decided to dispatch remote. | Apache-2.0 | 1 |
| [`managed-model-endpoints`](skills/managed-model-endpoints/) | Register a model service in the managed family — a local model server container the daemon starts/stops on demand, or a remote upstream model API… | Apache-2.0 | 1 |
| [`using-model-endpoint`](skills/using-model-endpoint/) | Call a registered model endpoint over its native HTTP API from the endpoint's scoped inference kernel (BASE_URL preloaded). Load once a task needs… | Apache-2.0 | 4 |

## 元技能与自我认知

| 技能 | 说明 | 许可 | 文件 |
|---|---|---|---|
| [`skill-creator`](skills/skill-creator/) | Create new skills, modify and improve existing skills, and measure skill performance. Use when users want to create a skill from scratch, edit, or… | Apache-2.0 | 17 |
| [`customize`](skills/customize/) | Create, configure, and maintain custom agent profiles and author new skills via the `repl` tool. Use when the user wants to create an agent profile,… | Apache-2.0 | 1 |
| [`self-awareness`](skills/self-awareness/) | Claude Science's own session database schema and SDK surface for introspection via host.query(). Load this when you need to query your own… | Apache-2.0 | 1 |
| [`product-self-knowledge`](skills/product-self-knowledge/) | Stop and consult this skill whenever your response would include specific facts about Anthropic's products. Covers: Claude Code (how to install,… | Apache-2.0 | 1 |

---

## 技能写作约定

被 harness 识别为技能的关键是 `SKILL.md` 顶部的 YAML frontmatter：

```yaml
---
name: <slug>              # 必须与目录名一致，模型用 skill({skill:"<slug>"}) 调用
description: >            # 一段话说明「什么时候该用这个技能」，是检索语料
license: Apache-2.0
category: biomodels       # 可选分组
requirements: [gpu]       # 可选，声明硬件需求
metadata:
  display-name: AlphaFold2
  third_party:            # 可选，逐个列出上游权重/服务的许可
    - kind: weights
      name: AlphaFold2
      license: CC BY 4.0
---

# 正文标题

指令正文 ……
```

几个值得注意的约定：

- **`description` 决定可发现性。** 运行时的检索是 `BM25 + Jaccard` 双通道 RRF 融合（阈值 0.029），命中后技能会以 `<skill_discovery>` 块注入到对话里。`description` 要写「什么场景下该用」，而不是「这个技能是什么」。
- **`kernel.py` 会被注入宿主内核，且在装载前要过一道 Python AST 白名单校验**；它只导出零星辅助函数（例如 `scvi-tools` 只导出 `h5ad_safe_obs`）。
- **`references/` 是二级文档，不随技能一起注入**，只在需要时由模型显式读取，用来把 `SKILL.md` 控制在一屏之内。
- **模型类技能普遍不打包权重**，而是在运行时 `git clone` / 拉取，并在 `metadata.third_party` 里声明上游许可。

## 值得优先读的几个

| 技能 | 为什么值得看 |
|---|---|
| [`indication-dossier`](skills/indication-dossier/) | 唯一的**多阶段医学研究方法论**：5 个阶段 + 8 个可续跑 waypoint 文件，核心是反造假协议——每条 finding 强制带 `source_url` / `source_type` / `quote` 三字段，禁止构造 URL，查不到必须写 "Not publicly available" 并记入 `anomaly_flags` |
| [`literature-review`](skills/literature-review/) | 文献综述的落地实现：Crossref `update-to` 撤稿字段校验、doi.org HEAD 404 判定、确定性文本 lint（不走 LLM） |
| [`pdf-explore`](skills/pdf-explore/) | 把 PDF 当数据集扫的工程做法：页级 fan-out、批量上限 512 页、渲染图缓存，页级任务一律 pin Haiku 以控成本 |
| [`skill-creator`](skills/skill-creator/) | Anthropic 自己写技能的脚手架：评测循环、评分器、校验与打包脚本全在这里 |
| [`remote-compute-modal`](skills/remote-compute-modal/) | 10 个真实 Modal GPU 环境定义 + 4 万行 provider 适配层，展示远程算力是怎么接进 Agent 的 |
| [`figure-style`](skills/figure-style/) | 期刊级绘图规范的具体落地：全部约束用 matplotlib `rcParams` 表达，区分 correctness 与 aesthetics 两层 |

---

## 来源与完整性

提取自 `Claude-Science-0.1.56.exe`（PE32+ x64）末尾 `.bun` 节内嵌的 `assets.tar` —— 该安装包是 Bun 单文件编译产物，资源以未加密 tar 形式携带。

```
Claude-Science-0.1.56.exe
  └─ .bun 节 (72.3 MB)
       ├─ B:/~BUN/root/claude-science.exe   13.2 MB  harness 主 bundle
       └─ B:/~BUN/root/assets.tar-*.gz      57.7 MB → 128 MB tar
            └─ skills/                       ← 本仓库内容
```

技能文件为**逐字节原文**，未做任何改写。`MANIFEST.json` 记录每个文件的 sha256 与字节数，以及每个技能的 frontmatter 元数据，可用于校验完整性。

> 技能内容版权归 Anthropic 所有，各技能 frontmatter 的 `license` 字段（多为 `Apache-2.0`）与 `metadata.third_party` 中的上游声明为准；模型权重与服务另受各自上游许可约束，见 [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)。
