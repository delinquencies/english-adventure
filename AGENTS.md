# AGENTS.md — English Adventure

> **Repository operating contract for Codex and any other code-writing agent**  
> **Status:** Active implementation authority for the first vertical slice  
> **Product name:** TBD. **Never use “TradeLingo” in user-facing copy, identifiers, titles, or branding.**  
> **Initial product:** Mobile-first English-learning narrative adventure for Spanish-speaking beginners  
> **First deliverable:** A playable, beautiful, accessible **A0.0 — Hello, You!** episode and a useful journey map.

---

## 0. Read this before doing anything

You are the **lead engineer**, not an autonomous product manager or art director. Your job is to turn an approved learner journey into excellent functioning software, preserve the creative direction, and make progress in small verifiable increments. **Do not build a generic Duolingo clone. Do not replace the illustrated world with a quiz dashboard.**

**Read order:**
1. `AGENTS.md` (this file)
2. `docs/GAME_RULEBOOK.md` (or the same file at project root) — **canonical gameplay, curriculum, progress and learning rules**
3. `docs/A0_0_PRODUCT_AND_CONTENT_CONTRACT.md` (or the same file at project root)
4. `docs/ART_DIRECTION_DOSSIER.md` (or the same file at project root)
5. Existing source, package manifests, README, assets, and tests.

If any document or asset is missing, record it in `docs/DECISIONS.md` and proceed with a clearly labeled, reversible fallback where possible. **Never claim a document, asset, voice, or test exists without checking.**

### Decision precedence when sources disagree
1. Explicit latest product-owner instruction in the current task.
2. `GAME_RULEBOOK.md` for cross-product game, curriculum, localization, and assessment rules.
3. A0.0 product/content contract for episode-specific sequence, text, interaction, and validation.
4. Art dossier for visual execution.
5. This `AGENTS.md` for engineering procedure and scope.
6. Existing code and prototype behavior.
7. Your engineering preferences.

**Resolved changes since the older documents:**
- **The companion mascot IS THE FEMALE PROTAGONIST'S DOG.** Do not create or substitute a cat, fox, raccoon, imaginary creature, or arbitrary pet. The specific dog appearance, name, and breed are **not yet approved**. Provide a clearly marked temporary dog placeholder only if necessary; make it easy to replace without code rewrites.
- The supplied **female protagonist character sheet** (green jacket, gray hoodie, backpack; three poses) and **warm bedroom illustration** are visual references. The generated **matching kitchen** is reference material for a later episode. Do not assume the learner must have this fixed avatar forever; customizable avatars are out of scope.
- The newer, **restrained Western storybook** direction is authoritative; the earlier anime-like, high-gloss, lavender/gold mockups are inspiration for polished progress and map delight, **not** the art style to reproduce.
- **English is always the target language** in this first release. Spanish is the initial support/interface language. The setup must never accidentally imply the user is learning Spanish.
- **Speaking aloud is optional and unscored**. The MVP can offer “Say it with me” with playback and a pause for repetition. No microphone permission, recording, speech recognition, scores, or pronunciation claims.
- **A0.0 ends with a completed introductory exchange and the A0.1 preview**. Do not prematurely implement the full kitchen, commute, corner store, interviews, or vocational branches.

---

## 1. The product we are building

**One-sentence promise:** *Learn English by living a life in it.*

The learner begins a charming everyday adventure. They meet a witty dog companion, wake in a sunlit bedroom, say hello, learn basic phrases through small situations, and see the wider world on a journey map. Future episodes naturally lead through getting ready, breakfast, commute, shopping, neighborhood interactions, job interviews, and career-specific environments.

**Core experience loop:**
`Enter place → encounter understandable situation → hear/see English → act/respond → receive useful feedback → progress in story → revisit in review`.

The application should feel **like a premium, playable illustrated adventure with pedagogically useful interactions**. The interface must support the world rather than obscure it.

### Who this serves
Adults learning practical English, initially with Spanish-language support. They deserve respectful, readable, modern visuals—never childish or stereotyped treatment. Everyday language comes before job-specific specialization, but future learners with existing ability will have a placement/skip path (not part of this slice).

