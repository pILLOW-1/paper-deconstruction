# Paper Deconstruction Framework - Detailed Reference

## Complete Analysis Templates

### Problem Statement Templates

**Template 1: Failure-driven**
> Existing methods achieve ___ results on ___ task, but they typically rely on ___ assumptions. We find that once this assumption is violated in ___ scenarios, performance degrades significantly. Further analysis shows the key failure is not simply model capacity, but ___. This indicates the core challenge is ___.

**Template 2: Gap-driven**
> While ___ has made progress, it faces a fundamental challenge: ___. Current approaches address this by ___, but this leads to ___ limitations. A critical observation is that ___. This suggests the real bottleneck is ___.

**Template 3: Observation-driven**
> We observe a puzzling phenomenon: ___ varies significantly across ___, but ___ remains relatively stable. This stability suggests that ___ may be a more reliable signal than ___. However, current methods primarily rely on ___, which explains their ___ limitations.

### Transition Templates

**Template 1: From failure to insight**
> The above analysis not only shows the challenge exists but also reveals a potential breakthrough. Specifically, we observe that when ___ is destroyed, existing methods degrade明显; but when ___ is preserved or enhanced, performance remains stable. This leads us to think: what truly affects ___ may not be ___, but ___. Therefore, we further investigate whether ___ can serve as a key mechanism to alleviate this challenge.

**Template 2: From comparison to principle**
> Comparing successful and failed cases, we notice a pattern: ___ consistently correlates with success, while ___ shows no consistent relationship. This suggests that ___ is the true driver of ___. Building on this observation, we hypothesize that explicitly modeling ___ should improve ___.

**Template 3: From theoretical gap to new approach**
> Existing theory assumes ___, but in practice, ___ often holds. This mismatch explains why ___ methods fail in ___ scenarios. We propose a new framework that explicitly accounts for ___, which naturally leads to ___.

### Principle Statement Templates

**Template 1: Stability-based**
> Our core observation is: although ___ varies明显 across different ___, ___ remains relatively stable. This means relying directly on ___ causes generalization difficulties, while using ___ may alleviate the problem. Based on this, we propose a testable hypothesis: if ___ is indeed the key factor, then enhancing ___ should improve ___; conversely, when we destroy ___, this improvement should weaken.

**Template 2: Structure-based**
> We identify a structural property: ___ exhibits ___ characteristics that are invariant under ___. This invariance suggests that ___ can serve as a robust signal. Specifically, we show that ___ preserves this structure while ___ does not.

**Template 3: Decomposition-based**
> The key insight is that ___ can be decomposed into ___ and ___. While ___ is task-dependent and hard to optimize, ___ is more stable and can be explicitly modeled. This decomposition naturally suggests ___.

### Method Motivation Templates

**Module justification pattern:**
> **Module [Name]** addresses [specific failure mode] identified in Section [X]. It implements the principle of [principle] by [mechanism]. Without this module, [specific degradation], as verified in ablation study [Y].

**Example:**
> **Adaptive Temperature** addresses the overconfidence failure mode identified in Section 3.1. It implements the stability principle by dynamically scaling logits based on input uncertainty. Without this module, the model becomes overconfident on OOD inputs, degrading calibration by 15% (Table 3, row 3).

### Experiment Design Templates

**Main results statement:**
> We organize experiments around three questions: (1) Does the proposed method outperform strong baselines overall? (2) Is each key design necessary? (3) Do experimental phenomena support our mechanistic explanation? To answer these, we report main results, ablation studies, mechanism verification, and robustness analysis.

### Computational Resource Analysis Templates

**Cost breakdown statement:**
> We provide a detailed breakdown of computational costs. For a typical [duration] run on [task type], total API cost ranges from approximately $[X]–$[Y] USD. [Multi-agent runs / Training] incur approximately [N]× the single-agent cost. [Specific optimization] reduces costs by [percentage].

**Hardware requirements statement:**
> All experiments were conducted on [hardware specification]. [Task type A] was run on [GPU type × count] for [duration]. [Task type B] required only CPU instances, as [reason]. The dominant cost is [API calls / GPU compute / evaluation].

**Cost-effectiveness comparison:**
> Compared with [baseline], our method achieves [X]× higher improvement rate while requiring [Y]× fewer evaluations, resulting in [Z]× better cost-effectiveness. Specifically, [baseline] costs approximately $[A] per improvement point, while our method costs approximately $[B] per improvement point.

**Scaling analysis:**
> We analyze scaling behavior across configurations: [1 agent] costs $[X] with [score], [4 agents] costs $[Y] with [score], and [8 agents] would cost approximately $[Z]. The cost-performance tradeoff suggests [optimal configuration] for [budget constraint].

**Entry barrier statement:**
> To reproduce our results, researchers need: (1) API access to [model name] (estimated $[X] for full experiments), (2) [hardware specification] (or cloud instances at $[Y]/hour), and (3) approximately [time] of computation. The minimum viable experiment can be run for approximately $[Z] on [minimal setup].

