# PROVENANCE — how this rendering came to be

*Uyghur (ئۇيغۇرچە), chair 75. Lit and burned 2026-09-17. Floor 23,213 verses,
305,507 token rows.*

This is the record of how the text in this repository was produced — written
**while it was being produced**, not reconstructed afterwards. A
machine-assisted rendering has no standing unless you can see how it was made
and what went wrong with it, so this file says both.

---

## The approach

Every verse is rendered from the Hebrew of that verse, under a written
discipline: `docs/methodology/translation-discipline/ug.md` in the Selah
repository, which is itself written in Uyghur. Six rules govern it.

1. **The Hebrew token is the unit.** Every change is tied to a Hebrew token;
   word count equals gloss count. A rendering that cannot be laid beside the
   Hebrew token by token is not this kind of rendering.
2. **The Name stays the Name.** God's Name is not translated, it is
   transliterated — **ياھۋەھ**. So are אלהים → **ئېلوھىم**, אדני →
   **ئادوناي**, שדי → **شادداي**. The traditional titles a Uyghur reader
   would expect — **خۇدا · اﷲ · تەڭرى · پەرۋەردىگار** — are *not* used where
   the Name stands. They belong to the witnesses' tradition, not to this text.
3. **Both truths of Deut 6:4** — what is written, and how the Hebrew sounds.
4. **No foreknowledge.** The words of Gen 22:1 do not know Gen 22:13. Each
   verse in its own light; no later book reads back into an earlier one.
5. **Numbers and marks stay put.** Gematria, markers, letter counts — none is
   broken for the sake of a smoother reading.
6. **The translator has no word of his own.** Only the translation.
   Interpretation lives in another layer.

**The ⟨ ⟩ brackets do two different jobs, and the difference matters.**
`⟨את⟩` is the Hebrew direct-object marker, which Uyghur has no word for; it
is left standing so the reader can see it. `⟨word⟩` is a word Hebrew did not
write but Uyghur grammar requires — visibly marked as supplied, so you can
always tell what the Hebrew said from what the grammar needed.

## How it was actually produced

A relay rendered the corpus verse by verse against the discipline doc. It
completed with **51 verses of residue**, all of which turned out to be silent
truncation — raising the token ceiling from 12,000 to 24,000 landed every one.
Twelve verses had arrived with a flow but no token rows, and twenty-six with
a token count that disagreed with the Hebrew; those were re-pressed.

Then five repair passes, each idempotent, each re-runnable, all in
`dev/scripts/`:

| pass | what it did | count |
|---|---|---|
| `surface_restore.py` | restored Hebrew surfaces from the read-only floor | 4,345 |
| `ug_prophet_canon.py` | the prophet ruling below | 646 |
| `marker_normalise.py` | recovered damaged את markers | 637 |
| `ug_hand_pass.py` | Name spelling, and three erasure seats by hand | 264 |
| `flow_parity.py` | carried every token-row marker into the verse line | 2,706 |

## The decisions we had to make

**No later prophets in the Tanakh.** The rendering was using **پەيغەمبەر**
for **נביא**. It is an ordinary Uyghur word for *prophet* — and it is the word
Uyghur uses for Muhammad. Scott's ruling, 2026-09-17: *"we need to be careful
about bringing Muhammed into the Hebrew bible."* So **نەبى**, which is cognate
with נביא through the shared Semitic root נ-ב-א and carries no later figure
into the text. 646 substitutions.

The general rule this settled: **a word a language reserves for a
post-biblical figure does not render a Tanakh common noun, even when it is
that language's ordinary word for the thing.** The usual preference — the
language's own perfect word wins where one exists — does not reach that far.

**The Name is spelled ياھۋەھ.** The corpus carried a minority spelling
يەھۋەھ in 261 places. The discipline doc's own table names ياھۋەھ and the
corpus agreed with it sixty to one, so this was a correction, not a choice.

**Damaged markers are restored to the bare ⟨את⟩, never to an inflected
form.** When a marker had to be reconstructed, it would sometimes have been
possible to reconstruct it as ⟨אתי⟩ or ⟨אתו⟩. We do not: inventing a suffix
the text may not carry is worse than not restoring one. The corpus majority
is bare, 18,988 to 187.

**No repair may add what the floor never held.** Every marker cure is gated
on the Hebrew: a marker is only restored where the verse's own Hebrew carries
an את-family word. Eleven rows were refused on that ground — the text there
simply has no marker, and a repair that can invent one is not a repair.

**Both surfaces get cured, or neither.** Each verse exists twice: as token
rows and as a flowing line. A cure applied to one and not the other leaves
the reader receiving something the corpus does not contain. That failed twice
on an earlier chair before it became a rule.

---

## The record as it was taken

Running ledger, one fresh-300 window per other tick during the burn.
Nothing was repaired at the time of writing — the burn owned the tree. These
are the shapes the seating passes then had to cure, filed at the hour they
were seen.

