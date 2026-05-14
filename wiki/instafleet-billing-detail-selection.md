# instafleet Billing Detail Selection

**Summary**: Add the ability for users to select which billing detail is active for a booking, with auto-save and toast confirmation.

**Context**: [instacar]

**Sources**: PRO-2996 (Linear), kill-pipedrive initiative

**Last updated**: 2026-04-23

---

## Overview

Currently in instafleet, bookings can have multiple billing details displayed as cards, but there's no mechanism to explicitly select or mark which one is "active" or primary. This feature adds a simple, minimal UI change to allow users to select an active billing detail with immediate persistence.

## User Problem

Sales and customer success teams using instafleet need clarity on which billing detail is the active/primary one for a given booking. Without a selection mechanism, the workflow is ambiguous and can lead to payment issues or disputes.

## Solution

Add a radio button or selection indicator to each billing detail card. When a user selects a billing detail:
- The change persists immediately (auto-save) via API call
- A subtle toast notification ("Billing detail updated") confirms the action
- The UI visually distinguishes the active card from others
- No page refresh is required
- The change survives a page reload

## Acceptance Criteria

**Given** a booking with multiple billing details

**When** the user clicks to select a different billing detail as active

**Then**
- Selection saves immediately to the backend
- Toast notification confirms the action
- UI reflects the new active billing detail visually
- No page refresh required
- Change persists on page reload
- Toast auto-dismisses after 3 seconds

## Design Notes

- Minimal change: leverage existing billing detail card layout
- Selection indicator: radio button recommended
- Visual distinction: highlight, border, or background color change
- Toast: subtle, 3-second auto-dismiss
- Desktop and mobile: same interaction pattern

## Implementation Considerations

- Debounce rapid selections to prevent API race conditions
- API endpoint: update booking with selected billing detail ID
- Monitor API success rate and user interaction patterns
- Part of [[kill-pipedrive]] initiative for minimal MVP booking enhancements

## Related pages

- [[kill-pipedrive]] -- kill Pipedrive initiative to migrate Sales workflows into instafleet
- [[instafleet]] -- instacar's operational backbone for fleet and booking management
- [[carswaps]] -- related CS feature for vehicle swap flows in instafleet
