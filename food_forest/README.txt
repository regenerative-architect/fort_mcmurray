FORT MCMURRAY LIVING FOOD FOREST
Planetary Restoration Archive - Foster + Navi
Release 2.0.0 | research content dated October 13, 2026 | presentation rebuilt October 17, 2026

CONTENTS
  index.html  -- The whole app: HTML, CSS, JavaScript and three embedded fonts in ONE file (about 450 KB,
                 most of it the fonts).
  README.txt  -- This file: use, structure, extending, verification and limits.
  LICENSE.txt -- MIT (code), CC BY 4.0 (prose and layout concepts), SIL OFL (fonts), third parties.

START
  Open index.html in a current Chrome, Edge, Firefox or Safari. No install, account or server.
  Best: host it on HTTPS (GitHub Pages or any static host); IndexedDB is steadier on a stable origin.
  Reading, planning, the field tools and every audience work fully OFFLINE.
  Online only: outside source links, OpenStreetMap searches, and the optional adult peer room.

WHAT 2.0.0 IS: ONE FOREST, FOUR WAYS OF PRESENTING IT
  The facts are identical to 1.0.0. What changed is the PRESENTATION METHOD, chosen by a switch in the
  top bar (or the Display button). Switching reshapes the whole page, revealed in a circle that grows
  from the button you pressed.

  Audience     Scene                 Method       Voice     Motion  Emoji     Type
  Kids         summer morning        Quest map    storybook Lively  Lots      Fredoka
  Adults       autumn evening        Field guide  plain     Gentle  Few       Fraunces + Atkinson
  Community    spring blossom        Action board plain     Gentle  Some      soft Fraunces + Atkinson
  Groups       clear winter night    Briefing     formal    Still   None      Atkinson Hyperlegible

  Kids       Quests that earn stickers, a drawn tree that grows with progress, tree cards that open to
             reveal secrets, a stop/pause/go traffic-light explainer, a safety quiz that earns a badge,
             five stepping stones, a friendly guide (Sprout), optional read-aloud and big tap targets.
             The online peer room is closed to Kids, and any open room is left automatically on switching.
  Adults     Unhurried editorial reading, species "plates" ruled by ecological status, a contents list in
             the margin, minimal decoration.
  Community  Clear next steps (a "Your next step" card with a progress ring and a one-tap Mark done),
             people-first wording, a blossoming-orchard scene with bees.
  Groups     A status banner on every page, an executive summary, numbered sections and contents,
             registers and tables instead of cards, flat styling, and clean black-on-white printing.

  Four DIALS can override any audience's defaults (Display button): Animation (Still, Gentle, Lively),
  Emoji (None, Few, Some, Lots), Colors (Auto, Light, Dark) and Text size (Regular, Large, Largest), plus
  a switch to hide the animated forest. A device that asks for reduced motion starts at Still and can
  never exceed Gentle. Page changes are instant: Gentle fades the new page up, Lively staggers each block
  in, Still just shows it. All settings are saved only on the device.

THE LIVING SCENE
  Behind every page: a sky with a sun or moon glow, a four-layer treeline that grows hazier with
  distance (aerial perspective), a gusting wind that carries everything, and species by season: pollen,
  dandelion seed, butterflies and bees (Kids); aspen leaves and needles (Adults); apple blossom petals and
  bees (Community); fine snow (Groups). Leaves and petals tumble and brighten as they face the light;
  large soft foreground petals add depth. Daytime scenes have slow god rays; at night the light comes from
  stars, an aurora and fireflies. Every shadow falls away from the audience's own light source.
  The scene pauses in a hidden tab, hides any full-screen layer it is not using, and is a single still
  frame at Still motion. On a slow device it first draws particles at 30 frames a second, then thins them
  out if needed, so scrolling and reading stay smooth.

THE 14 PAGES (titles change with the audience)
  Overview, candidate areas, fruit-tree atlas, FireSmart/BearSmart, schools and learning, community
  action, partners, policy proposals, Council pathway, replication playbook, field log and costing, peer
  collaboration (optional, adults), data and settings, evidence and credits.

HOW IT IS BUILT, AND HOW TO EXTEND IT  (everything is in index.html; search for the numbered banners)
  CSS    00 fonts | 10 tokens | 20 layout | 30 components | 40 audience skins | 50 scene, motion, print
         Uses cascade layers, so an audience skin always wins over shared components cleanly.
  JS     01 helpers | 02 AUDIENCES (the registry) | DATA (research content) | 03 state and storage
         04 scene engine | 05 interface | 06 content blocks | 07 pages | 08 kids | 09 peer | 10 events

  ADD AN AUDIENCE (for example "Elders and knowledge keepers" or "Teens"):
    1. Add an object to AUDIENCES and its id to AUD_ORDER (02).
    2. Copy one [data-audience] structure block and its two colour blocks in the CSS tokens (10).
    3. Add a recipe for it to SCENES in the scene engine (04).
    4. Add a title for it in each ROUTES entry, and a voice in GUIDE if it needs new wording.
    The switcher, welcome cards, Display dialog, search, contents list and print pick it up automatically.
  ADD A PAGE: add to ROUTES and GUIDE, write a renderer, call defineView('id', grownUp, kids, after).
  ADD A KIDS QUEST or BADGE: add it to QUESTS or BADGES (08) and to QUEST_IDS or BADGE_IDS (03).
  ADD A PARTICLE: describe its behaviour in KD, paint it in buildSprites, add it to a SCENES list (04).
  UPDATE A FACT: edit the DATA block once; every audience updates.

