# Git for Scientists

## A Getting-Started Guide to Writing Research Papers with Markdown, Git, and Claude

*By *[*Yaniv Golan*](https://github.com/yaniv-golan)* — February 2026*

You've named a file `paper_final_v3_REALLY_final.docx`. You've lost track of which version has the updated Figure 3. A co-author just emailed conflicting edits of the same section. Sound familiar?

This guide shows you a better way — using **Git** for version control, **Markdown** for writing, and **Claude** as your plain-English interface. You never need to type a Git command. You just tell Claude what you want, and it handles the rest. This guide teaches the *concepts* so you understand what's happening.

All you need is the [Claude Desktop app](https://claude.ai) (free, macOS or Windows) and a paid plan (Pro, Max, Team, or Enterprise) for access to Code and Cowork.

**A note on timeliness**: AI tools evolve fast. The concepts in this guide (Git, Markdown, commits, diffs) are stable and timeless. The specific tool details (Claude's tabs, Cowork features, plan tiers) may change. This guide was written in February 2026 — if something looks different on your screen, check the [repo](https://github.com/yaniv-golan/git-for-scientists) for updates or [open an issue](https://github.com/yaniv-golan/git-for-scientists/issues) to let us know.

---

## How It All Fits Together

```
┌─────────────────────────────────────────────────┐
│            Claude Desktop App                    │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌───────────────┐  │
│  │   Chat   │  │  Cowork  │  │     Code      │  │
│  │          │  │          │  │               │  │
│  │  Think   │  │  Draft   │  │  Edit files   │  │
│  │  Ask     │  │  Create  │  │  Save (commit)│  │
│  │  Discuss │  │  Organize│  │  Undo         │  │
│  │          │  │          │  │  Branch       │  │
│  │          │  │          │  │  Push/Pull    │  │
│  └──────────┘  └──────────┘  └───────┬───────┘  │
│                                      │           │
└──────────────────────────────────────┼───────────┘
                                       │
                              Your project folder
                              (tracked by Git)
                                       │
                                       ▼
                              ┌─────────────────┐
                              │     GitHub       │
                              │  (cloud backup   │
                              │   + co-authors)  │
                              └─────────────────┘
```

**You** work in the Claude Desktop app. The **Code tab** manages your project folder with Git. **GitHub** syncs everything to the cloud and your co-authors. That's the whole system.

**How your work moves**: You write → you **commit** (saved on your computer) → you **push** (backed up to GitHub). That's the whole flow. Pulling is the reverse — it downloads your co-authors' latest commits from GitHub to your computer.

### Quick start (2 minutes)

1. Open Claude Desktop → **Code** tab → **Select folder** (your paper folder)
2. "Set up this folder as a Git project with a paper.md and README"
3. Write something in paper.md → "Commit my changes — first draft"
4. "Create a private GitHub repo and push everything"

Done. You have version control and cloud backup. Read on to understand what just happened and what else you can do.

---

## Part I: Why Bother?

### 1. The Problem You Already Have

That `paper_final_v3_REALLY_final.docx` on your desktop? That *is* version control — just done badly. And it breaks down fast: you can't get back to last week's draft, you don't know which version produced Figure 3, and someone just overwrote your changes in the shared Dropbox folder.

Git solves all of this. It gives you:

- **Unlimited undo** — every version of every file, recoverable as long as the repository exists (push to GitHub for real backup)
- **A complete history** — who changed what, when, and why, in a searchable log
- **Painless collaboration** — multiple people editing the same project without overwriting each other
- **It's free** — and runs on every operating system

Funder and journal mandates are heading this way too. NIH's Data Management & Sharing policy, NSF's DMS Plan requirement, and the FAIR principles all push toward versioned, transparent research outputs. A Git repository is concrete evidence of what changed and when.

### 2. Why Markdown?

If you've ever tried to figure out what changed between two versions of a Word document, you know the frustration. Word files are binary — opaque blobs that Git can store but can't meaningfully compare.

Markdown is plain text. That means Git can show you *exactly* what changed, word by word, line by line. And Markdown is simple:

```markdown
# Introduction

This study examines the relationship between **sleep duration**
and *cognitive performance* in undergraduate students.

## Key findings

1. Participants sleeping < 6 hours scored 23% lower
2. The effect was strongest for working memory tasks
3. No significant gender differences were observed

| Group       | Mean Score | SD   |
|-------------|-----------|------|
| < 6 hours   | 72.3      | 8.1  |
| 6-8 hours   | 88.7      | 6.4  |
| > 8 hours   | 91.2      | 5.9  |
```

That's it. Headings with `#`, bold with `**`, italic with `*`, numbered lists, and tables. You can learn everything you need in five minutes.

When you change a sentence in Markdown, Git shows you the old line and the new line, highlighted. (And for long paragraphs, you can ask for an even finer view that highlights individual words — more on that in Part V.) When you change a sentence in Word... Git shows you nothing useful.

![Markdown vs Word: how Git sees your changes](assets/Fig1.png)

You can write Markdown in any text editor. [Obsidian](https://obsidian.md) and [Typora](https://typora.io) are popular with researchers. Or you can write it directly inside Claude.

And when it's time to submit? Markdown converts to Word, PDF, HTML, or LaTeX with a single command (that Claude runs for you). More on that in Part VI.

### 3. The Claude Desktop App: Your Research Toolkit

The Claude Desktop app has three tabs, each suited to a different part of your research workflow.

**Chat** — The familiar conversation interface. Brainstorm research questions, debate your argument structure, ask Claude to explain a statistical concept, or get feedback on a paragraph you paste in. Best for back-and-forth thinking and Q&A.

**Cowork** — Your Research Assistant. Give Claude access to a folder on your computer, describe what you want done, and let it work. Claude reads, creates, and edits files in that folder — you approve the plan, then let it run (keep the app open while it works). It can queue multiple tasks and work through them. Best for bulk creative work: "Organize these 30 PDFs into a literature review spreadsheet," "Draft a methods section based on my analysis scripts," "Clean up and format all my references."

**Code** — Your Project Manager. This is Claude Code, running right inside the Desktop app — no terminal needed. Select a project folder, and Claude can read every file, edit them, *and* handle all the Git operations (saving, undoing, branching, pushing to GitHub). You tell it what to do in plain English. It has a built-in diff view that shows you exactly what changed before you accept. Best for the full write-review-save-collaborate cycle that this guide teaches.

**The key distinction**: Cowork is the talented RA who drafts sections and crunches data. Code is the project manager who tracks every version, files the paperwork, and makes sure nothing is ever lost. Use Cowork to *produce*. Use Code to *manage*.

Chat and Code are available on macOS and Windows. Cowork is currently a research preview, available on macOS only. Linux is not currently supported. Check [claude.com/pricing](https://claude.com/pricing) for the latest on plans and platform support. Pro, Max, Team, and Enterprise plans all include access. Cowork and Code use more of your usage allowance than Chat. (These details change frequently — the concepts in this guide stay the same even as the tools evolve.)

**Also worth knowing about**: [Nimbalyst](https://nimbalyst.com) is a free app that wraps Claude Code in a more visual interface — rendered Markdown, inline diffs, session management. It requires a Claude Pro or Max subscription. If you find the Code tab too text-heavy, it's a nice alternative that works with the same Git workflow.

### 4. Why Git Matters Even More with AI

AI tools like Claude can generate and revise text fast. That's powerful — but without Git, those changes are untraceable. Did you write that paragraph, or did Claude? Which version of the analysis code produced which results? If Claude's edit introduced an error, how do you get back to your version?

Git answers all of this:

- **See exactly what Claude changed** — the diff shows the before and after, line by line
- **Instant undo** — if Claude's edit isn't what you wanted, one request gets your version back
- **An audit trail for AI disclosure** — journals increasingly require it, and your commit history is the evidence
- **Clear attribution** — "I wrote the first draft (commit 1), Claude suggested revisions (commit 2), I manually edited the final version (commit 3)"

If you use AI to help write your paper, Git isn't optional. It's how you stay in control.

---

## Part II: Your First Project — Let Claude Set It Up

### 5. Getting Started

Open the Claude Desktop app. Click the **Code** tab. Click **Select folder** and choose (or create) the folder for your paper.

Git needs to be installed on your computer. On Mac, it usually is already — if not, Claude will prompt you to install it (one click). On Windows, Claude will guide you through installing it if needed.

You now have a session. Everything from here is a conversation.

> **You say:** "Set up this folder as a Git project for a research paper. Create a paper.md, a references.bib file, and folders for figures, code, and data. Add a .gitignore and a README."

Claude creates the files, sets up the folder structure, and initializes Git — all in one step:

```
my-paper/
├── README.md
├── paper.md
├── references.bib
├── figures/
├── code/
├── data/
└── .gitignore
```

Review what Claude created in the diff view. Accept the changes.

Your folder is now a **repository** — a project tracked by Git. Every time you **commit**, Git records a permanent snapshot you can return to. Until you commit, your edits are just a working draft — saved in your editor, but not yet in Git's history.

### 6. Writing and Saving Your Work

Write in `paper.md` using whatever text editor you like, or ask Claude to draft sections directly in the Code tab. When you've finished a meaningful chunk of work — a section, a round of edits, an updated figure — it's time to save a snapshot.

> **You say:** "Commit my changes — I finished the first draft of the introduction"

Claude stages the changed files and saves a snapshot with a descriptive message.

That's a **commit** — a permanent checkpoint you can always return to. Think of it like a named save point in a video game. You can have as many as you want, and you can always go back to any of them.

**How often should you commit?** After each meaningful chunk of work. Finished the introduction? Commit. Fixed a calculation error in the analysis? Commit. Updated Figure 3? Commit. You don't need to commit every keystroke, but don't wait until the end of the day either. The more commits you have, the more checkpoints you can return to.

### 7. Seeing Your History

> **You say:** "Show me the history of this project"

Claude shows a list of all your commits — when each was made, the message you (or Claude) wrote, and what files changed.

> **You say:** "Show me what changed in paper.md since last Tuesday"

Claude shows a **diff** — the exact lines that were added, removed, or modified, with surrounding context. Added lines show in green. Removed lines show in red.

> **You say:** "Show me what the methods section looked like in the version from two weeks ago"

Claude retrieves the old version so you can read it or compare it side-by-side with the current one.

A **diff** is like track changes in Word, but better: it's precise, it's permanent, and it works between *any* two points in your project's history — not just "current" and "previous."

![Your project's history — every commit is a checkpoint you can return to](assets/Fig2.png)

---

## Part III: Using Claude to Write and Edit Your Paper

### 8. The Write, Review, Save Cycle

This is the core rhythm of working with Claude Code on your paper:

1. **Write or ask Claude to edit.** "Strengthen the argument in the discussion section" or "Add a paragraph about limitations of the sample size."
2. **Review the diff.** Claude shows exactly what it changed. Accept, reject, or ask for adjustments. (For long paragraphs, ask Claude to "show me which words changed" for a finer view.)
3. **Commit.** "Save this — Claude improved the discussion section."
4. **Repeat.**

One important tip: **always commit your own work before asking Claude to edit.** That way you have a clean before-and-after — your version is saved as one commit, Claude's changes as the next. If you don't like what Claude did, you can undo just its changes without losing yours.

![The Write-Review-Save cycle](./assets/Fig3.png)

### 9. AI-Assisted Drafting with Cowork

Switch to the **Cowork** tab when you want Claude to handle bigger, more autonomous tasks. Give it access to your paper folder, describe the outcome you want, and let it work:

- "Read all the scripts in code/ and draft a detailed methods section for paper.md"
- "Go through data/results.csv and create a summary table with key statistics for the results section"
- "Review the full paper and list any inconsistencies between the methods and results"
- "Format all entries in references.bib into consistent APA style"

Cowork makes a plan, you approve it, then it works through the task — potentially for several minutes. Keep the app open while it runs.

**Important**: Cowork produces content, but it doesn't save it to your Git history. When Cowork finishes, switch to the **Code** tab to review the changes and commit them. That's what makes the work permanent and undoable. **Don't skip the review** — Cowork can occasionally introduce errors or inconsistencies, especially in technical content. The Code tab's diff view is your quality gate. (Note: Cowork is a research preview — it can access the internet and its conversations are stored locally, not in organizational audit logs. Avoid using it with regulated or sensitive data.)

A good handover prompt:

> "I just finished a Cowork session. Review the new files, check the formatting matches the rest of the paper, and commit the changes."

### 10. Using Chat for Thinking, Code for Doing

Use the **Chat** tab for open-ended thinking: "What are the strongest arguments against my hypothesis?", "Help me outline the discussion section," "Critique this paragraph."

Use the **Code** tab for anything that touches files: "Add that outline to paper.md," "Rewrite the abstract to be under 250 words," "Update Figure 2's caption."

Think in Chat, execute in Code.

---

## Part IV: Safety Nets — Undoing Things

### 11. When Things Go Wrong

This is where Git becomes your best friend. Researchers fear losing work more than almost anything — Git makes it nearly impossible.

> **You say:** "Undo the last change to paper.md"

Claude restores the file to its previous version. Done.

> **You say:** "Undo the last commit"

Claude reverses the entire last save point.

**If you already pushed the commit to GitHub**: tell Claude to "revert the last commit" instead — this creates a new commit that undoes the changes, which is safe for collaboration. "Undo" rewinds history, which is fine for local-only work but can cause problems if others have already pulled your changes.

> **You say:** "Show me what paper.md looked like 3 saves ago"

Claude retrieves it so you can read it or restore it.

A **restore** gets a file back to how it was at a previous commit. It's non-destructive — your full history is still there.

**The golden rule: if you committed it, you can always get it back.** This is why committing often matters. Every commit is a safety net.

And if you ever feel completely lost:

> **You say:** "I'm confused. Show me the last three versions of my paper and help me pick which one to go back to."

Claude will walk you through it.

### 12. Branches: Safe Experimentation

Sometimes you want to try something risky without touching your main draft. Maybe you want to reframe the entire argument. Maybe you want to let Claude take a radical pass at the introduction. Maybe you want to try a completely different statistical model.

> **You say:** "Create a branch called 'try-different-framing' and switch to it"

Now you're working on a parallel copy. Your main draft is completely untouched.

A **branch** is a "what if" scenario. What if I used a different statistical model? What if I reframed the Discussion for a different journal? You can explore that path without ever breaking the official version.

![Branches: your official draft is always safe on main](assets/Fig4.png)

Use cases for researchers:

- Let Claude rewrite the introduction while your version stays safe on `main`
- Try a completely different analysis approach
- Work on reviewer revisions without changing the submitted version

When the experiment works:

> "Merge try-different-framing back into main"

When it doesn't:

> "Switch back to main and delete the try-different-framing branch"

The Desktop app's Code tab can also run parallel sessions, so you can try two experiments side by side without them interfering with each other.

---

## Part V: Sharing and Collaborating with GitHub

### 13. Putting Your Paper on GitHub

GitHub is a website that hosts your Git repository, making it accessible from anywhere and to anyone you choose.

> **You say:** "Create a GitHub repository for this project and push everything up. Make it private."

Claude handles the entire process — creating the repo, connecting it to your local folder, and uploading your files. (The first time you connect to GitHub, Claude will walk you through signing in — it takes about 30 seconds.)

If Claude can't create the repo automatically, you can create an empty private repo on the GitHub website (skip the README), then tell Claude: "Add this GitHub repo as the remote and push." Same result, one extra step.

**Public vs. private**: keep it private during writing and review. Make it public upon publication for open science and reproducibility.

**Never put sensitive data on GitHub** — no patient data, no credentials, nothing covered by IRB, HIPAA, or GDPR. Use `.gitignore` to exclude sensitive files, and ask Claude to check before you push.

**Git is for text and small files.** If your datasets are large (hundreds of MB or more), keep them in `data/` but ask Claude to add them to `.gitignore` so they don't get uploaded. Store the big stuff on your university server, or on a data repository like [Figshare](https://figshare.com) or [OSF](https://osf.io) (which can also mint DOIs for your datasets).

**One more thing**: if you have data in Excel (`.xlsx`) or tables in Word (`.docx`), consider exporting them to `.csv` or Markdown. Git can track changes inside text files but treats Excel and Word as opaque blobs — you'll see that a file changed, but not *what* changed. Keep the originals wherever you like, but the Git-tracked version should be plain text when possible.

Your `README.md` becomes the project's front page on GitHub — describe your paper, list what's in each folder, and explain how to reproduce your results.

### 14. Working with Co-Authors

Add co-authors as collaborators on the GitHub website (your repo's Settings page, then Collaborators).

The daily rhythm, all via Claude Code:

> **Before you start working:** "Pull the latest changes from GitHub"

This gets any edits your co-authors have pushed since you last worked.

> **After you finish:** "Commit my changes and push to GitHub"

This saves your work and shares it with your co-authors.

**Commit often, in small chunks** — this is the single best tip for collaborative writing. The more frequently you and your co-authors commit, the less likely you are to edit the same paragraph at the same time. Small, frequent saves keep everyone in sync and reduce conflicts.

![The daily rhythm: Pull, Edit, Commit, Push](assets/Fig5.png)

**Reviewing paragraph changes**: Git normally shows changes line by line, which can make a one-word fix in a long paragraph look like you rewrote the whole thing. When that happens, ask Claude for a finer view:

> "Show me which words changed, not just the whole lines"

Claude will highlight the exact words that were added or removed within the paragraph — much easier to scan.

Some writers put each sentence on its own line to make diffs cleaner (called [Semantic Line Breaks](https://sembr.org)). It's optional — the word-diff approach above works fine with normal paragraphs.

When two people *do* edit the same paragraph, Git flags it as a **conflict** — it can't decide which version to keep. Claude Code can help:

> "Show me the conflict and help me pick the right version"

Or, if both versions have good parts:

> "Combine both versions — keep their new data points but use my original wording"

**Going further**: once your team is comfortable, GitHub has features like **Pull Requests** (co-authors review your changes before they're merged) and **Issues** (a shared to-do list for tracking tasks like "Write abstract" or "Update Figure 2"). These are optional — simple push/pull works fine to start.

---

## Part VI: From Draft to Submission

### 15. Converting Markdown to Submission Format

Journals usually want Word or PDF. Pandoc converts Markdown to almost anything.

> **You say:** "Convert paper.md to a Word document with APA citations using references.bib"

Claude installs anything needed (like Pandoc), runs the conversion, and produces `paper.docx`.

**How citations work**: In your Markdown, you write `[@smith2024]` where you want a citation. You keep your references in a `.bib` file (the standard BibTeX format that reference managers export). Pandoc combines the two to produce properly formatted in-text citations and a bibliography.

If you use [Zotero](https://www.zotero.org), the [Better BibTeX](https://retorque.re/zotero-better-bibtex/) plugin can auto-export your library to a `.bib` file that stays in sync whenever you add a paper.

**CSL styles** control the formatting — APA, Nature, IEEE, Chicago, and thousands more. You can ask Claude to find and apply the right one for your target journal.

**Heads up**: Markdown to Word works out of the box. Markdown to PDF requires a LaTeX engine (like TinyTeX). If it's not installed, Claude will try to set it up — but on some university-managed computers, you may not have permission to install software. **Plan B**: convert to Word first, then use Word's built-in "Save As PDF." You get the same result with zero installation.

Claude can also help with journal-specific formatting:

> "Format this paper for submission to [Journal Name]"

### 16. Tagging Milestones

> **You say:** "Tag this version as 'submitted-v1'"

This marks the exact state of your project forever. Later, you can always go back:

> "Show me the submitted-v1 version"

...and see exactly what you sent to the journal — every file, every line, exactly as it was.

Useful tags throughout the publication lifecycle: `submitted-v1`, `revision-1`, `accepted`, `camera-ready`.

**Make your repo citable**: ask Claude to add a `CITATION.cff` file to the project. GitHub will automatically show a "Cite this repository" button on your repo page. You can also archive a release to [Zenodo](https://zenodo.org) to mint a permanent DOI.

If you're making your repo public, ask Claude to add a `LICENSE` file too — `CC-BY 4.0` is common for academic papers and text, while `MIT` works well for code.

### 17. Handling Reviewer Revisions

Tag your submitted version first (see above). That freezes what you sent to the journal.

Then make your revisions. The best strategy is one commit per reviewer point, so your history reads like a checklist:

- "Address reviewer 2 comment on sample size"
- "Add supplementary figure per reviewer 1 request"
- "Rewrite limitations paragraph per editor suggestion"

Keep a `response-to-reviewers.md` file in the repo tracking what you changed and why.

Claude can help with the actual revisions:

> "Reviewer 2 says our sample size justification is weak. Read paper.md and strengthen that section."

And Claude can draft the response letter from your commit history:

> "Summarize everything I changed since submitted-v1 and draft a response-to-reviewers document"

When you're done, tag again:

> "Tag this as revision-1-submitted"

![Your complete paper history — from first submission to final version](assets/Fig6.png)

---

## Concepts Glossary

| Term | What it means |
| --- | --- |
| **Repository (repo)** | Your project folder, tracked by Git |
| **Commit** | A saved snapshot — with a note about what changed and why |
| **Diff** | A view showing exactly what's different between two versions |
| **Branch** | A parallel copy for experimenting without affecting your main work |
| **Merge** | Combining a branch back into the main version |
| **Push** | Uploading your commits to GitHub (the **remote** copy) |
| **Pull** | Downloading your co-authors' latest commits from GitHub to your computer (your **local** copy) |
| **Tag** | A permanent label on a specific commit (e.g., "submitted-v1") |
| **Conflict** | When two people changed the same line — Git asks you to pick |
| **.gitignore** | A list of files Git should not track (compiled outputs, big data, OS junk) |

---

## Cheat Sheet: What to Tell Claude Code

All of these work in the **Code** tab of the Claude Desktop app. No command line needed. These aren't commands to memorize — they're conversation starters. Rephrase however feels natural.

| What you want | What to say to Claude |
| --- | --- |
| Start a new project | "Set up this folder as a Git project for a research paper" |
| Save your work | "Commit my changes — I finished the results section" |
| See what changed | "Show me what I've changed since my last commit" |
| See full history | "Show me the history of this project" |
| Compare versions | "Compare the current intro to how it looked last week" |
| Undo a change | "Undo the last change to paper.md" |
| Undo a commit | "Revert the last commit" |
| Try something risky | "Create a branch called try-new-approach" |
| Share on GitHub | "Create a private GitHub repo and push this project" |
| Get co-author changes | "Pull the latest from GitHub" |
| Share your changes | "Push my commits to GitHub" |
| Convert for submission | "Convert paper.md to Word with APA citations" |
| Tag a milestone | "Tag this as submitted-v1" |
| Review paragraph edits | "Show me which words changed, not just whole lines" |
| Resolve a conflict | "Show me the conflict and help me pick the right version" |
| I'm lost | "Show me the last three versions and help me pick one" |

---

## Starter Templates

### `paper.md`

```markdown
---
title: "Your Paper Title"
author:
  - First Author
  - Second Author
date: 2026-02-06
bibliography: references.bib
---

# Introduction

# Methods

# Results

# Discussion

# References
```

### `README.md`

```markdown
# [Paper Title]

**Authors**: [Names]
**Status**: Draft | Submitted | In Review | Published

## About
Brief description of the paper and research question.

## Repository Structure
- `paper.md` — Manuscript (Markdown)
- `references.bib` — Bibliography
- `figures/` — Figures
- `code/` — Analysis scripts
- `data/` — Datasets

## Reproducing Results
Steps to regenerate figures and analysis from code and data.
```

---

## Sources

1. [A Quick Introduction to Version Control with Git and GitHub](https://pmc.ncbi.nlm.nih.gov/articles/PMC4718703) — Blischak, Davenport & Wilson, 2016, PLOS Computational Biology
2. [Git & GitHub Tutorial for Scientists](https://gitbookdown.dallasdatascience.com/)
3. [Git for Research Projects — The Turing Way](https://book.the-turing-way.org/reproducible-research/vcs/vcs-git-in-research)
4. [Git for Scientists](https://neurathsboat.blog/post/git-intro) — Neurath's Boat, 2019
5. [Curating Research Assets: Git Version Control](https://journals.sagepub.com/doi/full/10.1177/2515245918754826) — Vuorre & Curley, 2018
6. [Git Can Facilitate Greater Reproducibility in Science](https://pmc.ncbi.nlm.nih.gov/articles/PMC3639880/) — Ram, 2013
7. [10 Tips for Collaborative Writing with LaTeX and GitHub](https://willfondrie.com/2024/02/10-tips-for-collaborative-writing-with-latex-and-github/) — Fondrie, 2024
8. [Introducing Cowork](https://claude.com/blog/cowork-research-preview) — Anthropic, 2026
9. [Claude Code on Desktop](https://code.claude.com/docs/en/desktop) — Anthropic Documentation
10. [Claude Code Overview](https://code.claude.com/docs/en/overview) — Anthropic Documentation
11. [Getting Started with Cowork](https://support.claude.com/en/articles/13345190-getting-started-with-cowork) — Claude Help Center

---

**Start small.** Set up one project. Make one commit. The rest follows naturally.

---

*This guide is licensed under *[*CC-BY 4.0*](https://creativecommons.org/licenses/by/4.0/)*. You are free to share and adapt it with attribution.*
*Source: *[*github.com/yaniv-golan/git-for-scientists*](https://github.com/yaniv-golan/git-for-scientists)
*Found something outdated or have a suggestion? *[*Open an issue*](https://github.com/yaniv-golan/git-for-scientists/issues)* or *[*start a discussion*](https://github.com/yaniv-golan/git-for-scientists/discussions)* — help us keep this guide current.*
