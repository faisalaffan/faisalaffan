# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a GitHub profile README repository — a static markdown file that serves as Faisal Affan's personal portfolio/profile page on GitHub. It contains badges, links to social profiles, work experience, and featured projects.

## Repository Structure

```
FAISAL_README_GITHUB/
├── README.md      # GitHub profile page (static markdown)
├── LICENSE       # MIT License
└── .git/        # Git history
```

## Workflow

This is a **static content repository** — no build, test, or development commands needed.

- Edit `README.md` directly to update the profile
- Changes are committed and pushed to sync with GitHub profile

## Architecture Notes

- GitHub profile README auto-displays on the user's GitHub profile page
- Uses markdown with embedded HTML for complex layouts (badges, stats cards, gifs)
- External services: GitHub stats API, shields.io badges, giphy, vercel-based stats

## Notes

- No npm/node dependencies or package manager
- No CI/CD pipeline
- No tests
- No code to lint or format
