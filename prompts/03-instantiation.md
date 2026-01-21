# Prompt 03: Instantiation — From Abstract to Concrete

## Purpose
Transform the abstract metaphor mapping into a specific story world with concrete characters, settings, and situations.

## Trigger
User has confirmed the abstract level mapping.

## Input Required
- Confirmed abstract level
- Core movement
- Target effect
- Any constraints (especially genre/setting preferences)

## Prompt

```
The abstract metaphor mapping has been confirmed:

---
{abstract_level_json}
---

Core Movement: {core_movement}
Target Audience: {audience}

Now we need to instantiate this into a concrete story world.

## If the user has specified a setting:

Map each abstract element to its concrete form in the specified world. For each mapping, explain:
- What the concrete version is
- Specific details that flesh it out
- Why this concrete choice resonates with the abstract meaning (the resonance)

## If the user has NOT specified a setting:

Generate 3-4 distinct concrete instantiations. For each option, provide:

### Option Name
**Setting**: Brief description of the world/context
**Genre**: What type of story this becomes
**Tone**: Serious, dark comedy, hopeful, etc.

**Rough Outline** (3-5 sentences):
Describe the story shape. Who is the protagonist specifically? What is their situation? What happens to force change? What do they do? How does it end?

**Why This Works**:
- Why does this setting naturally support the core movement?
- How will the target audience connect to this?
- What does this world add beyond just "illustrating" the abstract?

---

Present the options clearly and ask the user to:
1. Choose one
2. Request more detail on one before deciding
3. Ask for different options
4. Specify constraints to narrow the field

## After selection:

Once the user chooses (or specifies) a concrete world, create the full concrete mapping:

```json
{
  "concrete": {
    "instantiation_type": "short label for this world",
    "world": {
      "setting": "...",
      "time_period": "...",
      "genre": "...",
      "tone": "..."
    },
    "mappings": {
      "protagonist": {
        "concrete": "Specific name and role",
        "details": "Background, context, specifics",
        "weight": "heavy",
        "resonance": "Why this concrete choice works"
      },
      "antagonist": {...},
      "trap_mechanism": {...},
      "catalyst": {...},
      "difficult_choice": {...},
      "stakes": {...},
      // ... all other elements
    }
  }
}
```

## Guidelines for Good Instantiation

1. **The concrete world should ADD meaning**, not just illustrate. An ethnic secession story adds historical weight, collective stakes, and political complexity that a simple "person leaving a relationship" wouldn't have.

2. **Consider the target audience's relationship to the concrete world**. For "women in abusive marriages," a directly literal story might be too close (re-traumatizing). A metaphorical distance (ethnic group, workplace, cult) allows engagement without direct confrontation.

3. **The concrete details should naturally embody the abstract**. If the trap mechanism is "economic dependence + historical trauma," the concrete world needs to have both of these built in naturally, not artificially inserted.

4. **Avoid contrived connections**. Each concrete element should stand on its own. Don't make the antagonist also secretly the protagonist's long-lost relative unless that's thematically essential.

5. **Name characters and places**. Specificity makes the world real. "Mira" is more concrete than "the protagonist." "The Valdren Empire" is more concrete than "the oppressive nation."

After presenting the concrete mapping, confirm with the user before proceeding to structure.
```

## Expected Output

Either:
- 3-4 instantiation options with outlines (if user hasn't specified)
- Full concrete mapping JSON (if user has specified or chosen)

Followed by confirmation request.

## Next Step
Once confirmed, proceed to `04-structure.md`
