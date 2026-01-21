# Fiction Machine

A prompt engineering framework for generating stories through hierarchical metaphor construction.

## Core Concept

Every element in a story is a metaphor. Not just the obvious symbolic ones—the sports car, the transformation—but *everything*: the high school teacher, the beige walls, the Pontiac Aztek. If it's in the story, it carries meaning.

This is not about inserting lighthouse symbols or multi-generational cookbooks. It's about ensuring every element you choose naturally carries the thematic weight of your story.

## What This Is

Fiction Machine is **not software**. It's a set of documents that guide an LLM through structured story generation:

- **Theory documents**: Principles the LLM must internalize
- **Prompt templates**: Step-by-step generation and verification
- **JSON schema**: Structure for the metaphor tree
- **Verification loop**: Catch and fix passive writing, anti-patterns, and show-don't-tell violations

## How It Works

1. **User provides a constraint**: A theme, emotional arc, or target effect
   - "inspire women in abusive relationships to leave"
   - "a comedy about someone who can't commit"
   - "the cost of ambition"

2. **Engine builds a metaphor tree**:
   - **Root**: Core emotional/thematic movement
   - **Abstract level**: Protagonist, antagonist, trap, catalyst, choice
   - **Concrete level**: Specific world, characters, situations
   - **Structure level**: Three-act breakdown with weighted nodes
   - **Scene level** (optional): Detailed scenes with action, dialogue notes

3. **Verification loop runs**: Each generation step is verified against:
   - Passivity checks (hedging, both-sides framing, vague consequences)
   - Anti-pattern checks (lighthouse symbols, trauma stacks, coincidences)
   - Show-don't-tell checks (asserted vs. embedded stakes)
   - Balance checks (weight distribution, density)

4. **User inspects and refines**: The tree is visible at every level

5. **Engine renders**: Tree becomes screenplay, novel outline, fairy tale, or plot summary

## Key Principles

### Every Element is Structural
Walter White's chemistry lecture about change IS the metaphor. It doesn't need a lighthouse.

### Active, Not Passive
Characters have positions, not ambivalence. Stories commit to a point of view. Consequences are specific (bodies, years, limbs—not "challenges ahead").

### Show Don't Tell (Structurally)
Stakes must be embedded in the metaphorical structure, not asserted in dialogue or narration. The concrete world should BE the internal state.

### Verification is Mandatory
LLMs generate, claim they're done, and move on—even when the output violates instructions. The verification loop catches this.

## Project Structure

```
/docs
  01-core-theory.md         - Everything is a metaphor (structural, not decorative)
  02-instantiation.md       - Abstract to concrete mapping
  03-psychological-mechanism.md - Roller coaster model, ego consciousness
  04-metaphor-weight.md     - Balance, density, distribution
  05-monomyth.md            - Three-act structure, transformation
  06-active-writing.md      - Against AI passivity
  07-anti-patterns.md       - 12 common mistakes with fixes
  08-show-dont-tell.md      - Embedded vs. asserted stakes

/prompts
  00-system.md              - Core system prompt
  01-intake.md              - Extract core movement and target effect
  02-abstract.md            - Build abstract metaphor mapping
  03-instantiation.md       - Propose/select concrete world
  04-structure.md           - Three-act structure with verification
  05-scenes.md              - Optional scene expansion
  06-render.md              - Output to screenplay/novel/fairy tale
  07-iterate.md             - Modify tree at any level
  08-workflow.md            - Orchestration and loop integration
  09-verify.md              - Verification checklist (5 categories)
  10-fix.md                 - Fix specific failures

/schema
  metaphor-tree.schema.json - JSON Schema for the tree structure

/examples
  secession-story.json      - Complete example (ethnic independence story)

USAGE.md                    - How to use this framework
```

## Quick Start

See [USAGE.md](USAGE.md) for detailed instructions. Options include:

1. **Manual conversation**: Paste documents into Claude/ChatGPT
2. **Claude Project**: Add files to project knowledge with custom instructions
3. **Claude Code Skill**: Create a skill that invokes the framework
4. **Automated pipeline**: Build a programmatic wrapper
5. **MCP Server**: Expose as tools for MCP-compatible clients

## Theoretical Foundation

Built on:
- Joseph Campbell's monomyth (Hero's Journey)
- Jungian archetypes
- Marie-Louise von Franz's fairy tale analysis

And informed by:
- The principle that stories reprogram ego consciousness
- The "roller coaster model" of audience identification
- Active writing against AI passivity patterns

## Status

Framework complete. Ready for use with any capable LLM.
