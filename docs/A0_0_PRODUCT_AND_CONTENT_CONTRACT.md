# English-Learning Adventure — A0.0 Product & Content Contract
**Status:** Approved baseline for vertical slice implementation  
**Version:** 1.0 · 2026-11-12  
**Working title:** English-Learning Adventure (product name TBD)  
**Episode:** `A0.0 — Hello, You!`  
**Companion specification:** `ART_DIRECTION_DOSSIER.md`

## 0. Decision register (locked)
- **Primary target language:** English. First supported instructional language: Spanish (`es`); architect for future additional languages.
- **Language support:** Instructions begin with clear Spanish support; English audio and English target-language text are primary. Native-language translations fade by demonstrated ability, never by an arbitrary time threshold. Learners can show translations at any time.
- **World structure:** Guided adventure with a visible primary storyline, meaningful optional choices, revisitable locations, and accessible alternative paths later. A0.0 itself is linear except for nonessential interactions.
- **Mascot:** Warm, witty traveling companion. Helpful, expressive, never condescending or relentlessly celebratory; no species/name is decided.
- **Speaking:** Optional **unscored** “Say it with me” practice. No microphone permission required, no speech-to-text, recording, or pronunciation grade for this slice.
- **Pedagogy:** Context before abstract grammar, no forced grammar lectures, meaningful errors and hints, no lives/energy penalties, story completion separate from language mastery.
- **Scope:** One polished onboarding-to-completion experience; episode A0.1 appears as next destination but is not playable in this slice.

## 1. Product promise and boundary
**Promise:** Learn English by living through small, everyday situations in a charming illustrated world. First action: introduce yourself to a companion; first outcome: understand and respond to a simple English greeting.

**Not in A0.0:** Trade selection, commute mechanics, corner store, open world, sign-in, payments, accounts, live AI dialogue, scored speech, full CEFR placement, backend, production adaptive review algorithm, or a full Spanish-learning pathway. No required mascot model beyond illustrated states.

**Definition of vertical-slice done:** A new Spanish-speaking user can start, configure support language/name, hear English, navigate all interactions, retry mistakes without punishment, request translations, optionally repeat speech aloud, finish the episode, see earned progress, refresh and resume, and return to the map without broken navigation.

## 2. Information architecture & world progression
The journey map is a persistent narrative overview, not a CEFR ladder. It displays unlocked location, completed locations, and two or more preview destinations. The first playable marker is **Hello, You!** A0.1 **Wake Up** is marked **Up Next** after completion; A0.2 **Breakfast**, A0.3 **Out the Door**, A0.4 **Get Moving**, **Corner Store**, **Around Town**, **New Opportunities**, and **Working Life** may be visible as art-directed previews, not clickable destinations. Clearly label inaccessible locations as previews and avoid fake interactions.

Current episode sequence:
`Welcome / language → Preferred name → Mascot introduction → Hello recognition → Build introduction → Good morning recognition → First dialogue → Farewell → Independent check → Completion / map`

Use progression model: `worldProgress` (chapter/episode/visited), `learningEvidence` (per outcome and hint dependence), `rewards` (first-hello badge). A user may complete with assistance; mastery must not automatically be asserted.

## 3. Specific learning objectives and language inventory
At the end of A0.0, a learner can attempt to:
- **LO-01:** recognize *Hello!* when heard and distinguish it from *Goodbye!*.
- **LO-02:** recognize *What's your name?* when heard clearly.
- **LO-03:** construct and use *I'm [preferred name].* as a self-introduction.
- **LO-04:** recognize *Good morning!* as a greeting appropriate to a morning setting.
- **LO-05:** recognize *Nice to meet you!* as a social response to an introduction.
- **LO-06:** choose *Goodbye!* as an appropriate farewell.
- **LO-07:** choose a suitable response to an unassisted greeting exchange, with replay allowed.

**Core assessed chunks:** `Hello!`, `Good morning!`, `What's your name?`, `I'm [name].`, `Nice to meet you!`, `Goodbye!`.

**Exposure-only chunks:** `See you later!`, `Tap`, `Listen`, `Continue`. Never grade exposure-only expressions as if mastered.

**Instructional guardrails:** Natural English audio; no one-to-one assumption that English word order maps to Spanish; do not evaluate name spelling or pronunciation. For all assessed items, the scenario must establish one defensible correct response. Maintain approved alternate responses when context permits.