### Locked pedagogy
- **Trojan-horse grammar:** teach useful phrases in situations, without forced grammar lectures.
- **Progressive immersion:** show Spanish support for novel A0 phrases; increasingly show English first; learner can always reveal translation on demand. Do not fade support by an arbitrary timer or silently remove it.
- **Guided adventure with optional choices:** story path is clear; side actions are optional and nonblocking. First slice is mostly linear.
- **Mistakes are recoverable:** hints, replay, retry; no lives, stamina penalties, shame, or forced grinding.
- **Completion ≠ mastery:** story can be completed with help; record independent first-attempt understanding separately.
- **Context beats answer-string matching:** accept sanctioned alternatives and never force an ambiguity to be “wrong.”
- **Audio is foundational:** meaningful English lines can be heard and replayed; also keep readable text and accessibility alternatives.

---

## 2. The vertical slice: exact boundaries

**Shippable demonstrator:** a user on a real phone can open the app, choose Spanish as the language they speak, enter a preferred name, meet the dog companion, hear/replay English phrases, complete an intro exchange with nonpunitive feedback, optionally repeat aloud, finish the episode, view a visible accomplishment, and return to a navigable illustrated map. Refreshing does not erase completion.

### Episode screens — canonical IDs
| ID | Interaction | Learning / behavior | Required completion |
|---|---|---|---|
| `S00` | Welcome + support language picker | Target language clearly English; Spanish and English as support-language options | Continue |
| `S01` | Preferred name | `What's your name?`; unicode-safe local name input; no spelling grade | Valid nonempty preferred name |
| `S02` | Dog-companion hello | `Hello! I'm your new friend!`; audio + optional translation; unscored repeat-aloud | Continue |
| `S03` | Recognize greeting | Audio `Hello!`; choose Hello vs Goodbye | Correct after any retries |
| `S04` | Build self-introduction | `What's your name?` → arrange `I'm` + `[name]` | Correct ordering after retries |
| `S05` | Recognize morning greeting | `Good morning!` → morning image vs night image | Correct after retries |
| `S06` | Short dialogue | Recognize suitable response in context | Correct after retries |
| `S07` | Farewell | `Goodbye!`; contextual choice, `See you later!` exposure only | Correct after retries |
| `S08` | Independent check | `Hello! What's your name?` → `I'm [name].`; English first, help on request | Answer, assisted allowed |
| `S09` | Episode complete + map | First Hello reward; shows learned phrases and A0.1 Wake Up preview | Save completion |

**The detailed per-screen content, distractors, localized feedback, learning outcomes, and conditions live in `A0_0_PRODUCT_AND_CONTENT_CONTRACT.md`.** Do not invent new exercise requirements where that document is explicit. If the full contract has exact variants, follow it over the shorthand table above.

### Six assessed language chunks
`Hello!` · `Good morning!` · `What's your name?` · `I'm [name].` · `Nice to meet you!` · `Goodbye!`

Exposure only: `See you later!` and icon-supported interaction verbs such as `Tap`, `Listen`, `Continue`. No vocabulary score for exposure-only words.

### In scope
- Functional mobile-first **PWA-friendly web application** (do not over-engineer installability).
- Real programmatic text and functional controls over illustrated scene assets.
- Reusable dialogue, prompt, option, hint, audio, feedback, completion, map components.
- Local JSON/TS curriculum content and deterministic answer handling.
- Local storage for preferences, episode progress, hint use, first attempts, and reward.
- Graceful audio availability state and safe static fallback assets.
- Scrollable illustrated map with accurate **completed / current / upcoming / locked** states, one playable episode only.
- Reduced-motion behavior, keyboard-accessible interactions, reasonable mobile touch targets.

### Explicitly out of scope
Authentication, accounts, payments, database/Supabase, live LLM characters, speech-to-text, pronunciation scoring, analytics SDKs, CEFR certification, full placement test, teacher dashboards, career tracks, branching story engine, kitchen gameplay, commute gameplay, internationalized payment systems, production-grade adaptive spaced repetition, multiuser sync, and a native mobile app.

