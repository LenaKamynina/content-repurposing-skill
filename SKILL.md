---
name: content-repurposing
description: Turns a raw YouTube video transcript into a brand-voiced LinkedIn post, an X/Twitter thread, and a newsletter section, following this brand's finalized voice and per-platform format rules. Use this whenever the user pastes or attaches a YouTube transcript and wants it turned into social or newsletter content, or asks to "repurpose this video," "turn this transcript into posts," "make a LinkedIn post and thread out of this," or similar — even if they don't name all three output formats explicitly. Also use when asked to regenerate or tweak just one of the three formats from a transcript already in the conversation.
---

# Skill: YouTube Transcript → Multi-Platform Content

## Input
- `transcript`: Full YouTube video transcript (raw text)

## Reference Files
- [brand-voice.md](brand-voice.md): Brand tone, vocabulary, and positioning
- [platform-formats.md](platform-formats.md): Format requirements for each output
- [examples/](examples/): Sample posts for format reference (if present) — check the matching file per platform (`linkedin-example.md`, `twitter-example.md`, `newsletter-example.md`) before drafting that platform's output

## Process

### Step 1: Extract Key Ideas
Read the full transcript. Identify:
- The central argument or main point (1 sentence)
- 3–5 supporting ideas or insights
- Any specific data points, stories, or examples worth preserving
- The actionable takeaway, if one exists

Do not paraphrase yet. Just extract and list.

### Step 2: Write the LinkedIn Post
Using brand-voice.md for tone and platform-formats.md for structure:
- Write a hook based on the most compelling idea from Step 1
- Develop the post using 2–3 of the supporting ideas
- End with a CTA or question
- Review: Does the first line work as a standalone hook? Is it under 300 words?

### Step 3: Write the X Thread
Using brand-voice.md for tone and platform-formats.md for structure:
- Tweet 1: Hook (standalone)
- Tweets 2–8: One insight per tweet from the Step 1 list
- Final tweet: CTA, summary, or question
- Review: Is every tweet under 280 characters? Does each stand alone?

### Step 4: Write the Newsletter Section
Using brand-voice.md for tone and platform-formats.md for structure:
- Write a short intro that sets context (1–2 sentences)
- Develop the main insight from the transcript (the "so what")
- Add a practical implication or next step
- Review: Is it 300–500 words? Does the section read as self-contained?

### Step 5: Output
Return all three pieces, clearly labeled:
- LINKEDIN POST
- X THREAD
- NEWSLETTER SECTION

Each separated by a horizontal rule. No meta-commentary about what was written.
