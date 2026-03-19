# 🌍 Global Perspectives News — See the Elephant Whole

> *Six blind men each touched a different part of an elephant and came away with six completely different truths. None of them were wrong. None of them were complete.*
>
> *This skill is built on that idea.*

---

## What This Is

**Global Perspectives News** is a Claude Code skill that generates personalized news digests — not from a single source, but from media across multiple countries, in the language of your choice.

The same story looks radically different depending on where you read it. A geopolitical conflict covered by US, Russian, Chinese, and Middle Eastern outlets will produce four entirely different narratives — each accurate within its own frame, each missing the others'.

Most people only access news in one or two languages, from one cultural context. That's not a failure of curiosity — it's just the reality of language barriers and information overload. This skill removes those barriers.

---

## The Idea Behind It

The inspiration is the ancient parable of the **blind men and the elephant** (盲人摸象).

Each person who touches the elephant believes they understand it. The man who touches the trunk thinks it's a rope. The man who touches the leg thinks it's a tree. They're all right. They're all wrong.

Global news works the same way. Take any major event:

| Outlet | What they call it |
|--------|-------------------|
| CNN (US) | "a humanitarian crisis" |
| TASS (Russia) | "NATO aggression" |
| Al Jazeera (Middle East) | "a failure of Western foreign policy" |
| Caixin (China) | "market and supply chain disruption" |
| Daily Maverick (Africa) | "another conflict the Global South will pay for" |
| Folha de S.Paulo (Brazil) | "a distant war with direct consequences for our food prices" |

All from the same event. All true in their own way. None of them complete.

**This skill gives you the whole elephant.**

It's designed for:
- People who want to understand the world, not just their corner of it
- Non-native speakers who can only comfortably read in one or two languages
- Anyone tired of algorithmic bubbles that only serve what you already believe
- Researchers, writers, analysts, and curious minds who want primary perspectives, not filtered summaries

You don't need to speak 10 languages. You just need to ask.

---

## What It Does

- **Asks what you care about** — from AI research to Champions League to local city news
- **Lets you choose media sources by country** — US, UK, China, Russia, Middle East, India, Africa, Latin America, and more
- **Delivers in your language** — English, Chinese, Spanish, French, Japanese, German, or bilingual
- **Structures depth by your preference** — headlines only, standard summaries, or deep analysis with "why it matters"
- **Flags when perspectives diverge** — e.g., *"US and Chinese sources frame this story very differently — see both angles below"*
- **Remembers your preferences** — save your settings so next time you just run `/global-perspectives-news` and it goes straight to searching

---

## How to Use

