# Prompt 03: Going Deeper — Adding Concrete Nodes

## Purpose
Add more concrete nodes to the tree, below the pattern-level nodes. This is where abstract patterns become specific characters, settings, and situations.

## The Gradient Continues

```
[Already built]
Root: "trapped → free"
  └── Pattern: "An entity that has accepted bondage"

[This prompt adds]
        └── Archetype: "An accommodator in a colonial context"
              └── Character: "Mira, 58, Kaelish council elder"
```

Each new level is more concrete than the one above.

## When to Use This

After the pattern-level nodes are established, the user can:
1. **Go deeper on one branch** — flesh out a specific element
2. **Explore alternatives** — see different ways to make a pattern concrete
3. **Add the user's concrete details** — if they provided specific story elements

## Input Required
- The current tree (with pattern-level nodes)
- Which node(s) to expand
- Any concrete details the user has provided or wants to use

## Prompt

```
Current tree state:
---
{current_tree_json}
---

User wants to expand: {node_to_expand}
Concrete details available: {user_provided_details}

## Step 1: Identify the Parent Node

The node being expanded:
- ID: {parent_id}
- Content: {parent_content}
- Abstraction level: {parent_level}

## Step 2: Propose Children

Create 3-4 potential child nodes, each more concrete than the parent.

For each option:

### Option [N]: [Short Name]

**Content**: [More specific version of parent]
**Why this works**: [How it embodies the parent pattern]
**Possible children**: [What might come next below this]

---

If user provided concrete details that fit this branch, one option should incorporate those details.

## Step 3: After Selection

Once user chooses an option (or provides their own):

Add the new node to the tree:
```json
{
  "id": "...",
  "parent_id": "{parent_id}",
  "name": "...",
  "content": "...",
  "abstraction_level": "[archetype/character/setting/scene/beat]",
  "function": "...",
  "resonance": "How this connects to parent",
  "weight": "heavy/medium/light",
  "children_hint": "What might come next"
}
```

## Step 4: Check Gradient Integrity

Verify:
1. New node is MORE CONCRETE than parent
2. New node is still connected (resonance is clear)
3. If this node will have children, they can be even more concrete

## Offer Next Steps

User can now:
1. Go deeper on this branch
2. Go deeper on a different branch
3. Add parallel siblings (alternative versions at this level)
4. Stop and view the current tree
5. Generate a logline from current tree
6. Render to output format
```

## Example: Expanding a Protagonist Pattern

**Parent node**:
```json
{
  "id": "protagonist_pattern",
  "content": "An expert whose skills are underutilized in legitimate life",
  "abstraction_level": "pattern"
}
```

**Proposed children**:

### Option 1: Academic Expert
Content: "A scholar or scientist working in a field that doesn't value their specific expertise"
Why: The gap between capability and recognition is institutionally enforced
Possible children: Chemistry teacher, historian at a mediocre college, researcher denied funding

### Option 2: Craftsperson Expert
Content: "An artisan or tradesperson whose mastery goes unrecognized in their market"
Why: The gap is economic—their skills exceed what people will pay for
Possible children: Master chef at a chain restaurant, furniture maker competing with IKEA

### Option 3: Service Expert
Content: "A professional in a helping field whose true capabilities are constrained by the system"
Why: Institutional rules prevent them from doing what they know they could do
Possible children: Doctor in a bureaucratic hospital, social worker with crushing caseload

### Option 4: [User's Detail]
If user said "chemistry teacher":
Content: "A chemistry teacher whose understanding far exceeds what high school curricula require"
Why: Directly uses user's input while connecting to pattern

---

User selects → new node added → tree grows deeper.

## Notes

- Don't rush to the bottom
- User may want to explore multiple branches in parallel
- Some branches may stay abstract while others go deep
- The tree is flexible—not every branch needs the same depth