**No invented “energy” mechanic, punitive hearts, purchase screen, or premium gating.** Rewards should be meaningful and modest: first conversation, learned phrases, small map progression.

---

## 3. Visual standards — high fidelity without fake interfaces

### Nonnegotiable art direction
- Contemporary **Western storybook/editorial casual game** aesthetic, grounded adult proportions, restrained expressions, clean fine outlines, warm daylight, tactile real-world objects, natural materials, nuanced shadows.
- Scene reference: supplied beige sunlit bedroom with clear door, window, shoes, dresser, coat, bed and generous negative space.
- Protagonist reference: illustrated woman with curly hair, green jacket, hoodie, backpack, dark pants. She is a visual reference character, not a prompt to infer the player's real identity.
- Companion is **her dog**; exact look is pending. Do not approve an invented design on behalf of the owner.
- Illustrated map is emotionally central: visible milestones, recognizable destinations, coherent winding route, completion states, and a sense of what is ahead.
- Avoid anime, chibi, giant sparkling eyes, gacha-like UI, fantasy glow, candy-gradient overload, heavy beveled/3D controls, sticker clutter, and corporate stock-vector flatness.

### Split artwork from UI
Treat every screen as three layers:
1. **Environment art**: text-free illustration (bedroom or illustrated map).
2. **Character art**: separate transparent sprites, consistent anchored position.
3. **Live interface**: accessible DOM/React/CSS/SVG for all dialogue, prompts, buttons, translations, options, feedback, progress and badges.

**Never ship a screenshot/mockup as one flat image with fake unclickable controls.** Never bake English text, Spanish translation, progress bars, or buttons into background images. Hotspots must correspond to visible objects, not random broad rectangles.

### Reference asset handling
If the original files are available, inspect and reuse them as reference/backdrop assets, avoiding artificial restyling. Known conversation export filenames may include:
- `1794537231743.jpeg` — protagonist character sheet
- `1794537244339.jpeg` — original bedroom
- `sunlit_cozy_kitchen_breakfast.png` — later-episode kitchen reference
- `a_clean_composite_promotional_mockup_of_a_language.png` — modern UI/map mood reference only

**Paths are not guaranteed inside a future repository. Discover and verify before use.** If only flattened art exists, use image + semantic positioned hotspots for the first slice; isolate layers later. Keep hotspot coordinate data outside visual components for easy refinement. Aspect-correct scaling and focal point preservation are mandatory. Do not crop out target objects on small screens.

### Design token starter set — proposed, not sacred
```css
:root {
  --paper: #FFF9EF;
  --surface: #FFFFFF;
  --ink: #263342;
  --muted: #647385;
  --primary: #27836B;
  --primary-pressed: #17614E;
  --gold: #F4B94D;
  --coral: #F27E65;
  --sky: #BFE5F3;
  --border: #D8E2E5;
  --success: #247A5C;
  --retry: #A75B36;
}
```
Use CSS variables/tokens, not scattered literal colors. Prioritize tested contrast over preserving any proposed hex. Choose **one** UI display family (e.g. Nunito Sans or Plus Jakarta Sans) and **one** readable body family (e.g. Inter or Atkinson Hyperlegible). Use lawful font delivery; never bundle proprietary fonts without license. No heavy animated gradients. Favor clean, calm, premium, human-scale composition.

### Responsive/interaction standards
- Mobile-first at ~360px wide, test 320px and 390px, tablet and desktop without broken scene geometry.
- Primary targets minimum **44×44 CSS px**, visible focus, pressed, selected, disabled and feedback states.
- UI must remain usable with zoom / dynamic text where feasible; avoid layout overflow in translated Spanish content.
- Text overlays must not cover answer objects. Use bottom sheets for dense exercise controls when appropriate.
- Reduced-motion preference respected. No mandatory motion or long unskippable intro.
- Prefer subtle 160–260ms transitions and a restrained reward moment over constant effects.

---

