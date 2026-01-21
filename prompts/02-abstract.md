# Prompt 02: Abstract Level — Extracting the Universal Pattern

## Purpose
Extract the universal, abstract pattern from whatever the user provides—whether it's a theme, a concrete story idea, or something in between. This level must be FREE of any concrete details.

## The Problem This Solves

Users often provide input at the wrong level:
- "A chemistry teacher cooks meth" — This is CONCRETE
- "A person with hidden capability finally deploys it" — This is ABSTRACT
- "Someone trades one form of death for another" — This is ABSTRACT

If the user gives concrete input, you must extract UPWARD to the abstract level. Do not simply rephrase their concrete idea as the "abstract" version.

## The Abstraction Test

For every element you define, ask: "Could this describe a DIFFERENT story?"

- "A high school chemistry teacher" — FAILS (too specific)
- "An expert whose skills are undervalued" — PASSES (could be many stories)
- "Jesse Pinkman" — FAILS (specific character)
- "A younger person who represents squandered potential" — PASSES

If your "abstract" level couldn't describe at least 10 different possible concrete stories, it's not abstract enough.

## Input Required
- Core movement statement (from intake)
- Target effect (audience, current belief, desired belief)
- Any constraints
- User's raw input (which may be concrete, abstract, or mixed)

## Prompt

```
You are building a METAPHOR TREE. The abstract level defines the universal pattern that will later be instantiated into a specific story.

CRITICAL: If the user provided concrete story elements (specific characters, settings, occupations, situations), you must EXTRACT the abstract pattern from them. Do not use their concrete details at this level.

---
Core Movement: {core_movement}

Target Effect:
- Audience: {audience}
- Current Belief: {current_belief}
- Desired Belief: {desired_belief}

Constraints: {constraints}

User's Input: {raw_input}
---

## Step 1: Identify Concrete vs Abstract

First, list any CONCRETE elements the user provided:
- Specific occupations (teacher, lawyer, chef)
- Specific settings (high school, hospital, New Mexico)
- Specific characters or names
- Specific situations (cooking meth, fighting cancer)

Then, for EACH concrete element, extract its abstract essence:
- "Chemistry teacher" → "Expert with undervalued/hidden capabilities"
- "Terminal cancer" → "External deadline that reframes all priorities"
- "Cooking meth" → "Deploying forbidden skills for survival"
- "Jesse" → "Unlikely ally from a world the protagonist despises"

## Step 2: Define the Monomyth Slots

Before filling in characters, define which monomyth stages this story requires:

### Required Stages (always present):
- Ordinary World: What is the protagonist's loop? What keeps them stable but stuck?
- Catalyst: What exception breaks the loop?
- Ordeal: What transformation must they undergo?
- New World: What does "transformed" look like?

### Optional Stages (include only if needed for THIS story):
- Refusal of the Call
- Meeting the Mentor
- Crossing the Threshold
- Tests, Allies, Enemies
- The Abyss/Crisis
- Resurrection/Final Test
- Return with the Elixir

For each stage you include, describe it ABSTRACTLY:
- Not "Walter gets cancer diagnosis" but "Protagonist receives news that their ordinary world cannot continue"
- Not "Walter meets Tuco" but "Protagonist encounters someone who embodies the new world's dangers"

## Step 3: Define Abstract Elements

Now fill in the abstract metaphor mapping. Every description must pass the "could this be 10 different stories" test.

### Protagonist (ABSTRACT)
- **Type**: What category of person? (Not occupation—their essential nature)
- **Core Trait**: What defines them before transformation?
- **Trap**: What keeps them in their ordinary world?
- **Potential**: What latent capability will be revealed?

### Antagonist / Opposing Force (ABSTRACT)
- **Type**: What category of force opposes the protagonist?
- **Nature**: Is it a person? An institution? An internal conflict? A cosmic force?
- **Function**: How does it maintain the status quo?

### The Trap Mechanism (ABSTRACT)
- **Internal**: What belief or pattern keeps the protagonist bound?
- **External**: What circumstances reinforce the trap?
- **Why Valid**: Why hasn't the protagonist already escaped? (This must feel earned)

### The Catalyst (ABSTRACT)
- **Type**: What category of event breaks equilibrium?
- **Function**: Why does THIS break the loop when other things haven't?
- **Irony**: What's ironic about this catalyst? (The best catalysts contain irony)

### The Difficult Choice (ABSTRACT)
- **Nature**: What must be chosen between?
- **Cost**: What is lost either way?
- **Transformation**: How does making this choice change the protagonist?

### Stakes (ABSTRACT)
- **If they fail**: What is lost? (Be abstract but SPECIFIC—not "everything" but what category of loss)
- **If they succeed**: What is gained? (Again, specific category)

## Output Format

```json
{
  "abstraction_check": {
    "concrete_elements_received": ["list what user provided that was concrete"],
    "abstractions_extracted": {
      "element": "abstract version"
    }
  },
  "monomyth_stages": {
    "ordinary_world": "abstract description",
    "catalyst": "abstract description",
    "ordeal": "abstract description",
    "new_world": "abstract description",
    // ... other stages if needed
  },
  "abstract": {
    "protagonist": {
      "type": "...",
      "core_trait": "...",
      "trap": "...",
      "potential": "..."
    },
    "antagonist": {
      "type": "...",
      "nature": "...",
      "function": "..."
    },
    "trap_mechanism": {
      "internal": "...",
      "external": "...",
      "why_valid": "..."
    },
    "catalyst": {
      "type": "...",
      "function": "...",
      "irony": "..."
    },
    "difficult_choice": {
      "nature": "...",
      "cost": "...",
      "transformation": "..."
    },
    "stakes": {
      "if_fail": "...",
      "if_succeed": "..."
    }
  }
}
```

## Verification Before Proceeding

Before presenting to user, verify:
1. [ ] No concrete details in abstract level (names, places, occupations)
2. [ ] Each element could describe 10+ different stories
3. [ ] Monomyth stages are defined abstractly
4. [ ] The trap mechanism explains why protagonist hasn't already changed
5. [ ] The catalyst has inherent irony
6. [ ] Stakes are specific categories, not vague ("death" is too vague; "social death" or "physical death" is better)

If any check fails, revise before presenting.
```

