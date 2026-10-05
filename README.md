# finance-agent-eval

Evaluation harness for LLM agents answering questions over financial data, measuring accuracy, calibration, and failure modes.

> **Status:** early development. The design below is the target; sections are marked as they are built.

## Problem

LLM agents are increasingly used to answer questions about financial data: variances, ratios, returns, reconciliations. A confident wrong number is worse than no answer. Accuracy alone does not tell you whether an agent can be trusted, so this project measures three things:

1. **Accuracy:** does the agent return the correct figure for a question with a known answer?
2. **Calibration:** when the agent says it is 90% sure, is it right about 90% of the time?
3. **Failure modes:** where and why does it fail (arithmetic slips, wrong period, misread table, unsupported claims)?

## Design

- **Question set:** a versioned set of financial questions over small, synthetic datasets, each with a ground-truth answer computed in code.
- **Agent interface:** a thin wrapper, so any model or agent can be plugged in and compared.
- **Scoring:** exact and tolerance-based matching for numeric answers.
- **Calibration:** confidence elicited per answer, then evaluated with reliability curves and expected calibration error.
- **Failure taxonomy:** each wrong answer is tagged with a failure category, so results show what breaks, not just how often.

## Planned structure

```
finance-agent-eval/
├── data/          synthetic datasets and question sets
├── src/           harness: agent interface, scoring, calibration
├── tests/         unit tests for scoring and calibration
└── results/       run outputs and plots
```

## Roadmap

- [ ] Synthetic dataset generator with ground-truth answers
- [ ] Scoring module with tests
- [ ] Agent interface and a first baseline
- [ ] Calibration metrics and reliability plot
- [ ] Failure taxonomy and first results write-up

## License

MIT
