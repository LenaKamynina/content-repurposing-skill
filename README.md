# Content Repurposing Skill

A Claude Code skill that turns a raw YouTube video transcript into three pieces of ready-to-edit content, all matching a defined brand voice and platform-specific format rules:

- A **LinkedIn post**
- An **X/Twitter thread**
- A **newsletter section**

You paste a transcript, and Claude reads it, pulls out the core argument and supporting points, and drafts all three formats — labeled and separated, no extra commentary.

## How it works

```
content-repurposing-skill/
├── SKILL.md               ← the workflow Claude follows (input → extract → draft → output)
├── brand-voice.md          ← tone, vocabulary, grammar rules, words to avoid
├── platform-formats.md     ← structural rules per platform (length, hooks, CTAs, etc.)
└── examples/
    ├── linkedin-example.md
    ├── twitter-example.md
    └── newsletter-example.md
```

`SKILL.md` is the entry point. It tells Claude to:

1. Extract the central argument, 3–5 supporting ideas, and any concrete data points from the transcript — without paraphrasing yet.
2. Draft the LinkedIn post, using `brand-voice.md` for tone and `platform-formats.md` for structure.
3. Draft the X/Twitter thread, same references.
4. Draft the newsletter section, same references.
5. Return all three, clearly labeled and separated by a horizontal rule.

`brand-voice.md` and `platform-formats.md` are reference files — Claude only reads them when the skill runs, so the main workflow file (`SKILL.md`) stays short. The `examples/` files anchor tone and phrasing with real, previously published posts.

## Using it

Claude Code automatically discovers skills placed in `.claude/skills/<skill-name>/` inside a project. Drop this folder there (or wherever your setup expects skills), then in conversation:

> Paste a YouTube transcript and ask Claude to repurpose it, e.g. "repurpose this video into a LinkedIn post, thread, and newsletter section."

The skill's description in `SKILL.md`'s frontmatter is what makes Claude reach for it automatically — you don't have to invoke it by name.

## Adopting this for your own brand

This copy was built using Mailchimp's actual voice guide and real published posts as the working example. To point it at a different brand, three files need real content — nothing else in the repo should need to change.

### 1. `brand-voice.md` — replace entirely

This currently holds Mailchimp's voice-and-tone guide verbatim (voice vs. tone, the four voice traits, grammar/punctuation rules, "words to avoid" list, etc.). Swap in your own brand's actual style guide. If you don't have one written down yet, you'll need to answer at minimum:

- What's the personality/traits that don't change across posts (the "voice")?
- How does tone shift by context (frustrated customer vs. celebratory announcement)?
- Any hard grammar/punctuation rules (Oxford comma, contractions allowed, em dash usage)?
- A "words to avoid" list — jargon, clichés, or terms that are off-brand.

Keep the same file structure (voice vs. tone as separate sections, a clear words-to-avoid list) — the rest of the skill assumes those exist, even if the content underneath is entirely different.

### 2. `platform-formats.md` — verify against what you actually publish

This currently defines: LinkedIn (150–300 words), X/Twitter thread (multi-tweet, 8 tweets max), and Newsletter section (300–500 words, narrative). Before reusing this file as-is for a new brand:

- **Check it matches your real output**, not just an idealized spec. In this build, the real Twitter and newsletter examples turned out not to match their own format rules (real tweets were standalone posts, not threads; real "newsletter" content was short promo blocks, not narrative sections) — that mismatch went unresolved and is worth deciding one way or the other for your brand: either fix the spec to match reality, or fix your publishing habits to match the spec.
- Update character/word limits, hook conventions, hashtag policy, and CTA style to your platform's actual constraints and your team's actual habits.
- Add or remove platforms as needed — if you publish to Instagram, Threads, etc., add a matching section here and a matching file in `examples/`.

### 3. `examples/*.md` — replace with your own real posts

Each file currently holds real Mailchimp posts as tone/format anchors. Replace with 1–2 real posts per platform from your own brand. When you do:

- **Prefer real, previously published examples over invented ones** — Claude anchors phrasing and rhythm to these, so fabricated "ideal" examples tend to produce blander output than genuine ones.
- If a real example doesn't structurally match what's in `platform-formats.md` (as happened here), don't force it — either flag the mismatch in the file (see the structural notes at the top of `twitter-example.md` and `newsletter-example.md` in this repo for the pattern) or resolve the mismatch by editing `platform-formats.md`.
- If an example happens to use a word or phrase from your own "words to avoid" list, don't silently fix the example — leave it as a real reference but note the conflict, so future drafts don't inherit that phrase (see the note in `linkedin-example.md`).

### 4. `SKILL.md` — usually untouched

The workflow itself (extract → draft LinkedIn → draft thread → draft newsletter → output) is brand-agnostic and shouldn't need edits for a brand swap. The one thing worth revisiting: the frontmatter `description` field determines when Claude reaches for this skill automatically. If your team's phrasing for "repurpose this" differs (e.g., you always say "atomize this video" instead), consider whether the description covers that language.

## Known limitations

- Input is transcript text only — there's no built-in way to fetch a transcript from a YouTube URL. You paste the transcript in manually.
- Output formats are fixed at three (LinkedIn, X thread, newsletter). Adding a fourth platform means adding a section to `SKILL.md`, `platform-formats.md`, and a new file in `examples/`.
- The skill hasn't been run through a structured, multi-case evaluation yet — validate against a few real transcripts from your own content before relying on it at scale.