---

## Corrections — facts this record reported and got wrong

Written after the burn completed and the whole tree could be counted.
Each of these was stated repeatedly during the burn on window evidence.

**1 · "Han 0 · Cyrillic 0 on every window" — wrong, eleven times.**
The full tree holds **Han 5, Cyrillic 4**. A fresh-300 window over 23,213
files is a **1.3% sample**; a five-file defect had almost no chance of
landing in one. Eleven clean windows were not a measurement of zero, they
were eleven draws that missed. *A repeated clean sample is not a clean
corpus, and saying "0 on every window" invited exactly the reading it got.*

**2 · "3,821 corrupt surfaces" — the real figure was 4,345.**
My probe required Hebrew **and** non-Hebrew both present. A **fully**
converted surface has no Hebrew left to trigger the mixture test and walked
straight past. The floor comparison has no such blind spot, which is the
argument for driving cures off the floor rather than off a description of
the damage. Same blind spot hides `⟨ئەت⟩` from the marker probe.

**3 · "the Turkic-sibling bleed" — it is Uyghur's own alphabets.**
`üstige` is ئۈستىگە in **ULY**, Uyghur's Latin script. Not Turkish. And it
is not only Latin: `تويمايдۇ` carries Cyrillic **а й д** — **USY**, Uyghur's
*third* official alphabet. The chair holds Uyghur in three alphabets and
mixes them **inside single words**.

**4 · "marker damage is ten forms" — the gradient does not enumerate.**
Reading seats gave three. The tree gave ten. After the first structural
pass, **110 more** survived that the inverse map could not read, because
`⟨ئאت⟩` inverts to **אאת** — a doubled alef, since the Uyghur hamza-carrier
is itself cognate to א and the original א was never converted. The lesson is
not "the list was short." It is that **a list was never the right instrument**.

**5 · "narrative carries 3–5× the markers of poetry" — wrong frame.**
Chronicles was predicted higher and came in lower. The window was
genealogy. The variable is **clause density with direct objects**, not
genre.

---

## Why the per-window rates below understate the corpus

At ~22,000 verses the window stopped walking forward and turned over into
**five books at once** — Genesis 91, 2 Chronicles 76, Exodus 56, Leviticus
47, Numbers 30. The relay had entered its **residue pass**: re-rendering the
verses the first sweep failed or skipped.

The damage density in that window is far higher than in any linear window —
9 marker-damage, 5 garble, 2 erasure, 2 register forks in 300 verses,
against near-zero in Psalms, Proverbs and Chronicles.

**So every per-window rate recorded below was measured on first-pass work
and understates the corpus.** The residue is where the hard verses live, by
construction. No corpus-wide rate can be stated from window sampling — only
from a full-tree count after the burn ends. The marker census in §3e is the
first such count and it is the one to trust.

---

## The thermometer has five sides, not three

The discipline doc named three (Han · Arabic religious diction · Turkic
siblings). The burn produced two more that a three-sided check reads cold.

| Side | What it catches | Status through 12,886 |
|---|---|---|
| **Han** (U+4E00–U+9FFF) | the state language saturating the model's Uyghur | **0 on every window** |
| **Cyrillic** (U+0400–U+04FF) | the USY archive script | **0 on every window** |
| **Latin** (A–Za–z) | Turkic-sibling bleed — arrives in Latin, not Arabic | Torah-clustered, then 0 |
| **Islamic register in Uyghur words** | `ئىماندار` · `دوزاخ` · `جەھەننەم` | **new — see Ezek 30:9** |
| **Rail-narration / marker-narration** | the chair talking *about* the rule | **new — see Ezek 34:2, 30:9** |

The Arabic-diction side was written to catch **اﷲ / الرحمن / رب العالمين**
— Arabic words in Arabic script. It does not catch the same register
arriving in *Uyghur* vocabulary. `ئىماندارلار` ("the believers") is an
ordinary Uyghur word; only its presence where the Hebrew has nothing makes
it a finding.

---

## Erasure — a hedge-shape, not a word

~0.05% of seats (tw was 0.24%). The chair sets the erasure and the rail
**side by side for one Hebrew construct**, reaching for whichever
traditional title is at hand. It is the easiest class to cure because the
right word is already in the verse.

### Habitat A — bare in the flow, apposed to the rail

| Seat | Reads | Hebrew |
|---|---|---|
| `deuteronomy/5/9`, `5/12` | `خۇدايىڭ ياھۋەھ ئېلوھىمىڭ` | יהוה אלהיך |
| `exodus/3/18` tok 12 | `خۇداسى — ئېلوھىمى` | אלהי |
| `2-kings/17/7` | `پەرۋەردىگارى — ياھۋەھ ئېلوھىملىرىغا` | — **a different title**, same construction |
| `ezekiel/28/26` tok | `ئېلوھىم — ئۆزلىرىنىڭ خۇداسى` | אלהיהם — and it propagated into the flow |
| `exodus/4/27` | the one plain substitution | |