## 4. Engineering architecture: simple, durable, swappable

### Start by inspecting the actual repository
Run appropriate lightweight discovery commands: `pwd`, `ls`, package manifest, tree of source/assets, current status. **Do not assume the project has already been initialized.** If a reusable React/Vite project exists, extend it. If no suitable project exists, propose and create a straightforward **React + TypeScript + Vite** mobile-first application only within approved task scope.

**Don't introduce** Next.js, Redux, GraphQL, Supabase, Firebase, a game engine, or complex state-machine libraries just because you can. Add dependencies only when concrete requirements justify them; explain changes.

### Preferred folder shape (adapt to existing repository rather than wrecking it)
```text
.
├── AGENTS.md
├── docs/
│   ├── A0_0_PRODUCT_AND_CONTENT_CONTRACT.md
│   ├── ART_DIRECTION_DOSSIER.md
│   ├── DECISIONS.md
│   ├── TASKS.md
│   └── QA_CHECKLIST.md
├── public/
│   ├── art/
│   └── audio/
├── src/
│   ├── app/                 # routing / application shell
│   ├── components/          # buttons, dialogue, progress, feedback
│   ├── scenes/              # bedroom, journey map
│   ├── exercises/           # exercise renderers / validators
│   ├── content/             # A0.0 exercise data / localized strings
│   ├── audio/               # audio catalog + playback abstraction
│   ├── state/               # progression and persistence
│   ├── styles/              # tokens and responsive layout
│   └── test/                # unit and flow tests
└── package.json
```

### Keep data, logic and rendering separate
- Curriculum item is structured data: stable IDs, learning objective, prompt, localization keys, audio reference, answers, alternatives, feedback, hints, scene target, next action.
- React renders from data rather than hardcoded lesson copy in screens.
- Answer validation is pure, separately testable logic. `correct` / `incorrect` must not be determined by translated labels or array position.
- Episode navigation is a finite, enumerated set of known states (`S00` ... `S09`) with guarded transitions; resist scattering screen progression across component-level booleans.
- Scene hotspots have stable IDs, coordinates/geometry, labels, and logical targets. Keep geometry separate from copy.
- Locale changes operate through a typed string catalog with English target phrases distinguishable from Spanish support copy.
- Audio uses stable asset IDs, a centralized play/replay adapter, and a graceful unavailable fallback. The app may not depend on a paid TTS call at render time.
- Use pre-generated voices when real audio becomes available. Until then, **mark audio as provisional**. Browser `speechSynthesis` can be an explicitly labeled dev fallback if suitable, never pretend it is licensed studio audio.

### Suggested domain types (illustrative, adapt to source contract)
```ts
type EpisodeScreenId =
  | 'S00' | 'S01' | 'S02' | 'S03' | 'S04'
  | 'S05' | 'S06' | 'S07' | 'S08' | 'S09';

type SupportedLocale = 'es' | 'en';
type ExerciseKind = 'visual-match' | 'sentence-build' | 'fill-blank'
  | 'tone-choice' | 'listen-respond';

type LearningEvidence = {
  objectiveId: string;
  attempts: number;
  firstAttemptCorrect: boolean | null;
  hintsUsed: number;
  audioReplays: number;
  completed: boolean;
};

type EpisodeProgress = {
  episodeId: 'A0.0';
  currentScreen: EpisodeScreenId;
  completed: boolean;
  updatedAt: string;
  evidence: Record<string, LearningEvidence>;
};
```
The full content contract wins over this illustrative shape. Use explicit versions for stored data; migrate or reset safely when schema changes.

### Store only what is needed
- Save support language, preferred name, A0.0 progress/evidence, and completion locally with a versioned storage key.
- Don't collect date of birth, real identity, location, microphone recordings, employment or immigration data.
- Escape/safely render user-supplied names; reject control characters and whitespace-only values; allow accents and non-English characters.
- Never place secrets in client code or repository. Do not use network requests for content that can be bundled with the slice.
- Handle private/incognito/local storage failures without crashing.

---

## 5. The curriculum engine: enforce observable learning

