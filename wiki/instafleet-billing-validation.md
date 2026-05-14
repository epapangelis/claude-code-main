# instafleet Billing Detail Validation

**Summary**: Add validation to prevent bookings from advancing to "Buy the Car" stage unless the active billing detail is fully completed.

**Context**: [instacar]

**Sources**: PRO-2997 (Linear), kill-pipedrive initiative

**Last updated**: 2026-04-23

---

## Overview

Currently, users can attempt to move a booking to "Buy the Car" stage even if the selected/active billing detail is incomplete. This creates data integrity issues and payment processing problems. The system must validate that all required fields in the active billing detail are filled before allowing the stage transition.

## Problem

Sales and ARM teams encounter booking progression failures because incomplete billing details are submitted. The workflow lacks a gating mechanism at the "Buy the Car" stage transition point to catch and prevent these incomplete submissions.

## Solution

Add validation logic triggered at the stage transition to "Buy the Car":
- Check if the active billing detail has all required fields populated
- If incomplete, display a clear error message listing missing fields
- Block stage transition until all required fields are complete
- Once complete, allow progression without friction

## Required Fields

Fields to validate (to be confirmed with Finance/ARM):
- Account Type
- Company Name
- First Name
- Last Name
- TIN
- D.O.Y.
- Activity
- Phone Number
- Email
- Address
- Postal Code

Clarify which are truly required vs. optional.

## Acceptance Criteria

**Given** a booking with incomplete active billing detail

**When** user attempts to transition to "Buy the Car" stage

**Then**
- Stage transition is blocked
- Error message appears specifying missing fields
- User is prompted to complete billing detail

**Given** a booking with complete active billing detail

**When** user attempts to transition to "Buy the Car" stage

**Then**
- Validation passes
- Stage transition completes
- No error displayed

## Implementation Notes

- Validation should occur at stage transition point (not during form input)
- Error messaging must be user-friendly and specific
- Consider whether some fields should be optional
- Coordinate with Finance/ARM on required field list
- Part of [[kill-pipedrive]] initiative for booking integrity

## Related pages

- [[kill-pipedrive]] -- kill Pipedrive initiative; booking workflow improvements
- [[instafleet]] -- instacar's operational backbone; booking and subscription management
- [[instafleet-billing-detail-selection]] -- related feature: allow users to select active billing detail
