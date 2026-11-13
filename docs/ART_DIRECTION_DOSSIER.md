# English-Learning Adventure — Art Direction Dossier
**Status:** Proposed visual production standard for approval  
**Version:** 1.0 · 2026-11-12  
**Reference:** Recent approved Western-style mobile app mockups; not a license to recreate image text as raster UI.  
**Scope:** A0.0 vertical slice first, extensible to neighborhood / commute / corner store / careers.

## 1. The visual north star
**A premium Western illustrated casual adventure game that happens to teach English.** Optimistic, characterful, mature enough for adult learners, inviting across different cultures, and readable on an ordinary mobile phone. The world should look worth exploring and the journey map should make progress emotionally satisfying.

**Descriptors:** storybook warmth, contemporary editorial character illustration, Western mobile casual game polish, crisp UI, sunlit everyday environments, expressive but grounded, tactile objects, inviting neighborhoods, deliberate visual hierarchy.

**Avoid:** anime facial grammar, manga speed lines, gacha-game motifs, chibi proportions, exaggerated kawaii eyes, Japanese school-life visual shorthand, heavily cel-shaded JRPG artwork, pixel-art nostalgia, generic corporate stock-vector people, overly childish preschool shapes, excessive gradients/gloss, neon cyberpunk, three-dimensional plastic toy rendering, stereotyped immigrant imagery, flags as the sole language identifier.

The audience is primarily adult English learners. Playfulness should **not** make the learner feel like a child.

## 2. Visual architecture — keep artwork and UI distinct
Three independent layers per screen:
1. **World art:** Illustrated, localized-neutral scenes and objects (raster/vector assets without copy).
2. **Character art:** Separate transparent PNG/WebP sprite layers / expressions and optional Rive/Lottie animations.
3. **Application UI:** Real React/CSS/SVG components for all English copy, translations, progress, buttons, option labels, achievement data, captions, hints, and navigation.

**Nonnegotiable:** No text, stars, badges, progress, or clickable buttons baked into scene illustrations. Designers may show them in mockups but production exports must isolate layers. No single flattened mockup is a shippable game screen.

## 3. Proposed color system (hex; tokens, not paint-by-numbers)
These are an initial reproducible palette, to be tested against real screens and accessibility contrast before locking final values.

| Token | Hex | Use |
|---|---|---|
| `paper` | `#FFF9EF` | Warm app background |
| `surface` | `#FFFFFF` | Cards, answer options |
| `ink` | `#263342` | Main typography |
| `muted` | `#647385` | Secondary text |
| `forest` | `#27836B` | Primary CTA, earned progress |
| `forest-dark` | `#17614E` | Pressed/contrast alternative |
| `gold` | `#F4B94D` | Rewards, sunlight, highlights |
| `coral` | `#F27E65` | Character accents, playful warmth |
| `sky` | `#BFE5F3` | Bright daytime backgrounds |
| `blue` | `#508DB9` | Travel, navigation, alternate UI accents |
| `lavender` | `#A49ACB` | Soft supporting accents |
| `outline` | `#D8E2E5` | Subtle component outlines |
| `feedback-good` | `#247A5C` | Correct feedback (also use icon/text) |
| `feedback-retry` | `#A75B36` | Try again (also use icon/text) |

**Usage ratio:** 65% light neutral surfaces, 20% quiet world illustration tones, 10% forest/blue UI actions, 5% reward accents. Scene palettes may vary by time/location while app chrome remains consistent. Verify text contrast to WCAG AA for normal text; accents alone must not communicate correctness.

## 4. Typography (license-safe, accessible)
- **UI headings:** `Nunito Sans` bold/extra-bold or `Plus Jakarta Sans` bold. Test both in actual components; choose **one** heading family, not a carousel of fonts.
- **Body / exercise text:** `Inter` or `Atkinson Hyperlegible`, with preference for clear letterforms and accessibility.
- **Optional expressive display:** A minimal, restrained headline treatment only on location titles; do not use script fonts for lesson content.
- **Type scale:** Mobile hero 28–32px; major screen heading 24–28px; prompt 21–25px; body 16–18px; labels 13–15px. True responsive styles, do not rasterize headings.
- **Line lengths:** prompt roughly 25–40 characters per line where possible; maintain comfortable line height and truncation-free Spanish layouts.
- Avoid childlike bubble lettering and overuse of uppercase.

