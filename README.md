# Bricks Builder Skill

An AI skill for one-shotting [Bricks Builder](https://bricksbuilder.io/) designs as JSON — hero sections, full landing pages, headers/footers, query loops with faceted filters, ACF-driven layouts, conditions, animations, and popups. Every settings key and value shape is verified against the Bricks **2.3.6** theme source, not guessed.

## What's inside

```
bricks-skills/            ← the repo is the skill
├── SKILL.md              ← start here: workflow, rules, routing table
├── references/           ← 19 focused references (loaded on demand)
│   ├── json-formats.md       clipboard / template / postmeta formats + validation
│   ├── style-settings.md     every _setting + exact JSON value shapes
│   ├── elements.md           full element catalog + nestable structures
│   ├── layout-recipes.md     grids, heroes, cards, overlap, sticky, full pages
│   ├── query-loops.md        hasLoop + query JSON for posts/terms/users
│   ├── query-filters.md      live search, facets, sort, AJAX pagination
│   ├── dynamic-data.md       {tags}, filters, args, {echo:}
│   ├── acf-providers.md      ACF deep dive (repeaters, groups, flexible) + Meta Box etc.
│   ├── conditions.md         _conditions JSON (incl. dynamic data conditions)
│   ├── interactions.md       _interactions, full animation list, recipes
│   ├── popups.md             popup settings, triggers, limits, AJAX context
│   ├── templates.md          template types, conditions, header behaviors
│   ├── components-classes.md components, global classes/variables, palettes
│   ├── theme-styles.md       theme styles, breakpoints, CSS pipeline
│   └── forms / woocommerce / hooks / custom-elements / assets-permissions
└── patterns/              ← 17 validated, paste-ready JSON files (see INDEX.md)
```

## Use it with Claude Code

```bash
# clone, then either work inside the repo (CLAUDE.md routes automatically)…
cd bricks-skills && claude

# …or install the skill globally:
git clone https://github.com/wpgaurav/bricks-skills ~/.claude/skills/bricks
```

Then just ask:

> "Build a SaaS landing page: split hero, logo strip, 3-col features, pricing, FAQ, CTA. Brand color #6d28d9."

> "Create a filterable course archive — search, category filter, price sort, AJAX pagination — as paste-ready JSON."

> "Team section from my ACF repeater `team_members` (photo, name, role, linkedin_url)."

You get a `.json` file: paste it into the builder (clipboard format) or import it via Bricks → Templates (template format).

## Use it with other AI tools

Paste `SKILL.md` plus the relevant reference file(s) into Claude.ai / ChatGPT / Gemini, then ask for the layout. The references are self-contained.

## Why this exists

LLMs reliably produce Bricks JSON that *parses* but silently fails: camelCase typography keys, flat box-shadows, invented breakpoint names, accordion items missing their structural classes. This skill pins the exact shapes from the source:

| Silent failure | Verified shape |
|----------------|----------------|
| `"_typography": {"fontSize": "18px"}` | `"_typography": {"font-size": "18px"}` |
| `"_boxShadow": {"offsetY": "8px"}` | `"_boxShadow": {"values": {"offsetY": "8"}, "color": {…}}` |
| `"_gradient": {"stops": […]}` | `"_gradient": {"colors": [{"color": {…}, "stop": "0"}]}` |
| `"_padding:tablet"` | `"_padding:tablet_portrait"` |
| accordion item = plain blocks | title/content wrappers need `_hidden._cssClasses` |

Plus the things docs rarely cover: the exact clipboard wrapper the builder writes, template condition objects, popup setting keys (including Bricks' own `popupJustifyConent` typo), filter element wiring, ACF repeater loop `objectType`s, and the `key:breakpoint:pseudo` settings grammar.

## Patterns

17 validated files in [patterns/](patterns/) — heroes, feature grid, pricing, testimonials slider, FAQ accordion (with FAQ schema), CTA, contact form, ACF team loop, filterable blog archive, header/footer/popup templates, plus three **BEM class-based test builds** (`bem-hero`, `bem-card-grid`, `bem-pricing`) where every style lives in `block__element--modifier` global classes. Each file passes a structural integrity check (tree reciprocity, class references, format keys). See [INDEX.md](patterns/INDEX.md).

## License

- Skill documentation & patterns: MIT
- Bricks theme: proprietary (not included) — [bricksbuilder.io](https://bricksbuilder.io/)
