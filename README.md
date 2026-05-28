# 🤖 Copilot Governance Starter Kit

> A fork-ready template that reduces GitHub Copilot token usage across your entire organisation — better suggestions, lower cost, zero manual setup per team.

---

## The Problem

Most teams use GitHub Copilot out of the box. That means:

- Copilot reads every open editor tab on every keypress
- Lock files, build output, and generated code pollute the context window
- `copilot-instructions.md` files grow into essays that cost tokens on every request
- No consistent standard across teams — every repo behaves differently

**Result:** High token consumption, inconsistent suggestion quality, and no visibility into usage patterns.

---

## What This Solves

This starter kit gives every team a pre-configured baseline that:

| Problem | Solution in this kit |
|---|---|
| Copilot reads irrelevant files | `.copilotignore` excludes build output, locks, fixtures, data files |
| Open tabs bloat context | `.vscode/settings.json` caps tabs at 8, enables preview mode |
| Instructions file is too long | `copilot-instructions.md` template enforces 300-token limit |
| Copilot runs on config/lock files | Per-language enable/disable in workspace settings |
| No team-wide standard | Fork this once, update per team, commit and enforce via PR |

---

## Getting Started

### Option A — Copy into an existing repo
```bash
# From your project root
curl -L https://github.com/YOUR_ORG/copilot-starter-kit/archive/main.tar.gz | tar xz --strip=1
```

Then:
1. Edit `.github/copilot-instructions.md` with your stack details
2. Review `.copilotignore` and add project-specific paths
3. Commit both files

### Option B — Use as a GitHub Template Repository
1. Go to this repo on GitHub → **Use this template** → **Create a new repository**
2. Follow Step 1–3 above

---

## Files Included

```
.
├── .copilotignore                   # Stops Copilot indexing noise files
├── .github/
│   └── copilot-instructions.md     # Template: lean repo-level instructions
├── .vscode/
│   └── settings.json               # Workspace settings: tab limits, language toggles
└── docs/
    └── copilot-hygiene.md          # 1-pager guide for developers
```

---

## Customising for Your Team

### Language / Framework
The `copilot-instructions.md` template is framework-agnostic. Fill in your actual stack:
- Language + version
- Framework
- Database + ORM
- Test runner
- Code conventions that *differ* from defaults

**Keep it under 300 tokens (~230 words). No exceptions.**

### Ignore Patterns
Add your project-specific generated folders to `.copilotignore`. Common additions:
```
# Examples of project-specific additions
storybook-static/
.storybook/
proto/generated/
migrations/
```

### Enable/Disable Copilot per Language
Edit `.vscode/settings.json` under `github.copilot.enable`. If your team actively writes Terraform, set `"terraform": true`. If you never use Copilot for SQL, set `"sql": false`. Commit this as a team decision — don't leave it to individuals.

---

## Presenting to Your Organisation

When rolling this out, lead with three numbers:

1. **Token reduction** — teams typically see 30–50% fewer tokens per session after applying `.copilotignore` and tab limits
2. **Suggestion quality** — narrower, relevant context = more accurate completions
3. **Consistency** — every team starts from the same baseline; onboarding is one `git clone`

---

## Contributing

This is an org-wide tool. Improvements should be proposed via PR, reviewed by at least two teams, and merged with a summary of what changed and why.

---

## Maintainers

| Name | Team | Contact |
|---|---|---|
| [YOUR NAME] | [YOUR TEAM] | [SLACK/EMAIL] |