## 5. Component design language
- Rounded rectangles: 14–20px radii for cards, 12–16px for buttons; small pill chips for progress/status, not everywhere.
- Buttons: confident solid forest primary, warm light secondary, clear pressed and focus states; min 44×44px interaction area.
- Shadows: restrained soft ambient shadows; no stacks of exaggerated floating cards.
- Borders: 1–2px quiet neutral with accessible selection outline.
- Prompts: highest hierarchy; supporting-language translations smaller and lower-emphasis, never equal in dominance to English target phrase.
- Dialogue: speech bubble logically anchored near speaking character, but avoid covering interaction objects; for small screens use a lower overlay panel.
- Correct feedback: small celebratory motion, affirmative sound where enabled, friendly text. Retry feedback: nonpunitive, no red full-screen fail state.
- Motion: 160–260ms UI feedback, gently looped mascot idle, 450–700ms reward payoff; obey reduced motion.

## 6. World art bible
**Rendering:** high-resolution 2D digital illustration, editorial/storybook edge control, subtle visible texture on surfaces, softly modeled shapes, realistic everyday object proportions, warm natural shadows, simplified but recognizable architecture.

**Perspective:** Scenes use a consistent 3/4 slightly elevated viewpoint where useful, with some eye-level character dialogue compositions. The journey map is a **stylized oblique illustrated plan**; don't shift randomly between orthographic isometric, top-down, and deep perspective within one map area.

**Environment detail:** Specific details make each location memorable (umbrella by doorway, cereal on counter, city bus shelter, flyers in store window), but leave low-detail safe space for overlay UI. Prioritize interaction clarity over decorative complexity.

**Age and cultural representation:** Range of adult ages, body types, skin tones, hair textures, and clothing; grounded everyday Western city setting without assuming US-only identity. Different occupations should look knowledgeable and dignified, not like costumed stereotypes.

**Lighting:** Early chapters have inviting morning sunshine with warm reflected light, blue shadows, and readable objects. Seasonal/time-of-day variations can unlock later. Avoid glowing fantasy effects unless narratively appropriate.

## 7. Mascot art specification (character identity is open)
**Role:** Witty, warm traveling companion who participates in scenes, points out affordances, and responds to progress.

**Required first-pass design explorations:** 3 alternative silhouettes: (A) recognizable friendly animal, (B) original small fantasy creature, (C) unusual expressive everyday object. Avoid humanoid anime companion and mascot designs visually close to a prominent existing language-learning brand.

**Proportions:** roughly 2.5–3.5 head-equivalents if animal/creature; not massive baby head/eyes. Distinct silhouette at ~72px tall. Expressiveness from brows, ears, posture, gesture and mouth; no extreme sparkling eyes.

**Palette:** Choose 2 principal colors + 1 accent; keep consistent across all states. Should work against pale sky, interior wall, and map greenery.

**States for A0.0:** neutral idle, wave/hello, listening/curious, approving, thinking/encouraging, walking to door, celebration. Sprite states share the same construction/line weights/lighting. Expressions should be legible at mobile scale.

**Personality direction:** Gentle clever humor (“First stop: a very important hello.”), never sarcasm toward a beginner. Companion acts as guide, not teacher-avatar delivering lectures.

**Export:** transparent WebP or PNG per pose with consistent anchor coordinates and full body in frame; master at 4× intended CSS size; avoid embedded shadows so environment shadow can be separately controlled.

## 8. The journey map — critical emotional centerpiece
**Function:** Show where the learner has been, where they are, and what feels attainable next. Should invite exploration without becoming a blank node ladder.

**Composition:** Tall, vertically scrollable illustrated neighborhood, with a winding walkable road that leads from bedroom/home into a bus stop, corner store, cafe, town square, interview office, then professional district. Core route visibly continuous; optional side routes branch and reconnect.

**Progress grammar:**
- **Completed:** vibrant location, small earned stamp/check integrated into *UI overlay*, optional subtle sparkle, clearly named episode.
- **Current:** gentle animated ring/highlight around location marker and obvious `Continue` action.
- **Available optional:** recognizable illustrated marker, quieter secondary CTA.
- **Locked future:** still visible (motivational) but low saturation/contrast, lock icon plus accessible status label; never entirely blank fog.
- **Upcoming preview:** distinguish `Coming next` vs locked requirement. Don't pretend unimplemented locations are playable.