PRIVACY AND ZERO-HARM DESIGN (non-negotiable)
  - No analytics, telemetry, cookies, accounts, remote fonts, images or scripts. Fonts are embedded.
  - The page makes NO network requests of its own. The only code that can: the optional peer room, which
    loads a version-pinned library from esm.sh after an adult ticks consent and presses Join.
  - Everything a person enters stays on the device (IndexedDB, with a small localStorage fallback). If the
    browser blocks all storage, the app keeps working and says once that changes will not be remembered.
  - Read-aloud uses ONLY the device's built-in (local) voices, so no text is sent anywhere. If there is no
    local voice, the button is simply not shown.
  - Kids: no chat, sharing, accounts, photos or location. The journal is local and warns not to write
    names or addresses. Peer rooms are closed to Kids. Printing a page never awards stickers or badges.
  - A Zero Harm and Anti-Coercion note is in the footer of every page.
  - CHANGE FROM 1.0.0: the literal email address of Council staff was REMOVED from the Council pages and
    the draft letter; they now point to the official Council page, which lists the current contact.
  - Peer packets are strictly validated, escaped, kept in a temporary inbox, and never saved unless a
    person reviews and chooses to.

LOCAL DATA
  Backups are schema-1 JSON, validated on import, and replace data only after a confirmation. Backups made
  by 1.0.0 still import, with every checklist step, screening, note and draft. Export before any reset.
  There is still no service worker and no background sync. HTTPS hosting does not automatically make the
  site available offline; downloading the HTML file does.

DECENTRALIZED PEER ROOM  (unchanged, still experimental)
  Adults generate a private room code, agree a strong password, join the same discovery network, wait for
  a real peer, then share ideas one at a time with consent. Public relays see connection metadata.
  IMPORTANT: this path has NOT been verified end to end between two real devices (see below).

INSTITUTIONAL, LEGAL AND ECOLOGICAL LIMITATIONS  (unchanged from 1.0.0)
  None of the six named areas is surveyed, approved or available to plant by this app. A location link is
  an area search, never a verified parcel. Unapproved planting on public, private, school, park or Treaty
  lands is not advised. RMWB Land Use Bylaw 26/001 sections 5.27.12 (FireSmart) and 5.27.13 (BearSmart)
  may rule out fruit plantings; the shrub restriction is not a permit for trees. Sites near wildlife
  corridors still need a wildlife conflict assessment. No municipal, library, school, Indigenous or
  corporate approval is claimed, and nothing is sent or requested on anyone's behalf. Funding, species
  biology, costs and pilot time ranges all need local verification. The kids' wording is a simplification
  of the same facts; grown-ups should check the official sources.

VALIDATION PERFORMED  (headless Chromium 141 through Playwright, October 17, 2026)
  - Every one of the 14 pages in all 4 audiences and both color schemes (112 renders): no console errors
    or warnings, no empty pages, no stray "undefined" or "NaN" text.
  - 81 scripted interaction checks, all passing: welcome dialog, audience switching and arrow keys,
    quests, badges, quiz, stepping stones, checklists and the Community next-step card, screening gates,
    costing, notes (with HTML-escaping), the Council draft (and that it contains no email address), ideas,
    backup export, valid and invalid import, reset, persistence across reload, display dials and reset.
  - Peer-room logic exercised against a MOCKED library (consent, join, share, validation of good and
    malicious packets, escaping, review-before-save, auto-leave for Kids). Read-aloud exercised against a
    MOCKED local voice (local voice only, emoji stripped).
  - axe-core 4.14 (WCAG 2.x A and AA plus best-practice rules) across all 112 states, run twice: once with
    the live scenery and once with it switched off, so translucent panels can be measured against their real
    background. No violations either time. Every text and background color pair in all 8 themes was also
    checked directly: 312 pairs, no failures, lowest text or button pair 4.68:1 against a 4.5:1 minimum.
  - Reduced motion, hidden-tab pausing, Still-mode stopping, 24 rapid audience switches with resizing, all
    browser storage blocked, a genuine 1.0.0-format backup, the 390 px phone layout, and print-to-PDF for
    the Groups site register and a Kids page (printing opened every panel and awarded nothing).
  - Static scan of the final file: no email addresses, no tracking code, no fetch, XHR or beacon calls, no
    remote assets, no inline event handlers, every outside link is https, every in-app route exists, every
    button has a handler.
  - Performance on a two-core test machine with NO graphics hardware (software rendering, the worst case):
    the animated scenes ran at about 29 to 38 frames per second, and Still motion or scenery-off at a full 60.
    Page changes appeared in about 10 to 40 milliseconds. Devices with a graphics processor do this work in
    hardware and should reach the display's full rate.
  NOT verified: Safari and Firefox (features such as View Transitions and scroll-driven animation fall back
  to simpler behaviour), real phones and tablets, manual screen-reader testing, real two-device peer
  connections, HTTPS hosting, the quality of read-aloud voices, and the legal and ecological facts carried
  over from 1.0.0. Please test those before relying on them.

OFFICIAL REFERENCES
  https://www.rmwb.ca/council
  https://www.rmwb.ca/landusebylaw
  https://lub.rmwb.ca/part-5-general-regulations/
  https://www.rmwb.ca/local-government/mayor-council-and-administration/plans-reports-and-studies/parks-master-plan/
  https://www.rmwb.ca/cip
  https://www.alberta.ca/provincially-regulated-weeds
  https://trystero.dev/docs/getting-started/
  See the in-app source ledger for more direct links.

IDEAS FOR A NEXT ITERATION (OPTIONAL, NOT IMPLEMENTED)
  - A versioned service worker and offline precache for a true installable PWA.
  - A two-device public-relay test of the peer room, and a fallback if the library API changes.
  - Classroom translation dictionaries after expert review.
  - A fifth audience for teens, added through the registry steps above.
  - Ground-truthed parcels only with explicit landowner approval; professional wildlife and FireSmart
    assessments.
