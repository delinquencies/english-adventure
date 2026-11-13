# English Adventure — Game & Learning Rulebook

**Document ID:** EA-RULES  
**Version:** 1.0 · November 13, 2026  
**Status:** Governing baseline — approved decisions consolidated; proposed details clearly marked  
**Product name:** TBD. “English Adventure” is an internal working label, not approved branding.  
**Target language in first release:** English  
**Initial learner support language:** Spanish (`es`); architecture should accommodate additional support languages later.

> **Product promise:** Learn English by living a life in it.
>
> **Player principle:** Learners use English to accomplish things in the world, rather than doing unrelated tasks simply to earn language exercises.

## How to use this rulebook

This document governs **product behavior, instructional design, progression, and assessment**. It is the primary source for game rules. It does *not* override episode-specific dialogue, asset coordinates, or implementation constraints that are consistent with it.

**Source hierarchy:**
1. New, explicit product-owner decisions, recorded in the decision log below.
2. This `GAME_RULEBOOK.md` for cross-product gameplay/curriculum rules.
3. `A0_0_PRODUCT_AND_CONTENT_CONTRACT.md` for exact A0.0 scenes, prompts, answers, and transitions, where consistent with the rulebook.
4. `ART_DIRECTION_DOSSIER.md` for visual design proposals and approved art constraints, where consistent with the rulebook.
5. `AGENTS.md` for engineering procedure, coding scope, and agent handoffs, where consistent with the rulebook.
6. Existing prototype/code and implementation preference.

**Conflict protocol:** Do not silently choose. Log the conflicting statements, apply the latest explicitly approved owner decision when known, and ask for an owner decision if the conflict changes behavior or scope. Fix conflicting documents after approval. A speculative design proposal cannot override a locked rule.

**Status vocabulary:** **LOCKED** = explicitly agreed or established behavior; **BASELINE** = implementation default, may change through review; **PROPOSED** = not approved; **DEFERRED** = outside the current vertical slice; **OPEN** = requires a decision.

---

## 1. Nonnegotiable product principles

| ID | Status | Rule | Implication |
|---|---|---|---|
| P-01 | LOCKED | Teach **English through everyday life**. | The first story is home → morning routine → commute → corner store → neighborhood → opportunities → careers, not a trade-selection quiz. |
| P-02 | LOCKED | Situations drive lessons. | Every activity has a narrative purpose and a communicative objective. |
| P-03 | LOCKED | **Guided adventure with optional choices.** | Show a clear main route; optional scenes and routes may branch and reconverge. |
| P-04 | LOCKED | **Gradually fading native-language support.** | English becomes more prominent with demonstrated ability; translations and hints always remain accessible. |
| P-05 | LOCKED | Mistakes are recoverable, not punitive. | Hints, replay, explanation, retry; no loss of life/energy for errors. |
| P-06 | LOCKED | Story completion is distinct from language mastery. | A scene can finish with assistance; evidence of independent comprehension is tracked separately. |
| P-07 | LOCKED | Speaking in A0.0 is **optional and unscored**. | Never require microphone permission or pronunciation grading for first episode. |
| P-08 | LOCKED | Adult-friendly, warm, witty tone. | Never patronize, shame, stereotype, or infantilize learners. |
| P-09 | LOCKED | Revisit learned language in new situations. | Curriculum tags permit later reviews and transfer tasks. |
| P-10 | LOCKED | Show truthful accomplishments. | Do not fabricate streaks, stars, mastery, badges, or completed locations in the live UI. |

## 2. Audience, language, and localization

**Primary first-release journey:** Spanish-speaking absolute beginners learning English. The initial UI can also offer English as a support language for testing/accessibility; it does not make Spanish the target language. Do not ask the learner which language to study unless additional target languages genuinely ship.

### L-01 — Progressive immersion [LOCKED]
- Early onboarding provides native-language support for setup and unfamiliar concepts.
- English target phrases are audible and visually prominent from the first encounter.
- Teach with images, scene context, gestures, and clear speech before independent challenge.
- After learners demonstrate comprehension, move to English-first prompts. **Do not fade translations by timer, episode count alone, or arbitrary thresholds.**
- Keep a visible path to request translation, replay, or easier instructions; allow learners to restore more support in preferences.
- Asking for help does **not** reduce story rewards or block progression. It may be recorded as learning evidence.
- Never use flags as the *only* way to label languages.

