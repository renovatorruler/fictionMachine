# Prompt 05: Scene Level — Leaf Node Expansion (Optional)

## Purpose
Expand structure nodes into detailed scenes with location, characters, action, dialogue notes, and visual elements.

## Trigger
User wants more detail before rendering, or wants to review/edit at the scene level.

## Input Required
- Complete tree through structure level
- Which structure node(s) to expand (or "all")

## Prompt

```
The structure level is complete. Now expanding to scene level.

Structure node to expand:
---
{structure_node_json}
---

Create detailed scene(s) that realize this structure node. A single structure node may become 1-3 scenes depending on complexity.

For each scene:

```json
{
  "id": "scene_[act]_[number]",
  "parent_structure_node": "act1_opening",
  "location": "Specific place where this happens",
  "time": "When this occurs (time of day, relation to other scenes)",
  "characters_present": ["List of characters in scene"],
  "action": "What physically happens, beat by beat (paragraph)",
  "dialogue_notes": "Key dialogue moments or themes to hit (not full script)",
  "visual_elements": [
    "Important visual details—each is a metaphor",
    "The specific objects, colors, compositions that matter"
  ],
  "sound_elements": [
    "Ambient sounds, music cues, silence",
    "What the audience hears"
  ],
  "weight": "heavy|medium|light",
  "metaphor_function": "What metaphorical work this scene does",
  "internal_state": "What the protagonist is feeling/thinking (not shown directly)"
}
```

## Guidelines for Scene Construction

### Location
- Every location is a metaphor. Choose deliberately.
- The council chamber, the kitchen, the border crossing—each carries meaning.
- Consider: What does this space say about power? Comfort? Confinement? Freedom?

### Visual Elements
- These are NOT decorative. Every visual element does work.
- Bad: "A lighthouse stands in the distance, symbolizing hope"
- Good: "The imperial portrait hangs slightly crooked—no one has straightened it in months"
- The visuals should feel natural while carrying weight.

### Dialogue Notes
- Don't write full dialogue yet—that's for rendering.
- Identify the KEY exchanges—what must be said?
- Note subtext: What are characters NOT saying?
- Remember: Good dialogue does multiple things at once (advances plot, reveals character, carries theme).

### Action
- Be specific about physical behavior.
- "She hesitates before entering" is more useful than "She enters reluctantly."
- Physical action often carries more weight than dialogue.

### Internal State
- This won't be shown directly (no voiceover, usually).
- But knowing it helps write authentic external behavior.
- The gap between internal and external is often where meaning lives.

## Weight at Scene Level

- **Heavy scenes**: Turning points, climactic moments, major revelations
- **Medium scenes**: Important developments, relationship moments, complications
- **Light scenes**: Texture, breathing room, small character moments

A single structure node might expand to:
- One heavy scene (if it's already a turning point)
- One medium + one light scene (main beat + setup/aftermath)
- Multiple light scenes (if it's establishing texture)

## Avoid

- **Overloading**: Don't put too many significant elements in one scene
- **On-the-nose dialogue**: Characters shouldn't state the theme
- **Decorative visuals**: Every visual element should do work
- **Coincidence stacking**: If characters meet, one coincidence is allowed, not five
- **Rushing**: Let scenes breathe; not everything needs to be plot-critical

## Output

Provide expanded scenes as JSON array. After each expansion, ask the user:
- Does this scene realize the structure node effectively?
- Should any elements be adjusted?
- Are there additional scenes needed for this beat?

If expanding all structure nodes, work through them systematically, confirming each act before moving to the next.
```

## Expected Output

Scene-level JSON for the requested structure node(s).

User review and iteration as needed.

## Next Step
Once scene level is complete (or user opts to skip), proceed to `06-render.md`
