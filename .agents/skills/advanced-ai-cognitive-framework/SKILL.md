---
name: advanced-ai-cognitive-framework
description: Use this skill to analyze AI-generated content, research, reports, plans, decisions, prompts, or workflows that require fact/inference separation, uncertainty handling, hallucination control, source verification, context engineering, reasoning decomposition, human review, or AI governance. Do not use it for simple creative writing where factual reliability is irrelevant.
---

# Advanced AI Cognitive Framework

## Mission

Apply a rigorous AI cognition and reliability workflow. Do not merely generate a fluent answer. Build a traceable path from task definition to evidence, reasoning, verification, risk, and action.

## Trigger Conditions

Use this skill when the task involves one or more of the following:

- explaining why AI may be wrong
- reviewing AI-generated claims
- checking factual reliability
- designing prompts or context
- research, reports, teaching materials, or strategic analysis
- high-stakes medical, legal, financial, security, policy, or compliance content
- agent workflows, RAG, memory, tools, or multi-agent systems
- converting an idea into a repeatable Codex workflow
- identifying hallucinations, unsupported claims, or hidden assumptions

Do not trigger for:

- purely fictional writing
- casual brainstorming with no factual claims
- basic formatting or translation where the source text is authoritative
- trivial coding edits unrelated to reasoning quality

## Required Operating Model

Treat the task through the following layers:

1. **Probability** — model output is generated, not automatically verified.
2. **Patterns** — fluent patterns may not equal correct meaning.
3. **Context** — missing or conflicting context changes the answer.
4. **Prompt** — vague goals and constraints increase error.
5. **Reasoning** — decompose complex tasks and expose assumptions.
6. **Tools** — identify what requires external search, code, files, or APIs.
7. **Memory** — separate stable user context from temporary task details.
8. **Retrieval** — obtain current or domain-specific evidence.
9. **Multi-agent review** — use independent critique when stakes justify it.
10. **Human judgment** — preserve accountable human decisions.
11. **Governance** — address privacy, security, compliance, bias, and auditability.
12. **Operationalization** — turn successful work into reusable instructions and checks.

For detailed definitions, read `references/FRAMEWORK.md`.

## Mandatory Workflow

### Step 1 — Define the task

Write a compact task contract:

```text
Goal:
Audience:
Decision or deliverable:
Scope:
Constraints:
Required freshness:
Risk level:
Done when:
```

If critical information is missing, ask only the minimum necessary questions. Otherwise, state reasonable assumptions explicitly and proceed.

### Step 2 — Build a claim map

Classify every load-bearing statement:

- `FACT` — directly supported by evidence
- `INFERENCE` — logically derived from evidence
- `ASSUMPTION` — accepted temporarily without proof
- `UNKNOWN` — cannot be determined from available information
- `OPINION` — subjective judgment
- `RECOMMENDATION` — proposed action tied to a goal

Never silently promote an assumption into a fact.

### Step 3 — Assess context quality

Check:

- Is the objective precise?
- Are key terms defined?
- Is the date or time range known?
- Is the jurisdiction or market known?
- Are the audience and use case known?
- Are source files complete?
- Are constraints contradictory?
- Is there a desired format and acceptance test?

Label context quality:

```text
HIGH: sufficient for reliable execution
MEDIUM: usable with stated assumptions
LOW: likely to produce material error
```

### Step 4 — Select the evidence strategy

Choose the minimum adequate strategy:

| Task | Minimum evidence |
|---|---|
| Stable general concept | established references |
| Current event/product/software | current official source |
| Research claim | original paper or authoritative review |
| Legal/regulatory | current official law/regulator |
| Medical/health | guideline, regulator, or peer-reviewed evidence |
| Financial decision | current filings/data plus uncertainty |
| Internal project | repository files and explicit user context |

Do not invent citations. Do not cite a source that was not actually inspected.

### Step 5 — Decompose reasoning

For complex tasks, create:

```text
Question
├── Subproblem A
├── Subproblem B
├── Subproblem C
└── Integration criteria
```

For each subproblem, record:

- evidence needed
- assumptions
- method
- failure modes
- verification method

Do not reveal private hidden chain-of-thought. Provide concise, auditable reasoning summaries, decision criteria, calculations, and evidence links.

### Step 6 — Run verification

Use the protocol in `references/RELIABILITY_PROTOCOL.md`.

At minimum:

1. check source relevance
2. check source date
3. check claim-source alignment
4. check contradictory evidence
5. check units, numbers, and definitions
6. check whether the conclusion exceeds the evidence
7. distinguish absence of evidence from evidence of absence

For high-risk work, require independent verification or human review.

### Step 7 — Produce the answer

Default output:

```markdown
## 任務定義

## 核心結論

## 已知事實

## 推論與假設

## 資訊缺口

## 查證與證據

## 分析／方案

## 風險與限制

## 信心等級

## 下一個最佳行動
```

Use the detailed templates in `references/OUTPUT_TEMPLATES.md` when appropriate.

### Step 8 — Perform a final quality gate

Before completion, verify:

- [ ] No unsupported claim is presented as fact.
- [ ] Current claims use current sources.
- [ ] Important uncertainty is visible.
- [ ] Recommendations are linked to goals and evidence.
- [ ] High-risk decisions retain human review.
- [ ] The output format matches the request.
- [ ] Completion criteria are satisfied.
- [ ] No action, test, citation, or file change is falsely claimed.

## Confidence Scale

Use one of:

- **High** — strong, directly relevant evidence; low contradiction
- **Medium** — reasonable evidence with material limitations
- **Low** — sparse, indirect, outdated, or conflicting evidence
- **Not assessable** — insufficient evidence

Confidence is not a probability unless a quantitative method was actually used.

## Risk Levels

### Low

Examples: brainstorming, teaching analogy, internal outline.

Action: basic claim separation.

### Medium

Examples: market analysis, business plan, public educational content.

Action: source verification, limitations, review checklist.

### High

Examples: medical, legal, financial, cybersecurity, regulatory, safety-critical.

Action:

- current authoritative sources
- stronger source hierarchy
- explicit uncertainty
- independent or human review
- no autonomous final decision

## Anti-Hallucination Rules

- Say “unknown” when information is unavailable.
- Never create a plausible but unverified citation.
- Never imply that a command, test, upload, commit, or review occurred unless it actually occurred.
- Do not infer private facts about a person without evidence.
- Do not rely on memory for potentially changed facts.
- Do not use fluent wording to conceal uncertainty.
- Do not equate repeated model answers with independent confirmation.
- Do not use synthetic examples as empirical evidence.

## Prompt Upgrade Pattern

When improving a prompt, rewrite it using:

```text
ROLE:
GOAL:
CONTEXT:
INPUTS:
SCOPE:
CONSTRAINTS:
EVIDENCE STANDARD:
PROCESS:
OUTPUT FORMAT:
QUALITY CHECK:
DONE WHEN:
```

Do not add role-play language unless it improves task performance.

## Codex Operational Pattern

For repository tasks:

1. inspect repository instructions
2. locate relevant files
3. summarize current state
4. plan changes
5. modify the smallest necessary set
6. run available checks
7. review the diff
8. report what changed and what remains uncertain

When a workflow repeats, recommend capturing it as a skill, reference, script, or `AGENTS.md` rule at the correct scope.

## Completion Response

End with a compact execution summary:

```text
Result:
Evidence status:
Confidence:
Human review required:
Files/actions completed:
Open issues:
```