## 4. Screen-by-screen interaction contract
Every screen needs: screen ID, goal, visible controls, audio, support text, entry/exit behavior, success/error/hint states. Mobile-first portrait; controls at least 44×44 CSS px; never rely solely on color or audio.

### S00 — Start / support language
- **Goal:** User understands this is an app for learning **English**, not a Spanish-language-learning game.
- **Content:** Headline `Learn English for real life.`; supporting sentence translated into selected UI language; `I speak...` picker initially offers **Español** and **English**. Target language is visibly `English` and is not independently selectable in this slice.
- **Controls:** Language picker, `Continue`, accessible audio preview optional.
- **Behavior:** Selecting Español changes setup/instructions immediately. Selection is editable later. `Continue` stores `supportLanguage` and enters S01.
- **No grade.** No text displayed only inside background art.

### S01 — Preferred name
- **Goal:** Personalize dialogue without grading text input.
- **English line:** `What's your name?` with play-audio control.
- **Spanish helper:** `¿Cómo te llamas?` plus a short instruction `Escribe el nombre que quieres que usemos.`
- **Controls:** Text input (`maxLength=32` characters), Continue, Back, play.
- **Validation:** Trim surrounding whitespace; require at least one visible character; reject control characters; escape interpolated text in rendering; do not infer/legal-name request. Allow unicode/accents. For audio, do not synthesize untrusted names into pre-generated voice in v1: visual personalization only; mascot can say `Nice to meet you!` in audio and show name in text.
- **No grade.** Store locally and let user edit under Settings.

### S02 — Mascot hello
- **Goal:** Introduce companion and recognize first English greeting.
- **Scene:** Bedroom corner with companion entering/waving. Companion says `Hello! I'm your new friend!` (exposure audio), then a speech chip emphasizes `Hello!`.
- **Translation:** On first exposure Spanish helper is visible (`¡Hola!`). Replay optional; repeated audio never penalized.
- **Controls:** Replay, optional `Say it with me` (play phrase, encourage learner to speak; no microphone), Continue.
- **No grade.** Advance after dialogue revealed; avoid long unskippable animation.

### S03 — Hello recognition
- **Goal:** LO-01.
- **Prompt:** Mascot says `Hello!`; learner sees two labeled speech-bubble choices `Hello!` and `Goodbye!`, each with symbolic illustration or icon where helpful.
- **Format:** A / contextual visual match.
- **Correct:** `Hello!`.
- **Error:** Friendly short response (`Not quite. That one's for leaving.`) plus translation if needed; retry with no lives removed.
- **Success:** Companion waves and replays phrase; `Continue` available.
- **Evidence:** firstAttemptCorrect, attempts, hintsUsed, replays.

### S04 — Introduce yourself
- **Goal:** LO-02 + LO-03.
- **Prompt:** `What's your name?` (audio, initially supported). Target response: `I'm [name].`.
- **Format:** B / two-tile sentence build, `[I'm]` + `[preferredName]`, with clear tap-to-build alternative to drag.
- **Correct:** Ordering tokens `I'm`, `name`. Name display is user-derived safe text; punctuation optional.
- **Error:** Demonstrate word sequence visually and allow retry.
- **Success:** Text bubble `Nice to meet you, [name]!` with audio `Nice to meet you!` (without name) to avoid on-demand TTS.
- **Optional speech:** `Say it with me` lets learner speak after playback; unscored, no recording.
- **Evidence:** LO-02 recognition exposure; LO-03 construction performance. Do not claim spoken production demonstrated.

### S05 — Good morning recognition
- **Goal:** LO-04.
- **Scene:** Dawn sunlight / clear morning inside room.
- **Audio:** `Good morning!`.
- **Format:** E / listen and select between sunrise and night-sky images. No native-language translation automatically shown on the independent response; hint control remains available.
- **Correct:** Morning / sunrise image.
- **Error:** `Morning means the start of the day.` / localized helper available, then retry.
- **Accessibility:** Images have descriptive alternate text; neither answer relies on color alone.

### S06 — First dialogue
- **Goal:** LO-02 and LO-03 transfer.
- **Audio:** Mascot `Hello! What's your name?`.
- **Format:** E / choose natural response between `I'm [name].` and `Goodbye!`.
- **Correct:** `I'm [name].`.
- **Translation:** Hidden initially, available by tap. Audio can be replayed at normal/slower speed. Hints recorded, not penalized.
- **Success:** Mascot `Nice to meet you!` (LO-05 exposure); brief reaction.

