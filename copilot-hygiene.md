# Copilot Hygiene Guide
> A practical 1-pager for every developer. Pin this. Share this.

---

## Why This Matters

GitHub Copilot charges per token. Every suggestion, every Chat message, every `@workspace` query consumes tokens from a context window. **The bigger the context, the higher the cost and the worse the suggestion quality.** Less noise in → better code out.

---

## The 5 Rules

### 1. Close Tabs You're Not Using
Copilot reads every open editor tab as context. Ten open files means ten files worth of tokens sent with every completion request.

✅ Keep 4–6 tabs open max  
✅ Use `Ctrl+W` / `Cmd+W` aggressively  
✅ Enable tab limit in workspace settings (already configured)

---

### 2. Use `#file` Instead of Leaving Files Open
In Copilot Chat, reference specific files with `#file:path/to/file.ts` instead of keeping them open.

```
# Instead of opening 5 files, use:
@workspace #file:src/domain/orders.ts explain the createOrder function
```

This sends only the file you need, not everything in your tabs.

---

### 3. Use Scoped Commands, Not Open-Ended Chat
Scoped slash commands send less context than open questions.

| Instead of... | Use... |
|---|---|
| "What's wrong with this code?" | `/fix` with selected code |
| "Explain everything" | `/explain` with selection only |
| "Write tests for the whole service" | Select one function → `/tests` |
| "What does this repo do?" | `@workspace /explain` scoped to one folder |

---

### 4. Keep `copilot-instructions.md` Lean
The `.github/copilot-instructions.md` file is **injected into every single Copilot request** in your repo. Every extra sentence costs tokens on every request, multiplied across every developer, every day.

✅ Max 300 tokens (roughly 200–250 words)  
✅ Bullet points only — no prose explanations  
✅ Only rules that *differ* from sensible defaults  
✅ Never paste code examples into it  

---

### 5. Don't Use Copilot for the Wrong File Types
Copilot is configured in `.vscode/settings.json` to disable itself on JSON, YAML, lock files, and other config/generated content. **Don't override this** — you won't get useful suggestions and you'll burn tokens.

If your team edits Terraform or Dockerfiles heavily and wants Copilot enabled there, update the settings centrally and commit the change — don't do it per-person.

---

## Quick Reference Card

```
✅ DO                              ❌ DON'T
───────────────────────────────    ──────────────────────────────
Close tabs not in use              Leave 20 tabs open
Use #file: in Copilot Chat         Rely on open tabs for context
Use /fix, /explain with selection  Ask open-ended Chat questions
Keep instructions.md under 300t   Write essays in instructions.md
Commit .copilotignore updates      Ignore the ignore file
```

---

## Files in This Starter Kit

| File | Purpose |
|---|---|
| `.copilotignore` | Stops Copilot indexing irrelevant files |
| `.github/copilot-instructions.md` | Template for lean repo-level instructions |
| `.vscode/settings.json` | Disables Copilot on noise file types, limits open tabs |
| `docs/copilot-hygiene.md` | This guide |

---

## Onboarding a New Team

1. Fork or copy this repo template into your project
2. Edit `.github/copilot-instructions.md` with your actual stack
3. Review `.copilotignore` and add any project-specific folders
4. Share this guide with the team in your onboarding docs

---

*Questions or suggestions? Raise a PR against the org template repo.*
