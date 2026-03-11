# HTML Slides Studio

`html-slides-studio` is a Codex skill for turning a detailed outline or manuscript into a high-aesthetic, single-file HTML slide deck.

It is designed for people who want:

- HTML slides instead of PPT
- stronger visual systems and front-end interactions
- a strict workflow of `style choice -> input collection -> page planning -> confirmation -> generation`
- editable decks with speaker notes, image insertion, autosave, and full-HTML save

This public repository contains the **sanitized public version** of the skill.
All templates use placeholder text. No private deck content, names, QR codes, or client material are included.

## What The Skill Does

When triggered, the skill does not jump straight into writing slides.
It forces a more reliable workflow:

1. Ask the user to choose one of four design languages
2. Collect the missing talk inputs
3. Plan the slide list first
4. Wait for confirmation
5. Generate or revise the final HTML deck

This is useful when the user already has a topic, draft, or manuscript and wants a strong presentation layer instead of asking AI to invent the whole talk from scratch.

## Design Languages

The skill ships with four visual systems:

1. `A · Warm Editorial`
2. `B · Dark Terminal`
3. `C · Swiss Grid`
4. `D · Japanese Ink`

Template assets live in:

- `assets/template-a-warm-editorial.html`
- `assets/template-b-terminal.html`
- `assets/template-c-swiss.html`
- `assets/template-d-ink.html`

## Built-In Capabilities

- Single-file HTML output
- 16:9 presentation layout
- Page-plan confirmation before generation
- Speaker notes / presenter view
- Front-end edit mode
- Local autosave for edits
- `Ctrl+S` / `Cmd+S` full-document save
- Full HTML serialization so edits persist to the whole file
- Image insertion, drag, and resize
- Print CSS for per-slide PDF export

Important detail:

- Direct write-back to the same `.html` file depends on the browser supporting the File System Access API and the user granting permission.
- If direct write-back is unavailable, the deck falls back to downloading a complete updated HTML file.

## Repository Structure

```text
.
├─ SKILL.md
├─ agents/
│  └─ openai.yaml
├─ assets/
│  ├─ slides-template-v3.html
│  ├─ template-a-warm-editorial.html
│  ├─ template-b-terminal.html
│  ├─ template-c-swiss.html
│  └─ template-d-ink.html
├─ references/
│  ├─ content-playbook.md
│  ├─ design-rules.md
│  └─ implementation-rules.md
└─ scripts/
   └─ new_slides.ps1
```

## Install

If you use Codex local skills, copy this folder into your Codex skills directory.

Typical location on Windows:

```text
C:\Users\<your-user>\.codex\skills\html-slides-studio
```

Typical location on macOS / Linux:

```text
~/.codex/skills/html-slides-studio
```

After copying, the skill can be triggered as:

```text
Use $html-slides-studio ...
```

## Example Prompts

```text
Use $html-slides-studio to turn my detailed outline into a single-file HTML slide deck.
```

```text
Use $html-slides-studio. Start by asking me to choose A/B/C/D, then help me plan the deck before writing code.
```

```text
Use $html-slides-studio to revise this existing HTML deck, keep the interaction quality high, and add edit/save behavior.
```

## Expected Input Shape

The skill works best when the user already has:

- a topic
- an audience
- a duration
- a reasonably detailed outline

Minimal example:

```text
Style: A
Title: Your talk title
Subtitle: optional
Speaker: your name / org / date
Audience: who this is for
Duration: 45 minutes

Outline:
Part 1 - Problem
  1.1 Friction today
  1.2 Why now
Part 2 - Method
  2.1 Workflow
  2.2 Demo
Part 3 - Action
  3.1 Risks
  3.2 Next steps

Special requirements:
- needs screenshots
- needs speaker notes
- needs PDF export compatibility
```

## Public / Private Boundary

This repository is intentionally public-safe:

- placeholder templates only
- no personal QR codes
- no real course manuscript
- no client files
- no private contact information

If you want to use the skill for real work, replace the placeholders locally after installation.

## Notes

- `SKILL.md` is the machine-facing instruction file that drives Codex behavior.
- `README.md` is the human-facing introduction for repository visitors.
- The public templates are examples and starting points, not finished decks.

## License

No license file is included by default.
Add one if you want to explicitly allow reuse, modification, or redistribution.
