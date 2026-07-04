# yahya-shihabe.pages.dev

**Portfolio & agency proof hub** - bilingual (English/Swedish) landing page that features public showcase projects alongside Swedish SMB proof-of-concept demos.

Live site: [yahya-shihabe.pages.dev](https://yahya-shihabe.pages.dev)

---

## What this is

This is Showcase 3 in a portfolio proof roadmap. It serves two audiences from a single page:

| Audience | Language | What they see |
|----------|----------|---------------|
| **Remote employers** | English | Project portfolio (Showcase 1 & 2), tech stack, architecture, deployed demos, SMB demo concepts |
| **Swedish SMB prospects** | Swedish | Service pitch, 3 screenshot-backed chatbot concepts (FriluftsByn, LS Bygg, The Unit), process, about |

A language toggle (EN / SV) switches the view with a fade transition, and all shared UI elements (nav labels, CTAs, booking section) update text via `data-i18n` attributes.

## Architecture

This is a **single static HTML file** deployed on Cloudflare Pages - no build step, no framework, no runtime dependencies.

```
index.html
├── Tailwind CSS (CDN) - utility styling
├── Fraunces + Inter (Google Fonts) - display and body type
├── Cal.com embed - booking widget
└── i18n.js (inline) - language toggle and scroll-reveal
```

## Featured projects

The English portfolio section links to two public proof projects:

| Project | Live demo | GitHub |
|---------|-----------|--------|
| **[AI Receptionist & Lead Capture](https://ai-receptionist-demo.yahya-shehabi01.workers.dev)** | Chat widget + D1 persistence + owner dashboard | [06Yahya/ai-receptionist-demo](https://github.com/06Yahya/ai-receptionist-demo) |
| **[Agent Workflow Playground](https://agent-workflow-playground.yahya-shehabi01.workers.dev)** | 3 workflows: prospect research, CRM enrichment, follow-up drafting | [06Yahya/agent-workflow-playground](https://github.com/06Yahya/agent-workflow-playground) |

Screenshots for both projects are loaded from the respective GitHub repos' `docs/screenshots/` directories.

## SMB demos

Three screenshot-backed chatbot prototypes for Swedish local-business niches. The live page links to local proof screenshots instead of archived Render apps.

- **FriluftsByn** - `/assets/demo-friluftsbyn.png` (nature experiences, Höga Kusten)
- **LS Bygg & Snickeri** - `/assets/demo-lsbygg.png` (construction, Piteå)
- **The Unit** - `/assets/demo-theunit.png` (gym and martial arts, Luleå)

## Verification

To validate a clean deploy:

1. Load `https://yahya-shihabe.pages.dev` - English portfolio view renders with no console errors
2. Click `SV` toggle - all content switches to Swedish, nav labels and CTAs change
3. Click `EN` toggle - English content restores
4. Check `#projects` section - two project cards visible with live demo links
5. Check `#client-work` section - three chatbot screenshot cards visible and all links return 200
6. Check `#contact` - Cal.com booking widget loads
7. Check on mobile (390px viewport) - no horizontal overflow, sticky CTA visible

## Local development

```bash
# No build step - open the file directly
open index.html
# Or serve with any static server for Cal.com embed to work
python3 -m http.server 8000
```

## Deployment

Cloudflare Pages auto-deploys from the `main` branch of `06Yahya/Yahya-Shihabe`.

```bash
git add index.html
git commit -m "update: portfolio proof hub with EN/SV toggle"
git push origin main
```

The live site at `yahya-shihabe.pages.dev` updates within 60 seconds.

## What this proves (for employers)

- Cross-language UI with i18n architecture in a single static file
- Public proof hub that aggregates and references deployed projects
- Clean, accessible design with Tailwind and custom scroll-reveal
- No build step, no framework - just HTML, CSS, and JS that ships
- Deployed and inspectable end to end

## License

MIT
