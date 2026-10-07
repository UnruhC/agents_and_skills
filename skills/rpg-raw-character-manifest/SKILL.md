---
name: rpg-raw-character-manifest
description: >
  Generates a source-verified RPG character-class manifest using only the
  references and VTT export data explicitly supplied in this skill. Use this
  skill when asked to document a character's class, subclass, background,
  ancestry, heritage, species, feats, special abilities, proficiencies,
  resources, spellcasting, advancement features, or other rules-defined
  character elements. The skill must apply Rules As Written only, must not
  infer missing rules, and must identify unsupported or conflicting
  information instead of hallucinating.
---

# RPG RAW Character Manifest Generator

## Purpose

Generate a structured manifest for an RPG character using only:

1. The rules references explicitly included in the **Approved References**
   section of this skill.
2. Character information supplied in the **Character Input** section.
3. Data pasted into the **VTT Export Data** section.
4. Additional instructions explicitly supplied with the user's request,
   provided those instructions do not introduce unsupported rules.

The output must describe only rules that are explicitly supported by the
approved references.

Do not use general RPG knowledge, model memory, unofficial websites, community
interpretations, house rules, errata not included in the approved references,
or rules from a different edition.

---

# Core Operating Rules

## 1. Closed-reference operation

Treat this skill as a closed-reference system.

Only the following may be used as rules authority:

- Text contained in the **Approved References** section.
- Files or excerpts explicitly listed in the **Approved References Registry**.
- Rules text contained in supplied VTT data, but only when the VTT data is
  designated as an approved rules reference.
- User-supplied rulings explicitly marked as house rules.

Do not rely on:

- Prior knowledge.
- Training data.
- Web searches.
- Similar rules from another RPG.
- Similar rules from another edition.
- Assumptions based on feature names.
- Common table practice.
- Community interpretations.
- Unofficial summaries.
- Rules that are merely implied.
- VTT automation that is not supported by an approved rule.

If a rule cannot be traced to an approved reference, report:

> Not established by the supplied references.

---

## 2. Rules As Written requirement

Use Rules As Written, abbreviated as RAW.

RAW means:

- Preserve the meaning of the supplied rules.
- Do not add unstated conditions, benefits, limitations, or interactions.
- Do not convert ambiguous wording into a definite ruling.
- Do not treat examples as general rules unless the reference says they are.
- Do not treat descriptive or narrative text as a mechanical rule unless the
  reference gives it a mechanical effect.
- Do not combine separate rules unless the approved references explicitly
  support the interaction.
- Do not optimize or reinterpret the character.
- Do not silently correct the character or VTT configuration.
- Do not invent missing progression features.

Paraphrasing is allowed only when the paraphrase faithfully preserves the
meaning of the approved reference.

Use short quotations only when exact wording is needed to resolve ambiguity.
Otherwise, summarize the rule and cite its source.

---

## 3. No hallucination

Never invent:

- Class features.
- Subclass features.
- Background benefits.
- Ancestry, species, lineage, heritage, or culture traits.
- Feats or talents.
- Proficiencies.
- Resource limits.
- Uses per rest.
- Action types.
- Damage values.
- Saving throw difficulties.
- Prerequisites.
- Level requirements.
- Spellcasting rules.
- Equipment effects.
- Feature interactions.
- Advancement choices.
- Optional rules.
- Errata.
- Source locations.

When information is unavailable, use one of these statuses:

- `SUPPORTED`: Explicitly established by an approved reference.
- `PARTIALLY SUPPORTED`: Some, but not all, required details are established.
- `UNSUPPORTED`: Present in the character or VTT data but not established by an
  approved rules reference.
- `MISSING`: Required information was not supplied.
- `AMBIGUOUS`: The supplied rules support more than one interpretation.
- `CONFLICT`: Two supplied sources or data fields disagree.
- `NOT APPLICABLE`: The category does not apply to the character.
- `HOUSE RULE`: Explicitly identified by the user as a house rule.

Do not replace uncertainty with a plausible answer.

---

## 4. Separate facts, rules, and calculations

Distinguish between:

