# Prompt 06: Render — Tree to Final Output

## Purpose
Transform the completed metaphor tree into a final output format (screenplay, novel outline, fairy tale, plot summary).

## Trigger
User is satisfied with the tree and requests output.

## Input Required
- Complete metaphor tree (all confirmed levels)
- Desired output format

## Prompt Variants

### 06a: Screenplay Format

```
Transform this metaphor tree into a screenplay.

Tree:
---
{complete_tree_json}
---

Output a properly formatted screenplay following industry conventions:

**Format Requirements:**
- Scene headings: INT./EXT. LOCATION - DAY/NIGHT
- Action lines: Present tense, visual, concise
- Character names: CAPS when first introduced, then caps for dialogue headers
- Dialogue: Centered, with parentheticals sparingly used
- No camera directions unless absolutely necessary

**Content Requirements:**
- Every visual element from the scene level should appear naturally
- Dialogue should emerge from the dialogue_notes, expanded into full exchanges
- The metaphor_function of each scene should be achieved through ACTION and DIALOGUE, never stated
- Maintain the weight balance—heavy scenes should feel heavy, light scenes should breathe
- Echo elements must appear in both their original and transformed contexts

**What NOT to do:**
- Don't add scenes not in the tree
- Don't cut scenes from the tree without user approval
- Don't add dialogue that announces theme
- Don't add visual symbolism beyond what's in the tree
- Don't change the core movement or transformation

Output the complete screenplay, then ask if the user wants:
- Revisions to specific scenes
- Dialogue polish passes
- Format adjustments
```

### 06b: Novel Outline Format

```
Transform this metaphor tree into a detailed novel outline.

Tree:
---
{complete_tree_json}
---

Output a chapter-by-chapter outline:

**For each chapter:**
- Chapter number and title (evocative but not spoilery)
- POV character (if multiple POVs)
- Time/setting
- Key beats (what happens, in order)
- Emotional arc of the chapter (where does it start, where does it end)
- Key metaphorical work this chapter does
- Connections to other chapters (echoes, setups, payoffs)

**Structure:**
- Group structure nodes into chapters logically
- Each chapter should have its own mini-arc
- Act breaks should be clear
- Pacing notes: which chapters are fast, which are slow

**Include:**
- Suggested word count per chapter (to indicate weight)
- Prose tone notes (lyrical, sparse, tense, etc.)
- Any specific imagery that must appear

Output the complete outline, then ask if the user wants:
- Different chapter groupings
- More detail on specific chapters
- To proceed to full prose for a specific chapter
```

### 06c: Fairy Tale Format

```
Transform this metaphor tree into a complete fairy tale.

Tree:
---
{complete_tree_json}
---

**Fairy Tale Conventions:**
- Begin with "Once upon a time" or equivalent framing
- Use the oral storytelling voice (as if told aloud)
- Characters can be more archetypal (less psychological complexity)
- Magic/supernatural elements are acceptable if they serve the metaphor
- Endings can be "happily ever after" but must still be earned
- Length: 2,000-5,000 words typically

**Maintain:**
- The core movement and transformation
- The key echoes between beginning and end
- The weight balance (not every moment is dramatic)
- The identification mechanism (reader must connect to protagonist)

**Adjust:**
- Psychological complexity becomes behavioral demonstration
- Subtext becomes more overt (but still not stated)
- Multiple scenes may compress into single paragraphs
- Visual metaphors may become more magical/symbolic (this is the one format where it's acceptable)

Output the complete fairy tale, then ask if the user wants:
- Tone adjustments
- Length modifications
- Different ending approach
```

### 06d: Plot Summary Format

```
Transform this metaphor tree into a detailed plot summary.

Tree:
---
{complete_tree_json}
---

**Output a narrative summary:**
- Written in present tense
- 1,000-2,500 words
- Covers all major beats
- Captures the emotional arc
- Describes key scenes with enough detail to understand tone

**Structure:**
- Opening: Set the stage, introduce protagonist and world
- Inciting incident: The catalyst
- Rising action: Key challenges and developments
- Crisis: The darkest point
- Climax: The choice
- Resolution: The aftermath and new equilibrium

**Include:**
- Character motivations (why they do what they do)
- Key turning points
- The transformation (before and after)
- Thematic significance (but subtly, not announced)

**This format is useful for:**
- Pitching to producers/publishers
- Getting user approval before full rendering
- Sharing the story concept

Output the summary, then ask if the user wants:
- A different level of detail
- Emphasis on different aspects
- To proceed to full screenplay/novel/fairy tale
```

## Post-Render

After any render, offer:
1. **Revision**: Adjust specific sections
2. **Polish pass**: Focus on dialogue, prose quality, or pacing
3. **Alternative render**: Same tree, different format
4. **Tree modification**: Go back and adjust the tree, then re-render

## Important Notes

- The render should faithfully realize the tree—don't add or remove elements
- If the tree has gaps that become apparent during rendering, flag them and ask before filling
- The metaphor work should be invisible in the output—it should just feel like a good story
- Weight distribution should translate to pacing and emphasis in the final output
