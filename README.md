# Humanizer (Türkçe destekli)

[![GitHub stars](https://img.shields.io/github/stars/onur-ardal/humanizer?style=flat)](https://github.com/onur-ardal/humanizer/stargazers) [![Upstream](https://img.shields.io/badge/upstream-blader%2Fhumanizer-blue)](https://github.com/blader/humanizer)

Yapay zekâya yazdırdığın metni, söylediğini değiştirmeden bir insan yazmış gibi okunur hâle getiren agent skill'i. Bu repo [blader/humanizer](https://github.com/blader/humanizer)'ın Türkçe destekli bir fork'udur: İngilizce kalıpların hepsi olduğu gibi duruyor, üstüne Türkçe metin için ayrı bir kural katmanı ekledik.

Türkçe yapay zekâ metni iki şeyle ele verir kendini. Birincisi her dilde görülen alışkanlıklar: "sadece X değil, aynı zamanda Y", tek satırlık dramatik kapanışlar, üçlemeler, uzun tireler. İkincisi Türkçeye özgü izler: art arda -mektedir, her paragrafı "Bu bağlamda" diye açmak, "güçlü bir ekibe sahibiz" gibi İngilizceden taşınmış yapılar, "dağıtım (deployment)" gibi zorla çevrilmiş teknik terimler. Skill metin Türkçeyse [`references/turkce.md`](references/turkce.md) dosyasını da okuyup ikisini birlikte uygular.

**Önce:**
> Günümüzde yapay zekânın hızla gelişmesiyle birlikte, yazılım geliştirme süreçleri köklü bir dönüşüm geçirmektedir. Bu bağlamda, ekibimiz sadece kod yazmakla kalmayıp, aynı zamanda müşterilerimize uçtan uca değer katan çözümler sunmaktadır. Kapsamlı deneyimimiz, dinamik yapımız ve yenilikçi yaklaşımımız ile sektörde fark yaratıyoruz. Peki bunun sırrı ne? Tek kelimeyle: tutku. 🚀

**Sonra:**
> Yapay zekâ yazılım geliştirmeyi değiştiriyor. Ekibimiz deneyimli ve müşterilerimiz için projeleri uçtan uca üstleniyor.

Humanizer insan okur için düzenler. Yapay zekâ dedektörlerini atlatmak hedefi değildir.

## Kurulum

Claude.ai ve Claude Desktop: repoyu ZIP olarak indir (**Code → Download ZIP**) ve Ayarlar'dan skill olarak yükle.

Claude Code:

```text
/plugin marketplace add onur-ardal/humanizer
/plugin install humanizer@humanizer
```

Diğer agent'lar (Codex, Cursor, Gemini CLI vb.):

```bash
npx skills add onur-ardal/humanizer --global --agent '*'
```

## Kullanım

```
/humanizer

[metni buraya yapıştır]
```

Ya da düz Türkçe iste: "Bu metin yapay zekâ gibi durmasın: [metin]". Kendi sesine uysun istersen önce kendi yazdığın 2-3 paragrafı örnek olarak ver.

## Türkçeye özgü kalıplar

26 İngilizce kalıbın Türkçe karşılıkları `references/turkce.md` içinde. Bunlara ek olarak:

| # | Kalıp | Önce | Sonra |
|---|-------|------|-------|
| T1 | -mektedir zinciri, yapanı belli olmayan cümle | "güncellemeler gerçekleştirilmiştir. İyileştirmeler sağlanmıştır." | "Sistemi güncelledik ve iyileştirdik." |
| T2 | Her paragrafın başında bağlaç | "Bu bağlamda… Öte yandan… Sonuç olarak…" | Bağlacı sil, ilişkiyi cümle kursun |
| T3 | Boş genel giriş ve kapanış | "Günümüzde teknolojinin hızla gelişmesiyle…" | İlk gerçek iddiayla başla |
| T4 | Çeviri kokan yapı | "güçlü bir ekibe sahibiz", "günün sonunda", "Bizim ekibimiz" | "ekibimiz güçlü", "eninde sonunda", "Ekibimiz" |
| T5 | Uzun ortaç zinciri, hep sonda biten cümle | "…karşılaştıkları sorunların çözülmesine yönelik geliştirilen yöntem" | İki cümleye böl; yerinde devrik cümle |
| T6 | İngilizce noktalama ve yazım | "A, B, ve C", "3.5", "50%", "API'a" | "A, B ve C", "3,5", "%50", "API'ye" |
| T7 | Zorla çevrilmiş teknik terim, parantez içi İngilizce | "dağıtım (deployment) işlem hattı (pipeline)" | "deployment pipeline'ı" |
| T8 | Hitap tutarsızlığı | "yapmalısınız… bak", "Değerli okuyucular" | Tek hitap |
| T9 | Sosyal medya kancaları | "Büyük bir gururla duyurmak isterim ki 🚀", "🧵 Bir thread 👇" | Asıl iddiayla başla |
| T10 | Yüklemsiz isim öbeği cümlesi | "Kurumsal standartlara uygun, korunaklı bir altyapı." | "Altyapı kurumsal standartlara uygun." |

## Upstream ile senkron

İngilizce çekirdek (`SKILL.md`) bilerek blader'ın sürümüne yakın tutuluyor; Türkçe kurallar ayrı dosyada. blader yeni sürüm çıkardığında:

```bash
git remote add upstream https://github.com/blader/humanizer.git
git fetch upstream && git merge upstream/main
```

Çakışma genelde yalnızca README ve SKILL.md'deki birkaç satırlık Türkçe kancada çıkar.

---

# Humanizer (English, upstream documentation)

Humanizer makes AI-written text sound like a person wrote it, without changing what it says. It is built on Wikipedia's [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), the guide Wikipedia editors use to catch AI-generated text, and it works in Claude Code, Codex, and any other agent that supports skills.

**Before:**
> I'm thrilled to announce that shared drafts are finally here! 🚀 For months, our own team was drowning in files named final_v7.docx — and we knew there had to be a better way. Now two people can edit the same doc at once, with every change appearing live for both of them. It's not just a feature; it's a whole new way to collaborate. Comments stay anchored to the exact sentence they reference, even as the text around them evolves. And the best part? It's available today on every plan, completely free. Let that sink in.

**After:**
> Shared drafts are out today. For months our own team passed around files named final_v7.docx, so we built a way for two people to edit the same doc at once, with each person's changes showing up live for the other. Comments stay pinned to the sentence they're about, even when the text around them changes. It's free on every plan.

In a blind test, judges preferred Humanizer's rewrite over the original AI text 16 times out of 16 ([#229](https://github.com/blader/humanizer/issues/229)).

Humanizer edits for human readers. Getting past AI detectors is not a goal, and detectors still flag most of its output.

## The five strongest tells

These are the most common signs of AI writing, and Humanizer rewrites any of them on sight:

1. **Not X but Y:** "It's not just a feature, it's a shift."
2. **One-line closers:** "Let that sink in."
3. **Sayings that sound deep:** "At its core, what really matters is..."
4. **A staged run-up:** "Here's the thing." "Honestly?"
5. **Arguing with no one:** "I'm not saying X, but..."

Humanizer checks for [26 patterns](#the-26-patterns) in all.

## Installation

Once installed, the skill answers to `/humanizer`.

### Claude Code

```text
/plugin marketplace add onur-ardal/humanizer
/plugin install humanizer@humanizer
```

The plugin answers to `/humanizer:humanizer`. It needs Claude Code 2.1.142 or newer; on older versions, use `npx skills add onur-ardal/humanizer --global --agent claude-code`.

### Codex

```bash
npx skills add onur-ardal/humanizer --global --agent codex
```

### Claude.ai and Claude Desktop

Download this repository as a ZIP (**Code → Download ZIP**) and upload it as a skill in Settings.

### Other agents

```bash
npx skills add onur-ardal/humanizer --global --agent '*'
```

This installs Humanizer for every agent the Skills CLI supports, including Gemini CLI, GitHub Copilot, and Windsurf. Leave off `--global` in any command above to install it only in the current project. For an agent the Skills CLI does not know, copy `SKILL.md` into its skill folder.

## Usage

Call the skill directly:

```
/humanizer

[paste your text here]
```

Or ask in plain language:

```
Please humanize this text: [your text]
```

To rewrite a file, give Humanizer its path:

```
Humanize the prose in docs/launch-post.md
```

### Match your voice

If you want the rewrite to sound more like you, include a sample:

```
/humanizer

Here's a sample of my writing for voice matching:
[paste 2-3 paragraphs of your own writing]

Now humanize this text:
[paste AI text to humanize]
```

Humanizer follows the sample's rhythm, word choice, punctuation, and deliberate quirks, including dashes if you use them.

## How it works

A language model writes whatever is most likely to come next, so by default it makes the choice that fits the widest range of readers and subjects. A person chooses for one reader and one subject. Every tell Humanizer looks for is a form of that default choice: a sentence that signals importance instead of adding a fact, rhythm or formatting applied by rule, an ordinary fact dressed as a pivotal one, text left over from the chat, or a reply that re-explains what the reader already knows.

> "LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."
> Wikipedia, ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)

Humanizer marks every tell it finds, strongest first. It drafts a rewrite without treating the original structure as fixed, checks the draft against the patterns and the original claims, and then writes the final version. It does not make things up. A name, number, date, quote, citation, or other factual detail must come from the source or the writer, and if a sentence needs a detail that is missing, Humanizer asks instead of inventing one.

When you paste text, Humanizer shows its work: the first rewrite, a short critique of anything that still sounds artificial, and the final version. Point it at a file and it changes only the prose, leaving code, data, frontmatter, and link targets alone. Personal writing keeps the writer's opinions and quirks. Technical and reference prose stays neutral and plain.

## The 26 patterns

The patterns are numbered by strength and frequency. The first five justify an edit on a single sighting. Patterns marked *weak alone* count only when several tells share a passage, because a careful writer may use any one of them on purpose.

### A. Staging instead of stating

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 1 | **Not X but Y** | "It's not just X, it's Y", "This doesn't mean X. It means Y." | State the point directly |
| 2 | **One-line closers and dramatic fragments** | "That is the real win." after every section; "This shows the importance of..." after an example; "No prior. No nostalgia." | Cut the closer that repeats or explains the example; merge fragments into a specific claim |
| 3 | **Sayings that sound deep** | "At its core, what matters is...", "Symmetry is the language of trust" | Replace the saying with the specific claim |
| 4 | **Staged run-up before the point** | "Let's dive in", "Honestly? It depends..." | Remove the run-up and state the point |
| 5 | **Arguing with no one** | "This isn't mainly about...", "A tempting approach would be..." | Remove the unraised objection or fake option; keep any real claim |

### B. Rhythm by rule

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 6 | **Forced triads** | "innovation, inspiration, and insights"; three examples plus a lesson | Use the number of items the meaning needs |
| 7 | **Repeated sentence openings** | "She noted... She noted... She filed..." | Merge the sentences or change the subject |
| 8 | **Dashes as the universal connector** (*weak alone*) | "institutions—not the people—yet this continues—" | Use periods, commas, colons, or parentheses; match a sample that uses dashes |
| 9 | **Stacked qualifiers** (*weak alone*) | "could potentially possibly be argued" | Keep only qualifiers the source supports |
| 10 | **Hyphenated pairs everywhere** (*weak alone*) | "the report is high-quality" | Keep the hyphen before the noun or where the dictionary has one |
| 11 | **Passive voice and missing subjects** (*weak alone*) | "No configuration file needed" | Name the actor when that helps |

### C. Inflation and borrowed authority

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 12 | **Overused AI words** | "delve... testament... landscape... showcasing" | Use plain words |
| 13 | **Inflated significance** | "marking a pivotal moment", "Despite challenges... continues to thrive", "The future looks bright" | Keep the fact and drop the significance; end on the last concrete fact |
| 14 | **Vague connection or association** | "associated with the leadership of", "in connection with" | State the relationship the source gives |
| 15 | **Shallow -ing riders** | "symbolizing... reflecting... showcasing..." | Keep only what the source supports |
| 16 | **Sales language** | "nestled within the breathtaking region" | State what the thing is |
| 17 | **Borrowed authority** | "Experts believe...", "cited in NYT, BBC, FT, and The Hindu" | Name a real source and what it said, or remove the claim or list |
| 18 | **Avoiding is, are, and has** | "serves as... features... boasts" | "is... has" |

### D. Formatting by rule

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 19 | **Bold as decoration** | "**OKRs**, **KPIs**"; "**Performance:** Performance improved" | Remove the bold; turn a labeled list into prose |
| 20 | **Decorative headings** | "Strategic Negotiations And Partnerships", "🚀 Launch Phase:", "The decision, on one screen" | Sentence case; remove emojis and arrows; name what the section holds |
| 21 | **Curly quotation marks** (*weak alone*) | `said “the project”` | `said "the project"` |

### E. Leftovers from the chat and the draft

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 22 | **Chatbot residue** | "Great question! ... I hope this helps!" | Remove the wrapper and keep the content |
| 23 | **Knowledge-limit disclaimers and guesses** | "While details are limited in available sources, it appears..." | State what the source shows, or remove the sentence |
| 24 | **A heading repeated in the first sentence** | "## Performance" + "Speed matters." | Let the heading do the work |
| 25 | **Writing about the document instead of its subject** | "This function was added to replace...", "compiled from...", "The table below compares..." | Describe the subject; state a convention only when the reader cannot see it |

### F. Writing for the wrong reader

| # | Pattern | Before | After |
|---|---------|--------|-------|
| 26 | **Re-explaining what the reader knows** | A reply that walks the diagnosis and proves the plan works before the decision | Lead with the decision; leave the diagnosis and the proof for the ticket that follows |

## Full example

**Before (AI-sounding):**
> I recently spent five unforgettable days in Lisbon last October, and let me tell you — this city completely stole my heart. From the moment I checked into my charming hotel perched high in the historic Alfama district, I knew I was somewhere truly special.
>
> Yes, the famous hills are challenging — with countless stairs between my hotel and everything else, my legs certainly felt it! — but every climb rewards you with breathtaking, panoramic views that make it all worthwhile.
>
> No trip would be complete without riding the iconic Tram 28, a roughly forty-minute journey shared with plenty of fellow travelers eager to capture the magic. And the food? Simply divine. While the pastéis de nata at Pastéis de Belém are a beloved national treasure, my absolute favorite came from a hidden gem in Graça, still warm from the oven.
>
> But what truly makes Lisbon special isn't just the sights — it's the feeling. Wander just a block or two above the main squares and you'll discover a quieter, more authentic side of the city, inviting you to slow down and savor every moment.
>
> Of course, the must-see São Jorge Castle offers stunning views over the rooftops below. The queues can be long, but the experience is absolutely worth it for any history buff or curious traveler.
>
> Would I go back? Absolutely — next time in spring, and with better shoes! Lisbon isn't just a place to visit; it's a place to fall in love with, again and again. ✨

**After:**
> I spent five days in Lisbon last October. My hotel was up in Alfama, with a lot of stairs between it and everything else, and my legs felt every one of them. The views from the top were worth the climb.
>
> Everyone tells you to ride Tram 28, so I did. The trip took about forty minutes, and most of the car was other tourists taking pictures out the windows. The custard tarts at Pastéis de Belém are the famous ones, but my favorite came from a place in Graça, still warm from the oven.
>
> The part of Lisbon I liked best starts a block or two above the main squares, where the streets go quiet and nobody is in a hurry. São Jorge Castle has good views over the rooftops and a long queue to get them.
>
> I'd go back, in spring next time, and with better shoes.

## Sources

- Turkish additions: [`references/turkce.md`](references/turkce.md).

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) is the source for the pattern list.
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) maintains the page.

## Version history

See [CHANGELOG.md](CHANGELOG.md).

## License

MIT. Original work © 2025 Siqi Chen ([blader/humanizer](https://github.com/blader/humanizer)); Turkish additions © 2026 onur-ardal.

If Humanizer helps you, a star helps other people find it.