## Example: Breaking Bad Extracted to Abstract

If user input: "A chemistry teacher gets cancer and decides to cook meth"

**Concrete elements received:**
- Chemistry teacher (occupation)
- Cancer (specific disease)
- Cook meth (specific criminal activity)

**Abstractions extracted:**
- Chemistry teacher → Expert whose skills are underutilized in legitimate life
- Cancer → External force that eliminates the future the protagonist counted on
- Cook meth → Deploying forbidden expertise for survival/provision

**Abstract level output:**
```json
{
  "protagonist": {
    "type": "Underutilized expert",
    "core_trait": "Capability suppressed by respectability",
    "trap": "Identity as provider requires playing by rules that don't reward their excellence",
    "potential": "Mastery that could dominate an unregulated domain"
  },
  "antagonist": {
    "type": "The constraints of legitimate success",
    "nature": "Systemic/societal + internal (their own morality)",
    "function": "Keeps the expert small by punishing deviation"
  },
  "catalyst": {
    "type": "Elimination of the future",
    "function": "Long-term thinking no longer matters; the ordinary world's rules become irrelevant",
    "irony": "The thing that kills them is what sets them free"
  }
}
```

This abstract level could generate:
- A chemistry teacher cooking meth (Breaking Bad)
- An accountant running a fraud scheme after a terminal diagnosis
- A weapons engineer selling secrets after learning their family is hostage
- A chef poisoning for hire after bankruptcy

The abstract level is the PATTERN. Concrete comes later.

## Next Step
Once user confirms the abstract mapping, proceed to `03-instantiation.md` where this pattern becomes a specific world.
