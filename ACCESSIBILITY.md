# Accessibility: Under the Oasis

Audit and validation report for https://aminebrr.github.io/Khettara/ (single page, English and French, Arabic terms), November 2026.

The target is WCAG 2.2 Level AA. The page has been tested with automated tools, a keyboard walk-through, an accessibility-tree check and responsive checks. It has **not** been tested with real screen readers, so it does not claim full WCAG 2.2 AA conformance. See "Still to test by hand".

## A. Audit of the live site (before changes)

### Strengths already in place
- A skip link, and `header`, `nav`, `main` and `footer` landmarks; one `h1`, with `h2` per chapter and `h3` inside.
- The `lang` attribute on `<html>` follows the EN/FR switch, and the hidden language is removed from the accessibility tree.
- Lesson tabs follow the ARIA tab pattern, with arrow keys.
- The 3D model's labels are real buttons with `aria-pressed`. Turning the model already had 44 px arrow buttons, and the slider had a label and a spoken value.
- Partial reduced-motion support: the hero photo animation, the water flow and the rain stopped.
- No horizontal scrolling at 320 px. Body text is 17–20 px with a line height of 1.6.

### Problems found

| # | Issue | WCAG 2.2 | Severity |
|---|---|---|---|
| 1 | Top bar text over the hero photograph: menu links 1.9–2.4:1, inactive "FR" about 1.0:1 (measured with the real photo) | 1.4.3 | High |
| 2 | The 3D model could only be zoomed by pinch or scroll wheel, with no named viewpoints; no static equivalent unless WebGL failed | 2.1.1, 2.5.7, 1.1.1 | High |
| 3 | When the 3D model failed, the slider and buttons still showed and did nothing (CSS overrode `hidden`) | 4.1.2, 3.2 | High |
| 4 | Informative photographs had empty `alt` | 1.1.1 | Medium |
| 5 | No section navigation on phones (links were hidden) | 2.4.5 | Medium |
| 6 | The language buttons and the logo link had accessible names that did not contain their visible label | 2.5.3 | Medium |
| 7 | 3D labels were 22 px tall on phones; the logo link was 14 px wide | 2.5.8 | Medium |
| 8 | Lesson tab durations: 4.27:1 contrast | 1.4.3 | Medium |
| 9 | Unfilled circles in the counts graphic: 2.2:1 against the ochre | 1.4.11 | Medium |
| 10 | Moving the slider while a picture was being rendered silently undid the change | Functional | Medium |
| 11 | ARIA labels stayed in English when the page was in French; the language change was not announced | 3.1.2, 4.1.3 | Low |
| 12 | Arabic text had no `dir="rtl"`; a French source title and English titles in French text had no `lang` | 3.1.2 | Low |
| 13 | The readout was a live region, so screen readers spoke on every slider step; the wording read "18% Weak flow. of the tunnel…" | 4.1.3 | Low |
| 14 | Camera moves were still animated with reduced motion on | 2.3.3 (AAA) | Low |
| 15 | No loading message for the 3D model | 4.1.3 | Low |
| 16 | "3,000 m × 0.015 = 45 m" read inconsistently by screen readers | 1.3.1 | Low |

**Not applicable:** there is no audio or video (so no captions are needed), no forms other than the slider, no maps, and no dialogs. The phone menu added below is the only dismissible overlay.

## B. Changes made

The visual identity, layout, copy, typefaces, palette and 3D implementation are kept.

**Keyboard and focus**
- Focus ring: `3px solid #D97736`, 4 px offset, as requested. On ochre sections and the footer the ring is ink, because orange on ochre is only 1.1:1. Controls drawn over the 3D scene add a dark halo so the ring stays visible on sand and water.
- A "Skip the 3D model to its text description" link before the model.
- **3D model:**
  - New Viewpoint buttons: Surface, Underground, Water outlet, Reset view, Zoom in, Zoom out.
  - Esc clears the selected label.
  - Every action is announced through one polite live region.
- Lesson tabs: Home and End keys added; tab panels are focusable.
- **Phone menu:** a "Sections" button opens the section links.
  - It uses `aria-expanded`.
  - Esc closes it and returns focus to the button.
  - Choosing a link or clicking outside also closes it.

**3D model**
- A visible "Loading the 3D model…" status.
- If WebGL or three.js fails:
  - a clear error with a link to the description;
  - the dead controls are hidden;
  - the description opens.
- A new "Diagram and text description of the model" section, open on demand:
  - a labelled cross-section SVG diagram with a written caption;
  - a description list of every labelled element, with sources;
  - what each scenario does (87%, 58%, 18% and 0% of the tunnel collecting water), noting that these are model values.
