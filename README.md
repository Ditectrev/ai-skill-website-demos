# Website demo skills

This repo is the install list for quick website demos. It does not build the sites. A link to this repo does not install anything: Cursor only loads skills that are already on the machine, or already inside the project you have open.

## Skills

| Skill | When to use it |
| --- | --- |
| `frontend-design` | While building. Sets type, color, and layout from the industry and the brief. |
| `core-web-vitals` | After the build. Checks loading, interaction, and layout shift. |
| `accessibility` | After the build. Checks keyboard use, contrast, labels, and focus. |
| `seo` | After the build. Checks titles, descriptions, canonicals, and indexing. |
| `web-design-guidelines` | After the build. Checks Vercel’s interface rules for forms, focus, and interaction. |
| `vercel-site-poc` | While building. Next.js demo: brand, languages, search, themes, preview banner, share cards, redirects, contact links, legal pages, a “Crafted by Ditectrev” footer link, and `llms.txt`. |

`vercel-site-poc` lives in this repo at `.cursor/skills/vercel-site-poc/SKILL.md`. Commit that file. A Cloud Agent only sees skills inside the repo it is working on. There is no personal copy on this Mac.

## Cloud Agent, new website repo

Start the agent from this repo, or paste this repo’s URL in the task. The agent must copy these into the new website repo before building:

- `.cursor/skills/vercel-site-poc/`
- `package.json` (the `skills` list and the `skills` script)
- `package-lock.json`
- `skills-lock.json`

Then, in the new repo, it runs:

```bash
npm install
npm run skills
```

That installs `frontend-design`, `core-web-vitals`, `accessibility`, `seo`, and `web-design-guidelines` into that repo’s `.agents/skills/`. Those five are not committed. `vercel-site-poc` is committed, so it is already there after the copy.

In the task, name the industry, the audience, and the job of the page. If a live site exists, say that its colors and type are the brief.

## Once per machine

Run this from any folder. The skills then show up in every new project on this Mac. Start a new Agent chat afterward.

```bash
npx skills add addyosmani/web-quality-skills --skill core-web-vitals --skill accessibility --skill seo -g -a cursor -y
npx skills add vercel-labs/agent-skills --skill web-design-guidelines -g -a cursor -y
npx skills add anthropics/skills --skill frontend-design -g -a cursor -y
```

In the new project, describe the site. Name the industry, the audience, and the job of the page. If a live site exists, say that its colors and type are the brief.

Use `/frontend-design` while building. Use `/core-web-vitals`, `/accessibility`, `/seo`, and `/web-design-guidelines` after. You can also describe the job and let Cursor attach the skills whose descriptions match.

## Another machine

Clone this repo, then restore the same five skills into it:

```bash
npm install
npm run skills
```

That fills `.agents/skills/` here only. Repeat the global commands above so new website repos on that machine see them too.

Commit `package.json`, `package-lock.json`, `skills-lock.json`, and `.cursor/skills/`. Do not commit `node_modules` or `.agents/`.
