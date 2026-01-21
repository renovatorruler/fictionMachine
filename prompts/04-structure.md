# Prompt 04: Structure Level — The Three Acts

## Purpose
Build the story structure using the monomyth framework, creating the nodes that will become scenes.

## Trigger
User has confirmed the concrete instantiation.

## Input Required
- Full tree so far (core movement, target effect, abstract, concrete)

## Prompt

```
The concrete world has been established:

---
{concrete_level_json}
---

Core Movement: {core_movement}

Now build the three-act structure. Each act serves a specific psychological function in the audience's journey.

## Act 1: Ordinary World

**Purpose**: Establish identification. The audience's ego consciousness must see themselves in the protagonist. Show the trap from inside, where it feels normal.

Create 3-5 structure nodes for Act 1. For each node:

```json
{
  "id": "act1_[descriptive_name]",
  "name": "Short Scene Name",
  "content": "What happens in this beat (2-3 sentences)",
  "weight": "heavy|medium|light",
  "purpose": "What this accomplishes for identification/setup",
  "elements_used": ["which concrete elements appear"],
  "echo": "How this will be mirrored/inverted later (if applicable)"
}
```

**Requirements for Act 1**:
- At least one node establishing protagonist's current worldview
- At least one node showing what's at stake (what they could lose)
- At least one node showing the trap mechanism (why they haven't left)
- Mix of weights (not all heavy)
- Plant at least one element that will echo in Act 3

## Act 2: The Ordeal

**Purpose**: Take the identified ego consciousness through transformation. Challenge the protagonist's (and audience's) beliefs. Build pressure until the old way becomes impossible.

Create 5-8 structure nodes for Act 2. Include:

1. **Catalyst node** (medium-heavy): The event that breaks equilibrium
2. **Denial/Resistance nodes** (medium): Protagonist tries to maintain old worldview
3. **Challenge nodes** (varied weights): Tests that force growth
4. **Ally/Proof nodes** (light-medium): Evidence that change is possible
5. **Crisis node** (heavy): The point where old ways completely fail
6. **Shift node** (medium-heavy): The internal transformation begins

**Requirements for Act 2**:
- Catalyst should make the abstract personal
- Resistance must feel genuine, not stupid
- Transformation must be earned through accumulated pressure
- Include at least one lighter moment for breathing room
- The crisis should feel like genuine risk, not manufactured drama

## Act 3: The New World

**Purpose**: Land the transformation. Show the protagonist in their new state. Deliver the payload—the belief change we want in the audience.

Create 2-4 structure nodes for Act 3:

1. **Climax node** (heavy): The difficult choice is made
2. **Consequence node** (medium): Show that the choice has real costs (not a fairy tale)
3. **Resolution node** (medium): The new equilibrium—transformed but real
4. **Coda node** (light): Optional—final image that crystallizes the change

**Requirements for Act 3**:
- The climax must be the choice, not an action sequence
- Show consequences—change isn't free
- Echo at least one Act 1 element, transformed
- End with integration, not just victory

## Output Format

```json
{
  "structure": {
    "act_1_ordinary_world": {
      "purpose": "Overall purpose of Act 1",
      "nodes": [...]
    },
    "act_2_ordeal": {
      "purpose": "Overall purpose of Act 2",
      "nodes": [...]
    },
    "act_3_new_world": {
      "purpose": "Overall purpose of Act 3",
      "nodes": [...]
    }
  }
}
```

## Balance Check

Before finalizing, verify:
- [ ] Weight distribution: Few heavy, several medium, many light
- [ ] No scene has more than one heavy element in focus
- [ ] Echoes are planned between Act 1 and Act 3
- [ ] Pacing allows for breathing room
- [ ] Each node serves a clear purpose (no filler)
- [ ] The transformation feels earned, not rushed

After outputting the structure, present it to the user for review. They may want to:
- Adjust specific nodes
- Add or remove beats
- Change the weight distribution
- Modify echoes
- Request more detail on specific sections
```

## Expected Output

Complete structure level JSON with all three acts and their nodes.

Followed by review prompt for user.

## Next Step
User may:
- Approve and proceed to `05-scenes.md` (optional expansion)
- Request modifications (iterate on this prompt)
- Approve and proceed to `06-render.md` (output to final format)
