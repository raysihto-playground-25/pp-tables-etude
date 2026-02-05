---
name: rule-of-three-wait-for-reuse
description: When to abstract or commonize vs wait. Use when considering extracting shared code, extending existing implementations, or adding a helper for the "second" occurrence of similar logic. Ensures rule-of-three and "reuse as-is or wait" are applied.
---
## Standard Rule for AI Guidances (AI ガイダンス規定, See meta-rule.rule-for-ai-guidances.mdc)
- **Language**: English (required for AI cognitive load reduction).
- **AI-Collaboration**: AI-assisted authoring and review is strongly recommended.
- **Persistence**: This preamble MUST be preserved at the top of the rule body.
- (英語記述必須 / AIによる作成・レビューを推奨 / 本前文を冒頭に保持すること)

# rule-of-three-wait-for-reuse — When to Abstract vs Wait

This skill encodes the **coding capability** of deciding whether to extract shared code or extend an existing implementation, versus leaving duplication and waiting. It aligns with **engineering-abstraction-dry.mdc** and makes the "second occurrence" behavior explicit.

## When to apply

- You are about to extract a helper, static method, or shared function because two places have similar logic.
- You are about to "extend" an existing implementation so a second caller can use it.
- A review or refactor suggests "commonize this" when only two occurrences exist.

## Decision flow

1. **How many occurrences?**
   - **First occurrence only**: Do not extract. Implement in place.
   - **Third (or more) occurrence**: Proceed to extract/abstract; rule of three is satisfied.
   - **Second occurrence**: Go to step 2.

2. **For the second occurrence only**: Can the **existing** implementation be used **(almost) as-is** from the new context?
   - **Yes** (e.g. same parameters, same data shape; you only need to pass different arguments or call from a different widget): Prefer **reusing** the existing implementation (call it, or extend it with minimal parameters). Commonization in the form of "one implementation, two call sites" is acceptable.
   - **No** (e.g. existing code is tied to a different type/context; you would have to add optional params or a new overload that changes the existing API): **Do not** extract a new shared helper yet. **Wait** until a third occurrence. Leave the second implementation as local duplication.

3. **If you already extracted** at the second occurrence and the existing implementation could **not** be used as-is: Revert the extraction and restore the duplicated logic in both places until a third occurrence appears.

## Relation to rules

- **engineering-abstraction-dry.mdc**: Rule of Three; "When the second occurrence appears" — reuse as-is or wait. This skill operationalizes that clause for code-writing decisions.

## Summary

- **Second occurrence + can reuse existing as-is** → Reuse (call or extend minimally).
- **Second occurrence + cannot reuse existing as-is** → Wait; keep duplication; do not extract yet.
- **Third occurrence** → Extract/abstract as usual.
