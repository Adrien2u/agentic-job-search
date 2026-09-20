# workspace/

Your data lives here. Nothing in this directory ships with the repo — it's created by `SETUP.md` when you run it.

| Folder | Holds |
|---|---|
| `documents/` | uploaded source documents (past resumes, reviews, writing samples, portfolios) |
| `profile/` | `profile.md`, `master-resume.md`, `star-stories.md`, `outreach-log.md`, deep-module outputs |
| `applications/` | `tracker.csv`, `weekly-log.md`, and one folder per application with the tailored resume, cover letter, saved posting, and notes |
| `research/` | one company brief per employer |
| `interviews/` | one prep doc per interview round |

Application folders are named `{{COMPANY}}-{{ROLE}}/`.

## Privacy

This whole directory is gitignored by default, along with `config.md` at the repo root. Your search doesn't get committed unless you decide it should.

If you forked this into a **private** repo and want your search versioned — which is genuinely useful, since you get a history of every resume version and every decision — delete the `workspace/**` and `config.md` lines from `.gitignore`.

Do not do that in a public repo.
