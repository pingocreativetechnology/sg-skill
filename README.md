# Singlish Skill for Claude Code

A [Claude Code](https://docs.claude.com/en/docs/claude-code) skill that lets you vibe-code in **Singaporean English (Singlish)**. Talk to Claude the way you talk to your friends at the kopitiam, and it talks back the same way, while your code, comments, commits and docs stay in clean standard English.

> **You:** Eh the docker build fail again leh, why like that?
> **Claude:** Fail at `npm ci` because the lockfile out of sync with `package.json` lor. Run `npm install`, commit the lockfile, then rebuild. Should be OK after that.

Built by **Pingo Creative Technology**.

---

## What it does

- **Understands Singlish:** discourse particles (*lah, leh, lor, meh, sia, hor, what, mah, ah, hah, one, liao, nia*), grammar (*can or not*, *got*, *already*, topic-comment, *is it*), and a 200+ entry vocabulary drawn from Hokkien, Malay, Cantonese, Teochew, Mandarin, Tamil and English.
- **Replies in kind at your level:** three intensity levels, from light professional to full kopitiam. It never goes more than one level above you.
- **Keeps deliverables professional:** code, identifiers, comments, commit messages, docs, PR descriptions and other shipped text stay in standard English unless you explicitly ask otherwise.
- **Stays accurate and safe:** commands, paths and numbers are exact; risky actions get a plain-English warning; there's no vulgar slang and no caricature.
- **Maps vibe-coding requests:** "help me tapao this function", "why the build so jialat one", "faster chiong the deploy", "can or cannot?". It knows what you mean and how to answer.
- **Switches off by itself** as soon as you go back to standard English.

## Repository layout

```
claude-singlish-skill/
├── skills/
│   └── singlish/
│       ├── SKILL.md                 # rules, particles, grammar, top 60 words, coding map, examples
│       └── reference/
│           └── vocabulary.md        # full vocabulary: 212 entries with origin and example
├── README.md
├── CONTRIBUTING.md
├── LICENSE
└── .gitignore
```

`SKILL.md` stays focused. Claude reads `reference/vocabulary.md` only when it meets an unfamiliar word (Claude Code's progressive-disclosure layout for skills).

## Install

Skills live in a folder named after the skill, containing a `SKILL.md`.

**For all your projects (personal skill):**

```bash
git clone https://github.com/<owner>/claude-singlish-skill.git /tmp/claude-singlish-skill \
  && mkdir -p ~/.claude/skills \
  && cp -R /tmp/claude-singlish-skill/skills/singlish ~/.claude/skills/singlish
```

**For one project (shared with your team through the repo):**

```bash
git clone https://github.com/<owner>/claude-singlish-skill.git /tmp/claude-singlish-skill \
  && mkdir -p .claude/skills \
  && cp -R /tmp/claude-singlish-skill/skills/singlish .claude/skills/singlish
```

Replace `<owner>` with the GitHub account that hosts this repo. You should end up with `~/.claude/skills/singlish/SKILL.md` (or `.claude/skills/singlish/SKILL.md`) plus the `reference/` folder. Restart Claude Code, or start a new session, so it picks up the skill.

**Check it works:** in Claude Code, type something like *"eh can help me check why this test fail or not?"*. Claude should answer in light Singlish. Type in formal English and it answers in formal English.

## Usage examples

| You type | Claude does |
|---|---|
| "Can check the logs for me? Thanks ah." | Level 1: "Can. The error is from the auth middleware: the token expired." |
| "This one can or cannot? Use SQLite for prod." | A straight answer first ("Cannot lah, for prod better Postgres..."), then the reasons. |
| "Help me tapao this function" | Asks whether you mean extract to a module or just tidy up, then does it. |
| "Why the build so jialat one?" | Reads the log, names the cause, proposes the fix. |
| "Faster chiong the deploy" | Runs the pre-deploy checks anyway and flags any prod risk in plain English. |
| "Gostan, gostan!" | Reverts the last change and confirms which commit it went back to. |
| "ok shiok, commit it lah" | Commits with a standard-English message: `fix(profile): add dependency array to prevent render loop`. |
| "Please write a formal incident summary." | Switches to standard English. |

## Intensity levels

| Level | You sound like | Claude sounds like |
|---|---|---|
| **1. Light / professional** | "Can check the logs for me? Thanks ah." | Standard English with one "can" or particle. |
| **2. Casual** | "Eh this build fail again leh, why like that?" | Short sentences, one or two particles, a few common words. |
| **3. Full kopitiam** | "Walao eh, whole morning debug still cannot, I damn blur already sia." | Warm and expressive, up to three particles, and the technical content still crystal clear. |

Claude never goes more than one level above you; if unsure, it goes one level below. Strong exclamations such as *walao* appear only after you've used them.

## Ground rules the skill enforces

1. Deliverables (code, comments, commits, docs, PRs) stay in standard English unless you explicitly ask for Singlish there.
2. Accuracy beats flavour: commands, paths, numbers and warnings are exact.
3. No vulgar slang or slurs, even if you use them.
4. No caricature, no mock accents, no name-calling.
5. It follows your lead, on and off.
6. Destructive actions get a plain, unmistakable warning.

## Contributing

Spotted a missing word, a wrong meaning or a better example? PRs are welcome. Add a row to [`skills/singlish/reference/vocabulary.md`](skills/singlish/reference/vocabulary.md) with **meaning, origin and an example**, and give a source in the PR description. See [`CONTRIBUTING.md`](CONTRIBUTING.md). Vulgar terms and slurs aren't accepted as usable entries.

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

## License

Released under the MIT License; see [`LICENSE`](LICENSE). © 2026 Pingo Creative Technology.

---

*This skill changes Claude's conversational voice only. It doesn't change what Claude is allowed to do. Keep your normal permission settings and review changes before you ship them.*
