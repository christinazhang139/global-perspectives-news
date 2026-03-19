---
name: global-perspectives-news
description: Generate a personalized global news briefing by asking about your interests, then searching the web and delivering a structured, readable digest. Use this to stay informed on topics that matter to you without manual searching.
type: interactive
---

## Purpose

Generate a personalized news briefing tailored to your interests. You tell Claude what topics you care about and how you want the output—Claude searches the web and delivers a clean, structured digest of the most relevant stories from the past 24-48 hours.

This is not a generic news feed. It's a focused intelligence briefing built around your specific needs—whether that's AI research, cloud-native engineering, startup funding, geopolitics, or anything else.

**Requires:** Tavily MCP (for live web search). If Tavily is not connected, Claude will note it and offer to proceed with its training knowledge as a fallback.

---

## Key Concepts

### The Briefing Model
A good daily briefing has three properties:
1. **Signal over noise** — only stories with real substance, not clickbait or rehashes
2. **Scannable structure** — grouped by topic, with one-sentence summaries and source links
3. **Configurable depth** — headlines only, or with context and implications

### Story Quality Criteria
Stories included must meet at least two of:
- Published or updated in the last 48 hours
- From a recognized publication or primary source
- Contains new information (not just opinion or recap)
- Directly relevant to the stated topic

### Anti-Patterns (What This Is NOT)
- **Not a search engine:** This synthesizes results, not just dumps links
- **Not a RSS reader:** Each run is a fresh search, not a subscription feed
- **Not political commentary:** Summarizes facts, does not editorialize

---

## Application

### Global Navigation Rules

- **"back" / "上一步" / "返回"** — go back to the previous step
- **"restart" / "重新开始"** — go back to Step 1, clear all selections
- **"skip" / "跳过"** — skip current step, use default value
- **"done" / "算了"** — exit the skill immediately

---

### Step 0: Check for Saved Preferences

Before asking anything, check if a preferences file exists at `~/.claude/global-perspectives-news-prefs.json`.

**If the file exists**, greet using the saved `language` field:

> *[Use saved language: "Chinese" → Chinese only; "English" → English only; "Bilingual" → both]*
>
> 上次你看了 [topics]，今天还想看这些吗？ *(if Chinese or Bilingual)*
> Last time you followed: [topics]. Want the same today? *(if English or Bilingual)*
>
> 1. **Yes, go** — search now
> 2. **Yes, but add/change something**
> 3. **No, start fresh**

If user selects 1 → skip Steps 1-4, go to Step 5.
If user selects 3 → delete prefs file, go to Step 1.

**If no file exists**, go directly to Step 1.

---

### Step 1: Ask About Interests

> "Welcome! What would you like to read about today?
>
> **Just tell me what you're interested in** — any topic works.
>
> Or pick from the list:
> 1. Technology & AI
> 2. Finance & Economy
> 3. Geopolitics & World Affairs
> 4. Science & Research
> 5. Career & Workplace
> 6. Business & Strategy
> 7. Environment & Climate
> 8. Sports
> 9. Entertainment & Media
> 10. Health & Lifestyle
> 11. Law, Crime & Justice
> 12. Travel & Places
> 13. Culture & Society
> 14. Just surprise me
> 15. Top 10 by location — tell me a country or city"

**CRITICAL — mandatory steps by mode:**

| Mode | Step 2 (sources) | Step 3 (subtopics) | Step 4 (language + depth) |
|------|-------------------|--------------------|---------------------------|
| Specific topics (1-13) | ✅ Required | ✅ Required | ✅ Required |
| Just surprise me (14) | ✅ Required | ⛔ Skip | ✅ Required |
| Top 10 by Location (15) | ⛔ Skip | ⛔ Skip | ✅ Required |

---

### Step 2: Ask About Media Source Countries

