# sg-skill: vibe code in Singlish with Claude Code

**Website:** https://sg-skill.pingocreativetechnology.com

**sg-skill lets you vibe code in Singlish with Claude Code, then ship in standard English.** sg-skill is a Singlish skill for [Claude Code](https://docs.claude.com/en/docs/claude-code) that lets Claude understand Singaporean English (Singlish) and reply at your level, while your code, comments, commits and docs stay clean and professional.

> **You:** Eh the docker build fail again leh, why like that?
> **Claude:** Fail at `npm ci` because the lockfile out of sync with `package.json` lor. Run `npm install`, commit the lockfile, then rebuild. Should be OK after that.

Built by **[Pingo Creative Technology](https://pingocreativetechnology.com)**.

**Keywords:** Singlish, Singaporean English, Singapore English, Singapore, kopitiam, discourse particles, Claude Code, Claude skills, Agent Skills, vibe coding, AI coding assistant, LLM

**Tags:** #Singlish #Singapore #ClaudeCode #ClaudeSkills #AgentSkills #VibeCoding

---

## Purpose

Many Singaporeans think and chat in Singlish, especially when they're relaxed, stuck or celebrating. sg-skill lets you talk to Claude the way you'd talk to a friendly colleague at the kopitiam, and Claude talks back the same way. You stay the same careful engineer, and so does Claude: only the conversational voice changes.

The aim is to sound like a friendly Singaporean colleague, never a caricature. Singlish is treated as a real, rule-governed way of speaking, not a joke.

## What's included

All of this lives in two files: [`SKILL.md`](skills/singlish/SKILL.md) and [`reference/vocabulary.md`](skills/singlish/reference/vocabulary.md).

- **6 hard rules** that always apply (see [Ground rules](#ground-rules-the-skill-enforces)).
- **When to switch on and off:** triggered by Singlish particles, grammar or vocabulary, or by asking for Singlish. A single stray "lah" gets Level 1 at most, and group contexts such as PR reviews and issue replies stay in standard English.
- **3 intensity levels:** light / professional, casual and full kopitiam, with a simple rule of thumb for judging yours from your last two or three messages.
- **18 discourse particles and tags** with their function, tone and an example: *lah, leh, lor, meh, sia, hor, what, mah, ah, hah, one, liao, nia, can, cannot, or not, is it* and *bah*.
- **19 key grammar patterns** with standard-English equivalents, such as topic-comment ("This function ah, too long already"), dropped articles and "be", *can or not*, *got*, *already* / *liao*, reduplication ("try try first"), the *kena* passive and "then" for "if".
- **Code-switching habits:** mixing Hokkien, Malay and Cantonese words in one sentence, switching to standard English for warnings, steps and quoted errors, and answering in Mandarin only if you're clearly writing in it.
- **Top 60 words** in `SKILL.md`, from *shiok*, *jialat* and *sian* to *gostan*, *lobang* and *huat*.
- **Full vocabulary reference:** 212 entries in 8 themed sections, each with origin, meaning and an example, plus a list of words to understand but never use. Claude reads it only when it meets a word it doesn't recognise.

  | Section | Entries |
  |---|---|
  | 1. Exclamations and reactions | 24 |
  | 2. Feelings and states of mind | 23 |
  | 3. People and types | 31 |
  | 4. Food, drink and daily life | 33 |
  | 5. Work, effort and trouble | 48 |
  | 6. Quality and judgement | 13 |
  | 7. Talking, thinking and understanding | 28 |
  | 8. Set phrases | 12 |
  | **Total** | **212** |

- **22 vibe-coding requests** mapped to what they mean and how Claude should respond, such as "this one can or cannot?", "help me tapao this function", "why the build so jialat one?", "die die must pass CI" and "gostan, gostan!".
- **6 example dialogues:** one at each intensity level, a commit message (always standard English), switching back to formal English, and a risky action at Level 3.

## Repository layout

```
sg-skill/
├── skills/
│   └── singlish/
│       ├── SKILL.md                 # rules, levels, particles, grammar, top 60 words, vibe-coding map, examples
│       └── reference/
│           └── vocabulary.md        # full vocabulary: 212 entries with origin, meaning and example
├── docs/
│   ├── description-short.md         # short listing description
│   ├── description-long.md          # longer description
│   └── social/                      # promo post drafts
├── README.md
├── CONTRIBUTING.md
├── LICENSE
└── .gitignore
```

`SKILL.md` stays focused. Claude loads `reference/vocabulary.md` only when it needs it, following Claude Code's progressive-disclosure layout for skills.

## Installation

A skill is a folder named after the skill that contains a `SKILL.md`. Copy the `skills/singlish` folder, including its `reference/` subfolder, to one of these places:

| Scope | Destination |
|---|---|
| Personal (all your projects) | `~/.claude/skills/singlish` |
| Project (shared with your team through the repo) | `.claude/skills/singlish` in the project root |

The repo is at https://github.com/pingocreativetechnology/sg-skill (or download it as a ZIP from that page).

**Personal skill:**

```bash
git clone https://github.com/pingocreativetechnology/sg-skill.git /tmp/sg-skill
mkdir -p ~/.claude/skills
cp -R /tmp/sg-skill/skills/singlish ~/.claude/skills/singlish
```

**Project skill** (run from your project root):

```bash
git clone https://github.com/pingocreativetechnology/sg-skill.git /tmp/sg-skill
mkdir -p .claude/skills
cp -R /tmp/sg-skill/skills/singlish .claude/skills/singlish
```

You should end up with `SKILL.md` and `reference/vocabulary.md` inside the `singlish` folder. Start a new Claude Code session (or restart it) so the skill is picked up.

## Usage

There's nothing to invoke. Just write the way you normally would. Claude reads your last two or three messages, picks a level, and never goes more than one level above you.

**Level 1: light / professional**

> **You:** Can you check why the login test is failing? Thanks ah.
> **Claude:** Can. `login.spec.ts` fails because the mock returns `401`. The fixture token expired on 1 Oct. I've regenerated it in `fixtures/auth.json` and the test passes now.

**Level 2: casual**

> **You:** Eh this build fail again leh, why like that?
> **Claude:** Fail because the env variable missing lor. Add `API_KEY` in `.env` then rerun, should be OK.

**Level 3: full kopitiam**

> **You:** Walao eh, whole morning debug this useEffect still cannot, I damn blur already sia. Help me lah.
> **Claude:** Aiyoh, steady, don't stress lah. Your `useEffect` got no dependency array, so every render it run again and set state, then loop non-stop. Add the deps at the back:
> ```tsx
> useEffect(() => {
>   fetchUser(id);
> }, [id]);
> ```
> Confirm settle one. Go makan first, come back test.

Then say *"ok shiok, commit it lah"* and the commit message still comes out in standard English: `fix(profile): add dependency array to prevent useEffect render loop`.

Switch back to formal English ("Please write a formal incident summary for the stakeholders") and Claude switches with you.

### Intensity levels

| Level | You sound like | Claude sounds like |
|---|---|---|
| **1. Light / professional** | "Can check the logs for me? Thanks ah." | Standard English with at most one particle or one "can". |
| **2. Casual** | "Eh this build fail again leh, why like that?" | Short sentences, one or two particles, one or two common words. |
| **3. Full kopitiam** | "Walao eh, whole morning debug still cannot, I damn blur already sia." | Warm and expressive, up to three particles, technical content still crystal clear. |

Rule of thumb: 0 to 1 particles or slang words means Level 1, 2 to 4 means Level 2, and 5 or more (or heavy Hokkien or Malay) means Level 3. If Claude is unsure, it goes one level below. If you're stressed or something is on fire, it drops a level and gets to the point.

## Verify it loaded

1. Check the files are in place:

   ```bash
   ls ~/.claude/skills/singlish        # or: ls .claude/skills/singlish
   # SKILL.md  reference
   ```

2. Start a new Claude Code session and ask *"What skills are available?"*. `singlish` should be in the list.
3. Type something like *"eh can help me check why this test fail or not?"*. Claude should answer in light-to-casual Singlish. Then type in formal English and it should answer in formal English.

## Ground rules the skill enforces

1. **Deliverables stay in standard English.** Code, comments, commits, docs, PRs and anything else you ship, unless you explicitly ask for Singlish there.
2. **Accuracy beats flavour.** Commands, paths, flags, numbers, versions and warnings stay exact.
3. **No vulgar slang or slurs**, even if you use them.
4. **No caricature:** no mock accents, no stacking slang for comedy, no name-calling.
5. **It follows your lead,** on and off.
6. **Safety is never casual.** Destructive or irreversible actions get a plain, unmistakable warning.

## Contributing

Spotted a missing word, a wrong meaning or a better example? Issues and pull requests are welcome. Every vocabulary entry needs a meaning, origin and example, plus a source in the PR description. Vulgar terms and slurs aren't accepted as usable entries. See [`CONTRIBUTING.md`](CONTRIBUTING.md) for the details.

## Sources

Meanings and particle functions were checked against:

- **Oxford English Dictionary** Singapore English additions: *lah*, *sinseh* (March 2000); *kiasu* (March 2007; Word of the Day, 11 February 2015); *ang moh, blur, shiok, sabo, lepak, sotong, wah, teh tarik, hawker centre, HDB* (March 2016); *Ah Beng, aiyah, aiyoh, atas, ang pow, hongbao, char kway teow, kopitiam, mamak, bodoh* (September 2016); *agak-agak, boleh, BTO, jialat, kaypoh, Mat Salleh, play play, wayang* (March 2026). Via oed.com update pages, *The Straits Times*, CNA and Language Log.
- **Jack Tsen-Ta Lee**, *A Dictionary of Singlish and Singapore English* (mysmu.edu / singlishdictionary.com).
- **Colin Goh & Y. Y. Woo**, *The Coxford Singlish Dictionary* (2002; 2nd ed. 2009), from TalkingCock.com.
- **Wikipedia**, "Singlish" and "Singlish vocabulary" (consulted October 2026).
- **Gupta, A. F.** (1992). "The pragmatic particles of Singapore colloquial English." *Journal of Pragmatics* 18(1), 31–57.
- **Wee, L.** (2002). "*Lor* in colloquial Singapore English." *Journal of Pragmatics* 34(6); and (2004) "Reduplication and discourse particles", in L. Lim (ed.), *Singapore English: A Grammatical Description*.
- **Lim, L.** (2007). "Mergers and acquisitions: on the ages and origins of Singapore English particles." *World Englishes* 26(4).
- **Leimgruber, J. R. E.** (2013). *Singapore English: Structure, Variation, and Usage* (CUP); (2016) "*Bah* in Singapore English", *World Englishes*.
- **Deuber, D., Leimgruber, J. R. E. & Sand, A.** "Singaporean internet chit chat compared to informal spoken language", *Journal of Pidgin and Creole Languages* (particle functions table).
- **Mothership**, "17 Singlish words that offer so much more than their English equivalents" (2014); **Rice Media** essays on Singlish and identity.
- **Wiktionary** (*chope*, *siong*) and **singlish.net** (*OTOT*).
- A sample of public **X posts** (July–October 2026) to check current usage (*bo jio*, *walao*, *shiok sia*, *can or not*, *paiseh*, *pangseh*).

Singlish varies by speaker, ethnicity and generation, and spelling isn't standardised. Corrections are welcome.

## Licence

Released under the MIT License; see [`LICENSE`](LICENSE).

Copyright (c) 2026 [Pingo Creative Technology](https://pingocreativetechnology.com).

---

*sg-skill changes Claude's conversational voice only. It doesn't change what Claude is allowed to do. Keep your normal permission settings and review changes before you ship them.*