`2-kings/17/7` is why the cure cannot key on `خۇدا` alone: the same slot
took **پەرۋەردىگار** instead. Sweep the whole list —
خۇدا · اﷲ · تەڭرى · پەرۋەردىگار · رەب + English God/Lord/LORD.

`ezekiel/28/26` is why it must sweep **both surfaces**: the doubled gloss
sits in the token row *and* reached the flow.

### Habitat B — inside a ⟨supplied-word⟩ bracket

`jeremiah/46/18` —

> …ئىسمى ياھۋەھ تسېۋائوت بولغان **⟨خۇدا⟩** —

The Hebrew has only *the King, whose name is YHWH Tsevaot*. The chair
supplied **خۇدا** as an apposition and put it in the supplied-word bracket,
which is exactly where a bracket-blind sweep will not look.

**A cure that sweeps only bare flow reads B cold. One that sweeps only
brackets misses A. Sweep both.**

---

## `رەب` is never a bare substring match

The eighth time a census without a whitelist measured its own blindness.
A raw substring count said **8 erasure seats**; the truth was **3**.

`رەب` is legitimately present in three ways:

- inside **ئەرەب** — *Arab / Arabia*, glossing Hebrew **ערב**
  (`ezekiel/27/21`, `jeremiah/46/1`)
- inside **ئەرەبە** — *the Arabah*, glossing **הערבה** (`jeremiah/39/4`)
- as itself, the correct gloss of Hebrew **רב** in the Babylonian titles
  **رەب-سارىس** and **رەب-ماگ** — Rab-saris, Rab-mag (`jeremiah/39/3`)

Match on word boundaries, strip the two host words first, and exclude any
seat whose surface is **רב** or **ערב**.

---

## Register garble — the chair narrating its own rail

Two seats, both in Ezekiel, both new to this chair and neither seen on
tw or ff.

### `ezekiel/34/2` — the rail leaks in as an imperative

> …ئېيت: **خۇدا شۇنداق دەيدۇ دېمە**، ئادوناي ياھۋەھ شۇنداق دەيدۇ: ۋاي پادىچىلارغا!

*"say: **do not say 'God says thus'**, Adonai Yahweh says thus:"* — the
chair wrote its own discipline into the verse as a command, then obeyed it
in the next clause. The rendering that follows is correct; the instruction
in front of it is not text.

Same verse also carries the **wrapper class**:

> ئۆزلىرىنى **⟨⟨את⟩ ئۇلارنى⟩** باقاتتى

A marker nested inside a supplied-word bracket — the exact tw root-wound
shape `⟨⟨את⟩ asase⟩`. First sighting on ug. `dev/scripts/tw_bracket_unbalanced.py`
parks every intact `⟨את⟩` behind a `` sentinel before rebalancing,
and that guard is not optional (it is what broke Gen 1:25 on tw when absent).

### `ezekiel/30/9` — three defects in one verse, and the worst of them

> …**⟨ئەت⟩ بەلگىسىنى كۆرسىتىپ** تۇرىدۇ؛ … چۈنكى **ئىماندارلارغا** — قاراڭ، ئۇ كەلمەكتە.
> **⟨⟨ئىزاھ: ئەرەب يېزىقىدا بۇ ئايەت تۆۋەندىكىدەك⟩⟩**

1. **`⟨ئەت⟩ بەلگىسىنى كۆرسىتىپ`** — *"showing the ⟨et⟩ marker"*. The chair
   **transliterated את into Uyghur letters** (ئەت) and then wrote a sentence
   about it, making the marker an object of the verse. A marker count sees
   `⟨ئەت⟩` as neither a marker nor a supplied word.
2. **`⟨⟨ئىزاھ: …⟩⟩`** — *"⟨⟨note: in Arabic script this verse is as
   follows⟩⟩"*. A translator's-note stub in doubled brackets, whose payload
   never arrived. Rule 6 (*the translator has no word*) violated in the
   machine's own voice.
3. **`ئىماندارلارغا`** — *"to the believers"*, where MT has no such word.
   Islamic register arriving in ordinary Uyghur vocabulary.

---

## The marker arrives in the wrong script — and the count reads it as absent

`⟨ئەת⟩` — sorry, `⟨ئەت⟩` — is **את transliterated into Uyghur letters**. It
has two behaviours, and only one of them is narration:

