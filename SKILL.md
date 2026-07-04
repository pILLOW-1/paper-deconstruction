---
name: paper-deconstruction
description: "Deconstruct academic papers using a structured framework for top-tier conference writing (ICML/NeurIPS/ICLR). Analyzes papers across 7 dimensions: problem clarity, principle transition, key observation, method motivation, experimental rigor, computational resource analysis, and future research directions. Use when reviewing papers for writing quality, preparing literature reviews, learning from accepted papers, or improving your own paper drafts."
---

# Paper Deconstruction Framework

Deconstruct papers using the "问题→原理→方法→证据" (Problem→Principle→Method→Evidence) closed-loop framework. The goal is to evaluate whether a paper tells a complete scientific story, not just presents a method.

## Core Principle

> Top conference papers are NOT "method manuals" but "evidence chains for scientific claims."

A competitive paper must close a loop:
1. Problem and challenge are real and important
2. Something motivates thinking about the principle
3. A new principle or key observation is proposed
4. Method naturally follows from the principle
5. Experiments solidly support all claims

## Seven-Dimension Analysis

### 1. Problem & Challenge (问题与挑战)

Evaluate whether the problem is specific, important, and verifiable.

**Three-layer structure:**
- **Task layer**: What task? Input/output? Settings?
- **Challenge layer**: What's the key difficulty? Why existing methods fail?
- **Evidence layer**: Can the challenge be demonstrated via experiments, counterexamples, or theory?

**Key questions:**
- Is the problem concrete (not "existing methods perform poorly in complex scenarios")?
- Is there a motivating experiment showing the challenge exists?
- Can the failure mode be systematically demonstrated?

**Template for problem statement:**
> Existing methods achieve good results on ___ task, but rely on ___ assumptions. We find that when this assumption is violated in ___ scenarios, performance degrades significantly. Analysis shows the key failure is not simply model capacity, but ___. This indicates the core challenge is ___.

### 2. Challenge → Principle Transition (从挑战到原理)

Evaluate whether the transition from challenge to insight is natural, not abrupt.

**Four motivation sources:**
- **Failure mode driven**: Methods fail under ___ conditions but work under ___ conditions, suggesting the real problem is ___ not ___
- **Comparative observation driven**: While ___ varies across models/data, ___ remains stable, making it a more reliable signal
- **Theoretical gap driven**: Existing methods implicitly depend on ___ assumption, but target scenarios don't satisfy it
- **Diagnostic experiment driven**: A controlled experiment shows changing ___ significantly affects performance, while changing ___ has little effect

**Key question:** Is there a "bridge" explaining why this challenge naturally leads to this principle?

**Template for transition:**
> The above analysis shows the challenge is real and suggests a potential breakthrough. Specifically, we observe that when ___ is violated, methods degrade明显; but when ___ is preserved, performance remains stable. This leads us to think: what truly affects ___ may not be ___, but ___. Therefore, we investigate whether ___ can be a key mechanism.

### 3. Principle / Key Observation (原理或关键观察)

Evaluate whether there's a new understanding, not just a new module.

**Innovation types:**
- New understanding or phenomenon
- New theoretical explanation
- New problem decomposition
- New stable signal source

**Key requirements:**
- Must be verifiable
- Must explain why it relates to the challenge
- Must explain how it can alleviate the challenge
- Must produce testable consequences

**Template:**
> Our core observation is: although ___ varies明显 across different ___, ___ remains relatively stable. This means relying directly on ___ causes generalization difficulties, while using ___ may alleviate the problem. Based on this, we propose a testable hypothesis: if ___ is indeed the key factor, then enhancing ___ should improve ___; conversely, when we destroy ___, this improvement should weaken.

### 4. Method Motivated by Principle (方法由原理导出)

Evaluate whether each module has a clear motivation from the principle.

**For each key module, answer three questions:**
1. What specific problem does it solve?
2. How does it implement the principle/observation?
3. What degradation happens when removed?

**Complexity assessment:**

| Method State | How to Strengthen |
|--------------|-------------------|
| Complex method, weak story | Don't add modules; strengthen motivation, mechanism analysis, ablation |
| Simple method, strong insight | Don't add complexity for complexity's sake; emphasize new observation/problem/theory |
| Simple method, weak insight | Need elevation: redefine problem, dig mechanism, add theory, design distinguishing experiments |
| Complex method, weak experiments | Highest risk; remove modules, strengthen baselines, prove each module necessary |

