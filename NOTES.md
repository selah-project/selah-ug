# NOTES — selah-ug, chair 75

Working notes in English. The reader-facing documents
(`README.md`, `CONTRIBUTING.md`, `LICENSE.md`) are in Uyghur, as
this chair's own documents should be.

Lit 2026-09-17. Burn complete same day. Floor 23,213.

---

## Burn signature

| | |
|---|---|
| relay | `batch/relay-move-on! [:ug]`, engine-side |
| done-file | `{:missing-after-pass 1379, :residue 51, :status :moved-on-with-residue}` |
| final | 23,213 / 23,213 verses · **305,507 / 305,507 token rows** |
| gleaning | rung 1 (24000) cleared **all 51** residue |

**The residue was silent truncation, not model failure.** Every one of the
51 landed by raising `max-tokens` from 12000 to 24000 — exactly what
`batch.clj`'s ceiling note says to try first. It also explains why the
failures arrived in adjacent pairs (`1-samuel/16/3`+`16/4`,
`genesis/22/21`+`22/22`): batch-of-2 calls truncating as a unit.

Later rungs: 32000 for the 12 empty-token seats and the 26 count-mismatch
seats; 48000/`:glm-5.3`/0.7 for the script-bleed and erasure stragglers.

---

## The one mechanism

This chair's defects are not a list. They are **one behaviour** in four
places: the chair substitutes an equivalent character from whichever
writing system it holds, **mid-word, stopping partway**.

| Where | Direction | Example | Count |
|---|---|---|---|
| token **surfaces** | Hebrew → Arabic by **cognate** | `לא→لא` · `מלך→مלך` · `ויאמר→ויאמر` | **4,345** |
| **markers** | Hebrew → Arabic, partial | `⟨ئאת⟩` `⟨אت⟩` `⟨وאת⟩` `⟨אات⟩` `⟨ئת⟩` … | **637** |
| supplied **words** | Arabic → **Hebrew**, the reverse | `⟨אەلگە⟩` for ئەلگە · `⟨הەممىسىنى⟩` for ھەممىسىنى | 8 |
| Uyghur **words** | UEY → ULY / USY | `قېرىndاشلىرى` · `شundaqla` · `تويمايдۇ` · `پادіشاھ` | 166 |

The cognate map is **correct scholarship**: ל→ل, מ→م, ב→ب, נ→ن, and
פ→**پ**, ג→**گ** — two letters Arabic does not have and Uyghur does. The
chair knows the correspondence perfectly and applies it in the one place it
must never go.

**Chinese is the odd one out and is not orthographic.** `葡萄زارىڭنى` —
葡萄 is the Chinese word for *grape*, substituted for ئۈزۈم inside the
Uyghur word for vineyard; `ئى穷تۇر` likewise (穷, *poor*). The discipline
doc named Chinese saturation as this chair's largest hazard and the probe
looked for **characters**; it arrived as **word-substitution**. A script
check finds that only by accident.

---

## Cures, in the order they must run

1. `surface_restore.py ug` — the floor is authoritative; restores every
   Hebrew surface. **4,345.** Re-run after every re-render: the sweep after
   the 85-verse script-bleed pass restored **21 more**, which says the bleed
   is the model's standing behaviour, not an artifact of one pass.
2. `ug_prophet_canon.py` — Scott's ruling (below). **646.**
3. `marker_normalise.py ug` — **637** over two passes; 19,297 preserved.
4. `ug_hand_pass.py` — Name spelling **261**, plus 3 erasure seats by hand.
5. `flow_parity.py ug` — **2,706** markers carried into the flows.

Residue for a later hand list: **334 flow-parity losses · 14 gains · 22
damaged brackets the floor gate correctly refuses · `genesis/40/13`'s stray
`⟨ئىبرانىيچە⟩`.**

---

## Rulings applied

**No later prophets in the Tanakh** (Scott, 2026-09-17) — *"we need to be
careful about bringing Muhammed into the Hebrew bible. Not beautiful."*
پەيغەمبەر is Persian-derived and is the word Uyghur uses for Muhammad;
**نەبى** is cognate with נביא, root נ-ב-א. 646 substitutions, stem swap with
the suffix intact. A word a language reserves for a post-biblical figure
never renders a Tanakh common noun, **even when it is that language's
ordinary word** — the posture clause does not reach it.

**Name spelling** — ياھۋەھ, not يەھۋەھ. The discipline doc's D1 table names
it and the corpus agreed sixty to one. 261 cured; not a fork.

---

## For Scott — open

**The inflected-את question, at this chair's scale.** 4,212 rows carry an
inflected Hebrew surface glossed with a bare `⟨את⟩` — ואת 2,194 · אתו 581 ·
אתכם 347 · אתם 315 · אותם 190 · מאת 120. The chair flattens ~96% and
preserves 4%. Standing recommendation is *keep the suffix*, which would
mean expanding all 4,212.

**But את is two words**, and this is why the question is harder than it
looks: the direct-object marker and the preposition *with* are homographs,
and **the en floor brackets both** — `2-samuel/3/27` reads
`אתו → ⟨את⟩ with him`, across **435 floor rows**. A blanket expansion would
stamp the object-marker bracket onto 435 prepositions **fleet-wide**. The
floor is read-only. The two questions have to be answered together.

**Fleet, found while sweeping for the prophet word:** fa carries 231
`پیامبر` and ps 122 `پیغمبر` while **live and serving**; sd carries **261
corrupt surfaces**, also live. `surface_restore.py` and the prophet cure
both generalise per language, but these are served text.

---

## What this chair taught the instrument

- **A repeated clean sample is not a clean corpus.** "Han 0 · Cyrillic 0 on
  every window" was asserted eleven times on fresh-300 windows — a 1.3%
  sample of 23,213 files. The tree held Han 5 and Cyrillic 4.
- **A word list never closes.** `رەب` is legitimate inside ئەرەب (Arabia),
  ئەرەبە (the Arabah), رەبكە *and* رەبقە (both Rebekah), گارەب (Gareb),
  تېرەبىنت (terebinth), يارەب (Yareb), ئورەب (Oreb), رەببەسى (Rabbah), and
  as the gloss of רב in Rab-saris. Thirteen whitelist failures across six
  chairs were one failure: **every word a defect uses is also a word the
  text uses.** The fix is a structural probe gated on the floor.
- **Idempotence proves the pass is stable, not that the corpus is sound.**
  The marker pass reported clean over 110 damaged markers its own inverse
  map could not read.
- **A report clause on a cure pass finds what no probe was looking for.**
  The prophet pass's "gloss cured on a surface outside נביא" report is what
  surfaced `amos/7/14`'s `نביא` and, through it, all 4,345 corrupt surfaces.