- **`ezekiel/30/9` — narrated.** `⟨ئەت⟩ بەلگىسىنى كۆرسىتىپ` (*"showing the
  ⟨et⟩ marker"*). The marker became an object of the sentence.
- **`psalms/16/7` — in the correct slot, wrong script.**
  `مەن ⟨ئەت⟩ ياھۋەھنى بەركەتلەيمەن` against MT `אברך את יהוה`. The marker is
  doing the marker's job, in the right place, spelled in the wrong alphabet.

The second is the dangerous one. **A marker count sees nothing there.** Every
`⟨ئەت⟩` in a marker slot is a marker the census scores as missing, which
means the marker gap on any window containing them is *understated*. The
scan now reports `MARKERS-TRANSLITERATED` as its own line. The cure is a
one-for-one rewrite `⟨ئەت⟩ → ⟨את⟩`, but it must run **before** any gap is
measured or acted on.

### The wrapper class has a grammatical cause

`psalms/21/7` — `سېنىڭ چېھرىڭ ⟨⟨את⟩ بىلەن⟩ ئۇنى شادلىققا چۆمدۈردۈڭ`
against MT `תחדהו בשמחה את פניך`.

Uyghur is **postpositional**. Hebrew writes את *before* its object; the
Uyghur supplied word (بىلەن, *with*) must land *after*. The chair resolved
the collision by wrapping marker and postposition in one outer bracket.
On tw — a prepositional language — the same class appeared as
`⟨⟨את⟩ asase⟩`, marker then noun. Same shape, opposite grammar, same cause:
a prefix-position marker meeting a language that does not have one.

This is worth knowing before the repair pass runs: the wrapper is not
random noise, and on an RTL postpositional chair it will be *more* common
around supplied function words than around nouns.

## Draft-speak — the verse rendered twice

`psalms/31/9` —

> «مېنى دۈشمەن قولىغا تۇتقۇن قىلمىدىڭ، پۇتلىرىمنى كەڭ جايدا تۇرغۇزدۇڭ»
> **دېمەك**، سەن مېنى دۈشمەننىڭ قولىغا تۇتقۇن قىلمىدىڭ، پۇتلىرىمنى كەڭ
> جايدا تىك تۇرغۇزدۇڭ.

The whole verse rendered **twice** — once quoted, once plain, joined by
*دېمەك* (*"that is to say"*). The ff lane-6 draft-speak family. Neither
half is wrong; the doubling is.

### Two whitelist saves in this one seat

1. **`دېمە` lives inside `دېمەك`.** The rail-narration probe matched the
   *"that is to say"* connective, not the `خۇدا شۇنداق دەيدۇ دېمە`
   imperative. Ninth time a census measured its own blindness. The probe
   now requires `دېمە` not be followed by ك.
2. **Psalms versification is HEBREW, with the superscription counted.**
   Read against English numbering, `psalms/31/9` looks like it carries
   31:8's content and I nearly filed an off-by-one. It does not — Hebrew
   31:9 *is* English 31:8, because the title is verse 1. See
   `title-verses-included`. **Never check a Psalm seat against an English
   reference.**

## The licensing test — what finally replaced the word lists

`proverbs/20/22` —

> «ياملىققا ياملىق قايتۇرىمەن» **دېمە**؛ ياھۋەھكە ئۈمىد باغلا، ئۇ سېنى قۇتقۇزىدۇ.

against MT `אל תאמר אשלמה רע קוה ליהוה ויֹשע לך`. The token rows read
`אל → دېمە` and `תאמר → دېمە`. **This is the correct rendering** — *"do not
say"* — and אל תאמר is a standing Proverbs formula (3:28, 20:22, 24:29).
Tenth time a census measured its own blindness.

The pattern across all ten is now plain, and it is one pattern:

| Probe | Legitimate host |
|---|---|
| `رەب` | ئەرەب (Arab), ئەرەبە (the Arabah), and رەب glossing **רב** |
| `دېمە` | دېمەك (*that is to say*), and دېمە glossing **אל תאמר** |
| Latin letters | Uyghur's own بۇ/بىز/ئۇ/بار/يوق look Turkish and are its own |
| `a`/`do`/`be`/`we` (tw) | all four are Twi words |
| 雅威 / 야훼 (fleet) | **are the Name**, in two characters |

**A word list can never be the discriminator, because every word a defect
uses is also a word the text uses.** What separates them is whether a token
row licenses it:

> Text in the **flow** with no **surface** behind it is the chair speaking.
> Text a gloss also carries is translation.

`ezekiel/34/2`'s `خۇدا شۇنداق دەيدۇ دېمە` is unlicensed — no token row
glosses it. `proverbs/20/22`'s `دېمە` is licensed by אל and תאמר. Same word,
opposite verdicts, and the test needs no vocabulary at all.

The scan's garble probe now runs the licensing test instead of a word list.
This is the same principle as the delimiter-strip guarantee on tw: **measure
against what the floor actually holds**, not against a list of things that
look wrong.

### A fusion note, not a defect

Both `אל` and `תאמר` gloss to the single word `دېمە`. Uyghur's negative
imperative is one word, so two Hebrew tokens legitimately map to it. That
duplicates the gloss string without breaking `token count == gloss count`.
Same family as the ratified case-suffix ruling — intact-stem inflection is
lawful.

## The marker does not arrive in one wrong form — it arrives partly converted

The Esther window turned the transliterated-marker finding into something
larger. **את does not fail into a single alternative spelling.** It fails
along a gradient, and every point on the gradient is invisible to a counter
looking for `⟨את⟩`.

| Form | Codepoints | Seat |
|---|---|---|
| `⟨את⟩` | Hebrew alef + tav | intact |
| `⟨ئەت⟩` | fully transliterated into Uyghur | `psalms/16/7`, `esther/3/13` |
| **`⟨ئאت⟩`** | **U+0626 Arabic yeh-w-hamza + U+05D0 HEBREW ALEF + U+062A Arabic teh** | `esther/3/8` |
| **`⟨אت⟩`** | **U+05D0 HEBREW ALEF + U+062A Arabic teh** — no hamza | `1-chronicles/22/12` |
| **`⟨⟨⟩`** | **evacuated — bracket emitted, content lost** | `esther/1/11` |

`1-chronicles/22/12` is the cleanest demonstration that these are two
surfaces: the **token row is correct** (`את → ⟨את⟩`) while the **flow**
carries the damaged `⟨אت⟩`. Third time on this chair. The same verse's
genuine supplied words — `⟨ئۈستىدە⟩`, `⟨ئۈچۈن⟩` — are untouched and the
structural probe correctly ignores them, because they carry no Hebrew
codepoints to mix.

`⟨ئאת⟩` is the one that matters. The chair began converting את into Uyghur
letters and **stopped halfway**, leaving the Hebrew alef embedded between
two Arabic-script letters. It is neither `⟨את⟩` nor `⟨ئەت⟩`, so **both**
counters score it absent.

`⟨⟨⟩` at `esther/1/11` — MT `להביא את ושתי המלכה` — is the marker slot
emitted with its contents gone, doubled and unbalanced. This is precisely
the shape `tw_bracket_unbalanced.py` will try to rebalance, and precisely
why its `` sentinel guard is not optional: an unguarded rebalance
here is what broke Gen 1:25 on tw.

### The corpus-wide count — 22,119 files, taken 2026-09-17

I found three damaged forms by reading seats. **There are at least ten.**

| Form | Count | What it is |
|---|---:|---|
| `⟨את⟩` | **18,106** | intact |
| `⟨ئەت⟩` | **302** | fully transliterated — pure Arabic script, so **neither** a Hebrew-block nor a mixed-block probe catches it |
| `⟨وאت⟩` | 80 | Arabic waw + Hebrew את |
| `⟨אت⟩` | 74 | Hebrew alef + Arabic teh |
| `⟨ئאت⟩` | 76 | Arabic hamza-carrier + Hebrew alef + Arabic teh |
| `⟨אات⟩` | 6 | Hebrew alef + **Arabic** alef + Arabic teh |
| `⟨ئת⟩` | 5 | Arabic hamza-carrier + Hebrew tav |
| `⟨אتئۇ⟩` | 4 | intact את with an Arabic pronoun glued inside the bracket |
| `⟨ۋئאت⟩` | 3 | Uyghur waw + hamza + Hebrew alef + Arabic teh |
| `⟨את مېنى⟩` | 3 | intact את plus an Arabic word inside the same bracket |
| `⟨⟩` / `⟨⟨⟩` | 8 | evacuated |
| `⟨⟨את⟩` | 17 | wrapper — unbalanced open |

**Damaged total: 295 mixed-or-evacuated-or-wrapped, plus 302
transliterated = 597, about 3.2% of all markers.**

This is the vindication of the structural probe, and it is not a small one.
Reading seats gave me three forms and would have kept giving me more, one
window at a time, indefinitely. **A form-list would never have closed.**
The property — *a bracketed body mixing the Hebrew block with the Arabic
block, or empty* — closed it in one pass.

Note the one form the property probe still misses: **`⟨ئەت⟩` is pure Arabic
script**, so it mixes nothing. It needs its own count, and it is the largest
single damaged class at 302.

### Not damage — the inflected and conjoined marker, 184 seats

A separate 184 seats carry the marker in **pure Hebrew with a prefix or
suffix**, exactly as the text writes it:

| Form | Count | |
|---|---:|---|
| `⟨ואת⟩` | 100 | waw + את — *and [the]* |
| `⟨אתו⟩` | 25 | את + 3ms suffix |
| `⟨אתם⟩` | 25 | את + 3mp suffix |
| `⟨אתכם⟩` | 18 | את + 2mp suffix |
| `⟨ו-את⟩` · `⟨ו את⟩` | 7 | waw separated |
| `⟨אותם⟩` · `⟨מאת⟩` | 7 | plene, and מן + את |

**These are not defects.** They are the Hebrew form as written, and they are
the pending **inflected-את question** arriving at scale on a new chair. The
standing recommendation — **keep the suffix** — is what the data supports
here: 184 seats where flattening to bare `⟨את⟩` would silently discard a
conjunction or a pronoun the text actually carries.

**Awaiting Scott. Do not flatten these.**

### The probe has to be structural, like the licensing test

A list of wrong forms is always one form behind, for the same reason a
whitelist of suspect words was. The scan now detects the **property**, not
the spelling:

- a bracketed body that is **empty** → evacuated
- a bracketed body mixing the **Hebrew block** (U+0590–05FF) with the
  **Arabic block** (U+0600–06FF) → mixed-script

Two structural probes now carry what five word-lists could not: the
**licensing test** for register, and **marker damage** for the markers.

### Position drift has the same cause as the wrapper

`esther/3/13` reads `پۈتۈن يەھۇدىيلەرنى ⟨ئەت⟩ يوقىتىشقا` against MT
`להשמיד … את כל היהודים`. The marker sits **after** its object, because
Uyghur is SOV and the object moved in front of it. Same postpositional
collision that produced `⟨⟨את⟩ بىلەن⟩` at `psalms/21/7`. The repair pass
cannot assume the marker precedes what it governs on this chair.

## Daniel's bilingual seam — a PASS, recorded

Daniel 2:4 is where the Hebrew gives way to Aramaic, and it is a standing
hazard. The chair handled it:

> ۋە كاسدىيلار پادىشاھقا **ئارامىيچە** سۆزلىدىلەر: «ئەي پادىشاھ، ئەبەدىي ياشىغىن…»

The token rows render Aramaic surfaces (`מלכא → ئەي پادىشاھ`,
`לעלמין → ئەبەدىي`, `חיי → ياشىغىن`) without stumbling, and the flow names
the switch. No finding — filed because a clean result at a known hazard is
worth as much as a defect.

## Marker gap tracks the BOOK — and the denominator matters

Reading a small gap as improvement is as wrong as reading a large one as
degradation. Always take the gap against the token-row count.

| Window | Rows w/ ⟨את⟩ | Flow | Gap |
|---|---|---|---|
| Leviticus | 315 | — | 135 |
| Joshua | — | — | 91 |
| 1 Samuel | — | — | 89 |
| 1 Kings | — | — | 94 |
| 2 Kings | 305 | — | 97 |
| **Isaiah** | **59** | — | **22** |
| Jeremiah 39–46 (prose) | 293 | 171 | 122 |
| **Ezekiel** | **162** | **84** | **78** |
| **Psalms** | **23** | **15** | **8** |
| **Proverbs** | **12** | **6** | **6** |
| **Esther + Daniel + Qohelet** | **133** | **73** | **60** |

| **1+2 Chronicles** | **83** | **57** | **26** |

Two predictions, one right and one wrong, and the wrong one is worth more.

Est+Dan was predicted before it was measured — narrative returning after
the wisdom books had to swing the density up, and it did.

**Chronicles was predicted to swing higher still. It did not** — 83 marker
rows in 4,027 token rows, well below Esther–Daniel's 133 in 5,214. The
framing *"narrative carries 3–5× the markers of poetry"* is wrong. The
window is **genealogy**: prose made of name lists, with almost no clauses
taking a direct object.

The variable is not narrative-versus-poetry. It is **clause density with
direct objects**. Genealogy is prose that behaves like poetry for markers.
A gap read against the wrong expectation is as misleading as a gap read
with no denominator at all.

Narrative books carry three to five times the markers of oracle books. The
gap follows the density, not the quality. `flow_parity.py` closes it in one
pass at seating (it closed 1,987 on tw).

---

## Latin script — NOT a sibling language. Uyghur's own word, half-romanized.

**I had this wrong for most of the burn and the Chronicles window corrected
it.** I recorded `exodus/29/3`'s `üstige` as *Turkish bleed — a sibling
language intruding*. It is not. **`üstige` is the ULY romanization of
ئۈستىگە** — Uyghur's own word, written in Uyghur's own Latin alphabet.

Chronicles made the mechanism unmissable, because there it happens
**mid-word**:

| Seat | Reads | Should be | What happened |
|---|---|---|---|
| `1-chronicles/26/7` | **ئوغullar** | ئوغۇللار (*sons*) | stem in Arabic script, **plural suffix in Latin** |
| `1-chronicles/23/17` | **رەھavىيا** | Rehabiah, גלוסה of **רחביה** | first and last syllables Arabic, **middle syllable Latin** |
| `exodus/29/3` | **üstige** | ئۈستىگە | the whole word romanized |

`1-chronicles/26/7` writes `ئوغۇللىرى` **correctly at the start of the same
verse** and then half-romanizes the same stem a few words later. And
`رەھavىيا` sits in the **token row** (`רחביה → رەھavىيا`), not only the flow.

This is the same failure as the marker: **partial conversion along a
gradient**, not substitution by a foreign form. The diagnosis, and therefore
the cure, is different from what I first filed:

- **Not** "a sibling language is bleeding in" → would be cured by a
  vocabulary guard against Turkish/Uzbek/Kazakh words.
- **But** "the archivist script is surfacing where the reader's script
  belongs" → cured by transliterating ULY→UEY, and it can strike **inside a
  single word**, so a word-level check is not enough.

This is the **script-home ruling** failing in exactly the way that ruling
was written to prevent: *romanization never wins v1*. Here it is not winning
the corpus, it is winning individual syllables.

Rate: 4 Exodus · 1 Leviticus · 4 Numbers · 1 Deuteronomy · **0** in Joshua,
1 Samuel, 1 Kings, Isaiah, Jeremiah, Ezekiel, Psalms, Proverbs,
Esther–Daniel · **4 in Chronicles**. Not monotone — it returns.

Separately, `⟨ئAgainst⟩` at `exodus/32/33` — English inside a marker
bracket, the tw *706 untranslated English* family.

---

## THE ONE MECHANISM, stated properly at the end of the burn

The chair substitutes **equivalent characters from whichever writing system
it holds**, mid-word, stopping partway. It shows up in four places and they
are not four findings:

| Where | Direction | Example | Count |
|---|---|---|---|
| Token **surfaces** | Hebrew → Arabic, by **cognate** | `לא→لא` · `מלך→مלך` · `ויאמר→ויאמر` | **4,345** |
| **Markers** | Hebrew → Arabic, partial | `⟨ئאת⟩` `⟨אت⟩` `⟨وאت⟩` `⟨אات⟩` … | **637** |
| Supplied **words** | Arabic → **Hebrew** (the reverse!) | `⟨אەلگە⟩` for ئەلگە · `⟨הەممىسىنى⟩` for ھەممىسىنى | 8 |
| Uyghur **words** | UEY → ULY (Latin) / USY (Cyrillic) | `قېرىndاشلىرى` · `شundaqla` · `تويمايдۇ` · `پادіشاھ` | 86 mixed + 80 whole |

The cognate map is *correct scholarship* — ל→ل, מ→م, ב→ب, נ→ن, and
פ→**پ**, ג→**گ** which Arabic lacks and Uyghur has. The chair knows the
correspondence perfectly. It applies it in the one place it must never go.

**The odd one out is Chinese, and it is not orthographic at all.**
`葡萄زارىڭنى` — **葡萄 is the Chinese word for grape**, substituted for
ئۈزۈم inside the Uyghur word for vineyard. `ئى穷تۇر` likewise (穷, *poor*).
The discipline doc named Chinese saturation as the chair's largest hazard
and expected it as *characters*; it arrived as **semantic word-substitution
inside a compound**, which a script check catches only by accident. Five
seats, and only a full-tree sweep found them.

**Still outstanding at this point in the seating:** the ULY/USY→UEY
transliteration (166 seats), the erasure cure (31 seats, three habitats),
and `⟨is⟩`×5 / `⟨the⟩`×5 — English function words in supplied brackets,
the tw *706 untranslated English* family.

## The prophet fork — and the ruling that settled it

`2-chronicles/36/12` and `36/16` render **הנביא** as **پەيغەمبەر**.
`ezekiel/34/2` renders the verb as **نەبىلىك قىل**.

Corpus census: **پەيغەمبەر in 171 files · نەبى in 154 files.** The chair is
using both, near evenly, with no rule.

**The split is the defect, not either word.** Same family as tw's Judah
`Yuda` 537 vs `Yehuda` 256 and Babel `Babilon` 141 vs `Babel` 90.

The call is genuinely Scott's, because the two rulings pull opposite ways:

* **THE POSTURE OF THE CHAIRS** says the language's own perfect word wins
  when it exists — and **پەيغەمبەر is Uyghur's own ordinary word for
  prophet**, the one a reader expects.
* **But پەيغەمبەر is also the word Uyghur uses for Muhammad**, which is why
  it sat on the Islamic-register side of the thermometer in the first
  place. نەبى is closer to **נביא** and carries no such freight.

This is not the خۇدا case: پەيغەمبەر erases no Name and replaces no divine
title. It is a register question about a common noun, and it wants a ruling
rather than a repair.

---

## The erasure has a THIRD habitat — and this one reaches the reader

`2-chronicles/35/3`, token row:

> `אלהיכם → خۇدايۇلار (ئېلوھىڭلار)`

The **erasure leads and the rail is parenthesised**. This inverts tw's
`Eloohim (Onyankopon)`, where the rail led. And the flow carries
**`خۇدايۇلار` alone** — the parenthetical never propagated.

That is the worst of the three habitats, because the other two leave the
rail somewhere a reader can find it. Here the reader receives only the
erasure.

| Habitat | Where | Reader sees |
|---|---|---|
| A — bare, apposed to the rail | flow + row | both |
| B — inside a ⟨supplied⟩ bracket | flow | both |
| **C — erasure primary, rail in parens** | **row only** | **erasure alone** |

The same verse also shows the conjoined marker being handled **two different
ways within one book**: `ואת → ⟨את⟩` here (waw dropped) against
`numbers/18/17` `ואת → ⟨وאت⟩` (waw converted to Arabic). Neither preserves
it as written.

## Filed, not yet a lane

- `jeremiah/46/1` — the flow reads like 46:2's content (*concerning Egypt…
  concerning Pharaoh Necho*) where MT 46:1 is *the word of YHWH… concerning
  the nations*. For the Tekoa tough-verse lane.