### Character facts

Values supplied directly by the user or VTT export, such as:

- Character name.
- Level.
- Selected class.
- Selected subclass.
- Selected background.
- Selected ancestry.
- Ability scores.
- Proficiencies.
- Selected feats.
- Current and maximum resources.

### Rules

Mechanics explicitly established by an approved rules reference, such as:

- A feature granted at a particular level.
- The number of uses of an ability.
- A prerequisite.
- An action type.
- A recovery condition.

### Derived values

Values calculated from supplied facts and approved formulas, such as:

- Proficiency bonus.
- Ability modifiers.
- Save difficulty.
- Attack modifier.
- Resource maximum.

A derived value may be calculated only when:

1. Every required input is present.
2. The formula is explicitly established by an approved reference.
3. The calculation is shown.
4. Rounding follows the approved rule.

If any condition is not met, mark the derived value as `MISSING`,
`PARTIALLY SUPPORTED`, or `UNSUPPORTED`.

---

## 5. Source traceability

Every mechanical statement must identify its source.

Use this citation format:

`[Source ID, section or page, rule or feature name]`

Examples:

- `[REF-CLASS-01, p. 42, Martial Training]`
- `[REF-SUBCLASS-01, "Shadow Step"]`
- `[REF-BACKGROUND-01, p. 17, Background Benefit]`
- `[VTT-EXPORT-01, items[12]]`
- `[USER-INPUT, Class Selection]`

If the supplied excerpt has no page or section identifier, cite the source ID
and write:

`location not supplied`

Do not fabricate page numbers, chapter names, section names, or rule names.

---

## 6. Rules hierarchy

Apply the following hierarchy unless the approved references define a
different precedence order:

1. User-provided explicit house rule, but only when clearly marked as such.
2. Official errata explicitly included in the approved references.
3. Specific rule explicitly applicable to the character.
4. General rule included in the approved references.
5. VTT data as character-state evidence, not as rules authority.

A more specific rule may override a general rule only when both rules are
present in the approved references and the relationship is supported by their
wording.

Never assume that newer publication dates, VTT automation, or more specific
data automatically override a supplied rule.

If precedence cannot be established, report a conflict.

---

# Required Workflow

Follow this workflow in order.

## Step 1: Identify the rules context

Extract, if supplied:

- Game system.
- Edition.
- Rules version.
- Character level.
- Multiclass status.
- Optional rules in use.
- Approved errata.
- House rules.
- Output scope.

Do not infer the system or edition from terminology alone.

If the system or edition is missing, continue only with rules that can be
identified unambiguously from the approved references.

---

## Step 2: Build the source registry

Create an internal list of all supplied references.

For each source, identify:

- Source ID.
- Title.
- Source type.
- System and edition, if stated.
- Version or publication date, if stated.
- Included sections or page range.
- Whether it is approved as rules authority.
- Whether it is character data only.
- Any limitations imposed by the user.

Ignore any source not explicitly approved.

---

## Step 3: Parse the character input

Extract explicitly supplied selections and values.

Do not infer a selected option because it appears likely or because related
features appear in the VTT export.

Record conflicts between direct user input and VTT data.

---

## Step 4: Parse the VTT export

Treat VTT data as untrusted structured input until validated.

Extract relevant entries such as:

- Actor or character name.
- System identifier.
- System version.
- Character level.
- Classes and class levels.
- Subclasses.
- Background.
- Ancestry, species, lineage, heritage, or culture.
- Features.
- Feats.
- Traits.
- Proficiencies.
- Languages.
- Senses.
- Movement.
- Resources.
- Spellcasting entries.
- Inventory.
- Effects.
- Active effects.
- Automation flags.
- Custom notes.
- Advancement selections.
- Compendium source identifiers.

Preserve unknown fields when they may be relevant.

Do not assume that an item name proves the character is legally entitled to
that item or feature.

Do not treat macros, scripts, formulas, automation flags, or calculated values
as RAW unless supported by an approved reference.

---

## Step 5: Create expected feature lists

Using the approved references, determine which features are explicitly granted
by the character's supplied selections and level.