### L-02 — Pronunciation and inclusion [LOCKED for principle; DEFERRED for recognition implementation]
- Clear pronunciation examples and replayable audio are foundational.
- Spoken responses may have multiple valid phrasings and accents.
- Speech recognition is a possible later capability; transcription accuracy must not be passed off as pronunciation quality.
- Do not penalize recognized regional accents simply for differing from a synthetic voice.
- A0.0 must work without a microphone.

### L-03 — Locale handling [BASELINE]
- Store support-language choice independently from target-language choice.
- Do not hard-code Spanish into reusable UI components; localize strings through structured content.
- Support long translated strings and screen-reader labels.
- External-facing English lesson material should not be accidentally translated into Spanish as the language being taught.

## 3. World structure and learner agency

**Core loop:** `Enter location → encounter situation → hear/see meaningful English → choose/construct/respond → consequence and feedback → advance → return for review`.

### G-01 — Main quest and side actions [LOCKED]
- A clearly marked current objective must always exist.
- Side tasks, alternate commutes, and revisitable locations add variety but do not withhold essential language or dead-end the learner.
- Branches should **reconverge** when feasible (walking, bus, bike, or car eventually lead toward the corner store).
- Optional choices can alter dialogue or practice sets; they must not make later required content incomprehensible.

### G-02 — Level/map relationship [LOCKED]
- A **world map** shows past locations, the current location, accessible choices, and visible upcoming destinations.
- Its purpose is orientation, anticipation, and a sense of accomplishment—not a fake feature list.
- Visible locked content must be honestly labeled unavailable; do not present unusable controls as active.
- Finished areas remain revisitable for review or optional branches.
- The world story and the CEFR level are separate axes; story completion must not assert CEFR certification.

### G-03 — Unlocks [BASELINE]
- Completion of required narrative objectives unlocks the next story step, even when hints were needed.
- Mastery indicators evolve based on independent, retained performance.
- Existing English speakers should eventually access placement/skip paths into relevant professional content; this feature is **DEFERRED** beyond A0.0.
- Never require completion of dozens of irrelevant general lessons just to reach a trade pathway.

### G-04 — Consequences [LOCKED]
- Language actions produce legible fictional consequences: the correct object is selected, a character responds, a purchase advances, or a route changes.
- Incorrect answers trigger coaching and retry rather than fictional humiliation or unsafe outcomes.
- Hazards and safety instructions must be accurate; don't reward unsafe decisions.

## 4. Curriculum architecture

**Structure:** `Target language → industry/general track → internal stage/CEFR band → world chapter → episode → scene → interaction/exercise → tracked learning objective`.

**A0 is an internal pre-A1 label, not an official CEFR band.** A1/A2/B1/B2 are instructional targets aligned with CEFR communicative capabilities; app completion alone is not a CEFR credential.

### C-01 — Dual objective rule [LOCKED]
Every episode has:
1. **Narrative objective:** what changes in the world (e.g., meet a companion; buy breakfast).
2. **Communicative objective:** what the learner can understand or do in English (e.g., greet and introduce themselves; request and pay for an item).

A scene or exercise lacking a relevant objective must be removed or justified as brief atmosphere, not presented as learning evidence.

### C-02 — Practical, implicit grammar [LOCKED]
- Introduce usable phrases in context; grammar is learned through repetition and variation.
- No mandatory abstract grammar lecture to advance.
- Short actionable feedback is mandatory after errors; deeper explanations can be optional.
- Grammar should be introduced in a **pedagogically appropriate order**, independently of location art.

### C-03 — Beginner load and scaffolding [BASELINE]
- A0/A1 lessons should introduce **roughly 3–7 new words or chunks**, adjusted to difficulty and complexity.
- Start with recognition and meaningful audio/visual context; then supported response; then independent transfer.
- Reuse previously introduced phrases; no surprise testing of exposure-only language.
- Typical later beginner lesson: approximately 8–12 interactions, **not a mandatory count**; A0.0 follows its fixed approved screen contract.