### S07 — Farewell
- **Goal:** LO-06.
- **Scene:** Companion stands near bedroom doorway and says `See you later!` (exposure-only).
- **Format:** contextual response choice.
- **Choices:** `Goodbye!` (correct), `What's your name?` (incorrect).
- **Feedback:** `Goodbye is something we say when leaving.`. Allow retry.

### S08 — Independent check
- **Goal:** LO-07 plus evidence for LO-02/LO-03.
- **Audio:** `Hello! What's your name?` (spoken once automatically; replay allowed). No automatic translation.
- **Format:** E / one response choice or short word-bank construction of `I'm [name].`; choose **one** form for implementation and use it consistently (recommended: word-bank assembly to test production-by-construction).
- **Hints:** Optional bilingual helper and slow playback. A hint-assisted correct answer still completes story, but evidence must label `assisted`.
- **Incorrect:** Supportive retry; after two wrong attempts give a guided demonstration. No lockout.

### S09 — Episode complete
- **Goal:** Celebrate an actual accomplishment, not imply CEFR proficiency.
- **Display:** `First Hello` badge, location marked completed on map, expressions encountered, prompts for review as needed, CTA `View journey`, secondary CTA `Replay episode`.
- **Story unlock:** `A0.1 — Wake Up` displayed as next destination (`Coming next` or non-playable until implemented). Never launch a blank screen.
- **Scoring:** `episodeComplete=true` on reaching S09; independent evidence tracked separately. No XP economy required for v1.

## 5. Interaction rules across all screens
- English phrase is visually prominent; Spanish instruction is distinct in a quieter helper treatment, not the main content.
- Auto-play spoken English **once per new phrase** when allowed by browser/user settings; if blocked, show large obvious play button and don't auto-skip.
- Playback controls: replay and optionally 0.8× speed; loading/failed audio states with accessible text. Sound-off mode must remain usable with text.
- Prompt submission pattern: user selects/constructs answer → presses `Check` → inline feedback appears → `Continue`; prevent accidental double submission.
- Hint pattern: `Need a hint?` reveals short Spanish support or contextual visual cue. Record hint usage. No negative points.
- Back: preserve previous responses; expose a confirmation only when leaving episode would discard unsaved work (progress is normally autosaved).
- Text should not appear baked into illustrations. UI owns all localization, progress, controls, and spoken-language captions.
- On reducing motion, skip celebratory transitions; screen readers have text labels; tappable objects have names and focus states.

## 6. Minimal durable content schema
Persist content separately from React views. Suggested TypeScript discriminated union:

```ts
type Locale = 'en' | 'es';
type ExerciseKind = 'visual_match' | 'word_order' | 'listen_choice' | 'context_choice';
type LearningObjectiveId = 'LO-01'|'LO-02'|'LO-03'|'LO-04'|'LO-05'|'LO-06'|'LO-07';
type LocalizedText = { en: string; es: string };

type AudioRef = {
  id: string;
  src: string;                // local asset path, e.g. /audio/a0-0/hello.mp3
  spokenLocale: 'en-US';
  transcript: string;
};

type Exercise = {
  id: string;
  kind: ExerciseKind;
  objectives: LearningObjectiveId[];
  prompt: LocalizedText;
  englishFocus?: string;
  audio?: AudioRef;
  options?: Array<{ id: string; label: string; imageSrc?: string; alt?: string }>;
  tiles?: Array<{ id: string; label: string }>;
  acceptedAnswers: string[][];  // answer option IDs or ordered tile IDs
  feedback: { correct: LocalizedText; retry: LocalizedText; hint: LocalizedText };
  allowReplay: boolean;
  allowSlowPlayback: boolean;
  optionalSayItWithMe?: boolean;
};

type Episode = {
  id: 'a0-0';
  title: LocalizedText;
  targetLanguage: 'en';
  objectives: LearningObjectiveId[];
  scenes: Array<{ id: string; sceneAssetId: string; exerciseId?: string; dialogueIds?: string[] }>;
  exercises: Exercise[];
  reward: { id: 'first-hello'; label: LocalizedText };
};

type ExerciseAttempt = {
  exerciseId: string;
  attempts: number;
  firstAttemptCorrect: boolean;
  completed: boolean;
  hintsUsed: number;
  replayCount: number;
  slowPlaybackUsed: boolean;
};

type LearnerProgress = {
  schemaVersion: 1;
  preferredName: string;
  supportLanguage: 'es'|'en';
  currentScreenId: string;
  completedEpisodes: string[];
  attempts: Record<string, ExerciseAttempt>;
  badges: string[];
  updatedAt: string;
};
```