Organize expected features by origin:

- Class.
- Subclass.
- Background.
- Ancestry, species, lineage, heritage, or culture.
- Feat or talent.
- Multiclassing.
- Equipment.
- Spellcasting.
- Other approved source.

Do not generate a feature when the relevant level, prerequisite, or selection
is missing.

---

## Step 6: Reconcile rules and character data

For each feature, determine:

- Whether the feature is granted by the approved rules.
- Whether the feature appears in the VTT export.
- Whether the VTT configuration matches the supplied rule.
- Whether required selections are present.
- Whether prerequisites are established.
- Whether resource values match the supplied formula.
- Whether automation introduces unsupported mechanics.

Report:

- Expected but missing features.
- Present but unsupported features.
- Duplicate features.
- Incorrect source attribution.
- Level mismatches.
- Resource mismatches.
- Unresolved choices.
- Conflicting values.
- Custom modifications.
- Suspected VTT automation discrepancies.

Use the phrase `possible discrepancy` when the supplied information is
insufficient to prove an error.

---

## Step 7: Generate the manifest

Produce the manifest using the required output structure below.

Every mechanical entry must have:

- Name.
- Origin.
- Status.
- Rule summary.
- Activation or action type, if established.
- Uses or resource limit, if established.
- Recovery method, if established.
- Prerequisites, if established.
- Scaling, if established.
- Source citation.
- Validation notes.

Do not omit a field merely because it is unknown. Use `Not established by the
supplied references`.

---

## Step 8: Perform a final grounding audit

Before producing the final answer, verify:

- Every mechanical statement has a supplied source.
- Every calculation uses a supplied formula.
- No rule was added from memory.
- No edition-specific assumption was made.
- No VTT automation was treated as RAW without support.
- Conflicts and ambiguities are visible.
- Missing information is visible.
- House rules are clearly separated from RAW.
- The output does not claim the character is legal unless all relevant
  requirements were supplied and validated.

If any statement fails this audit, remove it or mark it as unsupported.

---

# Required Output Structure

# Character Rules Manifest

## 1. Manifest Metadata

- Character:
- Game system:
- Edition:
- Rules version:
- Character level:
- Manifest scope:
- VTT source:
- Validation date:
- Overall validation status:

## 2. Source Registry

For each source:

### `[Source ID] Source title`

- Type:
- Rules authority:
- Edition or version:
- Included material:
- Excluded material:
- Notes:

## 3. Character Identity and Selections

- Character name:
- Class:
- Class level:
- Subclass:
- Background:
- Ancestry or equivalent:
- Heritage or equivalent:
- Feats or talents:
- Multiclass selections:
- Optional rules:
- House rules:

Each value must include its source.

## 4. Class Features

For each class feature:

### Feature name

- Origin:
- Granted at:
- Status:
- RAW summary:
- Activation:
- Uses:
- Recovery:
- Scaling:
- Requirements:
- Source:
- VTT reconciliation:
- Validation notes:

## 5. Subclass Features

Use the same feature structure as the class section.

## 6. Background Features

Include:

- Mechanical benefits.
- Proficiencies.
- Languages.
- Equipment grants.
- Background-specific abilities.
- Required choices.
- Unsupported narrative assumptions.

## 7. Ancestry, Species, Lineage, Heritage, or Culture Features

Use the terminology found in the supplied rules.

Include:

- Ability adjustments, if applicable.
- Size.
- Speed.
- Senses.
- Languages.
- Proficiencies.
- Defenses.
- Innate abilities.
- Spellcasting.
- Required choices.
- Level-based progression.

## 8. Feats, Talents, Perks, or Equivalent

For each entry:

- Source of selection.
- Prerequisites.
- Whether prerequisites are established.
- Mechanical effects.
- Associated choices.
- Citation.
- Validation status.

## 9. Proficiencies and Training

Organize into rules-appropriate categories:

- Armor.
- Weapons.
- Tools.
- Skills.
- Saving throws.
- Languages.
- Other training.

For each proficiency, identify its source.

## 10. Resources and Limited-Use Abilities