- Reduced motion: camera moves become instant, damping is off, and the setting is followed live if the visitor changes it.
- **Slider and readout:**
  - The slider's spoken value now reads as a sentence, for example "18% of the tunnel still captures water. Weak flow."
  - The preset buttons announce their result.
  - The readout is no longer a chatty live region.
- Bug fixed: a background render no longer reverts the visitor's slider setting.

**Images**
- All six photographs and the cut-away render now have alt text describing what is visible. The captions keep the place, author and licence.

**Contrast and target size**
- The top bar is now solid night, which raises the links to 15:1 and the inactive language to 8.8:1.
- **Contrast fixes:**
  - Lesson durations: 5.6:1.
  - Counts outlines: 4.0:1.
- **Larger targets:**
  - Language buttons and the phone menu button: 44 × 44 px.
  - Logo link: at least 44 px.
  - Menu links: 45 px tall.
  - 3D labels: 28 px (32 px on phones).
  - Footnote links: a larger invisible hit area.

**Languages**
- `aria-label`s switch with the language (turn buttons, zoom, scenarios, lessons, counts graphic).
- The switch announces "English version" or "Version française".
- The language buttons are named "EN English" and "FR Français".
- Arabic text has `lang="ar" dir="rtl"`.
- The source list and photo credits carry `lang="en"`, the SNRT source `lang="fr"`, and "The Voices of Water" inside French text `lang="en"`.

**Motion**
- The requested global `prefers-reduced-motion` rule is added alongside the existing one.

**Semantics**
- `[hidden]` always wins over component display rules.
- The maths line has a spoken version ("3,000 metres times 0.015 equals 45 metres", plus a French version).

**Lessons**
- A short inclusion note: pupils work in pairs with separate roles (handling, timing, recording), so no step depends only on fine motor control or sight. The "Dig a well" effect can also be shown with the model's slider or its text description.

## C. Validation

| Check | Before | After |
|---|---|---|
| Lighthouse accessibility, desktop | 97 | 100 |
| Lighthouse accessibility, mobile | 97 | 100 |
| Lighthouse best practices / SEO | 100 / 100 | 100 / 100 |
| axe-core 4.11 (WCAG 2.0–2.2 A/AA plus best practice), 4 runs: desktop and phone × EN and FR | 2 rules failing (contrast, label in name) | 0 violations |
| axe-core with reduced motion on | not run | 0 violations |
| html-validate (recommended rules) | pass | pass |
| Horizontal scroll at 1440, 1024, 640 (200% zoom of 1280), 390 and 320 px | none | none |
| Console errors | none | none |

**Manual checks done**
- Tab through the whole page: the order is logical, every stop has a visible ring, and there are no keyboard traps.
- Enter and Space work on all buttons; arrow, Home and End keys work on the lesson tabs.
- Esc closes the phone menu (focus returns to the button) and clears the selected 3D label.
- Viewpoints and zoom move the camera; announcements are spoken in the active language.
- Switching to French updates `html lang`, the labels and the announcement.
- The no-3D fallback was tested by blocking three.js: the error, the opened description and the hidden dead controls all behave as intended.
- Reduced motion: CSS animations end at once and camera moves are instant.
- Text over photographs, measured with the real Wikimedia images at 1024 px:
  - hero title 4.7:1 at worst;
  - Arabic word 3.3:1 at worst (large text, so the requirement is 3:1);
  - standfirst 7.4:1, byline 6.5:1, credit 7.3:1;
  - "Pump, or disappear?" header 6.8:1 or more.

**Test conditions:** Lighthouse and axe ran on a local copy, with stand-in images for the photographs (the test machine cannot reach Wikimedia) and software 3D rendering. Lighthouse performance scores from that setup are not meaningful and are not reported.

### Still to test by hand
- Real screen readers: NVDA or JAWS with Chrome or Firefox, VoiceOver on macOS and iOS, TalkBack on Android. In particular, check the 3D labels, the live announcements and the lesson tabs.
- Text over the hero photograph on phones, with the real photo. The desktop check passed; the phone check could not be run.
- Windows High Contrast / forced colours.
- Real touch devices: the model's drag gestures, and label positions as the camera moves.

### Known limits
- **3D labels move with the camera.** A label can disappear while focused if the camera moves it off screen.
- **Hard to see without vision.** The 3D view itself remains a visual experience; the text description and diagram are its equivalent.
- **Small inline links.** Footnote numbers and photo-credit links inside sentences are smaller than 24 px. They fall under the inline exception of WCAG 2.5.8; footnotes have an enlarged hit area.
- **Long reading sections.** Some sections are long. The copy was kept as written, by design.