### C-04 — Five exercise families [LOCKED]
| Code | Name | What it trains | Important rule |
|---|---|---|---|
| A | Visual Match | Identify an object/meaning in context | Image must unambiguously represent target. |
| B | Scrambled Sentence | Build a useful phrase from blocks | Accept valid variants and accessible non-drag alternatives. |
| C | Fill-in-the-Blank | Select missing grammatical/lexical part | Avoid multiple correct answers unless accepted. |
| D | Tone Translation | Choose appropriate social/professional register | Primarily B1/B2; don't force adult social nuance on absolute beginners. |
| E | Listen & Respond | Comprehend spoken prompt and respond | Audio replay and accessible alternatives; no microphone requirement by default. |

An episode **does not have to contain all five**; select the mechanic that assesses its objective.

### C-05 — Conversation in every episode [LOCKED]
- Every episode must contain at least one exchange where a character speaks and the learner supplies a contextually appropriate response.
- At A0 this can be a two-turn scripted exchange with recognized/assembled answers.
- At higher levels increase unpredictability, explanation, politeness, and spoken interaction.
- A page of unrelated vocabulary taps does not satisfy this criterion.

### C-06 — Real-world transfer [LOCKED]
- Every episode ends in a short application of its primary communicative objective in a **slightly changed context** or with less visible help.
- Repeated identical answers without contextual variation are insufficient for demonstrated learning.
- Transfer assessment is initially constrained and not a claim of unrestricted conversational fluency.

### C-07 — Curriculum progression [BASELINE]
| Internal episode / region | Narrative action | Language focus |
|---|---|---|
| A0.0 — Hello, You! | Set up, meet dog companion, exchange first greeting | Hello; Good morning; What's your name?; I'm [name]; Nice to meet you; Goodbye |
| A0.1 — Wake Up | Begin morning routine | Familiar objects, actions, basic commands |
| A0.2 — Breakfast | Make simple breakfast choices | Food, have/want/need, basic requests |
| A0.3 — Out the Door | Dress and gather essentials | Clothes, belongings, simple locations |
| A0.4 — Get Moving | Choose and begin commute | Directions, transportation, where/go/stop |
| A1 — Corner Store / Around Town | Shop, ask, navigate services | Prices, quantities, polite requests, appointments |
| A1–A2 — New Opportunities | Explore work and basic interviews | Introductions, routines, experience, plans |
| A1–B2 — Working Life | Apply language in optional occupational tracks | Job-specific comprehension, consultations, problem solving, de-escalation |

Story stage and CEFR level are not synonymous. Later job-interview tasks should have multiple difficulty bands. This table is a **roadmap**; only A0.0 is in the current implementation scope.

## 5. Feedback, completion, assessment, retention

### A-01 — Answer validity [LOCKED]
- Define preferred answers, legitimate alternatives, and deliberately incorrect distractors.
- If an answer is grammatically and contextually valid, don't mark it wrong merely for departing from a canonical string.
- Use visuals and dialogue to disambiguate contexts (e.g., *on the open truck bed* versus *in an enclosed truck*).
- Names and personal details are not graded for spelling or pronunciation.

### A-02 — Errors and support [LOCKED]
- Immediate feedback must say or show **why** an answer works and what to try next.
- Permit replay, hints, and retry; no lives, energy, or streak loss for misunderstanding.
- Feedback uses words/icons, not color alone.
- If an exercise cannot load its audio or image, provide a genuine recovery/fallback state; don't trap the learner.

### A-03 — Independent evidence versus completion [LOCKED]
Track at minimum:
- `story`: current scene/episode, visited and completed locations.
- `learningEvidence`: learning objective, first-attempt correctness, assistance/hint used, retries, later recall when available.
- `rewards`: earned achievements, backed by actual events.

- Completion may occur after assisted retries.
- Independent evidence can only be claimed from a sufficiently independent attempt.
- **Do not award a CEFR level based on completion percentage.**
- No fabricated XP, badges, or streak counts.

### A-04 — Spaced reinforcement [LOCKED principle; algorithm DEFERRED]
- Tag expressions and objectives for targeted later reviews.
- Later episodes reuse weak and aging expressions in new contexts.
- Delayed recall matters more than immediate right-answer streaks.
- A0.0 stores evidence; it does not need a production adaptive learning algorithm.

### A-05 — Honest progress UI [LOCKED]
- Show narrative progression, language competence/learning evidence, and optional exploration separately when available.
- Make the next destination obvious, and completed tasks satisfying.
- Represent preview/locked content accurately.
- Celebrations should be proportional; no promise of fluency from one scripted exchange.

## 6. Characters, narration, and audio

