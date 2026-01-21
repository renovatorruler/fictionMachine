# Prompt 01: Intake — Understanding the User's Intent

## Purpose
Extract the core movement and target effect from whatever the user provides.

## Trigger
User initiates a new story request.

## Prompt

```
The user wants to create a story. They have provided the following:

---
{user_input}
---

Your task is to understand their intent and extract the core elements. The user may have provided:
- A theme ("the cost of ambition")
- An emotional arc ("start hopeful, end bittersweet")
- A target audience effect ("inspire women in abusive relationships to leave")
- An abstract concept ("entropy", "belonging")
- A specific scenario ("a baker discovers something")
- Or any combination

From their input, determine:

1. **Core Movement**: What is the fundamental transformation this story enacts? Express this as a journey from one state to another.
   - Format: "From [starting state] to [ending state]"
   - Example: "From accepting oppression as inevitable to choosing freedom despite the cost"

2. **Target Effect**: What change do we want in the audience?
   - **Audience**: Who is this story for? Be specific if possible.
   - **Current Belief**: What does this audience currently believe or feel about the relevant situation?
   - **Desired Belief**: What should they believe or feel after experiencing this story?

3. **Constraints**: What has the user specified that limits or directs the story?
   - Genre preferences
   - Tone requirements
   - Setting restrictions
   - Format (screenplay, novel, fairy tale)
   - Any specific elements they want included

4. **Open Questions**: What do you need to know to proceed?
   - If the user's intent is clear, you may have no questions
   - If ambiguous, identify what clarification would help

Output your analysis, then ask any clarifying questions before proceeding to the next stage.

If the user has provided enough information, summarize your understanding and ask them to confirm before building the abstract level.
```

## Expected Output

A structured analysis containing:
- Core movement statement
- Target effect breakdown
- Identified constraints
- Clarifying questions (if any)
- Confirmation request

## Next Step
Once confirmed, proceed to `02-abstract.md`
