# Prompt 02: Abstract Level — Mapping the Core Elements

## Purpose
Create the abstract metaphor mapping that will be instantiated into a concrete story.

## Trigger
User has confirmed the core movement and target effect from intake.

## Input Required
- Core movement statement
- Target effect (audience, current belief, desired belief)
- Any constraints

## Prompt

```
Based on the confirmed core movement and target effect:

---
Core Movement: {core_movement}

Target Effect:
- Audience: {audience}
- Current Belief: {current_belief}
- Desired Belief: {desired_belief}

Constraints: {constraints}
---

Create the abstract metaphor mapping. This level defines WHAT the story is about in universal terms, before we decide the specific world/setting.

Define each of the following elements:

## Required Elements

### Protagonist
- **Description**: What type of entity embodies the "before" state? (Not a specific character yet—the abstract role)
- **Weight**: Heavy
- **Function**: How does this entity serve the core movement? Why will the target audience identify with them?

### Antagonist
- **Description**: What type of force maintains the status quo / creates the trap?
- **Weight**: Heavy
- **Function**: How does this force embody what keeps the audience stuck?

### Trap Mechanism
- **Description**: What keeps the protagonist bound? (Both practical and psychological)
- **Weight**: Medium
- **Function**: Why hasn't the protagonist already made the change? This must feel valid.

### Catalyst
- **Description**: What type of event breaks the equilibrium?
- **Weight**: Medium
- **Function**: Why does THIS thing shift the calculus when other things haven't?

### Difficult Choice
- **Description**: What is the nature of the choice the protagonist must make?
- **Weight**: Heavy
- **Function**: How does this choice embody the transformation?

### Stakes
- **Description**: What is at risk? What is lost by staying vs. risked by leaving?
- **Weight**: Medium
- **Function**: Why is this choice genuinely difficult?

## Optional Elements (include if relevant)

### Allies
- Who or what supports the protagonist's growth?
- Assign weight (usually light to medium)

### Obstacles
- Internal: What beliefs/patterns does the protagonist fight within themselves?
- External: What systemic or environmental forces resist change?
- Assign weights

Output the abstract level as a JSON object following this structure:

```json
{
  "abstract": {
    "protagonist": {
      "description": "...",
      "weight": "heavy",
      "function": "..."
    },
    "antagonist": {...},
    "trap_mechanism": {...},
    "catalyst": {...},
    "difficult_choice": {...},
    "stakes": {...},
    "allies": [...],
    "obstacles": [...]
  }
}
```

After outputting, confirm with the user that this abstract mapping captures their intent before proceeding to concrete instantiation.
```

## Expected Output

JSON object with abstract element mappings, followed by confirmation request.

## Next Step
Once confirmed, proceed to `03-instantiation.md`