**Example analysis (from CORAL):**

| Component | Cost | Percentage | Notes |
|-----------|------|------------|-------|
| LLM API calls | $30-60/run | ~85% | Claude Opus 4.6 |
| Evaluation | $3-6/run | ~10% | Subprocess execution |
| Infrastructure | <$1/run | <1% | Monitoring loop |
| **Single run total** | **$33-67** | **100%** | 3-hour single agent |
| **Full paper** | **$1000-5000** | - | 11 tasks × 4 runs |

**Comparison with related work:**

| Method | Primary Cost | GPU Needed | Total Cost | Cost Efficiency |
|--------|-------------|------------|------------|-----------------|
| CORAL | API calls | No (CPU) | $1000-5000 | 40.7% improvement rate |
| OpenEvolve | API calls | No (CPU) | $800-4000 | 11.2% improvement rate |
| DGM | API calls | A100 (eval) | $500-2000 | SWE-bench: 20→50% |
| Genie | Training | 8-32 A100 | $10k-50k | 11B video model |

**Ablation study structure:**
| Variant | Performance | Δ | Conclusion |
|---------|-------------|---|------------|
| Full method | X | - | Best overall |
| w/o Module A | Y | -Z | Module A contributes Z |
| w/o Module B | W | -V | Module B contributes V |
| Baseline | U | -T | Gap with baseline is T |

**Mechanism verification structure:**
> To verify our principle, we conduct three types of experiments:
> 1. **Correlation analysis**: Show that ___ correlates with ___ (r=0.XX, p<0.01)
> 2. **Perturbation test**: When we artificially破坏 ___, performance degrades by ___%
> 3. **Controlled comparison**: Under controlled conditions, methods using ___ outperform those using ___ by ___%

**Robustness reporting:**
> We report results across 5 random seeds (mean ± std). Hyperparameter sensitivity analysis shows performance is stable within ___% across reasonable settings. Efficiency analysis demonstrates ___ speedup with ___ overhead.

### Common Weaknesses and Fixes

| Weakness | Symptom | Fix |
|----------|---------|-----|
| Problem too vague | "Existing methods perform poorly in complex scenarios" | Specify failure mode, add motivating experiment |
| Contribution feels like engineering | Just stacking modules without insight | Add theoretical understanding, key observation, or mechanism explanation |
| Method-story disconnect | Modules don't correspond to challenges | Check each module against Section 2; remove or re-explain non-corresponding modules |
| Experiments only report scores | Tables without analysis | Add ablation, mechanism verification, controlled variables, variance, efficiency |
| Claims too large | "We solve X" without boundaries | Narrow claims, state applicable conditions, failure cases, limitations |
| Costs not reported | "We used GPT-4" without $ amounts | Add API cost breakdown, hardware requirements, total budget |
| No cost comparison | Only performance comparison with baselines | Add cost-effectiveness analysis (score per dollar) |
| Entry barrier unclear | Cannot reproduce without asking authors | Specify minimal setup, estimated costs, time requirements |
| Boilerplate limitations | "Future work will explore..." without specifics | Add specific, actionable directions with priority |
| No field connection | Work exists in isolation | Connect to broader trends and open problems |

### Future Research Direction Templates

**Limitation discussion template:**
> While [method] has proved effective, several limitations remain. First, [limitation 1], which means [impact]. An exciting direction for future work is [specific direction]. Second, [limitation 2], suggesting [direction]. Third, [limitation 3], which could be addressed by [approach].

**Extension direction template:**
> Building on our findings, several promising directions emerge: (1) [Direction 1], which would [benefit] by [approach]; (2) [Direction 2], extending [current work] to [new domain]; (3) [Direction 3], addressing [open problem] through [method].

**Cross-field connection template:**
> This work connects to several active research areas: [Area 1] (e.g., [Paper A]), where [connection]; [Area 2] (e.g., [Paper B]), suggesting [opportunity]; and [Area 3] (e.g., [Paper C]), where [combined direction].

**Priority assessment template:**

| Direction | Scientific Value | Feasibility | Impact | Recommendation |
|-----------|-----------------|-------------|--------|----------------|
| [D1: Specific direction] | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐⭐ | P0 - Highest priority |
| [D2: Specific direction] | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐☆ | P1 - High priority |
| [D3: Specific direction] | ⭐⭐⭐☆☆ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐☆☆ | P2 - Medium priority |

### Rating Scale

Use this scale for each dimension:

| Rating | Description |
|--------|-------------|
| ⭐⭐⭐⭐⭐ | Excellent - clearly addresses all requirements |
| ⭐⭐⭐⭐☆ | Good - mostly addresses requirements, minor gaps |
| ⭐⭐⭐☆☆ | Adequate - addresses basic requirements, notable gaps |
| ⭐⭐☆☆☆ | Weak - significant gaps in addressing requirements |
| ⭐☆☆☆☆ | Poor - fails to address requirements |

