# Query sets (fill the placeholders)

Placeholders: {NAME_*} = every name variant (native script + Latin
transliterations), {NICK} = each nickname/handle, {CITY}, {ROLE_*} = target
role titles, {STACK} = 3-5 core skills, {PROJECT_*} = notable projects or
packages, {EMPLOYER_*} = current and recent employers.
Use the operators your search backend supports (quotes, OR, site:).

## A. Name only: namesake noise
- "{NAME}"
- "{NAME}" {ROLE_short}  (e.g. QA, developer, designer)
- "{NAME}" {CITY}

## B. Sourcer boolean: role + stack
- "{SURNAME}" ({ROLE_1} OR {ROLE_2} OR {ROLE_3}) {STACK_1} {STACK_2}
- "{SURNAME}" {ROLE_1} remote
- site:<professional-network>/in "{SURNAME}" {ROLE_1}  (this confirms the
  profile exists; it can't filter by title any more)
- site:linkedin.com/advice/ intext:"{NAME}"  (contributor articles are still indexed)
- add `-jobs -hiring -apply -careers` to strip job-ad noise
- site:<regional-job-network> "{SURNAME}" {ROLE_1}  (see markets.md)
- "{NAME}" {notable claim}  (e.g. "committer", "maintainer", "speaker")

## C. Unique anchors
- {NICK}
- {NICK} + github / gitlab / linkedin / telegram / blog / each market network
- "{PROJECT_n}": does the subject's repo or page rank first, or a namesake's?
- package-registry author pages (npm, PyPI, Maven, crates, etc.)

## D. Employers and events
- "{SURNAME}" "{EMPLOYER_n}"
- "{NAME}" conference OR meetup OR podcast OR talk

## E. Risk sweep (logged-out)
- {NICK} reddit / x.com / youtube / forums / gaming sites / local forums
- "{NAME}" + old usernames the user mentions
