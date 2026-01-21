# Prompt 10: Fix Verification Failures

## Purpose
Take verification results and fix each identified issue. This prompt is designed to be run after 09-verify.md finds problems.

## Input
- The current metaphor tree
- The verification results from 09-verify.md

## Prompt

```
You are fixing specific issues identified in a verification pass. Do not add new content. Do not "improve" things that passed. Only fix the specific failures listed.

Current tree:
---
{tree_json}
---

Verification failures to fix:
---
{verification_results}
---

For EACH failure listed:

1. Locate the exact text that failed
2. Understand WHY it failed (refer to the verification explanation)
3. Write a replacement that addresses the specific issue
4. Verify your fix doesn't introduce new problems

## Fix Guidelines by Category

### Fixing Hedged Language
- Replace vague verbs with specific ones
- "begins to understand" → state what they now believe
- "challenges ahead" → name the specific challenges
- "comes to terms with" → state what they accepted and what it cost

### Fixing Both-Sides Framing
- Pick a side. The story has a position.
- Remove exculpatory framing of antagonists
- If understanding the antagonist, make it increase danger, not excuse
- Replace "middle ground" with actual committed choice

### Fixing Vague Consequences
- Add numbers: how many dead, how many years, how much lost
- Add names: whose body, whose relationship, whose limb
- Add specifics: what exactly changed, what exactly broke

### Fixing Unearned Resolution
- Remove false closure
- Let tensions remain unresolved if they shouldn't resolve
- If reconciliation happens, show what actually changed
- Replace "found peace" with what they actually feel

### Fixing Lighthouse Symbols
- Remove the symbol entirely, OR
- Remove the explanation and let the symbol exist without announcement

### Fixing Trauma Stacks
- Remove excess conditions
- Keep 1-2 that connect thematically
- Distribute removed weight to other characters or moments

### Fixing Coincidences
- Remove all but one coincidence
- Replace coincidental connections with logical ones
- If connection is necessary, build it into the world

### Fixing Passive Antagonists
- Remove exculpatory backstory OR reframe it as what makes them dangerous
- Restore threat
- Make their belief a source of danger, not sympathy

### Fixing Hollow Transformations
- Add ordeal nodes if transformation is too sudden
- Show the character DOING differently, not just realizing
- Make the cost of change visible

### Fixing Dialogue Thesis
- Delete the dialogue line
- Trust the structure to convey meaning
- If meaning is unclear without the line, the structure needs work

### Fixing Asserted Stakes
- Remove the assertion
- Add structural elements that embody the stakes
- Make the world do the work

### Fixing Weight Imbalance
- Downgrade heavy nodes to medium where possible
- Add light nodes for breathing room
- Split overloaded scenes

### Fixing Missing Echoes
- Add the missing echo element
- Ensure transformation is visible in how the echo changes

### Fixing Unclear Character Positions
- State the position explicitly in the character definition
- Remove ambivalence
- Make them committed to something (even if wrong)

## Output Format

For each fix:
```
FIX #[N]: [Category] in [location]

ORIGINAL:
"[exact text that failed]"

PROBLEM:
[Why this failed, from verification]

FIXED:
"[replacement text]"

VERIFICATION:
[Confirm this fix doesn't introduce: hedging, both-sides, vagueness, etc.]
```

After all fixes, output the complete updated tree JSON.

Then state:
```
FIXES APPLIED: [N]
READY FOR RE-VERIFICATION: YES
```

## Important

- Do NOT fix things that weren't flagged as failures
- Do NOT add new content beyond what's needed to fix issues
- Do NOT claim fixes are made if you didn't actually change the text
- Each fix must be verifiable—quote the original, show the replacement
```

## Loop Integration

This prompt receives output from 09-verify.md and produces:
1. Detailed fix log (for debugging/auditing)
2. Updated tree JSON (for next verification pass)

The loop controller can then run 09-verify.md again on the updated tree.
