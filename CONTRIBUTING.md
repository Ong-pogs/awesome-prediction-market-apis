# Contributing

Additions are welcome. This list is researched rather than scraped, so an entry has to carry enough for a reader to decide without opening the site.

## Entry format

```markdown
- **[Name](https://example.com)**: One sentence on what it actually does.
  An optional second line for the detail that matters.
  - **Best for:** the specific reader this suits
  - **Pricing:** what the vendor's own page says, or "not publicly listed"
  - **Phase:** live / beta / waitlist / stale / unmaintained
  - **Reviewed:** Mon YYYY
```

For open-source projects, replace **Pricing** with the repository facts:

```markdown
  - **Licence:** MIT · **Stars:** 1.2k · **Last commit:** Jul 2026
```

## What gets checked before merge

1. **The link resolves.** A 403 from a bot defence is fine; a 404 is not.
2. **Pricing is sourced from the vendor.** If the site does not publish pricing, the entry says `not publicly listed`. Do not estimate.
3. **Repository facts come from the GitHub API**, not from the project's own README.
4. **Phase is honest.** A repository with no commits in over a year is `unmaintained`, and it gets a ⚠️ note. This is not a judgement, it is what a reader needs before building on it.
5. **Scope.** Developer-facing surfaces: APIs, SDKs, MCP servers, data feeds, datasets, agent tooling. General macro data APIs and generic LLM frameworks with no prediction market surface are out of scope.

## Not accepted

- Referral or affiliate links.
- Entries for products with no public documentation and no way to evaluate them.
- Superlatives. Describe what it does, not how good it is.
- Anything presenting a cross-venue price gap as guaranteed profit. Gaps measured on mid-prices are indicative until checked against live depth, fees and resolution equivalence.

## Adding yourself

That is fine, and it is how most entries get here. Say so in the pull request and write the entry to the same standard as the rest. An entry that reads as marketing copy will be edited down to what it does.
