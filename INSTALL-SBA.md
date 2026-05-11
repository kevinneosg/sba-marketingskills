# Installing the SBA Marketing Skills Fork

Three install paths plus upstream-sync instructions.

---

## 1. Install as a Claude Code plugin

The repo includes `.claude-plugin/plugin.json` with `name: "sba-marketingskills"`. Three install options, pick whichever fits your workflow:

### Option A — Clone into the Claude plugins folder

```powershell
# Windows
cd $env:USERPROFILE\.claude\plugins
git clone https://github.com/kevinneosg/sba-marketingskills.git
```

```bash
# macOS / Linux
cd ~/.claude/plugins
git clone https://github.com/kevinneosg/sba-marketingskills.git
```

Claude Code will pick the plugin up on next session start.

### Option B — Reference a local clone from settings.json

If the fork is cloned somewhere else (e.g. inside `Scholarbasketball Workflow/sba-marketingskills`), add a plugin entry to `~/.claude/settings.json`:

```json
{
  "plugins": [
    {
      "name": "sba-marketingskills",
      "path": "C:\\Users\\imkry\\Documents\\Claude\\Projects\\Scholarbasketball Workflow\\sba-marketingskills"
    }
  ]
}
```

### Option C — Per-project install

Drop a `.claude/settings.json` inside a specific SBA project (e.g. `sba-marketing-assistant`) that references the local clone. This scopes the skills to that project only.

---

## 2. Set up in a specific SBA repo

Every SBA marketing project needs its own copy of the SBA context data file. The fork ships a canonical version; the consuming project gets a project-local copy that any of the 40+ marketing skills will read.

### One-time setup per consuming project

From the consuming project root (e.g. `sba-marketing-assistant/`):

```powershell
# Windows
mkdir .agents -Force
Copy-Item "..\sba-marketingskills\skills\product-marketing-context\SBA-DATA.md" ".agents\product-marketing-context.md"
```

```bash
# macOS / Linux
mkdir -p .agents
cp ../sba-marketingskills/skills/product-marketing-context/SBA-DATA.md .agents/product-marketing-context.md
```

Confirm the file is in place:

```powershell
ls .agents
```
Expected: `product-marketing-context.md`.

After this step, every marketing skill in the fork will read SBA context automatically — no further setup needed.

### When SBA reality changes (new programs, new venues, new metrics)

1. Update `Scholarbasketball Workflow/SBA-CONTEXT.md` first (the source-of-truth)
2. Refresh `sba-marketingskills/skills/product-marketing-context/SBA-DATA.md`
3. Re-copy to every consuming project's `.agents/product-marketing-context.md`

Consider scripting step 3 if multiple SBA projects consume the fork.

---

## 3. Keep in sync with upstream

The fork has `upstream` set to `coreyhaines31/marketingskills`. Periodically pull upstream changes:

```powershell
cd "Scholarbasketball Workflow/sba-marketingskills"
git fetch upstream
git checkout main
git merge upstream/main
```

### Expected conflicts

Conflicts only in the SBA-customized files:
- `README.md` (top section)
- `.claude-plugin/plugin.json` (name field)
- `skills/page-cro/SKILL.md` (addendum at bottom)
- `skills/copywriting/SKILL.md` (addendum at bottom)
- `skills/seo-audit/SKILL.md` (addendum at bottom)
- `skills/ad-creative/SKILL.md` (addendum at bottom)
- `skills/customer-research/SKILL.md` (addendum at bottom)

For each conflict in an addendum-ed file: keep the upstream content above the `---` separator, keep the SBA Addendum content below.

### If upstream adds a new skill

After merging, update `SBA-SKILL-MAP.md` — categorize the new skill into one of the four tiers (🟢🟡🟠🔴).

### If upstream renames or deletes a skill

The merge will surface the change. Update `SBA-SKILL-MAP.md` accordingly. If the renamed/deleted skill had an SBA addendum, move the addendum to the new location.

---

## Quick smoke test (after install)

After plugin install + per-project setup, ask Claude Code:

> "Read .agents/product-marketing-context.md and summarize the SBA brand voice."

Expected: Claude should reference parent-facing tone, italic-emphasis on one word per headline, words to avoid (users/customers/platform), and Singapore-specific patterns. If it references SaaS / B2B framing, the context file isn't being loaded — re-check step 2.
