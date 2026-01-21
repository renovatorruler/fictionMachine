# Using the Fiction Machine

## What This Is

Fiction Machine is a **prompt engineering framework** for generating stories through hierarchical metaphor construction. It's not a software application—it's a set of documents that guide an LLM through a structured story-building process.

The framework consists of:
- **Theory documents** (`docs/`): Principles the LLM must understand
- **Prompt templates** (`prompts/`): Step-by-step generation and verification
- **JSON schema** (`schema/`): Structure for the metaphor tree
- **Examples** (`examples/`): Reference implementations

## Ways to Use This

### Option 1: Manual Conversation (Simplest)

Copy the relevant documents into a conversation with Claude, ChatGPT, or another LLM.

**Setup conversation:**
```
I'm going to share a story generation framework with you. Please read and internalize these documents before we begin.

[Paste contents of:]
- docs/01-core-theory.md
- docs/06-active-writing.md
- docs/07-anti-patterns.md
- docs/08-show-dont-tell.md
- prompts/00-system.md
```

**Start generation:**
```
Now let's create a story. Here's my input:
[Your theme/audience/concept]

Follow the process in the prompts directory:
1. 01-intake.md - Extract core movement
2. 02-abstract.md - Create abstract mapping
3. 03-instantiation.md - Propose concrete worlds
4. 04-structure.md - Build three acts
```

**Run verification manually:**
```
Now run verification (09-verify.md) on what we've created.
Be harsh. Find every violation.
```

### Option 2: Claude Project (Recommended for Claude)

Create a Claude Project and add the framework files to the project knowledge.

1. Go to claude.ai → Projects → New Project
2. Name it "Fiction Machine"
3. Add files to Project Knowledge:
   - All files from `docs/`
   - All files from `prompts/`
   - `schema/metaphor-tree.schema.json`
   - One example from `examples/`

4. Set custom instructions:
```
You are the Fiction Machine, a story generation engine. You have access to the complete framework in your project knowledge.

When a user wants to create a story:
1. Follow the workflow in prompts/08-workflow.md
2. Run verification (09-verify.md) after each generation step
3. Fix any failures (10-fix.md) before presenting to user
4. Be harsh in verification—find problems, don't defend work

Output metaphor trees as JSON. Only present to user after verification passes.
```

5. Start conversations with story requests

### Option 3: Claude Code Skill

If you're using Claude Code, create a skill that invokes the framework.

**Create `/Users/[you]/.claude/skills/fiction-machine/SKILL.md`:**

```markdown
# Fiction Machine Skill

## Description
Generate stories through hierarchical metaphor construction.

## Trigger
User asks to create a story, write fiction, or build a narrative.

## Process

### 1. Load Framework
Read and internalize:
- /path/to/fictionMachine/docs/*.md
- /path/to/fictionMachine/prompts/00-system.md

### 2. Intake
Follow prompts/01-intake.md to extract:
- Core movement
- Target effect
- Constraints

### 3. Build Tree
Progress through:
- 02-abstract.md
- 03-instantiation.md (offer 3-4 options)
- 04-structure.md

### 4. Verify Loop
After each step, run 09-verify.md:
- If failures found, run 10-fix.md
- Repeat until all pass
- Maximum 5 iterations

### 5. Present to User
Only after verification passes.

### 6. Iterate or Render
User can modify (07-iterate.md) or render (06-render.md)
```

### Option 4: Automated Pipeline

For programmatic use, build a pipeline that:

1. Loads the framework documents
2. Runs prompts in sequence
3. Implements the verification loop
4. Outputs the final tree

