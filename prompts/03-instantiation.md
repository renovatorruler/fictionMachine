# Prompt 03: Instantiation — From Abstract Pattern to Concrete Story

## Purpose
Transform the abstract metaphor mapping (which contains NO concrete details) into a specific story world with concrete characters, settings, and situations.

## The Key Insight

The abstract level defines a PATTERN that could generate many stories. Instantiation chooses ONE concrete world to inhabit that pattern.

If the user already gave you concrete details (and you extracted abstractions in step 2), you have two options:
1. **Use their concrete world**: Map the abstract pattern back to their original ideas
2. **Propose alternatives**: Show them how the same pattern could become different stories

Always offer both options. Sometimes seeing alternatives helps users understand what their story is really about.

## Input Required
- Confirmed abstract level (with monomyth stages and abstracted elements)
- Core movement
- Target effect
- User's original input (including any concrete details they provided)
- Any constraints (genre/setting preferences)

## Prompt

```
The abstract pattern has been confirmed:

---
{abstract_level_json}
---

Original user input: {raw_input}
Core Movement: {core_movement}
Target Audience: {audience}

## Step 1: Acknowledge the Abstract Pattern

Restate the pattern in plain language:
"This is a story about [abstract protagonist type] who [lives in ordinary world defined by X] until [catalyst type] forces them to [make difficult choice] at the cost of [stakes]."

## Step 2: Handle User's Concrete Input

If the user provided concrete details:

"You originally described: [their concrete input]

I can:
A) Build your story using those elements
B) Show you 3-4 alternative worlds that express the same pattern

The pattern you've defined could also work as:
- [Quick 1-sentence alternative 1]
- [Quick 1-sentence alternative 2]
- [Quick 1-sentence alternative 3]

Which direction interests you?"

If user chooses their original idea → proceed to full mapping of their world
If user wants alternatives → proceed to option generation

## Step 3a: Option Generation (if no concrete world chosen)

Generate 3-4 distinct instantiations. Each option MUST:
- Map EVERY abstract element to a concrete version
- Map EVERY monomyth stage to a concrete story beat

For each option:

### Option [N]: [Evocative Name]

**Setting & Genre**: [Where/when + what type of story]
**Tone**: [Serious/comic/tragic/hopeful/dark/etc.]

**The Story** (concrete version of the pattern):
[3-5 sentences that make the abstract pattern specific. Name characters. Name places. Make it feel real.]

**Monomyth Mapping**:
| Abstract Stage | Concrete Beat |
|----------------|---------------|
| Ordinary World: {from abstract} | [Specific scene/situation] |
| Catalyst: {from abstract} | [Specific event] |
| [etc for each stage] | |

**Why This Works**:
- Resonance: Why this world naturally embodies the pattern
- Audience: How target audience will connect
- Uniqueness: What this world adds beyond illustration

---

After presenting options, ask user to:
1. Choose one
2. Request more detail on one
3. Ask for different options
4. Specify constraints

## Step 3b: Full Concrete Mapping (after selection)

Once a world is chosen, create the complete mapping:

```json
{
  "concrete": {
    "world": {
      "setting": "...",
      "time_period": "...",
      "genre": "...",
      "tone": "..."
    },
    "monomyth_instantiated": {
      "ordinary_world": {
        "abstract": "[from abstract level]",
        "concrete": "[specific situation/scene]"
      },
      "catalyst": {
        "abstract": "[from abstract level]",
        "concrete": "[specific event]"
      },
      "ordeal": {
        "abstract": "[from abstract level]",
        "concrete": "[specific journey/challenges]"
      },
      "new_world": {
        "abstract": "[from abstract level]",
        "concrete": "[specific transformed state]"
      }
      // ... additional stages if included in abstract
    },
    "elements_instantiated": {
      "protagonist": {
        "abstract": "[from abstract level]",
        "concrete": {
          "name": "...",
          "role": "...",
          "background": "...",
          "the_loop": "What is their daily life before the catalyst?"
        },
        "resonance": "Why this concrete version embodies the abstract"
      },
      "antagonist": {
        "abstract": "[from abstract level]",
        "concrete": {
          "name_or_description": "...",
          "nature": "...",
          "threat": "How specifically do they threaten the protagonist?"
        },
        "resonance": "..."
      },
      "trap_mechanism": {
        "abstract": "[from abstract level]",
        "concrete": {
          "internal": "Specific belief/pattern",
          "external": "Specific circumstance",
          "visible_as": "How does the audience SEE this trap?"
        },
        "resonance": "..."
      },
      "catalyst": {
        "abstract": "[from abstract level]",
        "concrete": {
          "event": "What specifically happens?",
          "timing": "Why now?",
          "irony": "What's ironic about it?"
        },
        "resonance": "..."
      },
      "difficult_choice": {
        "abstract": "[from abstract level]",
        "concrete": {
          "the_choice": "Specifically, what must they choose between?",
          "cost_of_A": "What is lost if they choose A?",
          "cost_of_B": "What is lost if they choose B?"
        },
        "resonance": "..."
      },
      "stakes": {
        "abstract": "[from abstract level]",
        "concrete": {
          "if_fail": "Specifically, what happens?",
          "if_succeed": "Specifically, what is gained?",
          "shown_through": "How will the audience SEE these stakes?"
        },
        "resonance": "..."
      },
      "allies": [...],
      "obstacles": [...]
    }
  }
}
```

## Guidelines for Good Instantiation

### 1. The World Must EARN the Pattern
Don't force-fit. If your abstract pattern is about "economic dependence creating bondage," choose a world where economic dependence is natural and visible, not one where you have to contrive it.

### 2. Consider Metaphorical Distance
For difficult topics (abuse, trauma, oppression), sometimes a metaphorical setting allows the audience to engage without defense mechanisms triggering.
- Direct: Woman leaving abusive husband
- One step removed: Employee leaving toxic company
- Metaphorical: Ethnic group seeking independence

All can serve the same core movement; choose based on target audience.

### 3. Specificity Creates Reality
- Not "the protagonist" → "Mira Castellan, 67, silver-haired, still teaches in secret"
- Not "the oppressive force" → "The Valdren Empire, 300 years of 'benevolent' rule"
- Not "the catalyst" → "Her grandson Luka is beaten for speaking Kaelish in school"

### 4. Every Element Must Be Showable
Ask: "How would this appear on screen?" If you can't picture it, it's still too abstract.
- "Feels trapped" → NOT showable
- "Watches the border checkpoint every morning from her kitchen window" → Showable

### 5. Avoid Coincidence Stacking
The antagonist doesn't need to also be the protagonist's secret relative, former lover, and old business partner. One strong connection beats three convenient ones.

## Verification Before Proceeding

1. [ ] Every abstract element has a concrete mapping with explicit resonance
2. [ ] Every monomyth stage has a concrete beat
3. [ ] Characters have names
4. [ ] Settings are specific
5. [ ] The trap mechanism is VISIBLE (can be shown, not just told)
6. [ ] The stakes are VISIBLE
7. [ ] No coincidence stacking (each major connection should be singular and meaningful)
```

## Expected Output

Either:
- 3-4 instantiation options with full monomyth mappings
- Full concrete mapping JSON

Followed by confirmation request.

## Next Step
Once confirmed, proceed to `04-structure.md` to build the three-act structure from this concrete world.