### Five formats (system-wide; use only those needed in A0.0)
- **A — Visual Match:** match image/context with vocabulary.
- **B — Scrambled Sentence:** construct phrases using tappable or draggable tokens; **tap is always an available alternative**.
- **C — Fill-in-the-Blank:** select missing word in context.
- **D — Tone Translation:** choose situationally professional/polite language (primarily later levels).
- **E — Listen & Respond:** comprehend authentic voice and act/respond.

A0.0 does not have to force all five formats into ten screens. Use the approved A0.0 content contract. **No gratuitous complexity.**

### Assessment behavior
- Every graded interaction has one clear target objective and defensible contextual answer(s).
- Feedback is specific, kind, brief and useful. Correct and retry states are visible through text and icon as well as color.
- Correct answer advances only after user understands/presses Continue; wrong answer offers retry, optional hint, and audio replay.
- Log first attempt separately from eventual completion; retries are unlimited.
- Asking for translation or replay is allowed and never blocks story progression.
- **“Say it with me” is exposure/rehearsal**, not proof of spoken proficiency; no measured pronunciation success.
- Record skill evidence granularly. Do not display formal CEFR certification or claim “fluent” from onboarding.
- Only one independent assessment should be marked as independent if completed without hint; the learner may still continue when assisted.

### Localization behavior
- The English target phrase is visually and acoustically primary.
- Spanish support is initially visible where A0.0 requires, and optional on later/independent prompts.
- Provide a consistently placed **Translate / Show meaning** affordance throughout the game.
- User can opt back into always-visible translations later; never trap them in immersion.
- Switching support language never changes English exercise correctness or target content.
- Do not hardcode flag icons as the sole marker of language; use names like `Español` and `English`.

### Audio behavior
- Every speech interaction shows who is speaking and permits replay.
- Replay does not reset attempts or cause multiple overlapping playbacks; stop prior clip when playing a new one.
- Respect a device's mute/autoplay restrictions. Provide a tappable play action if autoplay fails.
- Audio failures never softlock the story. For audio-specific exercises, provide a visibly identified accessibility/support fallback and record that the item was assisted, not independently heard.

---

## 6. Journey-map contract

The map is **not** a collection of arbitrary decorative badges. It should feel like a place with continuity and visible future possibilities.

**Required world markers:** `Hello, You!` (current / completed), `Wake Up` (next / preview), `Breakfast`, `Out the Door`, `Get Moving`, `Corner Store`, `Around Town`, `New Opportunities`, `Working Life` (later previews/locked). Display accurate statuses, even if the map art is only a single illustration.

**Required behavior:**
- Scroll/pan comfortably on mobile while maintaining accessible labels and controls.
- Mark current destination distinctly; completion is visible and persists.
- Show at least one appealing next destination and an intelligible route connecting milestones.
- Selecting current/completed A0.0 opens/resumes/replays it as applicable.
- Selecting locked destinations gives an informative non-deceptive preview, not broken navigation.
- Never fabricate star totals, learning history, streaks, or proficiency achieved. Use data-backed values only; the first-run experience should realistically start with zero achievements.

If assets are not suitable for a final polished map, build a clean interactive path over provisional/illustrated background and list **art dependencies** explicitly. **Functional statefulness matters more than a fake highly polished static map.**

---

## 7. Agent boundaries / change control

| Role | Owns | Must not silently change |
|---|---|---|
| Product owner (human) | Product identity, final creative and feature approvals | — |
| ChatGPT product/curriculum | Contract, pedagogy, task definition, QA criteria | Approved gameplay arbitrarily |
| Gemini / visual generation | Concept art, polished production assets, export references | App architecture / learning sequence |
| **Codex (you)** | Working app, components, tests, performance, integration | Naming, curriculum objectives, mascot identity, approved art style |

**Only one lead engineer writes the integration branch.** If multiple agents are used later, give them distinct branches/isolated files and require review. Do not have competing agents rewrite the same app shell.