This is a [Claude Code](https://claude.ai/claude-code) skill. To run it:

```bash
# In Claude Code, type:
/global-perspectives-news
```

**Requirements:**
- [Claude Code](https://claude.ai/claude-code) installed
- [Tavily MCP](https://tavily.com) connected (for live web search)

**Installation:**
```bash
# Copy the skill to your Claude skills directory
cp -r global-perspectives-news ~/.claude/skills/
```

---

## What It Looks Like

### Snippet 1 — Choose Your Lens

The first thing you pick is *whose eyes you want to see through*. Not a topic filter — a perspective filter.

```
Different countries cover the same story from very different angles.
Which countries' media would you like to draw from?

Official Media:
 1. United States      — CNN, NYT, WSJ, The Atlantic
 2. United Kingdom     — BBC, The Guardian, Financial Times
 3. Europe             — Der Spiegel (DE), Le Monde (FR), Kyiv Independent (UA)
 4. Russia             — RT, TASS, Kommersant (English editions)
 5. China              — SCMP, Caixin, Xinhua, Global Times (English editions)
 6. Middle East        — Al Jazeera, Arab News, Jerusalem Post, Haaretz
 7. Japan              — Nikkei Asia, Japan Times
 8. Singapore/APAC     — Straits Times, CNA
 9. India              — The Hindu, Times of India, Economic Times
10. Latin America      — El País América, Folha de S.Paulo, Infobae
11. Africa             — AllAfrica, Daily Maverick, The East African
12. Canada             — Globe and Mail, CBC News, Toronto Star, Maclean's
13. Australia & NZ     — ABC News Australia, Sydney Morning Herald, RNZ
14. South Korea        — Korea Herald, Chosun Ilbo (English), Hankyoreh
15. Turkey             — TRT World, Hurriyet Daily News, Daily Sabah
16. Southeast Asia     — Rappler (PH), Bangkok Post, Jakarta Post, CNA

Social Media (public sentiment):
17. Weibo              — Chinese public sentiment & trending topics (热搜榜)
18. Xiaohongshu        — Chinese lifestyle, consumer trends, Gen Z culture
19. TikTok / 抖音      — global and Chinese viral content, youth trends
20. Instagram          — visual culture, lifestyle, brand sentiment
21. Telegram           — war zones, political movements, opposition channels
22. LinkedIn           — professional sentiment, industry trends
23. Twitter/X          — global real-time reaction and trending hashtags
24. Reddit             — English-language community discussion and analysis

No filter:
25. Global / No preference — let the best sources win
```

---

### Snippet 2 — When Narratives Collide

When you select sources from opposing geopolitical camps, the briefing flags where they diverge — explicitly, without editorializing.

```
## 🌍 Iran-Israel Conflict — March 2026

- Iran launches "True Promise 4" — Wave 61 of missile strikes
  Source: Al Jazeera

- Israel intercepts Iranian barrage; IDF reports minimal damage
  Source: Jerusalem Post

- Pentagon: Iran's attack "reckless and destabilizing"
  Source: NYT

⚠️ Note: US/Israeli outlets emphasize aggression and military failure.
   Iranian/Russian outlets frame strikes as legitimate retaliation.
   Al Jazeera focuses on civilian impact and humanitarian cost.
   Daily Maverick (Africa): the Global South bears the oil disruption cost first.
   Folha de S.Paulo (Brazil): fuel costs hit Latin American consumers
   before any ceasefire is even discussed.
```

---

### Snippet 3 — The Same World, Your Language

A story from Caixin can arrive in Spanish. A story from Le Monde can arrive in Japanese.

```
Reading language:
  A. English
  B. Chinese 中文
  C. Spanish  Español
  D. French   Français
  E. Japanese 日本語
  F. German   Deutsch
  G. Bilingual — pick any two (e.g. "G, English + Chinese")

Depth:
  A. Headlines only  (title + one line)
  B. Standard        (title + 2-sentence summary)
  C. Deep            (title + summary + why it matters)
```

*Language stops being a wall.*

---

### Snippet 4 — Top 10 Local News, Anywhere

Ask for any city or country and get a ranked digest of what's actually happening there.

```
# 🏙️ Shanghai Today — March 19, 2026

1. F1 Chinese Grand Prix wraps up: 230,000+ attended over 3 days
   Source: Xinhua

2. Secondary housing transactions hit 12-month high
   Source: Caixin

3. Shanghai–Ningbo cross-sea rail corridor enters national 15th Five-Year Plan
   Source: Xinhua

## Today's Takeaway
Shanghai is accelerating on two tracks: global visibility and domestic market recovery.
```

---

## Supported Languages (Output)

| Language | Code |
|----------|------|
| English | A |
| Chinese 中文 | B |
| Spanish Español | C |
| French Français | D |
| Japanese 日本語 | E |
| German Deutsch | F |
| Bilingual (any two) | G |

---

## Supported Media Sources

**Official Media:** United States · United Kingdom · Canada · Australia & NZ · Europe · Russia · Turkey · China · Japan · South Korea · Southeast Asia · Singapore/APAC · India · Middle East · Latin America · Africa

**Social Pulse:** Weibo · Xiaohongshu · TikTok/抖音 · Instagram · Telegram · LinkedIn · Twitter/X · Reddit

---

## Philosophy

The goal is not to tell you what to think. It's to show you that multiple truths can coexist — and that understanding the world requires hearing more than one of them.

Language should not be the reason you only see part of the elephant.

---

## License

CC BY-SA 4.0 — Free to use, share, and adapt with attribution.

---

*Built with Claude Code · Powered by Tavily MCP*
