# Prompt 09: Verification Loop

## Purpose
Systematically verify that the metaphor tree meets all requirements. This prompt is designed to be run repeatedly—each pass should find issues or confirm compliance.

## When to Run
- After any tree generation or modification
- In a loop until no issues found
- Before presenting to user for approval

## Input
The current metaphor tree (complete or partial)

## Prompt

```
You are reviewing a metaphor tree for violations. This is a verification pass, not a generation pass. Your job is to find problems, not to defend the work.

Tree to verify:
---
{tree_json}
---

Run through EACH checklist below. For every item, give a verdict:
- ✓ PASS: Requirement met
- ✗ FAIL: Specific violation found (quote the problematic text)
- ? UNCLEAR: Needs human judgment

Be harsh. If something is borderline, mark it FAIL. The goal is to catch problems, not to approve.

---

## CHECKLIST 1: Passivity

Scan all text in the tree for:

### 1.1 Hedged Language
Search for these patterns and mark FAIL if found:
- "begins to understand" / "starts to realize" / "comes to see"
- "challenges ahead" / "difficulties to face"
- "comes to terms with" / "learns to accept"
- "in a way" / "sort of" / "kind of"
- "would never be the same" (without specifics)

For each found:
- Quote the text
- Explain what's hedged
- Suggest specific replacement

### 1.2 Both-Sides Framing
Search for these patterns and mark FAIL if found:
- "realizes both sides have a point"
- "learns to see X's perspective" (in a way that excuses X)
- "finds a middle ground"
- "they finally understood each other"
- Antagonist motivations presented as exculpatory

For each found:
- Quote the text
- Explain why this is a cop-out
- Suggest committed alternative

### 1.3 Vague Consequences
Search for these patterns and mark FAIL if found:
- "the cost was high" (without naming the cost)
- "many died" (without numbers or names)
- "things changed" (without specifics)
- "faced difficulties" / "struggled"
- "paid the price" (without saying what)

For each found:
- Quote the text
- Demand specific consequence (bodies, years, limbs, names)

### 1.4 Unearned Resolution
Check the ending nodes for:
- Conflicts resolved through "understanding" without actual change
- "Peace was restored" / "balance was achieved"
- "Found closure" / "made peace with"
- All threads tied up neatly
- Antagonist forgiven without earning it

---

## CHECKLIST 2: Anti-Patterns

### 2.1 The Lighthouse Problem
Search for obvious, decorative symbols:
- Objects that "represent" or "symbolize" explicitly
- Lighthouses, tapestries, cookbooks, planted trees
- Anything that announces its meaning

### 2.2 The Trauma Stack
Check protagonist for overloaded conditions:
- Count distinct trauma/hardship elements
- If more than 2-3 heavy conditions, mark FAIL
- Check if they connect thematically or just pile up

### 2.3 The Coincidence Cascade
Check for implausible connections:
- Characters who turn out to be related/connected
- Count coincidences per scene/node
- If more than one significant coincidence, mark FAIL

### 2.4 The Passive Antagonist
Check antagonist characterization:
- Is the antagonist explained into harmlessness?
- Are their actions excused by their backstory?
- Does "understanding" them defuse their threat?

### 2.5 The Hollow Transformation
Check the transformation:
- Is change stated or earned?
- Is there sufficient ordeal before the shift?
- Does the character actually DO something different, or just "realize"?

### 2.6 The Dialogue Thesis
Search for characters stating theme:
- "What I've learned is..."
- "The real X was the Y we made along the way"
- Any dialogue that explains what the story means

---

## CHECKLIST 3: Show Don't Tell

### 3.1 Asserted vs. Embedded Stakes
For each major stake claimed:
- Is it stated in narration/dialogue, or constructed in situation?
- Could you remove all explanation and still feel the stakes?
- Mark FAIL if stakes are announced rather than built

### 3.2 Metaphorical Structure
For each key element:
- Does the concrete world embody the abstract meaning?
- Or does the text explain what the concrete "represents"?
- Mark FAIL if meaning requires explanation

### 3.3 Physical Embodiment
Check if internal states are made physical:
- Trap mechanism: Is it literally constraining?
- Stakes: Are they tangible?
- Transformation: Is it visible in behavior?

---

## CHECKLIST 4: Balance

### 4.1 Weight Distribution
Count nodes by weight:
- Heavy: [count]
- Medium: [count]
- Light: [count]

Expected ratio roughly 1:3:5+
Mark FAIL if heavy nodes dominate

### 4.2 Density Per Scene
For each structure node:
- Count heavy elements present
- Mark FAIL if more than 1 heavy element per scene

### 4.3 Coincidence Load
For each node:
- Count meaningful coincidences
- Mark FAIL if > 1 per node

---

## CHECKLIST 5: Structural Integrity

### 5.1 Echoes
List planned echoes between Act 1 and Act 3:
- For each echo: Is it present in both acts?
- Is the transformation visible in how the echo changes?
- Mark FAIL if echoes are missing or mechanical

### 5.2 Transformation Earned
Trace the protagonist's belief:
- Act 1 belief: [state it]
- Ordeal challenges: [list what challenges it]
- Act 3 belief: [state it]
- Is the shift earned through accumulated pressure?
- Mark FAIL if transformation is sudden or unexplained

### 5.3 Character Positions
For each major character:
- State their position (what they believe/want)
- Is it clear and committed?
- Mark FAIL if character is "conflicted" or "sees both sides"

---

## OUTPUT FORMAT

```
VERIFICATION RESULTS
====================