Use `docs/DECISIONS.md` for explicit decisions and assumptions; distinguish `APPROVED`, `PROVISIONAL`, `NEEDS OWNER`. Do not falsely label your design tastes as product approvals.

### A task is accepted only if
1. It works (not just compiles).
2. It matches the approved user behavior and learning objective.
3. Its UI is usable on a small phone and with keyboard/touch.
4. It gracefully handles a wrong answer, missing audio, reload/resume and any relevant error states.
5. Tests/checks that exist run; new critical logic gets tests.
6. No unrelated scope expansion, broken flows, or stealth redesign occurred.
7. Changed files and limitations are documented.

---

## 8. Work sequence: small pull-request-sized tickets

### Phase 0 — Audit & set up (first task; do not skip)
- Inspect repository, dependencies, source, art and specs.
- Start app if possible; capture the current state (text summary and screenshots if tools permit).
- Compare against the approved A0.0 flow and list existing reusable components.
- Create/update `docs/TASKS.md`, `docs/DECISIONS.md`, `docs/QA_CHECKLIST.md`.
- Identify missing assets, explicitly noting **dog art still not approved**.
- **Do not immediately rebuild everything.** Propose smallest path to a usable foundation, and implement only the first approved ticket.

### Phase 1 — Interactive skeleton
- Make a functioning mobile shell, English-learning welcome, support-language picker, preferred-name input.
- Implement A0.0 screen transitions and resume semantics with temporary visual elements where necessary.
- Ensure clear Back, Continue, Skip only where the contract permits.

### Phase 2 — World and companion
- Integrate original bedroom art with correct aspect ratio.
- Add separate dog companion slot with temporary dog art if approved production art is unavailable; don't fabricate a locked character design.
- Build reusable dialogue overlay, hint/translate, and audio control.
- Avoid covering shoes, coat, door or other semantic objects with UI.

### Phase 3 — Real lesson
- Implement A0.0 data and validated S03–S08 interactions from contract.
- Add retries, first-attempt evidence, assisted states, and optional unscored repetition.
- All text localization/target language from structured content.

### Phase 4 — Journey and rewards
- Implement accurate scrollable illustrated map, episode completion, first-hello reward, next-stage preview, replay/restart and refresh persistence.
- No arbitrary fake XP or streaks.

### Phase 5 — Polish and QA
- Visual pass against approved references: clean outlines/scene art, not anime, not overly glossy.
- Test actual phone viewport widths; keyboard, screen readers where practical, reduced motion.
- Validate content, transitions, fallback states, and responsive geometry.
- Produce a demo-ready build with clear launch/preview instructions.

**No phase automatically authorizes work on the next one.** Complete the assigned task, report, then stop unless instructed otherwise.

---

## 9. Quality and testing gates

### Minimum functional tests
- New user starts in `S00`; visible English target and usable Spanish selection.
- Preferred name is accepted with accents, rejects blank/control-only input, renders safely.
- User can go Back without losing entered data.
- Intro English audio can be initiated/replayed or gracefully falls back.
- Correct answer gives positive feedback and transitions only when requested.
- Incorrect answer shows context-specific feedback, permits retry, and never deducts energy.
- Exercise answer validity is stable regardless of answer position or UI language.
- `S04` reflects the preferred name safely in the sentence.
- `S05` uses a distinct morning vs night cue; both are accessible.
- `S08` is independently trackable; showing a hint records an assisted attempt.
- Optional speaking requires no microphone permission and grants no performance score.
- Completing `S09` persists; reload restores map and completion correctly.
- Locked map nodes never route to nonexistent episodes.
- Changing support language does not change lesson target from English.
- Broken/missing audio does not freeze navigation.

### Minimum visual/accessibility tests
- 320, 360, 390px mobile widths; a larger mobile and desktop.
- No horizontal overflow; text remains readable; buttons 44px minimum.
- Interaction object hotspots align after resizing; target not hidden under overlays.
- Contrast and focus states meet practical WCAG AA goals.
- Screen-reader labels for icons/audio/scene interactions.
- Reduced motion avoids mandatory animations.
- Spanish helper lines are complete and fit the layout.
- Check on real device/browser when available; distinguish simulated tests from real-device tests.

