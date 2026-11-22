# You have been HRed: Sam Example (2026-11-23)

> Fictional person, fictional URLs (`example.com`). This shows the format, not real data.

## 1. Verdict in 3 lines
A sourcer would find Sam only through the handle `samx`. The name alone returns a
footballer and a dentist. The visible picture is "mid-level QA, maybe manual". The real
profile is senior SDET with OSS work. The main doubt is that the LinkedIn and GitHub
titles disagree, and there's no proof of seniority.

## 2. Verdict by reader lens
| Lens | Would reach out? | Why / doubt |
|---|---|---|
| Recruiter skim | Maybe | The headline "QA \| coffee \| memes" doesn't say SDET or Python |
| AI sourcing agent | Yes, mid-level | It links GitHub and npm by handle, but can't link LinkedIn |
| Hiring manager | Yes | Pinned repo `flaky-hunter` has tests, CI and a clear README |
| Culture screen | Neutral | One sarcastic 2019 post about recruiters is indexed |
| ATS filter | No | No "SDET", "pytest" or "CI/CD" in public text |

## 3. Search hit rates
| Pass | Queries | Hits on subject | Notes |
|---|---|---|---|
| A. Name only | 4 | 0/32 | Footballer and dentist with the same name |
| B. Boolean role + stack | 6 | 3/48 | Only via the GitHub profile |
| C. Anchors | 5 | 21/40 | `samx` is unique, npm and GitHub rank first |
| D. Employers/events | 3 | 1/24 | One 2023 meetup page |
| E. Risk sweep | 4 | 2/32 | An old forum account, the 2019 post |

## 4. Outsider dossier (blind)
| Field | What's visible | Source URL |
|---|---|---|
| Identity | Sam Example = `samx` (high confidence on GitHub/npm, low on LinkedIn) | https://example.com/github/samx |
| Title | "QA Engineer" (GitHub), "QA \| coffee \| memes" (LinkedIn) | https://example.com/linkedin/sam |
| Level guess | Mid | inferred from the titles, no years shown |
| Stack | Python, pytest, Playwright | https://example.com/github/samx/flaky-hunter |
| Location/format | Lisbon, format not stated | https://example.com/linkedin/sam |
| Evidence | 1 npm package (~2k weekly downloads), meetup talk 2023 | https://example.com/npm/~samx |
| Contacts | none public | |
| Red flags | 2019 post "recruiters are spam bots" | https://example.com/blog/2019/rant |

## 5. Score: 7/18
| # | Criterion | Score | Why | Best fix |
|---|---|---|---|---|
| 1 | Findability | 1 | Only the handle finds Sam | Put the handle on LinkedIn, the name on GitHub |
| 2 | Identity linking | 1 | LinkedIn isn't linked to GitHub | Add mutual links |
| 3 | Title consistency | 0 | Two different titles | Use "Senior SDET (Python)" everywhere |
| 4 | Keywords | 0 | Joke headline | Add the headline below |
| 5 | Evidence | 2 | Repo + package + talk | Pin them on LinkedIn Featured |
| 6 | Contactability | 0 | No channel | Add a work email or "open to" |
| 7 | Risky content | 1 | One rant | Unlist the 2019 post |
| 8 | Namesakes | 1 | Name is drowned out | Always use "Sam Example (samx)" |
| 9 | Market fit | 1 | Reads as mid QA | Make seniority visible |

## 6. Fixes
### Quick wins (< 1 h)
- LinkedIn headline: `Senior SDET · Python, pytest, Playwright · Test infra & CI · Open to remote (EU)`
- GitHub bio: `Senior SDET (Python). Author of flaky-hunter. linkedin.com/in/sam`
- Add the LinkedIn ↔ GitHub ↔ npm cross-links.
### This week
- An About paragraph with 2-3 numbers (suite runtime cut, flake rate).
### Longer-term
- A personal page with schema.org `Person` + `sameAs` links.

## 7. Consider hiding (you decide)
- The 2019 blog post: https://example.com/blog/2019/rant

## 8. Interview questions the footprint invites
- "Tell me about flaky-hunter. Why did you build it?"
- "Your talk mentioned parallel test sharding. How did you measure the gain?"

## 9. Diff since last run
First run, no baseline.

## 10. Next check
After updating LinkedIn, or in 3 months.