### Example Analysis Structure

```markdown
# CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery - Deconstruction

## Overall Assessment
CORAL is a high-quality paper that achieves a complete closed-loop from problem to evidence. 
Rating: ⭐⭐⭐⭐⭐ (4.5/5 average)

## 1. Problem & Challenge
- Problem specificity: ⭐⭐⭐⭐⭐
  - Clear: rigid control pipelines limit agent adaptability
  - Evidence: Table 1 shows baselines underperform on 10/11 tasks
- Challenge evidence: ⭐⭐⭐⭐☆
  - Motivating experiment present (Table 1, 2)
  - Could add visualization of failure modes

## 2. Challenge → Principle Transition
- Transition quality: ⭐⭐⭐⭐⭐
  - Natural bridge: "What if we let agents control the evolutionary process?"
  - Source: failure mode driven
- Key quote: "This raises a natural question: what if we let the agents themselves control the evolutionary process?"

## 3. Principle / Key Observation
- Observation clarity: ⭐⭐⭐⭐☆
  - Hypothesis clearly stated in Section 3.1
  - Could be more falsifiable
- Three sub-observations: autonomy, persistent memory, heartbeat intervention

## 4. Method Motivation
- Module-principle alignment: ⭐⭐⭐⭐⭐
  - Each component maps to a principle
  - Ablation (Table 3) validates each contribution
- Complexity: Appropriate - not over-engineered

## 5. Experimental Rigor
- Main results: ⭐⭐⭐⭐⭐ (11 tasks, 2 stress tests)
- Ablation: ⭐⭐⭐⭐⭐ (Table 3, clear component contributions)
- Mechanism: ⭐⭐⭐⭐☆ (Table 4, 5, trajectory statistics)
- Robustness: ⭐⭐⭐☆☆ (4 runs, could add variance analysis)

## 6. Computational Resource Analysis
- Cost clarity: ⭐⭐⭐⭐⭐
  - API costs clearly reported: $30-60/single agent/3h
  - Total budget: $1000-5000 for full paper
- Hardware transparency: ⭐⭐⭐⭐⭐
  - CPU-only (no GPU needed)
  - Clear model specification: Claude Opus 4.6
- Cost-effectiveness: ⭐⭐⭐⭐☆
  - 40.7% improvement rate vs 11-15% baselines
  - ~2.5× better cost-effectiveness than baselines
- Entry barrier: Medium
  - Requires API access to Claude Opus
  - ~$30 minimum for single experiment

## 7. Future Research Directions
- Limitation honesty: ⭐⭐⭐⭐⭐
  - Appendix A explicitly discusses 3 limitations
  - Each limitation is specific and actionable
- Direction specificity: ⭐⭐⭐⭐☆
  - Suggests training custom small models
  - Suggests role specialization for agents
  - Could be more specific on evaluation co-evolution
- Field connection: ⭐⭐⭐⭐☆
  - Connects to self-improvement (DGM, HyperAgents)
  - Connects to automated scientific discovery
  - Could connect more to quality-diversity search
- Priority assessment: Present (in analysis, not in paper)

## Self-Check Results
| # | Check | Rating |
|---|-------|--------|
| 1 | Specific, important problem | ✓ |
| 2 | Challenge proven | ✓ |
| 3 | Natural transition | ✓ |
| 4 | New principle/observation | ✓ |
| 5 | Method from principle | ✓ |
| 6 | Experiments support claims | ✓ |
| 7 | Alternative explanations ruled out | △ |
| 8 | Honest about limitations | ✓ |
| 9 | Complete story | ✓ |
| 10 | Costs clearly reported | ✓ |
| 11 | Cost-effectiveness compared | ✓ |
| 12 | Entry barrier clear | ✓ |
| 13 | Limitations honestly discussed | ✓ |
| 14 | Future directions specific | ✓ |
| 15 | Field connection clear | ✓ |

## Highlights
1. Clear hypothesis-driven writing
2. Thorough ablation showing component contributions
3. Mechanism verification via trajectory statistics
4. Honest limitation discussion (Appendix A)
5. Transparent cost reporting
6. Clear future research directions

## Improvement Suggestions
1. Add error bars or confidence intervals
2. Include hyperparameter sensitivity analysis
3. Discuss "more compute vs. better strategy" contribution
4. Add cost-effectiveness comparison table with baselines
5. Connect more explicitly to quality-diversity search literature
6. Add priority assessment for future directions

## Future Research Opportunities
1. **P0: Role specialization** - Inject different personalities/roles into agents to improve exploration diversity
2. **P0: Evaluator co-evolution** - Evolve evaluators alongside solutions to handle ambiguous evaluation
3. **P1: Knowledge graph** - Organize notes/skills into structured knowledge graph for better retrieval
4. **P1: Open-source model integration** - Reduce costs by integrating Llama/Qwen models
5. **P2: Scale to 100+ agents** - Design hierarchical coordination for massive parallel exploration
```