### CH-01 — Companion identity [LOCKED]
- **Mascot is the female protagonist's dog.** This decision supersedes older specs that called species undecided.
- Personality: warm, witty, curious, supportive traveling companion; humor in small doses, never distracting or infantilizing.
- Exact dog name, breed, markings, accessories, and design are **OPEN**; do not invent a final canon identity.
- A temporary *dog* placeholder is permitted for engineering, conspicuously marked and replaceable.
- Companion should guide, react, and step back as learner competence grows.

### CH-02 — Protagonist [BASELINE]
- Supplied illustrated female character in green jacket/gray hoodie/backpack is the current **visual reference protagonist**.
- Whether the player always controls that fixed character or can choose an avatar is **OPEN** and unnecessary to resolve for A0.0.
- Don't misrepresent the dog as a generic independent mascot divorced from the protagonist.

### CH-03 — Audio [LOCKED principles]
- English lines should have clear, replayable speech with labeled speaker.
- Prefer cached, versioned, pre-generated audio for fixed dialogue.
- Use transcript/captions where appropriate for accessibility, while preserving optional listening challenge modes.
- Narration and character voices should be distinct but not exaggerated stereotypes.
- Browser TTS may be used as a labeled development fallback; do not claim it is final voice acting.

### CH-04 — Speaking [LOCKED for A0.0]
- Provide optional “Say it with me” moments with model audio and pause for repetition.
- Do **not** access microphone, record speech, run speech recognition, or claim pronunciation grading in A0.0.
- Later speech-recognition or self-recording capabilities require separate approval and clear consent handling.

## 7. Accessibility and quality bar

| ID | Status | Quality rule |
|---|---|---|
| Q-01 | LOCKED | Beginner-friendly language and discoverable controls; no prior English presumed. |
| Q-02 | LOCKED | One meaningful dialogue exchange per episode; not only isolated word recognition. |
| Q-03 | LOCKED | Meaningful, understandable feedback after errors. |
| Q-04 | LOCKED | Clear view of current objective and honest progress. |
| Q-05 | LOCKED | Optional speaking never blocks introductory progression. |
| Q-06 | LOCKED | Visual and text alternatives to audio and non-color-only feedback. |
| Q-07 | BASELINE | Touch targets at least 44 × 44 CSS pixels, keyboard navigability, reduced-motion handling, screen-reader labels. |
| Q-08 | LOCKED | Test educational transfer and delayed recall; do not equate engagement with language acquisition. |
| Q-09 | LOCKED | Work vocabulary and safety information must be professionally accurate; harmful procedures do not become game rewards. |

**Speech-recognition quality rule:** When later implemented, speech transcription and pronunciation clarity must be evaluated as distinct capabilities. Never assume all speech recognition is on-device; document the actual engine, permissions, processing, and privacy behavior.

## 8. Art and UI boundary

**Visual direction [LOCKED]:** polished, adult-friendly **Western storybook / contemporary casual adventure**. Warm natural light, grounded character proportions, clean restrained linework, uncluttered reading surfaces, a desirable illustrated map. Avoid anime/kawaii/JRPG conventions and infantilizing graphics.

**Existing visual references [BASELINE]:** female three-pose character reference, sunlit bedroom reference, and matching kitchen reference (kitchen belongs to later content). The specific palette, typography, mascot appearance, final rig, asset scale, and map geography remain design approvals, not immutable rules.

**Implementation rule [LOCKED]:** Separate scene illustrations from real buttons, text, prompts, hotspots, overlays, progress indicators, and accessibility metadata. Do not ship a flattened AI mockup as the UI. All interactive affordances must actually function.

`ART_DIRECTION_DOSSIER.md` owns detail on palette proposals, perspective, asset dimensions, and image-generation guidance; a design update does not automatically change the learning rules.

## 9. A0.0 release contract — exact minimum

A0.0 **Hello, You!** is the first playable slice and should not be confused with A0.1 Wake Up.

**Sequence:** `S00` Welcome/support language → `S01` preferred name → `S02` meet dog → `S03` Hello recognition → `S04` assemble “I'm [name]” → `S05` morning greeting recognition → `S06` contextual response → `S07` farewell → `S08` independent short exchange → `S09` completion/map.

**Goals:** Recognize Hello / Good morning / What's your name / Nice to meet you / Goodbye; construct I'm [name]; respond to a short greeting exchange. “See you later,” “Tap,” “Listen,” and “Continue” are exposure, not mastery items.

