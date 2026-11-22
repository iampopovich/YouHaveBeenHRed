# How recruiters and sourcing agents evaluate candidates

A research summary with sources. Facts are dated; re-check yearly.

## 1. Do employers look at social media at all
- RU, RSHU (uprav.ru), 1,163 respondents: 75% view candidates' social profiles
  (24% always, 51% for some roles). 79% would reject over content that
  contradicts company values. Only 4% count a missing or closed profile as a
  negative. What they look at: photo/video 59%, tone and style 58%,
  hobbies 48%, comments/opinions 43%, subscriptions 33%, follower count 8%.
  https://uprav.ru/blog/kontent-sotssetey/
- RU, Rabota.ru + SberPodbor, Apr 2025, 350+ respondents: 65% have no such
  practice, 20% do it formally, 14% say it affects decisions. Among those who look:
  overall impression 72%, posts 66%, photos 59%, manner/comments 52%, avatar
  48%, subscriptions 34%, friends 28%.
  https://press.rabota.ru/kazhdiy-tretiy-rabotodatel-prosmatrivayet-sotsseti-kandidatov
- US: Harris Poll-based figures put social screening around 60% of employers.
  Background-check vendors (First Advantage, Veremark) report social media checks
  are growing as a formal screening step.
- Takeaway: what's visible matters more than how much you post. Hiding is cheap
  and rarely penalized. A professional profile is a plus for some roles.

## 2. AI sourcing agents (2026)
- Products: Juicebox/PeopleGPT (800M+ profiles, 30+ sources, autonomous
  agents), Pin, Gem, MiraDay, Metaview, Exa (web search API for recruiting).
- How they work: the recruiter writes a natural-language brief. The agent
  searches many sources and the open web in several steps, following signals
  (companies, tech stacks, projects, public work) and cross-checking them. It
  ranks candidates with an explainable reason, then often writes personalized
  outreach.
- Implication: exact keywords matter less than linked evidence an agent can
  verify and quote. Personalized outreach will cite your public posts, so
  make sure the posts you'd want quoted are the ones that surface.
  https://docs.miraday.ai/en/docs/sourcing/agentic-search
  https://juicebox.help/agents
  https://metaview.ai/resources/blog/ai-candidate-sourcing

## 3. Boolean and X-ray search today
- LinkedIn removed headline/title/location from what crawlers see. X-ray
  still confirms a named profile exists but can't filter lists by title or city.
- Workarounds: `site:linkedin.com/advice/ intext:"<title>"` (fragile), plus
  code hosts, personal sites, conference programmes, professional bodies, papers.
- Operators that matter: site:, intitle:, inurl:, intext:, filetype:, OR (in
  caps), -exclusion (`-jobs -hiring -apply -careers`), "exact phrase".
- Ethics test used by sourcers: could you tell the person how you found them
  without embarrassment? GDPR needs a lawful basis for processing.
  https://fullstackrecruiter.net/guides/boolean-and-x-ray-search-for-recruiters

## 4. ATS and AI resume screening
- Pipeline: parse into fields (contact, titles, dates, skills), then match against
  the job's requirements, then filter and rank. Many ATS now use an LLM to score
  fit. Unparseable layouts (tables, columns, images) lose fields.
- Keywords: mirror the job posting's titles, hard skills and tools. Consistent
  titles and dates across resume and profiles avoid "inconsistency" flags.
  https://jobscan.co/blog/blog-ai-resume-screening
  https://atsverification.com/blog/how-ats-scoring-works

## 5. Code hosts (tech roles)
- Recruiters rarely read code. Hiring managers sometimes do, especially for
  borderline or senior candidates. What gets looked at: the profile README,
  pinned repos, recent activity, READMEs with a clear purpose, and contributions
  to known projects. Practitioner threads (HN, Reddit) agree on this.

## 6. Signals agents use for identity linking
- The same name spelling and avatar, a shared handle, and mutual links (profile
  to site to profile). On a personal site, schema.org `Person` JSON-LD with
  `sameAs` URLs makes the link explicit for crawlers and agents.
