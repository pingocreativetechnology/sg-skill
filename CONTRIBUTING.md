# Contributing

Thanks for helping make the Singlish skill better. Issues and pull requests are welcome.

## Adding or fixing a word

Add a row to the right section of [`skills/singlish/reference/vocabulary.md`](skills/singlish/reference/vocabulary.md). Every entry needs all four columns:

| Term | Origin | Meaning | Example |
|---|---|---|---|
| shiok | Malay / Punjabi (OED) | Great, wonderfully satisfying | "Build in 8 seconds, shiok!" |

- **Meaning:** what the word really means in Singapore today. If it has more than one sense, give the main one first.
- **Origin:** Hokkien, Teochew, Cantonese, Mandarin, Malay, Tamil, English and so on. Write "uncertain" rather than guess.
- **Example:** one short, natural sentence, ideally from a coding or work context.
- **Source:** in the PR description, link a source (a dictionary, an article or an academic paper) or explain how the word is used.
- Mark sensitive words with a *Caution:* note. **Vulgar terms and slurs are not accepted** as usable entries; at most they get a name in the "never use" list.
- Only words you're confident about. If you're not sure of a word, leave it out.

## Changing the rules

Changes to `SKILL.md` (intensity levels, hard rules, the coding table) should keep the file focused. Put long lists in `reference/`. Never weaken the rule that code, comments, commits, docs and PRs stay in standard English by default.

## Style

- Keep tables valid Markdown, one entry per row.
- British spelling in prose, matching Singapore Standard English.
- Be respectful: Singlish is a living language, not a joke.

By contributing, you agree that your contributions are licensed under the MIT License.