**Navigation:** Journey map scrolls vertically; current location centered/within viewport; `Back to current` floating control if user explores far; top-level chapter overview. The location markers are **real interactive components**, not part of flattened scenery. At least one visual reward visible near the beginning.

**Map visual quality:** Distinct landmarks, lush but readable landscape, readable winding paths, cozy buildings, occasional characters, varied roof silhouettes, mixed tree shapes and pavement textures. Avoid resembling a theme-park map for toddlers; keep a tasteful editorial/casual game style.

**Map deliverables:** Long-form master at 1440px wide × at least 2800px tall (or multi-segment seamlessly tiling backgrounds); export at 2× mobile viewing scale; separate optional route highlights and interactive markers. Reserve safe areas for map UI. Generate/map markers as independent SVG/PNG or real DOM components.

## 9. Screen-specific layouts for A0.0
### Welcome
- Hero illustration: warm neighborhood at dawn with room for one clean headline and language picker.
- Headline: `Learn English for real life.` in actual UI, not in illustration.
- Adult-friendly polished onboarding; avoid flag-only language selection.

### Name capture
- Warm scene crop with companion peeking in; text field and clear CTA anchored lower third.
- English question visually prominent; Spanish explanation smaller below.

### Bedroom
- Landscape 3/4 interior cropped responsively; bed, window, door, dresser, shoes, coat hooks. Objects have unique silhouettes and selectable hit regions.
- Keep central/lower interaction objects uncluttered. Separate interactive objects into transparent images or SVG hit areas.
- Character placed left or lower corner; overlay dialogue anchored away from object hotspots.

### Exercise overlay
- World scene remains visible as context while interaction panel holds the prompt and answer choices.
- Consistent header progress; audio playback always visible for listening-based questions.
- Correct/incorrect response overlays must not replace the entire world with sterile quiz cards.

### Episode complete
- Reward moment should feel genuinely earned. Companion celebrates; `First Hello` badge appears, map route visually advances to A0.1.
- No giant numerical accuracy score in the learner's face; mastery review is subtle, transparent, and useful.

## 10. Practical production asset list (A0.0)
| Asset ID | Required layers/variants | Format | Suggested master |
|---|---|---|---|
| `welcome_city_dawn` | background only, no text | WebP | 1440×1920 |
| `bedroom_morning_bg` | architecture/furniture only | WebP | 1536×2048 |
| `bedroom_shoes`, `bedroom_door`, `bedroom_window` | individual interaction layers/hitboxes | transparent WebP + SVG regions | 512–1024px individual |
| `mascot_*` | 7 poses/states, same anchor | transparent WebP/PNG | 1024px tall per pose |
| `map_world_segment_01` | town/map without controls/labels | WebP | 1440×2800+ |
| `map_location_markers` | completed/current/locked/optional states | SVG / CSS | scalable |
| `badge_first_hello` | icon only, text in UI | SVG / WebP | 512px |
| `sunrise_choice`, `night_choice` | two distinct choice illustrations | WebP | 768×768 each |

Export sRGB; avoid overly sharp noise; compress reasonably for mobile and lazy-load map/world art. Build responsiveness through art direction plus CSS positioning, not cropping important objects at 320px width.

## 11. Image generation directions (copy-ready prompts)
These prompts are for assets only. Always include a separate **negative constraint** block.

### A. Bedroom environment — background only
> Production background illustration for a premium Western-designed casual mobile adventure game for adult English learners. A small cozy modern bedroom at sunrise, three-quarter slightly elevated perspective, natural furniture proportions, a neatly made bed, bedroom door, small dresser, jacket on hook, clear place for a pair of shoes near the doorway, warm soft daylight, tactile surfaces, elegant simplified detail, subtle painterly texture, contemporary editorial storybook illustration, cheerful but not childish. Compose vertical 3:4 portrait with clear lower-third visual safe zone for interactive lesson cards and uncluttered upper corner for companion dialogue. No characters. No UI. No words. No labels. Consistent clean outlines and restrained shadows.

**Negative constraints:** No anime, manga, chibi, JRPG styling, large glossy eyes, saturated gacha art, pixel art, photorealism, text, signage, app buttons, speech bubbles, gradients in the UI style, watermarks.

