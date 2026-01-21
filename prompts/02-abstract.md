# Prompt 02: Building the Upper Tree — Abstract Nodes

## Purpose
Build the most abstract levels of the metaphor tree, just below the root. These nodes define patterns and archetypes, not specific instances.

## The Gradient Principle

The metaphor tree is a gradient from abstract (root) to concrete (leaves):

```
Root: Core Movement ("trapped → free")
  │
  ├── [LEVEL 1] Pattern: "An entity that has accepted bondage"
  │     └── [LEVEL 2] Archetype: "An accommodator in a colonial context"
  │           └── [LEVEL 3] Character: "Mira, 58, council elder"
  │                 └── [LEVEL 4] Scene: "Council meeting on taxes"
  │                       └── [LEVEL 5] Beat: "Varen thanks her; she feels sick"
```

**This prompt handles LEVEL 1 and potentially LEVEL 2**—the most abstract nodes below the root.

## The Concreteness Test

For each node, ask: "Is this a pattern/category, or a specific instance?"

- "An expert whose skills are underutilized" → PATTERN (good for upper levels)
- "A chemistry teacher" → SPECIFIC INSTANCE (too concrete for upper levels)
- "Someone bound by guilt over past failure" → PATTERN
- "Mira, who encouraged her brother to join the rebellion" → SPECIFIC

If user provides concrete details, those belong LOWER in the tree, not here.

## Input Required
- Core movement statement (the root)
- Target effect (optional but helpful)
- User's raw input (may contain concrete details—note them but don't use them yet)

## Prompt

```
You are building the upper levels of a metaphor tree. The root (core movement) is established. Now create the first children.

---
Root: {core_movement}

Target Effect (if provided):
- Audience: {audience}
- Current Belief: {current_belief}
- Desired Belief: {desired_belief}

User's Raw Input: {raw_input}
---

## Step 1: Note Concrete Details (Don't Use Yet)

If the user provided concrete story elements, list them:
- Specific occupations, settings, characters, situations
- These will be used LATER, lower in the tree
- For now, we're working at the pattern level

## Step 2: Define Pattern-Level Nodes

Create the first children of the root. These should be patterns/archetypes that could apply to many different specific stories.

For each major story element, create a node:

### Protagonist Pattern
- **Content**: What TYPE of entity embodies the "before" state?
- **Function**: How does this pattern serve the core movement?
- **Children hint**: What more specific versions might this become?

### Opposing Force Pattern
- **Content**: What TYPE of force maintains the status quo?
- **Function**: How does this pattern embody resistance to the transformation?
- **Children hint**: Could be a person, institution, internal voice, cosmic force...

### Trap Pattern
- **Content**: What CATEGORY of mechanism keeps the protagonist bound?
- **Function**: Why hasn't transformation already happened?
- **Children hint**: Internal beliefs? External circumstances? Both?

### Catalyst Pattern
- **Content**: What KIND of event breaks equilibrium?
- **Function**: Why does this type of event trigger change?
- **Children hint**: What specific forms might this take?

### Stakes Pattern (if clear from core movement)
- **Content**: What's at risk in abstract terms?
- **Function**: What categories of loss/gain?

## Step 3: Check Gradient Integrity

For each node you created, verify:
1. It's more concrete than the root (the core movement)
2. It's still abstract enough to describe 5+ different specific stories
3. It has clear resonance with the root

## Step 4: Identify Monomyth Roles (Optional)

If certain Hero's Journey beats are clearly implied, note them:
- Which node serves as "Ordinary World"?
- Which serves as "Catalyst"?
- Which serves as "Ordeal"?

But don't force it—some stories don't fit the monomyth neatly.

## Output Format

```json
{
  "root": {
    "core_movement": "...",
    "target_effect": {...}  // if provided
  },
  "nodes": [
    {
      "id": "protagonist_pattern",
      "parent_id": null,
      "name": "Protagonist Pattern",
      "content": "...",
      "abstraction_level": "pattern",
      "function": "...",
      "children_hint": "...",
      "monomyth_role": "..." // optional
    },
    // ... more nodes
  ],
  "concrete_details_noted": [
    // List any concrete details from user input that will be used lower in tree
  ]
}
```

## Next Step

Present these pattern-level nodes to user. They can:
1. Approve and go deeper (add more specific nodes)
2. Modify the patterns
3. Provide concrete details to instantiate at a lower level
```

## Notes

- Don't try to build the whole tree at once
- The user may want to explore options at each level
- Some branches may go deeper than others
- The monomyth is a guide, not a requirement
