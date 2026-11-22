---
name: you-have-been-hred
description: "Audit your own public footprint the way a recruiter or an AI sourcing agent sees it: blind web search, outsider dossier, namesake and identity-linking checks, a 0-18 score and ready-to-paste profile fixes. Use when the user asks how HR/recruiters see them, wants to google themselves like a recruiter, audit their online presence before a job search, or says 'you have been HRed'. Self-audit only, read-only, public data only."
license: MIT
compatibility: "Any agent with web search and page fetch. A browser and code execution are optional."
metadata:
  author: iampopovich
  version: "1.0.0"
  tags: "career, job-search, recruiting, sourcing, osint, personal-brand, self-audit"
---

# You have been HRed

An agent-agnostic skill. It runs in any agent that can search the web and read
pages (Hermes, Claude Code, Codex, Cursor, others). It audits a person's public
footprint the way a recruiter or an AI sourcing agent would. It finds only what
is public, builds the dossier a sourcer would write, scores it against current
hiring practice, and proposes concrete fixes.

It was inspired by a setka.ru post by career consultant Maria Ivakina ("Что
изменится, когда вас будет гуглить ИИ"). The idea: sourcing agents read far more
of your public history than a human recruiter does. They can confuse you with a
namesake or take a joke literally. So look at yourself from the outside before
they do.

## When to Use
- The user asks "how does HR or a recruiter see me", "google me like a
  recruiter", "audit my online presence for job search", or "you have been HRed".
- Before a job search, or after updating a resume, LinkedIn, GitHub or a
  portfolio. Re-run and diff against the previous baseline.
- Before publishing career material (resume, post, README), to check it fits
  with what's already public.

## Consent and scope (mandatory)
- Self-audit only. The subject is the user, or someone who explicitly asked
  the user to audit them. Don't profile third parties: refuse and explain why.
- Public, logged-out data only. Don't bypass logins, paywalls or privacy
  settings, and don't use people-search or data-broker services.
- Read-only. Never edit profiles, post, message, or change privacy settings.
  Offer drafts and wait for explicit approval.

## Tool mapping
Use whatever the host agent provides:
- web search: any search tool or API. Run queries in batches, in a script
  if the agent supports code execution.
- page reading: a fetch/extract tool, or `curl` plus readability.
- JS-heavy pages: a headless browser if one is available. If it isn't, rely on
  search snippets and say so in the report.
- asking the user: the agent's question tool, or plain chat.

## Reader lenses
The same footprint is read by different readers, so judge it through each one.
Background on how each reads is in `references/hr-methods.md`.
- Recruiter skim (30-60 s): headline, title, location, and whether the
  person looks like a fit.
- AI sourcing agent: a natural-language brief, multi-step web search, matching
  on evidence (companies, stack, projects, public work), an explainable match
  reason. It reads everything public, mirrors included.
- Hiring manager / tech lead: opens the code, posts or portfolio and checks the
  depth of the work.
- Culture/background screen: tone, photos, comments, subscriptions, and
  content that clashes with company values.
- ATS / keyword filter: literal terms, titles and dates.

## Core rule: blind mode
Phase 1 must use ONLY what search and logged-out pages return. Ignore
everything the agent already knows about the user (memory, chat history, local
files, a profile system prompt). A fact counts as "known to HR" only if a public
URL shows it. Bring in insider knowledge only in phase 3. The gap between the
outside and inside pictures is the main deliverable.

## Procedure
1. Intake. Ask once and fill in `assets/intake.md`: name variants
   (native script + Latin transliterations + nicknames), city/country, target
   roles and level, target markets, work-format constraints, known profile URLs
   (optional, used only to check linking after phase 1), and a previous baseline
   path if one exists. Pick the market packs in `references/markets.md`.
2. Search (phase 1, blind). Run the query sets in `references/queries.md`
   with the placeholders filled in, about 8-10 results each. Save raw results to
   a scratch file (JSON: query, url, title, snippet, is_subject yes/no/unsure).
   Passes:
   - A. name only: how much namesakes drown the subject;
   - B. name + role/stack/city, sourcer boolean style;
   - C. unique anchors: nicknames, project and package names;
   - D. employers and events;
   - E. a risk sweep on social and forum sites. Optionally run a username
     checker (Sherlock, Maigret, WhatsMyName) on the user's own handles to find
     forgotten accounts. Do this only if the user agrees to install the tool.
   Record a hit rate per pass (results that really are the subject / total).
3. Visit the subject's hits logged out: code hosts, professional networks,
   regional job networks, blogs, package registries, talk pages, and the
   aggregators/mirrors that copy profiles. Note the headline, title,
   dates, location, contacts, and cross-links.
4. Outsider dossier. Write the 2-minute profile a recruiter would produce:
   identity (and how confident you are that the profiles belong to one person),
   current title and guessed level, stack, location/format, evidence, contacts,
   red flags, and the verdict "would I reach out, for which role, and with what
   doubt". Every line needs a source URL. Add a short verdict from each reader
   lens; they often disagree.
5. Gap analysis (phase 3). Now bring in the user's own account of themselves.
   Score the 9 criteria in `references/rubric.md` (0-2 each, /18), with reasons.
6. Fixes. Rank by impact/effort: quick wins (< 1 h), this week, longer-term.
   Give exact drop-in text (headline, About, bio, pinned items, a consistent
   name spelling, cross-links). List content that might be worth hiding
   neutrally. The user decides, so don't moralize. Also give 3-5 interview
   questions the footprint invites ("I saw your post about X..."), so the user
   is ready for them.
7. Deliver a report from `assets/report.md` into the user's documents
   folder, plus a short chat summary. Save a compact baseline (dated facts only)
   next to the report so the next run can diff against it. Keep personal data out
   of the skill directory.

## Pitfalls
- Common names make pass A mostly noise. That's a finding (namesake risk), not
  a failed search. Quantify it.
- Names transliterate differently (Alexander/Aleksandr/Oleksandr, Müller/Mueller/Muller).
  Check whether an agent could link the profiles without help. Shared
  nicknames, avatars and mutual links are what make the link work.
- Mirrors and aggregators keep stale bios, and agents read them. Report them.
- Professional networks often put logged-out pages behind an auth wall, and
  search snippets are frequently all a sourcer sees. Judge that snippet.
  Since LinkedIn stripped headline/title metadata from crawlers, X-ray search
  can confirm a profile exists but can't filter by title or city. Sourcers
  compensate with code hosts, personal sites, talks and `site:linkedin.com/advice/`.
- A closed or missing social profile is almost never held against a candidate
  (in surveys it's a negative for only a few percent of employers). Recommending
  "lock it down" is safe. Recommending "post more" is not automatically good.
- Joke headlines and bios read literally to keyword search and to LLM
  summarizers. Flag them as a keyword gap, not as a moral issue.
- An agent with memory of the user can't honestly simulate "ask an unknown
  LLM about me". Suggest the user asks a model they never used, logged out,
  and pastes the answer for comparison.
- Sensitive finds (health, family, religion, politics, legal) are reported
  neutrally with the URL and nothing more. In jurisdictions where speech
  carries legal risk, recommend proper legal advice rather than judging it.
