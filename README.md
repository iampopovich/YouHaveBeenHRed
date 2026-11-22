<h1 align="center">You Have Been HRed</h1>

<p align="center">An agent skill that shows you what a recruiter, or a recruiter's AI agent, finds and concludes about you from the public web.</p>

<p align="center"><a href="README.ru.md">Русский</a> · English</p>

Recruiters already google candidates. Now they also hand the job to AI sourcing
agents (Juicebox, Gem, MiraDay and others). An agent describes a role in plain language, searches the open web in
several steps, and returns people with a "why they match" explanation. An agent
reads much more than a human recruiter would: old posts, profile mirrors, a
namesake's page. It can take a joke literally. Most profile tools only rewrite
the LinkedIn text you paste into them. This skill works from the outside: it searches
for you the way a sourcer does, without anything your agent already knows about
you. Then it compares that picture with who you really are, and tells you what
to fix so the outside picture matches the roles you want.

> Status: v1.0.0. Instruction-only skill (no scripts, no API keys). It was developed
> with Hermes Agent and follows the [Agent Skills](https://agentskills.io) format, so
> it should work in any agent that supports it. Market packs cover global/remote tech,
> Russia/CIS and DACH. Contributions for other regions are welcome.

## What it does

**Searches for you like a sourcer, in blind mode**
- Five query passes: name only (namesake noise), boolean role + stack, unique
  anchors (handles, projects, packages), employers and events, a risk sweep.
- Ignores everything your agent remembers about you. A fact counts only if a public
  URL shows it.
- Records a hit rate per pass, so "your name is drowned by namesakes" becomes a number.

**Writes the dossier a recruiter would write in two minutes**
- Identity and confidence that the profiles are one person, title, guessed level,
  stack, location and format, evidence, contacts, red flags. Every line has a source.
- A separate verdict from five readers: a recruiter skim, an AI sourcing agent, a hiring
  manager, a culture/background screen, and an ATS keyword filter.

**Scores and fixes**
- Nine criteria, 0-2 each (/18): findability, identity linking, title consistency,
  keywords, evidence of impact, contactability, risky content, namesake confusion,
  market fit.
- Fixes ranked by effort, with drop-in text: headline, About, bio, pinned items,
  cross-links.
- Content you may want to hide, listed neutrally. You decide.
- Interview questions your footprint invites.
- Saves a baseline, so the next run shows what changed.

See [examples/sample-report.md](examples/sample-report.md) for a report on a
made-up person.

## Privacy and boundaries

- **Self-audit only.** The skill refuses to profile third parties.
- **Public, logged-out data only.** It doesn't bypass logins and doesn't use
  people-search or data-broker services.
- **Read-only.** It never edits profiles, posts, sends messages or changes privacy
  settings. It drafts, and you apply.
- Reports and baselines are written to your own documents folder, never into
  the skill directory.
- Sensitive finds (health, family, religion, politics, legal) are reported
  neutrally, with the URL and nothing else.

## Install

| Agent | Command |
|---|---|
| Any agent (skills CLI) | `npx skills add iampopovich/YouHaveBeenHRed` |
| Claude Code (plugin) | `/plugin marketplace add iampopovich/YouHaveBeenHRed` then `/plugin install you-have-been-hred@you-have-been-hred` |
| Claude Code (manual) | copy `skills/you-have-been-hred` to `~/.claude/skills/` |
| Codex | copy `skills/you-have-been-hred` to `~/.agents/skills/` |
| Hermes Agent | `hermes skills install iampopovich/YouHaveBeenHRed/skills/you-have-been-hred` |
| GitHub CLI | `gh skill install iampopovich/YouHaveBeenHRed` |
| Others (Cursor, Gemini CLI, ...) | copy the folder into the agent's skills directory |

What the agent needs: a web search tool and a page fetch tool. A headless browser
and code execution are optional. Without a browser, the skill relies on search
snippets and says so in the report.

## Use

Ask your agent something like:

```
You have been HRed: audit me. I'm a Python SDET in Lisbon, looking for remote roles in the EU.
```

The agent asks a few intake questions: name variants, handles, target roles and
markets, and anything you don't want searched. It then runs the audit and saves
`hred-<date>.md`.

Tip: also ask a chatbot you have never used, while logged out, "who is <your name>,
<your role>?" and paste the answer in. An agent that already knows you can't
honestly simulate that.

---

## For contributors

```
skills/you-have-been-hred/
  SKILL.md               the procedure (keep under ~500 lines)
  references/            queries, rubric, market packs, research on HR methods
  assets/                intake and report templates
.claude-plugin/          Claude Code plugin + marketplace manifests
examples/                a sample report on a fictional person
```

Rules that hold the skill together:
1. **Blind first.** Phase 1 uses only public evidence. Insider knowledge comes only in
   the gap analysis.
2. **Every claim has a URL.** A dossier line without a source gets removed.
3. **Agent-agnostic.** Describe capabilities ("web search", "page fetch"), never
   tool names of one specific agent.
4. **No personal data in the repo.** Examples use fictional people and
   `example.com` URLs.

To add a region, extend `references/markets.md` with the platforms local sourcers
use, and add any local-script query variants to `references/queries.md`.
Facts in `references/hr-methods.md` are dated and sourced, so update them
rather than add opinion.

Validate before a PR: `skills-ref validate skills/you-have-been-hred` or
`gh skill publish --dry-run`.

Inspired by Maria Ivakina's post
[«Что изменится, когда вас будет гуглить ИИ»](https://setka.ru/posts/01a1e4e4-bffe-7541-98e3-b501b77b9101).

License: [MIT](LICENSE).
