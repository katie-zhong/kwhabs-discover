# KW Go — Handoff Doc
*Impact-a-thon 2026 · Team [name]*

**What it is:** An accessible event discovery page for KW Hab and partner organizations. Community members pick or *say* what they like, then browse one event at a time — with audio read-aloud, high contrast, and a screen-reader list view built in.

**Live demo:** [GitHub Pages link] · **Repo:** [link] · Open `index.html` in any browser — no install, no build, no dependencies.

---

## What we built (in the prototype)

**Screen 1 — "What do you like?"**
- Big tappable chips: Interests (Arts, Food, Music, Games, Sports, Other) + Event Type (Free, Paid, Youth, Virtual, In-person)
- Voice input: press the mic, say what you want ("free music events") — live transcript shows your words, filters turn on automatically, and a scroll-down pointer guides you to confirm
- "Done — show my events" or "Skip — show all events"

**Screen 2 — "Events For You"**
- One event at a time (story style): photo, event name, organization + category tags, date/time/location/cost, short plain-language description
- Browse by: on-screen arrows, tap zones, swipe, or keyboard arrow keys
- "Event X of Y" progress counter + dots
- Read-aloud button: speaks the event and **highlights each part as it reads** (name → org → date → time → location → cost → description); press again to stop; using the mic stops it automatically
- "Register Here" → deep-links to each organization's own registration (registration stays with each NPO — KW Hab confirmed centralizing it isn't feasible)
- Filters: Event Type / Interests / Organization (7 orgs) accordions — events update instantly; mic works here too
- "Start fresh" button: clears everything and returns to Screen 1
- List view toggle: same events as a semantic list for screen readers
- High contrast toggle: black/yellow theme

## Accessibility in the prototype
- Large text (18px+), large buttons (44px+ targets), visual-first layout, plain language
- Keyboard navigable, visible focus rings, ARIA labels + live announcements
- Screen-reader list view (headings + links, no tap zones)
- High contrast mode; reduced-motion respected
- Audio read-aloud with synced highlighting (uses free built-in browser speech — $0)
- Voice input with visible transcript so users can verify and correct

## Key decisions
- **Filters first, feed second** — user never sees an overwhelming wall of events; "Skip" always available
- **One event per screen** — lowest cognitive load; answers "what's out there for me?", not "what's on Tuesday?"
- **Two views, one data source** — story view for low-literacy/cognitive access, list view for screen readers; one page can't serve both well
- **Registration stays with each org** — deep link out, no shared login problem
- **Everything renders from one event record** — name, org, category, cost, mode, youth, date, time, location, description. New channels (SMS, phone) = new renderers, no rebuild

## What we didn't build
- Real backend — events are a hardcoded array (`EVENTS` in `index.html`)
- NPO upload flow + org accounts/permissions
- SMS / phone channels
- Governance, disclaimers, moderation

## What to build next (in order)
1. **Database + org accounts** — one `events` table: `name, organization, category, cost, mode, youth, date, time, location, description, image, registration_url, expires_at`. Replace the `EVENTS` array with a fetch; everything else already works
2. **NPO flyer upload** — staff photograph a flyer → AI extracts the fields + drafts plain-language description → staff review → publish (free-tier vision models keep cost ~$0)
3. **Embeddable widget** — each org drops one script tag on their site: all events, their own, or a filtered view
4. **SMS channel** — text a number, answer one category question, get 3 matching events + reminders (Twilio, pennies per message)
5. **Phone line (IVR)** — dialpad or voice category pick, events read aloud from the same records

## Needs testing with real users
- Screen reader walkthrough (NVDA / VoiceOver / TalkBack) with actual users
- Category label + icon comprehension with low-literacy users
- Tap zone / swipe testing for motor accessibility
- Third-party WCAG 2.1 AA audit (colors designed to AA, not yet verified)
- Plain-language review of all copy by KW Hab

## Known limits / tips
- Voice input needs Chrome (or Edge) + mic permission + HTTPS (GitHub Pages works; opening the file directly won't allow the mic)
- Read-along highlight is most accurate in Chrome
- KW Hab logo loads from kwhab.ca — swap `src` to a local file for offline demos

## Open questions for KW Hab
- Who moderates postings across organizations?
- New phone number vs. extension on the existing line for SMS/voice?
- Which orgs pilot the flyer-upload flow first?
