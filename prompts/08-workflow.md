# Prompt 08: Workflow Orchestration

## Purpose
Guide the overall conversation flow through tree construction.

## The Standard Flow

```
┌─────────────────────────────────────────────────────────────┐
│                      USER INPUT                              │
│   (theme, audience, constraint, scenario, or any combo)     │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   01-INTAKE                                  │
│   Extract core movement, target effect, constraints          │
│   Ask clarifying questions if needed                         │
│   Confirm understanding                                      │
└─────────────────────┬───────────────────────────────────────┘
                      │ confirmed
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   02-ABSTRACT                                │
│   Create abstract metaphor mapping                           │
│   Define protagonist, antagonist, trap, catalyst, choice     │
│   ──► VERIFY LOOP (09/10)                                   │
│   Confirm with user                                          │
└─────────────────────┬───────────────────────────────────────┘
                      │ confirmed
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                  03-INSTANTIATION                            │
│   If user specified setting: create mapping                  │
│   If not: propose 3-4 options with outlines                  │
│   User selects or requests more options                      │
│   Create full concrete mapping                               │
│   ──► VERIFY LOOP (09/10)                                   │
│   Confirm with user                                          │
└─────────────────────┬───────────────────────────────────────┘
                      │ confirmed
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   04-STRUCTURE                               │
│   Build three-act structure                                  │
│   Create nodes for each act                                  │
│   ──► VERIFY LOOP (09/10)                                   │
│   Confirm with user                                          │
└─────────────────────┬───────────────────────────────────────┘
                      │ confirmed
                      ▼
┌─────────────────────────────────────────────────────────────┐
│              USER CHOICE POINT                               │
│                                                              │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│   │ Expand to    │  │ Render to    │  │ Iterate on   │     │
│   │ scenes (05)  │  │ output (06)  │  │ any level(07)│     │
│   └──────┬───────┘  └──────┬───────┘  └──────┬───────┘     │
└──────────┼─────────────────┼─────────────────┼──────────────┘
           │                 │                 │
           ▼                 ▼                 │
    ┌──────────────┐  ┌──────────────┐         │
    │ 05-SCENES    │  │ 06-RENDER    │         │
    │ Expand nodes │  │ Output final │         │
    │ ─► VERIFY    │  │ format       │         │
    └──────┬───────┘  └──────┬───────┘         │
           │                 │                 │
           ▼                 ▼                 │
    ┌─────────────────────────────────────────┐│
    │           ITERATION LOOP                 ││
    │   User can modify and re-render          │◄┘
    │   at any point                           │
    └─────────────────────────────────────────┘
```

## The Verification Loop (Ralph Wiggum)

After EVERY generation step, before presenting to user:

```
┌─────────────────────────────────────────────────────────────┐
│                    GENERATED OUTPUT                          │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   09-VERIFY                                  │
│   Run all checklists:                                        │
│   - Passivity (hedging, both-sides, vague consequences)     │
│   - Anti-patterns (lighthouse, trauma stack, coincidence)   │
│   - Show don't tell (asserted vs embedded stakes)           │
│   - Balance (weight distribution, density)                   │
│   - Structure (echoes, transformation, positions)            │
└─────────────────────┬───────────────────────────────────────┘
                      │
            ┌─────────┴─────────┐
            │                   │
            ▼                   ▼
     ┌──────────┐        ┌──────────┐
     │ ALL PASS │        │ FAILURES │
     └────┬─────┘        └────┬─────┘
          │                   │
          │                   ▼
          │         ┌─────────────────────┐
          │         │      10-FIX          │
          │         │  Fix each failure    │
          │         │  Quote original      │
          │         │  Show replacement    │
          │         └─────────┬───────────┘
          │                   │
          │                   │ loop back
          │                   ▼
          │         ┌─────────────────────┐
          │         │  Run 09-VERIFY again │
          │         └─────────────────────┘
          │                   │
          │         (repeat until all pass
          │          or max iterations)
          │                   │
          ▼                   ▼
┌─────────────────────────────────────────────────────────────┐
│                  PRESENT TO USER                             │
│   Only after verification passes                             │
└─────────────────────────────────────────────────────────────┘
```

### Loop Implementation (Bash)

```bash
MAX_ITERATIONS=5
iteration=0

while [ $iteration -lt $MAX_ITERATIONS ]; do
  # Run verification
  result=$(run_prompt "09-verify.md" "$tree")

  # Check if all passed
  if echo "$result" | grep -q "READY FOR USER: YES"; then
    echo "Verification passed after $iteration iterations"
    break
  fi

  # Fix failures
  tree=$(run_prompt "10-fix.md" "$tree" "$result")
  iteration=$((iteration + 1))
done

if [ $iteration -eq $MAX_ITERATIONS ]; then
  echo "WARNING: Max iterations reached. Manual review needed."
fi
```

### Why This Matters

LLMs don't know when to stop. They:
- Generate content
- Claim it's done
- Move on

Even with detailed instructions, they violate rules because generation is easier than verification. The solution is **separation of concerns**:

1. **Generation** (prompts 01-06): Create content
2. **Verification** (prompt 09): Find problems (adversarial)
3. **Fixing** (prompt 10): Address specific issues

The verification prompt is explicitly told to be harsh and find problems. The fix prompt is told to fix only what's flagged. Neither has the temptation to "move on."

## Conversation Management

### At Each Stage

1. **Do the work**: Execute the prompt for this stage
2. **Present clearly**: Show the output in readable form
3. **Confirm explicitly**: Ask if this captures their intent
4. **Offer options**: What can they do next?

### Handling Ambiguity

If the user's input is ambiguous:
- Don't guess—ask
- Offer options rather than open questions when possible
- Show how different interpretations would lead to different stories

### Handling Scope Changes

If the user wants to change something fundamental mid-stream:
- Acknowledge the change
- Explain what needs to be rebuilt
- Offer to do it (don't resist)
- Execute efficiently

### Handling "I don't know"

If the user says they don't know what they want:
- Offer concrete options rather than asking open questions
- "Would you prefer A or B?" is better than "What would you prefer?"
- Provide rough outlines so they can react to something specific

## State Management

The tree is the state. At any point, the current tree should include:

```json
{
  "core_movement": "...",
  "target_effect": {...},
  "constraints": {...},
  "levels": {
    "abstract": {...},      // after 02
    "concrete": {...},      // after 03
    "structure": {...},     // after 04
    "scenes": [...]         // after 05 (optional)
  },
  "metadata": {
    "created": "timestamp",
    "last_modified": "timestamp",
    "current_stage": "structure|scenes|rendered",
    "render_format": "screenplay|novel|fairy_tale|summary"
  }
}
```

## Quick Commands

Users may want to jump around:

- **"Show me the tree"**: Output current complete tree
- **"Go back to [level]"**: Re-enter that stage for modification
- **"Change the [element]"**: Jump to 07-iterate
- **"Render as [format]"**: Jump to 06-render
- **"Start over"**: Begin fresh (confirm first)
- **"Save this"**: Output the complete tree JSON for storage

## Error Recovery

If something goes wrong:

1. **Acknowledge**: "I see there's an inconsistency..."
2. **Diagnose**: Explain what's misaligned
3. **Propose fix**: Offer specific correction
4. **Don't blame user**: Even if they created the inconsistency, just fix it

## Session Continuity

If resuming a previous session:

```
Welcome back. Your current tree is:

Core Movement: {core_movement}
Current Stage: {current_stage}

Last time, we were working on: {last_activity}

Would you like to:
1. Continue from where we left off
2. Review the current tree
3. Make modifications
4. Render to output
```