**A0.0 acceptance checklist:**
- [ ] First-time learner sees **English** clearly identified as the language to be learned.
- [ ] Spanish support-language selection immediately changes setup/help copy; name is used correctly in dialogue.
- [ ] Dog companion is represented (temporary dog asset if final design is unavailable), never a cat/fox/raccoon.
- [ ] English speech is replayable or its unavailability is clearly explained with an accessible fallback.
- [ ] Introductory expressions are taught before being independently assessed.
- [ ] Every required exercise has meaningful retry, hint, and feedback behavior.
- [ ] A short genuine greeting exchange is completed; the final challenge is English-first with optional assistance.
- [ ] “Say it with me” is optional and unscored, without microphone access.
- [ ] Story completion is saveable and survives refresh; first-attempt/hint evidence is separately recorded.
- [ ] The map displays a truthful A0.0 accomplishment and A0.1 preview, not false unlocked activities.
- [ ] User can complete the flow with basic mobile accessibility and no dead ends.
- [ ] Tests cover localization, valid alternatives, retry/hint evidence, saved progress, and incorrect input.

**Out of scope for A0.0 [DEFERRED]:** native mobile apps, backend, accounts/auth, payments, data sync, adaptive mastery engine, real speech scoring, full commute, kitchen play, corner store play, interview simulation, trade tracks, avatar creator, and production placement test.

For exact prompts, answer options, localized microcopy and screen transitions, consult `A0_0_PRODUCT_AND_CONTENT_CONTRACT.md`.

## 10. Agent governance and change control

| Owner | Responsible for | Cannot change without explicit approval |
|---|---|---|
| Product owner | Locked product decisions and final acceptance | — |
| ChatGPT / curriculum lead | Learning objectives, content contracts, rulebook proposals, QA | Product positioning, locked mechanics, mascot identity |
| Gemini / art lead | Visual exploration, sprite/environment references, design specs | Pedagogy, story mechanics, approved art north star |
| Codex / engineering lead | Implement working app, tests, technical handoffs | Curriculum outcomes, product scope, art canon, speech policy |

### Change request format
```
CR-ID:
Requested change:
Reason / learner impact:
Affected rule IDs:
Affected documents and screens:
Backward compatibility / migration:
Status: PROPOSED | APPROVED | REJECTED
Owner decision and date:
```

**Rule changes need owner approval.** After approval, update this file first, then patch dependent content/specs and code; preserve a brief decision log. Do not treat an agent suggestion, screenshot, or AI-generated mockup as tacit approval.

### Decision log
| Date | Decision | Status |
|---|---|---|
| 2026-11-12 | English is first-release target; native-language support fades gradually but stays accessible. | LOCKED |
| 2026-11-12 | Guided adventure with optional choices; everyday life leads toward career pathways. | LOCKED |
| 2026-11-12 | A0.0 speaking is optional and unscored; companion personality warm and witty. | LOCKED |
| 2026-11-12 | Western storybook art direction instead of anime-inspired visual system. | LOCKED |
| 2026-11-12 | Companion is the protagonist's dog. | LOCKED |
| 2026-11-13 | Beginner-friendly grammar/context, dialogue, future speech-recognition readiness, and clear progress become explicit quality requirements. | LOCKED |
| 2026-11-13 | Consolidate cross-product rules into `GAME_RULEBOOK.md`; art and exact episode content remain separate. | LOCKED |

### Open decisions (not blockers for engineering first shell)
- Dog name, breed, marking, exact character turnaround, and voice.
- Whether protagonist artwork represents fixed avatar or selectable avatar.
- Exact visual design tokens, map geography, production animation implementation.
- Later speaking-recording feature, data privacy design, and speech evaluation method.
- Placement algorithm and how advanced learners jump to professional tracks.

## 11. Agent handoff requirement

Every implemented ticket should report:
```
TASK / STATUS:
FILES CHANGED:
RULE IDS / CONTRACT SCREENS AFFECTED:
BEHAVIOR VERIFIED:
TESTS RUN + RESULTS:
ASSUMPTIONS / PROVISIONAL ASSETS:
OPEN DECISIONS / RISKS:
ONE RECOMMENDED NEXT TASK:
```

**Do not proceed to the next major feature without verifying the current one.** Preserve the playable vertical slice and keep implementation changes reversible.