---

## Gate

First-hour gate **passed at 333 verses**: Han 0, Cyrillic 0, Latin 0,
erasure 0.

> Gen 1:1 — باشلىنىشتا ئېلوھىم ⟨את⟩ ئاسمانلارنى ۋە ⟨את⟩ يەرنى ياراتتى.

---

## Why there are versions

This is **ug.v1** — one rendering, produced once, under one discipline.

It is not meant to stand alone. Selah renders a language more than once
(en1, en2, en3 on the English chair), and the versions are not drafts
superseding one another. They are independent samples from the space of
faithful readings. Where two or three renderings **converge**, the Hebrew is
constraining the reading. Where they **scatter**, either the Hebrew
underdetermines it or the target language forces a choice the Hebrew never
made — and that scatter is a finding, not noise. A single rendering cannot
tell you which of those you are looking at.

The standard is the text's own. Deuteronomy 19:15 uses one verb twice:

> **לא יקום** עד אחד … על־פי שני עדים או על־פי שלשה־עדים **יקום דבר**
>
> *One witness shall **not rise up** … on the mouth of two witnesses or on
> the mouth of three witnesses **a word shall rise**.*

The verb is **יקום** — *stands, rises* — negated for the single witness and
affirmed for the two or three. And the thing that rises is **דבר**: a word.