**Template:**
> The method aims to operationalize the above observation. Module A addresses ___ by ___; Module B preserves or enhances ___ by ___; Module C controls ___ to ensure effectiveness under ___ conditions. Each module corresponds to a specific failure mode identified earlier, so the entire method is naturally derived from the core observation, not empirically stacked.

### 5. Experimental Rigor (实验论证)

Evaluate whether experiments support each claim systematically.

**Four required experiment types:**

| Type | Proves What | Common Forms |
|------|-------------|--------------|
| Main results | Method is effective overall | Compare with strong baselines / SOTA |
| Ablation | Each module is necessary | Remove / replace / simplify modules |
| Mechanism | Principle/observation holds | Controlled setting, correlation, perturbation, synthetic test |
| Robustness & cost | Method is stable and worth using | Seeds, variance, efficiency, hyperparameter sensitivity |

**Key principle:** Design experiments around claims, not around table count. If you claim X, design experiments to support X. If you propose a principle, design experiments to verify it.

**Common gaps to check:**
- Only main results, no mechanism analysis?
- No significance or variance reporting?
- No robustness verification?
- Alternative explanations not ruled out (larger model, more compute, lucky seeds)?

### 6. Computational Resource Analysis (计算资源分析)

Evaluate whether the paper provides clear, actionable information about resource requirements.

**Three-layer structure:**
- **Cost layer**: API costs, training costs, total experiment budget
- **Hardware layer**: GPU type/quantity, CPU requirements, memory needs
- **Efficiency layer**: Cost per improvement, evaluation efficiency, scaling behavior

