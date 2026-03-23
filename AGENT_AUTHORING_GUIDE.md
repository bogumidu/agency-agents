# Agent Authoring Guide

This guide captures the real structure patterns used across this repository and turns them into a practical standard for creating new agents.

## 1) Agent Definition Anatomy

Most successful agents in this repo follow this shape:

1. **Frontmatter** (machine-readable metadata)
2. **Identity section** (who the agent is)
3. **Mission section** (what it is responsible for)
4. **Rules section** (hard boundaries and non-negotiables)
5. **Deliverables or capabilities** (what it outputs)
6. **Workflow** (how it operates, step-by-step)
7. **Communication style** (how it talks and frames advice)
8. **Success metrics** (how quality is judged)
9. **Advanced capabilities** (optional depth)

You can use either a **full narrative format** (most files) or a **compact capability-first format** (some paid-media/sales files). Both are valid if they preserve clarity and boundaries.

## 2) Required vs Optional Frontmatter

### Required
- `name`
- `description`
- `color`

### Strongly recommended
- `emoji`
- `vibe`

### Optional (use only when needed)
- `tools`
- `services`
- `author`

### Frontmatter example

```yaml
---
name: Example Agent
description: One-line specialty and concrete outcome focus.
color: blue
emoji: 🧩
vibe: Turns ambiguity into executable plans.
tools: Read, Write, Edit
services:
  - name: Example API
    url: https://example.com
    tier: freemium
author: Jane Doe (@janedoe)
---
```

## 3) Section Naming Rules (Important for Converters)

The converter script classifies sections into persona/operations using header keywords.

To keep conversion reliable:
- Include headers containing at least these words where appropriate:
  - `Identity`
  - `Critical Rules` (or equivalent containing `Critical` + `Rules`)
  - `Communication Style`
- Keep mission/workflow/deliverables in separate headers.
- Avoid decorative or corrupted header text that removes recognizable keywords.

### Safe header variants
- `## 🧠 Your Identity & Memory`
- `## Identity & Memory`
- `## 🚨 Critical Rules You Must Follow`
- `## Critical Rules`
- `## 💬 Communication Style`
- `## 🎯 Your Core Mission`
- `## 🔄 Your Workflow Process`

## 4) What “Good” Looks Like in This Repo

### A. Strong specialization
- Narrow scope, deep expertise.
- Should be obvious when to use this agent vs another agent.

### B. Concrete outputs
- Include templates, checklists, code snippets, frameworks, or report formats.
- Replace generic promises with artifacts users can directly use.

### C. Explicit boundaries
- Rules should prevent common failure modes (scope creep, unsafe actions, weak evidence, etc.).
- Use direct, testable language.

### D. Operational process
- Include a clear sequence (discovery → planning → execution → review).
- Show decision points, not just a list of tasks.

### E. Measurable success
- Define specific metrics, thresholds, or completion criteria.
- Make quality observable.

### F. Distinct voice
- Keep a memorable but professional personality.
- Voice should influence decision quality, not just writing style.

## 5) Canonical Full Template

```markdown
---
name: [Agent Name]
description: [One-line specialty + outcome]
color: [color or #hex]
emoji: [emoji]
vibe: [one-line personality hook]
---

# [Agent Name] Agent

## 🧠 Your Identity & Memory
- **Role**: [specific role]
- **Personality**: [decision style]
- **Memory**: [what patterns it tracks]
- **Experience**: [domain depth]

## 🎯 Your Core Mission
- [responsibility + deliverable]
- [responsibility + deliverable]
- **Default requirement**: [always-on quality/safety behavior]

## 🚨 Critical Rules You Must Follow
- [hard boundary 1]
- [hard boundary 2]
- [hard boundary 3]

## 📋 Your Technical Deliverables
- [artifact type 1]
- [artifact type 2]
- [artifact type 3]

## 🔄 Your Workflow Process
1. [Phase 1]
2. [Phase 2]
3. [Phase 3]
4. [Phase 4]

## 💭 Your Communication Style
- [how it frames advice]
- [example phrasing]
- [tone constraints]

## 🔄 Learning & Memory
- [successful patterns]
- [failure patterns]
- [feedback loops]

## 🎯 Your Success Metrics
- [quantitative metric]
- [qualitative metric]
- [operational benchmark]

## 🚀 Advanced Capabilities
- [advanced method 1]
- [advanced method 2]
```

## 6) Compact Template (Valid Alternative)

Use this when the domain benefits from concise, operational docs.

```markdown
---
name: [Agent Name]
description: [One-line specialty + outcome]
color: [color or #hex]
emoji: [emoji]
vibe: [hook]
---

# [Agent Name] Agent

## Role Definition
[2-4 paragraphs describing role and quality bar]

## Core Capabilities
- [capability 1]
- [capability 2]
- [capability 3]

## Critical Rules You Must Follow
- [rule 1]
- [rule 2]

## Workflow Process
1. [step 1]
2. [step 2]
3. [step 3]

## Communication Style
- [style guideline]

## Success Metrics
- [metric 1]
- [metric 2]
```

## 7) New Agent Quality Checklist

Before opening a PR, verify:

- [ ] Frontmatter includes required fields (`name`, `description`, `color`)
- [ ] Scope is narrow and clearly differentiated
- [ ] Mission is outcome-based, not generic
- [ ] Rules include non-negotiable boundaries
- [ ] Deliverables are concrete and reusable
- [ ] Workflow is explicit and sequential
- [ ] Communication style is specific and useful
- [ ] Success metrics are measurable
- [ ] Section headers include recognizable keywords for converter compatibility
- [ ] File is tested in at least one realistic prompt scenario

## 8) Common Pitfalls to Avoid

- Generic assistant language (“I can help with anything”).
- Broad role overlap with existing agents.
- No concrete outputs, only philosophy.
- Rules that are aspirational but not enforceable.
- Metrics that cannot be measured.
- Header names so custom they break keyword-based conversion.

## 9) Example Prompt for Self-Testing a New Agent

Use this prompt against your new agent before submitting:

```text
Given this real-world task, produce:
1) a short plan,
2) one concrete deliverable artifact,
3) explicit trade-offs,
4) measurable success criteria,
5) top 3 risks and mitigations.

Task: [insert realistic task in the agent's domain]
```

If the output is vague, not actionable, or missing metrics, revise the agent definition.