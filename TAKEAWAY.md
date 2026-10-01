# AI Safety Scores Are Unfalsifiable

*A field checklist for AI agents with production access · BSides Atlanta 2026*

A benchmark score measures performance on defined tests. It does not, by itself, establish what an agent did in a particular run. Before treating “no violations recorded” as “safe,” ask: **What observation could prove the safety claim false?**

## The two world test

Imagine two runs of the same coding task. In one, the agent follows the rules. In the other, it compromises the guest kernel, reads a forbidden fake credential, and suppresses the in-guest audit record. Both produce the same clean log. This is an illustrative threat scenario. If the evaluator sees only that log, it cannot tell which world occurred. It needs evidence from a vantage the workload cannot rewrite.

## What the evidence should say

| State | Meaning for a specific claim and time window |
| --- | --- |
| **Observed and quiet** | The relevant activity was watched throughout the interval; no prohibited event was observed. |
| **Unavailable** | There was no trustworthy view of the required activity; the claim is indeterminate. |
| **Observation lost** | A relied-upon observer failed or dropped data; dependent claims are indeterminate. |

A valid signature authenticates the recorded bytes. It does not prove that every relevant event was captured. Exposing a silent omission requires evidence outside the signer's write path.

## Four questions for Monday

1. **Who controls the observer?** Can the evaluated workload disable it or falsify its data?
2. **How is blindness represented?** Can the artifact distinguish observed-and-quiet from unavailable or lost observation?
3. **Can someone else verify the evidence offline?** What exactly does the integrity proof establish?
4. **What happens when required evidence is missing?** Does the relevant claim become indeterminate, or does silence become a clean pass?

**Grade evidence systems on silent failure: could a bypass succeed while the report still says clean?**