### Verification commands
Use **whatever commands are actually defined** in the existing package; do not invent scripts. Usually `npm run dev`, `npm run build`, `npm run lint`, `npm test`. If scripts are missing, report honestly; add only justified scripts. Do not report `PASS` without having run the check.

---

## 10. Operating discipline

### Before implementing
Return a brief task plan: `Goal`, `Relevant requirements`, `Files likely affected`, `Acceptance test`, `Risks/missing inputs`. If a dependency is unresolved, prefer a non-destructive fallback and document it rather than turning the app into a different product.

### While implementing
- Keep diffs focused. No unrelated refactors or dependency churn.
- Reuse working code; don't delete an existing prototype without inspection.
- Preserve routes/styles/assets unless the ticket explicitly replaces them.
- Favor accessible semantic components and explicit types over clever abstractions.
- Never write secrets, fabricated content, or fake analytics into source.
- If code/tooling failures arise, investigate and fix the root issue within ticket scope.
- Make assumptions visible; do not get stuck endlessly discussing minor choices.

### At handoff — mandatory report format
```text
TASK: <short name>
STATUS: COMPLETE | PARTIAL | BLOCKED

IMPLEMENTED
- <observable behavior>

FILES CHANGED
- <path>: <why>

VERIFIED
- <exact command/test and result>
- <viewports or interactions actually checked>

DECISIONS / ASSUMPTIONS
- APPROVED: ...
- PROVISIONAL: ...
- NEEDS OWNER: ...

KNOWN LIMITATIONS
- <missing audio/art/device validation/etc.>

NEXT RECOMMENDED TICKET
- <one small, bounded task>
```

A screenshot is useful evidence but never substitutes for working interactions. A beautiful mockup is not a complete ticket. **Never claim that a static image, unverified command, or placeholder asset fulfills the final acceptance criteria.**

---

## 11. Immediate assignment for the next Codex session

**TASK CODE: `EA-001 — REPOSITORY AUDIT AND FIRST PLAYABLE SHELL`**

**Objective:** Inspect the existing repository and build (or stabilize) the smallest app that can run and move through `S00 → S01 → S02` while making the full `S00–S09` flow an explicit, testable plan. Do not implement the entire game in one pass.

**Required actions:**
1. Verify the source files, dependencies, scripts, and available art/contract documents.
2. Record divergences and missing files. Explicitly note that the companion is the protagonist's dog and approved breed/name/art are pending.
3. Start from existing React/Vite design if compatible; otherwise use React + TypeScript + Vite with minimal dependencies.
4. Make the welcome screen unmistakably about **learning English**. Let a learner select Spanish support, then enter a preferred name.
5. Add a first companion encounter screen with an unmistakably **temporary dog illustration placeholder** where necessary and functional text/dialogue controls. Do not substitute another species.
6. Define guarded transitions plus versioned local persistence; refresh must not destroy the user's selected language or name.
7. Make layout functional at mobile width and visually aligned to the approved Western art direction. Prioritize clean live UI and source assets over elaborate effects.
8. Add focused tests for name validation, language selection persistence, and transitions (using suitable test tools already installed or justified minimal additions).
9. Update task tracker, decisions, and QA checklist; hand off with actual verification outcomes.

**Success criteria:** A developer can run the app locally, choose `Español`, submit a preferred name, see the dog companion greeting in an accessible screen, go Back/Forward without losing choices, and refresh without resetting onboarding data. No broken controls, fake achievement totals, or unauthorized features.

**Stop after EA-001 and report.** The next engineering ticket should add real episode content and audio with a crisp acceptance checklist, not an unbounded request to build the rest of the product.

---

## Final reminder

Our competitive advantage is **English learned through a living, characterful, beautiful world**. Keep this promise intact at every layer. Do not sacrifice learning clarity for decoration, do not sacrifice delight for generic quiz components, and do not sacrifice working software for static visual fidelity.

**Build one authentic, exceptionally good five-minute experience. Then expand.**