### B. Journey map — background only
> Tall seamless illustrated journey map background for a premium Western casual adventure language learning game. Warm welcoming small modern town, gently winding connected road from a house in a residential area past bus stop, corner convenience store, bakery cafe, town square and small professional district. Three-quarter oblique illustrated map viewpoint, coherent perspective, distinctive architecture, lush but restrained planted trees, soft sunlit greens and terracotta roofs, warm cream paving, rich small environmental storytelling details, editorial storybook texture, enough visual breathing room for separately overlaid interactive episode markers. Vertical map optimized for long scrolling. No UI, no words, no labels, no numbered nodes, no stars, no badges, no locks, no characters with anime features.

**Negative constraints:** No Japanese anime town, no kawaii, no gacha, no huge head characters, no board-game numbering baked into art, no readable text, no fake buttons, no logos, no watermark.

### C. Mascot exploration — 3 concepts
> Concept-sheet exploration, three substantially different original mascot concepts for a sophisticated but warm Western casual adventure game that teaches practical English to adults: one friendly stylized animal, one small unusual fantasy creature, one expressive inanimate object. Each has a strong recognizable silhouette, grounded expressive body language, warm witty personality, restrained facial features, non-anime proportions, clean editorial cartoon design, limited coordinated palette, appealing at 72px height. Neutral background. For each concept show standing neutral, greeting wave, thoughtful and celebratory poses. No text, no lettering, no game UI, no resemblance to famous existing mascots.

**Negative constraints:** Avoid Duolingo owl resemblance, anime chibi, big glossy eyes, oversized cheeks, 3D vinyl-toy materials, babyish preschool styling, brand logos.

### D. Completion reward art
> Vertical celebration illustration for a mature but playful Western casual game teaching English: original companion character from supplied reference joyfully greeting learner in a sunlit cozy bedroom doorway, warm confetti-like paper shapes, clean elegant lighting, a subtle visual sense of a fresh adventure beginning. Leave clear space for a real UI badge and results text overlay. Same illustrated rendering, anatomy and palette as approved companion design. No text, no numerical scoring, no badges baked into art.

## 12. Art review gates
**Gate 1 — Direction:** Compare 2–3 coherent image examples with consistent Western adult-friendly visual grammar. Approve one; do not cherry-pick incompatible palettes/perspectives.

**Gate 2 — Mascot model sheet:** Confirm silhouette, expressions, size, palette, poses, and voice vibe; only then generate episode scene variants.

**Gate 3 — Scene consistency:** Bedroom and first map segment must match outline strength, lighting, texture, proportions, and environmental perspective.

**Gate 4 — UI integration:** Validate legibility and hit targets over the scene; verify text is real UI, no cropped hotspots, responsive small-screen layout.

**Gate 5 — Motion and performance:** Assess idle/feedback motions, reduced-motion behavior, total image payload, loading, and low-end Android performance.

Reject any asset that requires a complete front-end redesign to fit. Revisions should preserve approved silhouettes, proportions, colors, and perspective.

## 13. Per-agent instructions
**Gemini / visual concept agent** — Use only this dossier and A0.0 contract. Explore concept variations; never modify navigation or learning outcomes. Output named asset lists, sheet of consistent poses, and clear layout safe zones. Distinguish inspiration mockups from production exports.

**Image generation agent** — Use approved reference character sheets whenever creating a new mascot pose. Never invent new outfit/colors/facial structure between outputs. Generate scene backgrounds without UI. Keep camera angle and lighting continuity. Ask for approval before major stylistic changes.

**Codex / implementation agent** — Treat the CSS/SVG layer as the interface. Never crop text from image renders or hardcode interactions into raster backdrops. Use localization keys, semantic controls, responsive safe zones, and independent asset IDs. Preserve existing validated design tokens; report unavoidable inconsistencies.

**Product lead / QA** — Reject polished mockups that cannot be decomposed into art, components, and data. Validate user comprehension, adult appeal, map motivation, and readability before further illustration work.

## 14. Definition of visual success
- A casual glance clearly identifies this as an **English-learning adventure for adults**.
- The learner can point to the current map location, one completed milestone, and what's coming next.
- Dialogue and language choices are unmistakably interactive, regardless of native language.
- Mascot is a recognizable individual character, not a generic anime pet or a copy of a language app icon.
- Bedroom art remains beautiful when all interface overlays are hidden, and interface remains usable if art fails to load.
- The app's visual grammar is consistent from onboarding through the first earned badge.

**Do not lock the brand name, mascot species, or final palette without user sign-off. This dossier is the explicit production proposal, not a claim that every creative detail has already been approved.**