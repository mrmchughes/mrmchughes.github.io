---
publish: true
created: 2026-05-07
modified: 2026-05-07T16:03:35.093Z
---

# Untitled

> One-sentence description of what this technique does and why it matters.

## Trigger

What signal in enumeration tells you to reach for this? Be specific — "you see X in scan output" or "you have credential type Y." This is the most important field — it's what turns this note into a methodology entry instead of a reference card.

## Prerequisites

- Required access level (unauthenticated, low-priv user, admin, etc.)
- Required information (creds, hashes, knowledge of target)
- Network position (internal, external, foothold)
- Tools needed: \[\[]]

## Procedure

### Setup

```bash
# Tool installation, environment prep, etc.
```

### Execution

```bash
# The actual commands. Annotate non-obvious flags.
```

### Expected output

```
# What success looks like. Include a sample if non-trivial.
```

## Pivot

What does success unlock? Where do I go next?

- If you got X, head to \[\[]]
- If you got Y, head to \[\[]]
- Common follow-ons: \[\[]]

## OPSEC / Detection

- Noise profile: loud / moderate / quiet
- What logs are generated
- Common detection signatures (Sigma rules, EDR alerts)
- Mitigations / how to reduce noise

## Common pitfalls

- Things that look like the technique failed but are actually environmental
- Misconfigurations that change behavior
- Version-specific gotchas

## Variants

- Alternative approaches when the primary fails
- Related techniques that achieve the same goal: \[\[]]

## References

- Original research / disclosure
- HackTricks / PayloadsAllTheThings entry
- Tool documentation
- Boxes where you've used it: \[\[]]

## Related notes

- \[\[]]