**Pseudocode:**
```python
class FictionMachine:
    def __init__(self, llm_client):
        self.llm = llm_client
        self.framework = self.load_framework()
        self.tree = {}

    def load_framework(self):
        # Load all docs and prompts
        return {
            'system': read('prompts/00-system.md'),
            'theory': [read(f) for f in glob('docs/*.md')],
            'prompts': {name: read(f) for name, f in prompts},
            'schema': read('schema/metaphor-tree.schema.json')
        }

    def generate(self, user_input):
        # 1. Intake
        self.tree = self.run_prompt('01-intake', user_input)

        # 2. Abstract
        self.tree = self.run_with_verify('02-abstract')

        # 3. Instantiation (interactive)
        options = self.run_prompt('03-instantiation')
        choice = get_user_choice(options)
        self.tree = self.run_with_verify('03-instantiation', choice)

        # 4. Structure
        self.tree = self.run_with_verify('04-structure')

        return self.tree

    def run_with_verify(self, prompt_name, *args):
        result = self.run_prompt(prompt_name, *args)

        for i in range(5):  # Max iterations
            verification = self.run_prompt('09-verify', result)

            if 'READY FOR USER: YES' in verification:
                return result

            result = self.run_prompt('10-fix', result, verification)

        raise Exception("Max verification iterations reached")

    def run_prompt(self, name, *args):
        prompt = self.framework['prompts'][name]
        # Fill in template variables
        # Call LLM
        # Parse response
        return response
```

### Option 5: MCP Server (Advanced)

Build an MCP (Model Context Protocol) server that exposes the framework as tools.

**Tools to expose:**
- `fiction_intake` - Start a new story
- `fiction_abstract` - Build abstract layer
- `fiction_instantiate` - Propose/select concrete world
- `fiction_structure` - Build three acts
- `fiction_verify` - Run verification
- `fiction_fix` - Fix failures
- `fiction_render` - Output to format
- `fiction_get_tree` - Return current tree state

This allows any MCP-compatible client (including Claude Desktop) to use the framework.

## Tips for Best Results

### 1. Front-load the Theory
The LLM needs to internalize the theory documents before generating. If you skip this, you'll get lighthouse metaphors and trauma stacks.

### 2. Run Verification Ruthlessly
Don't trust the first output. Run 09-verify.md and actually fix what it finds. The loop exists because LLMs need it.

### 3. Be Specific in Your Input
"Write me a story" → Bad
"I want women in abusive relationships to feel inspired to leave" → Good
"A comedy about someone who can't commit to anything" → Good

### 4. Iterate at the Right Level
If something feels wrong:
- Wrong feeling/theme → Iterate at abstract level
- Wrong world/setting → Iterate at concrete level
- Wrong pacing/beats → Iterate at structure level
- Wrong details → Iterate at scene level

Don't try to fix structure problems with scene-level tweaks.

### 5. Trust the Framework, Not the LLM
The LLM will try to take shortcuts. The framework prevents this. If you skip verification, or let the LLM talk you out of running it, you'll get worse output.

## Output Formats

The metaphor tree can be rendered to:
- **Plot summary** - For pitching or high-level review
- **Novel outline** - Chapter-by-chapter breakdown
- **Screenplay** - Industry-formatted script
- **Fairy tale** - Short-form complete narrative

Use 06-render.md to transform the verified tree into your target format.

## Troubleshooting

**Problem:** Output has lighthouse metaphors / obvious symbols
**Cause:** LLM didn't internalize theory documents
**Fix:** Re-paste docs/01-core-theory.md and docs/07-anti-patterns.md

**Problem:** Characters are passive / see both sides
**Cause:** Passivity check not run or not enforced
**Fix:** Run 09-verify.md, enforce fixes from 10-fix.md

**Problem:** Consequences are vague
**Cause:** Show-don't-tell violation
**Fix:** Run verification, specifically check section 1.3 and 3.1

**Problem:** Story feels rushed
**Cause:** Structure level needs more nodes
**Fix:** Iterate at structure level, add ordeal beats

**Problem:** Verification keeps finding new issues
**Cause:** Fixes are introducing new problems
**Fix:** After 5 iterations, manual review needed. Check if there's a fundamental structure problem.
