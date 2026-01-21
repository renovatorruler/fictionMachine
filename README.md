# Fiction Machine

A metaphor engine for generating stories from thematic constraints.

## Core Concept

Every element in a story is a metaphor. Not just the obvious symbolic ones—the sports car, the transformation—but *everything*: the high school teacher, the beige walls, the Pontiac Aztek. If it's in the story, it carries meaning.

## How It Works

1. **User provides a constraint**: A theme, emotional arc, abstract concept, or target audience effect (e.g., "inspire women in abusive relationships to leave")

2. **Engine builds a metaphor tree**:
   - **Root**: The core emotional/thematic movement
   - **Level 1**: Abstract metaphor mapping (unempowered → empowered through difficult choice)
   - **Level 2**: Concrete instantiation (ethnic group, marriage, job, etc.)
   - **Level 3+**: Progressive detail—motivations, obstacles, characters, each as metaphor nodes
   - **Leaf nodes**: Actual story elements—scenes, dialogue, actions, objects

3. **User inspects and refines**: The tree is visible and editable

4. **Engine renders**: A breadth-first traversal of leaves produces the complete story in the chosen format (screenplay, novel, fairy tale, etc.)

## Theoretical Foundation

Built on:
- Joseph Campbell's monomyth (Hero's Journey)
- Jungian archetypes
- Marie-Louise von Franz's fairy tale analysis

## Project Structure

```
/docs           - Theory and framework documentation
/schema         - Metaphor tree structure definitions
/examples       - Sample metaphor trees and generated stories
/prompts        - LLM prompt templates for each stage
```

## Status

Under active development.
