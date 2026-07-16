# Studs — Visual Overhaul Correction + Infinite Feed (for Claude Code / Fable)

## Context
The current live build is still running the original dark teal-on-black theme across Connect, Play, and Locker — the candy/studs visual direction that was designed was never actually applied to the real app, only described. This prompt corrects that.

**Primary reference is the attached hand-sketched mockup** (bold color-blocked post cards — mustard yellow and blush pink — full-body Roblox avatar renders posed beside the text, chunky black-outlined like/repost icons, colored comment input bar with a paper-plane send button). Build toward that image directly. Any previously-generated HTML mockups are secondary — useful for peripheral ideas (nav layout, stud texture approach) but the sketch is the actual target for card design, color choices, and layout feel.

You are acting as the UI expert here: don't just replicate the sketch pixel-for-pixel — extend it into a full, coherent design system (consistent spacing, a real component set, responsive behavior, states for hover/empty/loading) the same way a designer would take a client's rough concept and turn it into a production-ready interface. Where the sketch is ambiguous or incomplete, make the best design decision and keep it consistent with the sketch's spirit: bold, colorful, chunky, playful, unmistakably Roblox-flavored — not a generic SaaS dashboard.

---

## Part 1 — Visual overhaul (Connect, Play, Locker)

**Scope boundary:** this applies to Connect, Play, and Locker only. Workshop/Analytics stays data-first and dark — but not sterile: it should still carry some of the product's personality (the pulse/live-indicator motif, occasional accent color, chunky headers) while remaining clearly analytical and technical rather than candy-colored. When the user navigates into Workshop from Play/Connect/Locker, the background and surrounding chrome should transition with a fade (not an instant hard cut) from the bright theme into the dark Workshop theme, and fade back when leaving — this transition should read as a deliberate "stepping into the office" moment, not a jarring flash. Flag back to me whether the landing/marketing page should move to the bright theme or stay dark like Workshop before changing it; don't decide that silently.

**Color**
- Move off the dark teal-on-black theme entirely for these three sections. Use flat, saturated pastel "candy" colors as the primary card colors — mustard yellow and blush pink from the sketch, expanded into a fuller palette in the same family (mint, periwinkle, lavender, tangerine) so different post authors/cards can be visually distinct
- Page background should be light/bright, not dark — this is the single biggest change from the current build
- Each user's chosen accent color drives their own card color, matching the sketch's per-author color-coding (yellow card for one dev, pink for another)

**Cards & structure**
- Solid flat color-block cards, thick black border (as in the sketch), rounded corners
- Full-body avatar render posed beside/behind the post text, not just a small circular profile icon — extend this into the pose/rotation/resizing system already scoped (front-facing, side profile, action poses like waving/sitting/leaning)
- Chunky, filled, black-outlined like/repost icons matching the sketch's icon style — not thin-line generic icons
- Colored comment input bar with a paper-plane send button, styled per the sketch, tinted to the card's accent color
- Hard offset drop shadows (not soft blur-only) for the "sticker/toy" feel the sketch implies

**Navigation**
- Centered Play/Connect/Workshop/Locker pills in the navbar, as already built
- Navbar color customizable per the earlier design (flat or studs-texture, user-selectable)

**Background texture**
- Real repeating square stud texture (not circular), small tile size, low contrast so it doesn't compete with text readability, tintable via CSS filter to match the selected background color — per the correction already made to the design

**Typography**
- Chunky rounded display font (Baloo 2 / Fredoka family) for usernames and headers, paired with a simpler readable body font — avoid default system-ui/Inter-only typography, which reads as generic

**As the UI expert, also design and apply (extending beyond the sketch):**
- Hover/active states for cards, buttons, and icons
- Empty states (e.g. "Your feed is waiting on you") restyled to match the new bright theme instead of the old dark one
- Loading/skeleton states for posts while content is fetched (see infinite scroll below)
- Consistent spacing and sizing rules so cards of different lengths (short post vs. long post with stat embed vs. post with full-body avatar) all still look intentional, not cramped or inconsistent

---

## Part 2 — Infinite post loading

Connect's feed (and any other list of posts — a profile's post history, a per-game community feed in Play) should load posts continuously from the database as the user scrolls, not load everything at once or require pagination clicks.

**Requirements**
- Initial load fetches a first batch of posts (reasonable page size, e.g. 15-20)
- As the user scrolls near the bottom of the loaded posts, automatically fetch and append the next batch — no "load more" button required
- Use cursor-based pagination against the database (e.g. keyed off post timestamp/ID) rather than offset-based, so the feed stays consistent even as new posts are created while the user is scrolling
- Show a lightweight loading indicator (skeleton cards matching the new bright card style, or a small spinner) while the next batch fetches
- Handle the end-of-results state gracefully (e.g. "You've caught up" message) rather than looping or erroring
- Apply the same infinite-loading pattern to any other post list in the app (profile pages, per-game community feeds in Play) for consistency, not just the main Connect feed

---

Attach the hand-sketch reference image to this prompt when handing it off. Everything from the earlier full recap prompt (onboarding order, full profile/post customizability, badges, Workshop features, etc.) still applies and is unaffected by this correction — this prompt is specifically about fixing the fact that the visual theme wasn't actually applied yet, and adding infinite feed loading.