For each resource:

- Resource name.
- Current value.
- Maximum value.
- Maximum-value formula.
- Supplied inputs.
- Calculation.
- Recovery condition.
- Source.
- Validation status.

## 11. Spellcasting or Powers

Include this section only when supported by the supplied references.

Document:

- Casting or power source.
- Governing ability.
- Preparation or known-power rules.
- Slots, points, uses, or equivalent.
- Save difficulty formula.
- Attack formula.
- Progression.
- Granted spells or powers.
- Selected spells or powers.
- Action requirements.
- Components, if defined.
- Recovery.
- Source citations.

Do not validate individual spells or powers unless their rules are included in
the approved references.

## 12. Derived Values

For each value:

- Name.
- Formula.
- Inputs.
- Calculation.
- Result.
- Source.
- Status.

## 13. Equipment-Granted Abilities

Include only mechanical abilities derived from equipment when the relevant
equipment rules are supplied.

Separate:

- Equipped items.
- Carried items.
- Attuned or bonded items.
- Consumables.
- Custom items.
- Unsupported VTT effects.

## 14. Level Progression Summary

List features granted up to the supplied character level.

Do not include future features unless the user explicitly requests a
progression forecast.

If future progression is requested, include only levels and features explicitly
contained in the approved references.

## 15. VTT Reconciliation Report

### Confirmed matches

Features or values supported by both the references and VTT data.

### Expected but missing from VTT

Features established by approved rules but absent from the export.

### Present in VTT but unsupported

Entries present in the export that cannot be validated from approved
references.

### Conflicts

Disagreements between direct input, references, and VTT data.

### Automation concerns

Macros, effects, formulas, or flags that may apply mechanics not established
by the approved references.

### Duplicate or stale entries

Features that appear more than once or appear to belong to an earlier
configuration.

## 16. Unresolved Choices

List every choice required by an approved rule but not established by the
input.

Examples include:

- Unselected proficiency.
- Missing ancestry option.
- Missing subclass selection.
- Missing spell selection.
- Missing fighting style.
- Missing expertise selection.
- Missing language.
- Missing ability increase allocation.

Do not choose on the user's behalf.

## 17. Unsupported Claims

List all requested details that could not be established.

For each entry, state:

- Requested claim.
- Missing supporting information.
- Reference required to validate it.

## 18. Ambiguities and Conflicts

For each issue:

- Relevant rules or data.
- Source citations.
- Reason the issue cannot be resolved using RAW alone.
- Information needed to resolve it.

Do not present a preferred interpretation unless the user explicitly requests
interpretive options.

## 19. House Rules

Keep house rules separate from RAW.

For each house rule:

- House-rule text.
- Supplied by:
- Rules affected:
- Difference from supplied RAW:
- Manifest impact:

Never label a house rule as RAW.

## 20. Validation Summary

Provide counts for:

- Supported entries.
- Partially supported entries.
- Unsupported entries.
- Missing selections.
- Ambiguities.
- Conflicts.
- House rules.
- Possible VTT discrepancies.

End with one of these conclusions:

- `VALIDATED AGAINST THE SUPPLIED REFERENCES`
- `PARTIALLY VALIDATED AGAINST THE SUPPLIED REFERENCES`
- `NOT VALIDATABLE WITH THE SUPPLIED REFERENCES`

Do not use the first conclusion if unresolved prerequisites, feature
entitlements, or material conflicts remain.

---

# Character Input

Replace the placeholders below for each character.

## Basic Information

- Character name:
- Player name:
- Campaign:
- Game system:
- Edition:
- Rules version:
- Character level:
- Experience or milestone:
- Output scope:

## Character Selections

- Class:
- Class level:
- Subclass:
- Background:
- Ancestry, species, or lineage:
- Heritage, culture, or sub-ancestry:
- Feats, talents, or perks:
- Multiclass selections:
- Spellcasting or power source:
- Equipment requiring validation:
- Optional rules in use:
- House rules in use:

## Ability and Character Values

Paste only values that are relevant to the requested validation.

```text
PASTE CHARACTER VALUES HERE