Its plain sense is legal testimony, and reading it as a rule for translation
is an analogy rather than something the verse itself names. But the analogy
holds where it matters: **one rendering is one witness.** Read this version
against the others, and against the Hebrew it is laid beside. Where they
agree, the word stands. Where they do not, you have found the place worth
looking at.

---

## What is still unresolved

These are open at the time of writing. They are listed because a rendering
that hides its unsettled questions is asking to be trusted rather than
checked.

**The inflected marker — 4,212 rows.** Hebrew writes the object marker with
prefixes and suffixes: **ואת** (*and*), **אתו** (*him*), **אתכם** (*you*),
**מאת** (*from*). This rendering flattens about 96% of them to a bare
`⟨את⟩`, preserving the inflection in only 187 places. Whether to expand all
4,212 is undecided — and it is harder than it looks, because **את is two
different Hebrew words**: the object marker, and the preposition *with*.
They are spelled identically. The English floor this rendering derives from
brackets **both**, in 435 rows — so a blanket expansion would stamp the
object-marker bracket onto 435 prepositions across every language at once.
The two questions have to be answered together.

**The twelve stones.** The breastplate stone names in the interface are
transliterations where Uyghur has no fixed vocabulary for them. They were not
checked against a Uyghur Bible's Exodus 28, because we did not have one. They
should be.