> "Which countries' media would you like to draw from?
>
> **Official Media:**
> 1. United States — CNN, NYT, WSJ, The Atlantic
> 2. United Kingdom — BBC, The Guardian, Financial Times
> 3. Europe — Der Spiegel (Germany), Le Monde (France), Kyiv Independent (Ukraine)
> 4. Russia — RT, TASS, Kommersant (English editions)
> 5. China — SCMP, Caixin, Xinhua, Global Times (English editions)
> 6. Middle East — Al Jazeera, Arab News, Jerusalem Post, Haaretz
> 7. Japan — Nikkei Asia, Japan Times
> 8. Singapore / Asia Pacific — Straits Times, CNA
> 9. India — The Hindu, Times of India, Economic Times, NDTV
> 10. Latin America — El País América, Folha de S.Paulo, Infobae
> 11. Africa — AllAfrica, Daily Maverick, The East African, Premium Times
> 12. Canada — Globe and Mail, CBC News, Toronto Star, Maclean's
> 13. Australia & New Zealand — ABC News Australia, Sydney Morning Herald, RNZ
> 14. South Korea — Korea Herald, Chosun Ilbo (English), Hankyoreh
> 15. Turkey — TRT World, Hurriyet Daily News, Daily Sabah
> 16. Southeast Asia — Rappler (PH), Bangkok Post, Jakarta Post, CNA
>
> **Social Media:**
> 17. Weibo — Chinese public sentiment via trending topics (热搜榜)
> 18. Xiaohongshu / RedNote — Chinese lifestyle, consumer trends, Gen Z culture
> 19. TikTok / 抖音 — global and Chinese viral content, youth trends
> 20. Instagram — visual culture, lifestyle, brand sentiment
> 21. Telegram — war zones, political movements, opposition channels
> 22. LinkedIn — professional sentiment, industry trends, executive commentary
> 23. Twitter / X — global real-time public reaction, trending hashtags
> 24. Reddit — English-language community discussion and analysis
>
> **No filter:**
> 25. Global / No preference — let the best sources win"

---

### Step 3: Narrow Down to Subtopics

Present subtopic menus only for selected categories.

**Technology & AI:** LLMs & AI research / AI products / Cloud native & K8s / Cybersecurity / Consumer tech / All

**Finance & Economy:** Global markets / Startups & VC / Crypto & Web3 / Fintech / Real estate / Commodities & energy / Central banks & monetary policy / Personal finance / All

**Geopolitics & World Affairs:** US politics / China & Asia Pacific / Europe / Middle East / Global trade & sanctions / Latin America / Africa / South Asia / All

**Science & Research:** AI & ML papers / Space & astronomy / Climate & environment / Health & medicine / Biology & life sciences / Physics & quantum / Robotics & engineering / Psychology & behavior / Archaeology & history / All

**Career & Workplace:** Remote work & hiring / Tech layoffs / Salary & compensation / Future of work & AI impact / Gig economy / Entrepreneurship / Workplace culture & DEI / All

**Business & Strategy:** M&A / IPOs & public markets / Corporate strategy & leadership / Regulatory & antitrust / Supply chain & logistics / All

**Environment & Climate:** Climate change / Green energy / Environmental policy / Natural disasters / Conservation / Corporate sustainability & ESG / All

**Sports:** Football/Soccer / Basketball / Formula 1 / Tennis / Olympics / Esports / Other sports / All

**Entertainment & Media:** Movies & film / Music / Gaming / Celebrities & pop culture / Streaming platforms / Awards & events / All

**Health & Lifestyle:** Fitness / Nutrition / Mental health / Medical breakthroughs / Public health / Wellness & longevity / All

**Law, Crime & Justice:** Major criminal cases / Court rulings / Regulatory enforcement / White-collar crime / Human rights / International law / All

**Travel & Places:** Travel destinations & tips / Aviation & airlines / Tourism trends / City & urban development / Immigration & visa / Outdoor & adventure / Luxury travel / Budget travel / All

**Culture & Society:** Social movements / Education / Demographics / Religion & traditions / Internet culture & viral trends / Language, arts & literature / Food culture / Fashion / Youth culture & Gen Z / Gender, identity & diversity / Urban life / All

**Shortcut:** "all" / "全部" / "everything" = select all subtopics for that category.

After collecting subtopics:
> "Got it. I'll cover: [list]. One more step — language and depth."

---

### Step 4: Ask About Reading Language and Depth

