# OnePercent Notes

## Concept
Web/mobile app about making very small changes to lifestyle rather than dramatic changes that fizzle out quickly. Based on the 1% improvement principle.

## MVP Scope
- Daily/progress tabs for 1% micro-adjustments
- Focus areas: steps, calories, screen time, water + custom activities
- Local quote of the day in footer
- Accountability partner ("buddy system") with invite flow
- Manage tab: show/hide activities, edit values/units/delta%, add custom activities
- Progress tab: 30-day trend graph with toggleable activities, totals/avg, local history stored in localStorage

## Technical Stack
- Frontend: HTML/CSS/JS single-page app (current mockup)
- Hosted: Python `http.server` on port 8766
- Future: Swift/iOS app for App Store distribution
- Quotes: Local `quotes.txt` file (curated from quotlr.com, 134 filtered lines)

## Key Design Decisions
- **Quotes**: Local static file instead of fetching from web. Curated list excludes inappropriate authors (Machiavelli, Castro, Sartre, Murdoch, etc.)
- **Delta limiter**: Adjustment percentage clamped to [-10, +10] to prevent ridiculous targets or breaking the app with extreme values
- **No personal info**: MVP does not collect emails or PII
- **Persistence**: localStorage for user data and visibility toggles

## Files
- `/home/opc/onepercent-mockup/index.html` - Main app
- `/home/opc/onepercent-mockup/quotes.txt` - Curated quotes (134 lines)
- `/home/opc/onepercent-mockup/add-quotes.sh` - Helper to append new quotes with dedup + blocked-author filter
- `/home/opc/oneproject_quotes.txt` - Master curated list before filtering

## Next Steps
- [ ] Add delta limiter validation to input fields (min=-10, max=10, clamp on save)
- [ ] Define buddy system UX flow (Option 2: return confirmation via existing channel)
- [ ] Plan Swift/iOS migration with HealthKit integration
- [ ] Add 1% calculator / coach feature
- [ ] Gentle reminder system with push notifications
- [ ] Weekly review / streak logic
- [ ] Widget for glanceable today screen
- [ ] Accountability partner invite flow (QR + blurb)

## Buddy System Design Notes
- No centralized server required for MVP
- Each device generates local keypair (public key = user ID)
- Invite flow: A sends shareable link/QR containing A's public key via Messages/Telegram/email
- B accepts → installs app → generates own keypair → sends confirmation QR/link back to A
- A receives B's public key → both apps paired
- Optional relay server later for automated handshake (never stores messages, only passes ephemeral invites)

## Future Enhancements
- HealthKit integration (steps, sleep, active energy, heart rate)
- Widget support
- Streak logic with mercy rules (miss a day = pause, not reset)
- End-to-end encrypted buddy sync
- Optional self-hosted relay for remote pairing