**Names not yet canonised.** Personal and place names were rendered per verse
and have not had a fleet-wide consistency pass.

## What is left in the text

Honest residue, not hidden:

- **334 verses** where a token-row marker could not be placed into the verse
  line automatically, and **14** where the line carries a marker the rows do
  not. Each needs a token-guided look; none was stripped blindly, because a
  surplus marker may equally mean a missing row.
- **22 damaged brackets** the floor gate correctly refused to repair — the
  Hebrew there carries no marker to restore.
- **182 token rows with an empty gloss**, which is why this corpus has
  305,325 word-glosses against a floor of 305,507. An empty gloss produces no
  entry rather than a false one.
- **`genesis/40/13`** carries a stray `⟨ئىبرانىيچە⟩` — "⟨in Hebrew⟩" — left
  over from the renderer explaining itself.

## How to check any of this

Every count in this file came from a script run against the files in this
repository. None of it requires trusting the account.

```bash
# verses and token rows
find . -name '*.json' | wc -l                      # 23,213

# the Name, and that the erasure list is absent from it
grep -rho 'ياھۋەھ' --include=*.json . | wc -l
grep -rl 'خۇدا\|اﷲ\|تەڭرى\|پەرۋەردىگار' --include=*.json .   # expect none

# markers intact vs damaged
grep -rho '⟨את⟩' --include=*.json . | wc -l
```

The repair passes themselves are in the Selah repository under
`dev/scripts/`, are idempotent, and report what they touch rather than
silently overwriting it. Running one a second time should report zero; if it
does not, something else has changed the tree.

The Hebrew surfaces in every `tokens[].surface` field are the read-only
floor, carried through unchanged. Any verse can be laid beside its Hebrew,
token by token, and the two counts compared. That is the whole point.