> "Two quick settings before I search:
>
> 1. **Reading language:**
>    - A. English
>    - B. Chinese 中文
>    - C. Spanish Español
>    - D. French Français
>    - E. Japanese 日本語
>    - F. German Deutsch
>    - G. Bilingual — pick any two (e.g., "G, English + Chinese")
>
> 2. **Depth:**
>    - A. Headlines only (title + one line)
>    - B. Standard (title + 2-sentence summary)
>    - C. Deep (title + summary + why it matters)"

Default if skipped: English, Standard.

---

### Step 5: Search for News

- Query: `[specific subtopic] [current year] [intent keyword]`
- Time range: last 48-72 hours
- Target: 3-5 high-quality results per topic

**Topic-specific query strategy:**

| Topic | Avoid | Use instead |
|-------|-------|-------------|
| Sports (specific league) | `football news latest` | `Champions League results March [year]` |
| AI research | `AI news latest` | `arxiv LLM [year] latest`, `machine learning breakthrough [year]` |
| Geopolitics (conflict) | `Iran Israel news` | `Iran Israel war update [date]` |
| Finance (crypto) | `crypto news latest` | `Bitcoin Ethereum price [year]` |
| Finance (markets) | `stock market news` | `S&P 500 today [date]`, `Fed rate decision [year]` |
| Business (M&A) | `company acquisition news` | `merger acquisition deal [industry] [year]` |
| Career (layoffs) | `tech layoffs` | `[company] layoffs [month] [year]` |
| Culture (food) | `food news latest` | `food trend [year]`, `viral food [platform] [year]` |
| Environment (policy) | `climate news` | `COP climate agreement [year]` |

---

### Step 6: Generate the Briefing

```
# Daily News Briefing -- [Date]

## [Topic Name]

- **[Story Title]**
  [Summary based on chosen depth.]
  Source: [Publication Name] -- [Full URL]

---
*Briefing generated on [date]. Sources: [countries selected]. Language: [language]. Depth: [depth].*
```

After all topics, add:

```
## Today's Takeaway · 今日总结
[1-2 sentences capturing the single most important theme across all stories.]
```

If social media sources selected, add:

```
## Social Pulse · 社交舆论
[Trending topics, sentiment signals — labeled as sentiment, not verified facts.]
⚠️ Social media content reflects public sentiment, not verified facts.
```

**Topic emoji guide:**
🤖 AI/LLMs · ☁️ Cloud/DevOps · 💰 Finance · 🌍 Geopolitics · 🔬 Science · 💼 Careers · 🔐 Security · 📱 Consumer Tech · 📊 Business · 🌿 Environment · ⚽ Sports · 🎬 Entertainment · ❤️ Health · ⚖️ Law · ✈️ Travel · 🌐 Culture

---

### Step 7: Offer Next Steps

**Part A — Save preferences:**

> "Want to save these as your daily default?
> 1. Yes, save — [topics] · [countries] · [language] · [depth]
> 2. No, ask me every time"

If yes, save to `~/.claude/global-perspectives-news-prefs.json`.

**Part B — Actions:**

> "What next?
> 1. Dive deeper on a specific story
> 2. Save this briefing to a markdown file
> 3. Change topics (keeps language & depth)
> 4. Change everything
> 5. Done"

---

## Common Pitfalls

### Pitfall 1: Too Many Topics
After Step 3, count total subtopics across all categories. If > 10:
> "You've selected [N] subtopics. Want me to:
> 1. Prioritize — I'll pick the 8 most important ones
> 2. Keep all, go shallow — Headlines-only depth
> 3. Keep all, full depth (may take longer)"

### Pitfall 2: Stale Results
Always include `latest` in queries. Flag stories older than 72 hours.

### Pitfall 3: Duplicate Stories
Cross-check before output. File each story under the most relevant topic only.

### Pitfall 4: Opinion Pieces
Prioritize primary sources. Label opinion pieces explicitly if included.

### Pitfall 5: Skipping Language/Depth
Step 4 is MANDATORY for every run. Never skip.

### Pitfall 6: Tavily Not Connected
Inform user and offer to proceed with training knowledge as fallback.

---

## References

- **Tavily MCP** — Required for live news retrieval
- `company-research` — For deeper dives into specific companies
- `pestel-analysis` — To contextualize macro news into strategic implications

---

**Skill type:** Interactive
**Suggested filename:** `global-perspectives-news`
**License:** CC BY-SA 4.0
