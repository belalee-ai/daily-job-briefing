# Daily Job Briefing

> [中文版](README.zh-CN.md)

A Claude Code skill that searches the latest job openings in your target city and industry every day, and delivers a personalized briefing with job recommendations, salary analysis, market trends, and an action checklist.

## Features

- **Personalized Matching** — One-time onboarding (8 questions, ~3 min) builds your profile; all recommendations are tailored to your background
- **3-Tier Sources** — Company career pages → Job platforms (BOSS Zhipin / Liepin / LinkedIn) → Industry media, ranked by credibility
- **4-Dimension Scoring** — Experience fit (35%) + Salary competitiveness (25%) + Growth potential (20%) + Preference match (20%)
- **6 Modes** — Full briefing / Quick briefing / Targeted tracking / History review / Bookmark tracking / Market overview
- **Bookmark System** — Say "bookmark XX" in chat to follow a position; supports smart decay and auto-archiving
- **Multi-Industry** — Pre-built company lists and search templates for AI, Internet, FinTech, Gaming, New Energy, and E-commerce

## Installation

```bash
git clone https://github.com/belalee-ai/daily-job-briefing.git ~/.claude/skills/daily-job-briefing
```

## Usage

After installation, use these trigger phrases in Claude:

| Phrase | What it does |
|--------|-------------|
| "job briefing" / "any new jobs today" | Generate a full daily briefing |
| "quick briefing" / "tldr" | First-tier picks only, compact format |
| "any updates from ByteDance" | Track a specific company |
| "my bookmarks" / "track progress" | Check latest status of all bookmarked positions |
| "market overview" / "salary trends" | Dedicated market analysis |
| "update my profile" | Change target city / industry / salary preferences |

## Optional Enhancements

- **Resume Matching** — Place your resume in `shared/resume/`; the briefing will reference your specific project experience for matching analysis
- **Web Access Skill** — Install [web-access](https://github.com/eze-is/web-access) to unlock browser scraping and authenticated access for enhanced search

## Directory Structure

```
daily-job-briefing/
├── SKILL.md                        # Core instruction file
├── LICENSE.txt                     # MIT License
├── README.md                       # This file
├── templates/
│   ├── daily-job-report.md         # Briefing output template
│   ├── user-profile-template.md    # User profile template
│   └── bookmarks-template.md       # Bookmark format template
├── shared/                         # Runtime data (auto-generated, gitignored)
│   ├── user-profile.md             # Your profile (created after onboarding)
│   ├── bookmarks.md                # Bookmarked positions
│   ├── report-index.md             # Briefing index
│   ├── reports/                    # Generated briefings
│   └── resume/                     # Your resume (optional)
└── references/
    └── search-sources.md           # Industry search sources & keyword templates
```

## Data & Privacy

All runtime data is stored locally in `shared/` and excluded from git via `.gitignore`:

- `user-profile.md` — your job search profile
- `bookmarks.md` — bookmarked positions
- `resume/` — your resume files
- `reports/` — generated briefings

**Nothing is uploaded to any server.** If you fork or share this repo, make sure `shared/` contains no personal data.

## License

MIT
