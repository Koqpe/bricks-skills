# Bricks Builder Skills

LLM-optimized skill documentation and development resources for [Bricks Builder](https://bricksbuilder.io/) WordPress theme.

## How to Use These Skills

> Just paste the link https://github.com/wpgaurav/bricks-skills to your AI assistant and tell it to read the skill files and it will take care of everything for you.

These skill files teach AI assistants how to work with Bricks Builder. Here's how to use them with different tools:

### With Claude Code (Terminal/CLI)

If you're using [Claude Code](https://claude.ai/code) in your terminal:

1. Open this folder in your terminal
2. Run `claude` to start Claude Code
3. Claude automatically reads `CLAUDE.md` and understands the skills
4. Just ask: *"Create a hero section with Bricks Builder"*

### With VS Code + Claude/Copilot Extensions

1. Open this folder in VS Code
2. The `CLAUDE.md` file provides context to AI extensions
3. For best results, open a skill file (e.g., `bricks-layouts.md`) in a tab
4. Ask your AI assistant to create Bricks layouts

### With Claude.ai, ChatGPT, or Gemini (Web)

1. **Copy the skill file content** - Open the skill you need (e.g., `bricks-layouts.md`)
2. **Paste into chat** - Start a new conversation and paste the skill content
3. **Ask your question** - Now the AI understands Bricks format

**Example workflow:**
```
1. Copy contents of bricks-layouts.md
2. Paste into Claude/ChatGPT/Gemini
3. Ask: "Create a pricing table with 3 tiers using Bricks Builder"
4. Copy the JSON output
5. In Bricks Builder, right-click in structure panel and paste
```

### With Cursor, Windsurf, or Other AI IDEs

1. Open this folder as your project
2. The AI will read `CLAUDE.md` for context
3. Reference skill files in your prompts: *"Using bricks-layouts.md, create a mobile-first grid"*

### Quick Start Example

**Want to create a card grid?**

1. Tell your AI: *"Read bricks-layouts.md and create a 3-column card grid with hover effects"*
2. Copy the generated JSON
3. In Bricks Builder, right-click in the structure panel
4. Select "Paste" or use Ctrl/Cmd+V
5. Elements and global classes are pasted together

## What's Included

### Theme Source Code (Optional)

- **`bricks/`** - Bricks Builder theme source (not included - paid product)

For best results, add the Bricks theme files to a `bricks/` folder in this repository. This allows the AI to reference actual element implementations, understand control structures, and provide more accurate code suggestions.

**To add Bricks source:**
1. Purchase Bricks from [bricksbuilder.io](https://bricksbuilder.io/)
2. Download the theme zip
3. Extract to `bricks/` folder in this repository
4. The `.gitignore` already excludes it from version control

### Skill Documentation

| Skill | Description |
|-------|-------------|
| [bricks-layouts.md](bricks-layouts.md) | Ready-to-paste sections, JSON formats, Core Framework CSS classes |
| [bricks-elements.md](bricks-elements.md) | Building custom elements with controls and rendering |
| [bricks-templates.md](bricks-templates.md) | Creating and managing templates programmatically |
| [bricks-hooks.md](bricks-hooks.md) | Complete filter and action reference |
| [core-framework.css](core-framework.css) | Utility-first CSS framework reference |

## Bricks Builder JSON Format

Bricks uses two distinct JSON formats:

### Sections (Copy/Paste Format)

For pasting directly into the builder via clipboard:

```json
{
  "content": [
    {
      "id": "sec001",
      "name": "section",
      "parent": 0,
      "children": ["con001"],
      "settings": {
        "_cssGlobalClasses": ["padding-vertical-xl"]
      }
    }
  ],
  "source": "bricksCopiedElements",
  "sourceUrl": "https://example.com",
  "version": "2.0.1",
  "globalClasses": [],
  "globalElements": []
}
```

### Templates (Site-Wide Assignment)

Full templates with metadata for importing via Bricks Templates system:

```json
{
  "id": 1195,
  "name": "header-new",
  "title": "Header New",
  "type": "header",
  "header": [...elements...],
  "global_classes": [...]
}
```

### Element Structure

Each element requires:

| Property | Description |
|----------|-------------|
| `id` | Unique 6-character alphanumeric ID |
| `name` | Element type (section, container, heading, etc.) |
| `parent` | Parent element ID or `0` for root |
| `children` | Array of child element IDs |
| `settings` | Element-specific settings |

### Key Element Types

**Layout:** `section`, `container`, `block`, `div`
**Content:** `heading`, `text`, `text-basic`, `button`, `image`
**Navigation:** `nav-nested`, `dropdown`, `toggle`
**Interactive:** `slider-nested`, `accordion`, `form`

## Responsive Breakpoints

Append breakpoint suffix to any setting:

| Breakpoint | Suffix | Max Width |
|------------|--------|-----------|
| Desktop | (none) | - |
| Laptop | `:laptop` | 1366px |
| Tablet Landscape | `:tablet_landscape` | 1024px |
| Tablet Portrait | `:tablet_portrait` | 991px |
| Mobile Landscape | `:mobile_landscape` | 767px |
| Mobile Portrait | `:mobile_portrait` | 478px |

Example:
```json
{
  "_direction": "row",
  "_direction:tablet_portrait": "column",
  "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))",
  "_gridTemplateColumns:mobile_portrait": "repeat(1, minmax(0, 1fr))"
}
```

## Using with LLMs

These skills are designed for use with LLM assistants (Claude, GPT, etc.) to:

1. **Generate layouts** - Create Bricks JSON markup from design descriptions
2. **Build custom elements** - Create PHP element classes with controls and rendering
3. **Set up query loops** - Configure posts, terms, and user loops
4. **Add hooks** - Implement filters and actions for customization
5. **Optimize styling** - Use Core Framework utility classes effectively

### Example Prompts

> "Create a 3-column responsive grid of feature cards using Bricks Builder. Each card should have an icon, heading, and description with hover effects."

> "Build a custom Bricks element for displaying team members with image, name, role, and social links."

> "Add a filter to modify the Posts element query to only show posts from the last 30 days."

The LLM will reference `bricks-layouts.md`, `bricks-elements.md`, and `bricks-hooks.md` to generate proper code.

## WP-CLI Commands

```bash
wp bricks regenerate_assets  # Regenerate CSS files
```

## Documentation

- Official: https://academy.bricksbuilder.io/
- Developer Docs: https://academy.bricksbuilder.io/collection/developer/

## License

- Theme source code: Proprietary (Bricks Builder license)
- Skill documentation: MIT
