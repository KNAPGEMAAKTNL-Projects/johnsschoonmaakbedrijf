---
paths:
  - src/components/**/*.astro
  - src/pages/**/*.astro
---

# Astro Conversion: Layout Preservation

When converting Stitch-generated HTML to Astro components, treat this as **mechanical translation, not creative interpretation**. Claude Code has a documented layout-normalization bias (GitHub issue #1638 on anthropics/claude-code) that causes it to "enhance" or "improve" code during structural transformations, even with explicit instructions not to.

## Absolute prohibitions

- NEVER add `max-w-*`, `mx-auto`, or `container` wrappers not present in the source HTML
- NEVER change `grid-cols-*`, `col-span-*`, or `gap-*` values
- NEVER normalize `py-*`, `px-*`, `mt-*`, `mb-*` spacing across sections
- NEVER symmetrize asymmetric layouts (e.g. converting a 7/5 grid split into 6/6)
- NEVER replace or simplify Tailwind class combinations
- NEVER remove classes you consider "redundant" or "unnecessary"
- NEVER restructure the HTML nesting or element hierarchy
- NEVER homogenize section heights or vertical rhythm

## Only these changes allowed

1. Add `---` frontmatter fence with imports
2. Import `Layout` and `Image` components
3. Wrap content in `<Layout>` tags
4. Convert `<img>` to `<Image>` with proper `src` imports (preserving ALL attributes)
5. Move `<head>` metadata to Layout props
6. Add responsive breakpoint classes (`sm:`, `md:`, `lg:`) as **additions** to existing classes — never replacing them
7. Add Astro-specific directives (`client:load`, `client:visible`, etc.)
8. Add `ViewTransitions` import and component
9. Extract shared elements (Header, Footer) into components — preserving their exact markup and classes
10. Add TypeScript prop types in frontmatter

## Visual regression verification

After every conversion, compare the Astro output against the source HTML using Playwright screenshot comparison:

```javascript
import { test, expect } from '@playwright/test';

test('homepage layout matches source', async ({ page }) => {
  await page.goto('file:///path/to/source/index.html');
  const source = await page.screenshot({ fullPage: true });
  await page.goto('http://localhost:4321/');
  await expect(page).toHaveScreenshot('homepage.png', {
    maxDiffPixelRatio: 0.01
  });
});
```

Set `maxDiffPixelRatio: 0.01` (1% tolerance) to catch layout drift while allowing minor rendering differences.

## CSS class diff check

Run this command to instantly verify no classes were added, removed, or changed during conversion:

```bash
diff <(grep -oP '(?<=class=")[^"]+' source.html | tr ' ' '\n' | sort -u) \
     <(grep -oP '(?<=class=")[^"]+' output.astro | tr ' ' '\n' | sort -u)
```

Any lines prefixed with `<` are classes that were dropped. Any lines prefixed with `>` are classes that were added. Only responsive breakpoint additions (`sm:`, `md:`, `lg:` prefixed classes) are acceptable additions. Removals are never acceptable.
