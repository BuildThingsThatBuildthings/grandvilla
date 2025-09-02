# Grand Villa MHC Website

Static website for Grand Villa MHC, a 55+ senior manufactured home community in Springfield, MO.

## Project Structure

```
/public             # Production files
  index.html        # Main website (single-page)
  styles.css        # Compiled styles
  main.js          # JavaScript functionality
  /assets          # Images and icons
  robots.txt       # SEO crawler directives
  sitemap.xml      # XML sitemap
  site.webmanifest # PWA manifest
  llm.txt         # LLM-readable description

/design            # Design system
  tokens.css      # CSS variables

/data             # Data files
  comps.json     # Apartment comparison data

/content          # Content management
/seo             # SEO configuration
/qa              # Quality assurance
/work            # Working files
```

## Key Features

- **Single-page design** with smooth scroll navigation
- **Pain-based hero hook** comparing to local 3BR/2BA apartment costs
- **Responsive layout** optimized for all devices
- **WCAG 2.1 AA compliant** accessibility
- **SEO optimized** with long-tail local keywords
- **DoorLoop integration** for resident portal and applications

## Development

### Local Development Server

```bash
# Python
python3 -m http.server 8000 --directory public

# Node.js
npx serve public
```

### Performance Targets

- Lighthouse Performance: ≥ 90
- Lighthouse Accessibility: ≥ 95
- Lighthouse SEO: ≥ 95
- Lighthouse Best Practices: ≥ 95

## Important Requirements

- **No emojis** - Use SVG line icons only
- **Exact pet policy language**: "We follow PetScreening.com's policies and approval process."
- **Verified facts only** - All content must trace to PRD variables
- **3BR/2BA comparisons only** - No 1BR or 2BR comparisons

## Contact

- Phone: (417) 869-5144
- Email: info@grandvillamhc.com
- Website: https://grandvillamhc.com

## License

© 2025 Grand Villa MHC. All rights reserved.