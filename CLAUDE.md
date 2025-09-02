# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website project for Grand Villa MHC, a 55+ senior manufactured home community in Springfield, MO. The project follows a strict PRD specification that must be adhered to exactly.

## Critical Requirements

### Variables Are Sacred
The PRD contains a fixed set of variables that MUST NOT be modified:
- Community Name: Grand Villa MHC
- Lot Rent: $365.00 per month
- Website Domain: grandvillamhc.com
- Contact Phone: (417) 869-5144
- All other variables in the PRD Variables block

### Core Non-Negotiables
1. **No emojis** - Use SVG line icons only (1.5px stroke)
2. **No RV terminology** - This is a permanent manufactured/mobile home community
3. **Pet policy exact language**: "We follow PetScreening.com's policies and approval process."
4. **Verification requirement**: Do not add any park facts not explicitly in the PRD variables

## Architecture

### Expected Directory Structure
```
/public
  index.html           # Single-page application with anchor navigation
  styles.css          # Main styles importing design tokens
  main.js            # Vanilla JS for interactions
  /assets            # Images, SVG icons, favicons
  robots.txt
  sitemap.xml
  llm.txt           # LLM manifest (required)
/seo
  meta.json
  schema.jsonld
/design
  tokens.css        # CSS variables for colors/spacing/typography
/content
  copy.md
/data
  comps.json       # 3BR/2BA apartment comparison data
/qa
  verification_log.md  # Maps every fact to source
```

### Technology Stack
- **Frontend**: Vanilla HTML/CSS/JavaScript (no frameworks)
- **Styling**: CSS with design tokens, responsive grid
- **Build**: Static files only
- **Portal**: DoorLoop integration at https://mhcpusa.app.doorloop.com/

## Development Commands

### Setup & Build
```bash
# Create directory structure
mkdir -p public/assets seo design content data qa work

# Development server (if needed)
python3 -m http.server 8000 --directory public
# or
npx serve public
```

### Quality Checks
```bash
# Validate HTML
npx html-validate public/index.html

# Check accessibility
npx lighthouse public/index.html --output json --output-path qa/lighthouse.json

# Verify all variables are used
grep -r "Grand Villa MHC\|365.00\|grandvillamhc.com" public/
```

## Key Implementation Notes

### Hero Section Pain Hook
Must auto-generate using local 3BR/2BA apartment data:
- Pattern: "Tired of paying $X for a 3-bed, 2-bath apartment in Springfield, MO?"
- X = computed from `/data/comps.json`
- Include source attribution and date

### Comparison Section Requirements
- Use 3BR/2BA apartments ONLY (no 1BR or 2BR)
- Show transparent monthly ownership calculation
- Include lot rent of $365.00
- Display sources and collection dates

### SEO Strategy
Long-tail local keywords to implement:
- "mobile home park in Springfield MO"
- "manufactured homes Springfield"
- "55+ manufactured home community Springfield"
- "lot rent Springfield MO"

### Color Palette
- Primary: Red (CTAs)
- Secondary: Blue (structure)
- Base: White
- Accent: Gold (dividers, icon strokes)

## Verification Requirements

Before any deployment:
1. Run verification check: Every fact must trace to PRD variables
2. Ensure `/qa/verification_log.md` is complete
3. Validate pet policy exact wording
4. Confirm no emojis present
5. Check that all CTAs link correctly:
   - Apply Now → https://mhcpusa.app.doorloop.com/
   - Resident Login → https://mhcpusa.app.doorloop.com/

## Performance Targets
- Lighthouse Performance: ≥ 90
- Lighthouse Accessibility: ≥ 95  
- Lighthouse SEO: ≥ 95
- Lighthouse Best Practices: ≥ 95

## Common Tasks

### Adding Content
Always verify against PRD variables before adding any community information. If a detail isn't in the PRD variables, omit it and add a TODO in `/qa/report.md`.

### Updating Apartment Comparisons
```bash
# Document sources in /data/comps.json with:
# - sources[] array
# - collected_at timestamp
# - 3BR/2BA average only
```

### Testing Responsiveness
Test breakpoints at 375px, 768px, 1024px, 1440px

## Important PRD References
- Full requirements: See `prd.md`
- Variables block: Lines 12-43 of `prd.md`
- Verification rules: Section 9 of `prd.md`
- QA criteria: Section 12 of `prd.md`