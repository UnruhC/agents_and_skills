---
name: dnd55-dark-matter-psi-warrior
description: >
  Generates a source-verified RAW character manifest for a level 3 D&D 5.5e
  Fighter with the Psi Warrior subclass in the Dark Matter science-fiction
  setting. Use this skill to validate Fighter features, Psi Warrior features,
  background benefits, species traits, origin feats, proficiencies, weapon
  masteries, equipment, science-fiction equipment, and VTT character data.
  The skill may use only the approved rules excerpts embedded in or supplied
  to this skill. It must not reconstruct missing D&D or Dark Matter rules from
  model knowledge.
---

# D&D 5.5e Dark Matter Psi Warrior Manifest

## Purpose

Generate a Rules As Written character manifest for the following fixed
character framework:

- Rules system: Dungeons & Dragons 2024 revision, commonly called D&D 5.5e
- Setting or supplement: Dark Matter: Sci-Fi 5.5E
- Class: Fighter
- Fighter level: 3
- Subclass: Psi Warrior
- Total character level: 3
- Multiclassing: Not permitted unless the user explicitly changes the scope
- Validation mode: Closed-reference RAW validation

The manifest combines rules from two distinct categories:

1. D&D 2024 core rules governing the Fighter, Psi Warrior, character creation,
   actions, rests, proficiencies, equipment, and derived values.
2. Dark Matter rules governing science-fiction species, backgrounds,
   equipment, weapons, armor, technology, setting-specific options, and any
   applicable variant rules.

Do not assume that Dark Matter replaces a D&D core rule unless an approved
Dark Matter excerpt explicitly says that it does.

---

# Non-Negotiable Grounding Rules

## Closed-reference operation

Use only:

- Rules text pasted into the Approved Reference Content section.
- Files explicitly registered in the Approved References Registry.
- Character selections explicitly supplied in Character Input.
- Character-state information contained in the VTT Export Data section.
- House rules explicitly identified as house rules by the user.

Do not use:

- Model memory of D&D.
- General knowledge about the Fighter.
- General knowledge about the Psi Warrior.
- General knowledge about Dark Matter.
- Unofficial character guides.
- Wiki pages.
- Search engine results.
- Earlier editions of Dark Matter.
- The 2014 D&D Fighter or 2014 Psi Warrior.
- Earlier playtest rules.
- A VTT compendium unless its rules text is supplied and approved.
- Rules inferred from an item, feature, effect, or compendium name.

The skill may recognize identifiers and organize supplied data, but an
identifier alone is not proof of a rule.

If an assertion cannot be supported, write:

> Not established by the supplied references.

---

# Edition Lock

The expected edition is:

```yaml
system: Dungeons & Dragons
core_rules_version: "2024"
informal_version_name: "5.5e"
supplement: "Dark Matter: Sci-Fi 5.5E"
class: "Fighter"
subclass: "Psi Warrior"
class_level: 3
total_level: 3