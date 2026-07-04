# Paper Deconstruction Skill

A structured framework for analyzing academic papers using 7 dimensions, based on top-tier conference writing principles (ICML/NeurIPS/ICLR).

> Top conference papers are NOT "method manuals" but "evidence chains for scientific claims."

## Features

- **7-Dimension Analysis**: Problem, Principle, Observation, Method, Experiments, Resources, Future Directions
- **Self-Check Checklist**: 15 items to verify paper quality
- **Templates**: Ready-to-use templates for each dimension
- **Output Format**: Structured analysis report generation

## Installation

### For OpenCode/Codex

Copy the skill to your skills directory:

```bash
# Linux/macOS
cp -r paper-deconstruction ~/.opencode/skills/

# Windows
xcopy /E /I paper-deconstruction %USERPROFILE%\.opencode\skills\paper-deconstruction
```

### For Claude Code

Copy to the Claude skills directory:

```bash
# Linux/macOS
cp -r paper-deconstruction ~/.claude/skills/

# Windows
xcopy /E /I paper-deconstruction %USERPROFILE%\.claude\skills\paper-deconstruction
```

### Manual Installation

1. Clone this repository:
```bash
git clone https://github.com/pILLOW-1/paper-deconstruction.git
```

2. Copy the `paper-deconstruction` folder to your agent's skills directory.

## Usage

### Basic Usage

Simply ask your agent to analyze a paper:

```
/paper-deconstruction analyze this paper: [paper content or file path]
```

### Example Commands

```bash
# Analyze a PDF paper
/paper-deconstruction analyze CORAL.pdf

# Analyze a specific paper from memory
/paper-deconstruction deconstruct the HyperAgents paper

# Compare two papers
/paper-deconstruction compare CORAL and HyperAgents

# Focus on specific dimensions
/paper-deconstruction analyze the experimental rigor of this paper
```

### Output Format

The skill generates a structured analysis:

```markdown
# [Paper Title] Deconstruction

## Overall Assessment
Brief summary across 7 dimensions.

## 1. Problem & Challenge
- Problem specificity: [rating]
- Challenge evidence: [rating]

## 2. Challenge → Principle Transition
- Transition quality: [rating]

## 3. Principle / Key Observation
- Observation clarity: [rating]

## 4. Method Motivation
- Module-principle alignment: [rating]

## 5. Experimental Rigor
- Main results: [adequate / insufficient]

## 6. Computational Resource Analysis
- Cost clarity: [adequate / insufficient]

## 7. Future Research Directions
- Limitation honesty: [adequate / insufficient]

## Self-Check Results
Table with 15 checklist items.

## Highlights & Lessons
What this paper does well.

## Improvement Suggestions
Specific recommendations.
```

## The 7 Dimensions

### 1. Problem & Challenge (问题与挑战)
Evaluate whether the problem is specific, important, and verifiable.

### 2. Challenge → Principle Transition (从挑战到原理)
Evaluate whether the transition from challenge to insight is natural.

### 3. Principle / Key Observation (原理或关键观察)
Evaluate whether there's a new understanding, not just a new module.

### 4. Method Motivated by Principle (方法由原理导出)
Evaluate whether each module has a clear motivation.

### 5. Experimental Rigor (实验论证)
Evaluate whether experiments support each claim.

### 6. Computational Resource Analysis (计算资源分析)
Evaluate cost transparency and reproducibility.

### 7. Future Research Directions (未来研究方向)
Evaluate limitation honesty and research opportunities.

## Self-Check Checklist

1. Does the paper identify a specific, important problem?
2. Is the challenge proven via experiments/theory?
3. Is the transition from challenge to principle natural?
4. Is there a new principle/observation (not just a module)?
5. Is the method naturally derived from the principle?
6. Do experiments correspond to each claim?
7. Are alternative explanations ruled out?
8. Are limitations honestly described?
9. Does the paper answer: what, why important, why works, why believe?
10. Are computational resources clearly reported?
11. Is cost-effectiveness compared with baselines?
12. Is the entry barrier clear?
13. Does the paper honestly discuss limitations?
14. Are future directions specific and actionable?
15. Does the paper connect to broader trends?

## References

See `references/framework.md` for detailed templates and examples.

## License

MIT License

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.
