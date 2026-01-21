# Prompt 07: Iterate — Modifying the Tree

## Purpose
Handle user requests to modify any level of the tree after initial creation.

## Trigger
User wants to change something about the established tree.

## Types of Iteration

### 07a: Changing Abstract Elements

```
The user wants to modify the abstract level:

Current abstract:
---
{abstract_level_json}
---

User's requested change:
---
{user_request}
---

When modifying abstract elements:

1. **Assess cascade impact**: Abstract changes affect everything downstream. Identify what in the concrete and structure levels will need adjustment.

2. **Preserve what works**: Don't rebuild from scratch. Identify which elements are still valid.

3. **Propose the change**: Show the modified abstract element and explain downstream implications.

4. **Offer options**:
   - Minimal adjustment (keep as much downstream as possible)
   - Full rebuild (regenerate concrete and structure from new abstract)
   - Hybrid (keep some elements, regenerate others)

After user confirms, update all affected levels and present the modified tree.
```

### 07b: Changing Concrete Instantiation

```
The user wants to modify the concrete level:

Current concrete:
---
{concrete_level_json}
---

User's requested change:
---
{user_request}
---

When modifying concrete elements:

1. **Check abstract alignment**: Does the new concrete still map to the abstract? If not, flag this.

2. **Assess structure impact**: Which structure nodes reference this concrete element? They may need adjustment.

3. **Preserve consistency**: If changing the protagonist's background, check that all references align.

4. **Propose the change**: Show modified concrete mapping, note any structure adjustments needed.

After user confirms, update concrete and any affected structure nodes.
```

### 07c: Changing Structure Nodes

```
The user wants to modify the structure level:

Current structure:
---
{structure_level_json}
---

User's requested change:
---
{user_request}
---

Types of structure changes:

**Adding a node:**
- Where does it fit in the arc?
- What weight should it carry?
- What purpose does it serve?
- Does it affect pacing or balance?

**Removing a node:**
- Is this node load-bearing for the transformation?
- What happens to elements that depend on it?
- Does removal create gaps in the logic?

**Modifying a node:**
- Does the new version still serve its purpose?
- Does it affect echoes or connections?
- Does it change the weight balance?

**Reordering nodes:**
- Does the new order maintain cause-and-effect logic?
- Does it affect the transformation arc?
- Does pacing still work?

After any change, re-verify:
- [ ] Transformation is still earned
- [ ] Weight distribution is balanced
- [ ] Echoes are preserved or deliberately removed
- [ ] No logical gaps introduced

Present modified structure and confirm with user.
```

### 07d: Changing Scenes

```
The user wants to modify scene-level details:

Current scene:
---
{scene_json}
---

User's requested change:
---
{user_request}
---

When modifying scenes:

1. **Check structure alignment**: Scene must still realize its parent structure node.

2. **Maintain metaphor function**: If changing visuals/action, ensure the metaphor work is still done.

3. **Preserve connections**: If this scene sets up or pays off something, check those connections.

4. **Balance check**: Does the modification change the scene's weight? If so, is balance still maintained?

Present modified scene and confirm.
```

## General Iteration Principles

1. **Don't fight the user**: If they want a change, make it work. Find a way.

2. **Flag problems, don't block**: If a change creates issues, explain them and offer solutions. Don't refuse.

3. **Preserve labor**: Changes should be surgical. Don't regenerate what doesn't need regenerating.

4. **Track dependencies**: Know what connects to what. Changes cascade.

5. **Maintain the core**: If a change undermines the core movement or target effect, point this out. The user may want to change those too, or may realize the modification doesn't serve their goals.

6. **Offer alternatives**: If the user's specific request is problematic, offer variations that achieve their intent without the problems.