**Key questions:**
- Are API costs clearly reported (model, tokens, total $)?
- Are hardware requirements specified (GPU model, count, training time)?
- Is the cost-effectiveness compared with baselines?
- Are scaling costs estimated (what happens with more agents/longer runs)?
- Is the entry barrier clear (what's needed to reproduce)?

**Cost breakdown template:**

| Component | Cost | Percentage | Notes |
|-----------|------|------------|-------|
| LLM API calls | $X | ~Y% | Model name, tokens |
| Training/compute | $X | ~Y% | GPU hours × price |
| Evaluation | $X | ~Y% | Per-eval cost × count |
| Infrastructure | $X | ~Y% | Storage, networking |
| **Total** | **$X** | **100%** | For paper results |

**Hardware requirements template:**

| Task Type | GPU Needed | GPU Count | Training Time | Inference Time |
|-----------|------------|-----------|---------------|----------------|
| Task A | Model X | N | T hours | t seconds |
| Task B | None (CPU) | 0 | - | t seconds |

**Scaling analysis template:**

| Configuration | Cost | Performance | Cost per Improvement |
|---------------|------|-------------|---------------------|
| 1 agent, 3h | $X | Score Y | $Z per point |
| 4 agents, 3h | $X | Score Y | $Z per point |
| 4 agents, 24h | $X | Score Y | $Z per point |

**Comparison with related work:**

| Method | Primary Cost | GPU Needed | Total Cost | Cost Efficiency |
|--------|-------------|------------|------------|-----------------|
| This paper | API/Training | Yes/No | $X | Score/$ |
| Baseline A | API/Training | Yes/No | $X | Score/$ |
| Baseline B | API/Training | Yes/No | $X | Score/$ |

**Common gaps to check:**
- API costs not reported (only "we used GPT-4")?
- GPU requirements vague ("single A100" without count/time)?
- No cost comparison with baselines?
- Scaling behavior not analyzed?
- Entry barrier unclear (can a student reproduce this)?

### 7. Future Research Directions (未来研究方向)

Evaluate whether the paper identifies meaningful next steps and research opportunities.

**Three-layer structure:**
- **Limitation layer**: What does the paper explicitly identify as limitations?
- **Extension layer**: What logical extensions naturally follow from the contributions?
- **Field layer**: How does this work connect to broader trends and open problems?

**Key questions:**
- Does the paper honestly discuss its limitations (not just boilerplate)?
- Are the suggested future directions specific and actionable?
- Are there research opportunities the paper misses?
- How does this work connect to the broader research landscape?
- What would be the highest-impact follow-up work?

**Limitation analysis template:**

| Limitation | Impact | Future Direction | Priority |
|------------|--------|------------------|----------|
| [Stated limitation 1] | [How it limits the work] | [Specific direction to address it] | P0/P1/P2 |
| [Stated limitation 2] | [How it limits the work] | [Specific direction to address it] | P0/P1/P2 |
| [Unstated limitation] | [Gap in the paper] | [How to address it] | P0/P1/P2 |

**Extension direction template:**

| Direction | Based On | Method | Expected Contribution |
|-----------|----------|--------|----------------------|
| [Direction 1] | [Paper finding/limitation] | [Approach] | [What it would achieve] |
| [Direction 2] | [Paper finding/limitation] | [Approach] | [What it would achieve] |

**Cross-field connection template:**

| Related Work | Connection Point | Research Opportunity |
|--------------|------------------|---------------------|
| [Paper A] | [Shared challenge/method] | [Combined direction] |
| [Paper B] | [Complementary approach] | [Integration opportunity] |

**Priority assessment:**

| Direction | Scientific Value | Feasibility | Impact | Recommendation |
|-----------|-----------------|-------------|--------|----------------|
| Direction 1 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐⭐ | P0 (highest) |
| Direction 2 | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐☆ | P1 (high) |
| Direction 3 | ⭐⭐⭐☆☆ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐☆☆ | P2 (medium) |

**Template for limitation discussion:**
> While [method] has proved effective, several limitations remain. First, [limitation 1], which means [impact]. An exciting direction for future work is [specific direction]. Second, [limitation 2], suggesting [direction]. Third, [limitation 3], which could be addressed by [approach].

**Template for extension directions:**
> Building on our findings, several promising directions emerge: (1) [Direction 1], which would [benefit] by [approach]; (2) [Direction 2], extending [current work] to [new domain]; (3) [Direction 3], addressing [open problem] through [method].

**Common gaps to check:**
- Only boilerplate limitations ("future work will...")?
- No connection to broader research trends?
- Missing high-impact follow-up directions?
- No priority assessment of directions?
- Limitations not honest or complete?

## Self-Check Checklist

1. Does the paper identify a specific, important problem (not vague pain points)?
2. Is the challenge proven to exist via experiments, cases, or theory?
3. Is the transition from challenge to principle clearly motivated?
4. Is there a new principle/observation/mechanism (not just a new module)?
5. Is the method naturally derived from the principle? Can each module answer "why is it needed"?
6. Do experiments correspond to each claim? Are there main results, ablation, mechanism verification, and robustness analysis?
7. Are alternative explanations ruled out (larger parameters, more training budget, seed偶然性, hyperparameter advantage)?
8. Are limitations, applicable scope, and failure cases honestly described?
9. Does the whole paper clearly answer: what problem, why important, why method works, why believe results?
10. Are computational resources clearly reported (API costs, hardware, total budget)?
11. Is cost-effectiveness compared with baselines?
12. Is the entry barrier clear (can others reproduce this work)?
13. Does the paper honestly discuss limitations (not just boilerplate)?
14. Are future research directions specific and actionable?
15. Does the paper connect to broader trends and identify high-impact opportunities?

## Output Format

Structure the analysis as:

```
# [Paper Title] Deconstruction

## Overall Assessment
Brief summary of paper quality across 7 dimensions.

## 1. Problem & Challenge
- Problem specificity: [rating]
- Challenge evidence: [rating]
- Key findings: [summary]

## 2. Challenge → Principle Transition
- Transition quality: [rating]
- Motivation source: [failure mode / comparative / theoretical / diagnostic]
- Key findings: [summary]

## 3. Principle / Key Observation
- Observation clarity: [rating]
- Verifiability: [rating]
- Key findings: [summary]

## 4. Method Motivation
- Module-principle alignment: [rating]
- Complexity assessment: [appropriate / over-complex / under-complex]
- Key findings: [summary]

## 5. Experimental Rigor
- Main results: [adequate / insufficient]
- Ablation: [adequate / insufficient]
- Mechanism verification: [adequate / insufficient]
- Robustness: [adequate / insufficient]
- Key findings: [summary]

## 6. Computational Resource Analysis
- Cost clarity: [adequate / insufficient]
- Hardware transparency: [adequate / insufficient]
- Cost-effectiveness: [adequate / insufficient]
- Entry barrier: [low / medium / high]
- Key findings: [summary]

## 7. Future Research Directions
- Limitation honesty: [adequate / insufficient]
- Direction specificity: [adequate / insufficient]
- Field connection: [adequate / insufficient]
- Priority assessment: [present / missing]
- Key findings: [summary]

## Self-Check Results
Table with 15 checklist items and ratings.

## Highlights & Lessons
What this paper does well and what can be learned.

## Improvement Suggestions
Specific recommendations for the paper.

## Future Research Opportunities
Top 3-5 specific, actionable research directions with priority assessment.
```

## References

See [references/framework.md](references/framework.md) for the complete framework with detailed templates and examples.