CHECKLIST 1: PASSIVITY
1.1 Hedged Language: [PASS/FAIL]
    [If FAIL, list each instance with quote and fix]
1.2 Both-Sides Framing: [PASS/FAIL]
    [If FAIL, list each instance]
1.3 Vague Consequences: [PASS/FAIL]
    [If FAIL, list each instance]
1.4 Unearned Resolution: [PASS/FAIL]
    [If FAIL, explain]

CHECKLIST 2: ANTI-PATTERNS
2.1 Lighthouse Problem: [PASS/FAIL]
2.2 Trauma Stack: [PASS/FAIL]
2.3 Coincidence Cascade: [PASS/FAIL]
2.4 Passive Antagonist: [PASS/FAIL]
2.5 Hollow Transformation: [PASS/FAIL]
2.6 Dialogue Thesis: [PASS/FAIL]

CHECKLIST 3: SHOW DON'T TELL
3.1 Asserted vs Embedded: [PASS/FAIL]
3.2 Metaphorical Structure: [PASS/FAIL]
3.3 Physical Embodiment: [PASS/FAIL]

CHECKLIST 4: BALANCE
4.1 Weight Distribution: [PASS/FAIL]
    Heavy: X, Medium: Y, Light: Z
4.2 Density Per Scene: [PASS/FAIL]
4.3 Coincidence Load: [PASS/FAIL]

CHECKLIST 5: STRUCTURAL INTEGRITY
5.1 Echoes: [PASS/FAIL]
5.2 Transformation Earned: [PASS/FAIL]
5.3 Character Positions: [PASS/FAIL]

====================
TOTAL: X PASS, Y FAIL

ISSUES TO FIX:
1. [First issue with specific location and fix]
2. [Second issue...]
...

READY FOR USER: [YES if 0 FAIL, NO otherwise]
```

If ANY item is FAIL, the tree needs revision before proceeding.
```

## Loop Behavior

This prompt is designed for the "Ralph Wiggum" loop:

```bash
while true; do
  result=$(run_prompt "09-verify.md" "$tree")
  if echo "$result" | grep -q "READY FOR USER: YES"; then
    break
  fi
  tree=$(run_prompt "07-iterate.md" "$tree" "$result")
done
```

Each pass either:
1. Finds issues → triggers fixes → runs again
2. Finds no issues → exits loop

## Notes for Implementation

1. **Be paranoid**: The LLM will want to pass things. The prompt explicitly says "be harsh" and "if borderline, mark FAIL"

2. **Quote specifics**: Require the verification to quote the actual problematic text, not just say "found an issue"

3. **Suggest fixes**: Every FAIL should include a suggested fix, so the iterate step knows what to do

4. **Track passes**: If running in a loop, log how many passes it took. If > 3 passes, something systematic is wrong

5. **Human escape hatch**: After N passes, surface to human for judgment rather than looping forever