Prefer actual per-exercise JSON objects with media IDs; never interpolate executable expressions from content. Internal `A0.0` corresponds to stable ID `a0-0`; no decimal numeric storage. English audio is real local media, not text-only placeholder at acceptance time.

## 7. Audio & localization content contract
**Required English audio IDs** (separate, reusable assets):
- `en.hello` — “Hello!”
- `en.good_morning` — “Good morning!”
- `en.whats_your_name` — “What's your name?”
- `en.im` — “I'm…” (only if useful; visual name should not pretend audio said it)
- `en.nice_to_meet_you` — “Nice to meet you!”
- `en.goodbye` — “Goodbye!”
- `en.see_you_later` — “See you later!”
- `en.hello_whats_your_name` — “Hello! What's your name?”
- `en.im_your_new_friend` — “Hello! I'm your new friend!”

**Audio production:** One consistent companion voice; understandable US English pronunciation, friendly adult delivery, no caricature. Normalize loudness and trim leading silence. Export production-safe formats (e.g. MP3 plus optional OGG); map IDs to paths. A licensed TTS source is required. Never depend on a secret TTS API key in the browser.

**Translation behavior:** UI and instruction strings localized via structured resources, not in art. Onboarding has proactive Spanish help. Later A0.0 English prompts favor audio+English, with native-language help discoverable on demand. Track hint use but do not hide help. An accessibility setting can keep bilingual display always on.

## 8. Progress, review, and feedback
**Episode completion:** Reaching S09 after completing all required learning interactions, with unlimited retries and hints.

**Independent evidence:** `firstAttemptCorrect && hintsUsed === 0` for selected objective probes; replay is allowed and not a failure. `needsReview` if assessment is assisted or incorrect at first independent attempt. This is a **heuristic for targeted review**, not certification, and speaking remains unscored.

**Review queue:** In v1 store objective IDs requiring review; surface a simple “Practice these again” option at completion. Do not build spaced-repetition scheduling engine until later.

**Rewards:** First completion awards `first-hello`; no rewards tied to money, streak penalties, loot boxes, or emotional manipulation.

## 9. App and technical acceptance criteria
1. Fresh user launches at S00, with target English unmistakable.
2. Spanish selection localizes directions; English learning phrases remain in English.
3. Preferred name appears safely in personalized text and remains after refresh.
4. Mascot audio plays on user request, with graceful handling of autoplay restrictions.
5. Each required exercise has clear correct/incorrect feedback and a retry path.
6. At least two exercise types work with true data-driven renderers; preferably all four used by this episode. **Five-format engine** is eventual platform goal, but Format C and Format D need not appear artificially in A0.0.
7. Hints and audio replay are usable at any time without reducing story progress.
8. User can leave/return and resume near the last interaction from local storage.
9. Completion unlocks visible map progression, awards badge once, and exposes replay.
10. Screen works at ~320px viewport width, common mobile viewports, and desktop; no overflow or text embedded in images.
11. Keyboard/screen reader alternatives exist for taps, choice grids, and word arrangement; reduced-motion supported.
12. No placeholder links/buttons pretending to function. No unapproved backend or account requirement.
13. Tests cover answer validation, resume/reload, language toggling, accessible names, and assisted vs independent evidence.

## 10. Implementation tickets (ordered)
1. Build app shell, localization resources, saved settings, screen state and journey map container.
2. Implement onboarding S00–S02 using art dossier composition and actual English clips.
3. Implement data-driven exercise renderers for S03–S08 plus reusable Check/Feedback/Continue shell.
4. Implement episode-complete screen, local persistence, objective evidence, map state and `First Hello` reward.
5. Accessibility, small-screen layout, media failure handling, mobile browser QA, polish.

**Agent handoff format:** For each ticket, report files changed, what works, what failed, tests performed, screenshots, deviations from specification, and next task. Request approval before deviating from locked rules.

## 11. Open decisions — intentionally NOT locked
- Final brand name and logo
- Final mascot species, name, silhouette and voice casting
- Exact art palette and typography choices (to be approved in separate art dossier)
- Broader language support and locale variants
- Full journey layout after A0.1, career tracks, monetization, login

Do not convert open decisions into assumptions. Use explicitly labeled placeholders in the build, without shipping AI-generated text baked into UI backgrounds.