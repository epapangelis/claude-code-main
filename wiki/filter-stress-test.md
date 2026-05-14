# Filter UI Stress Test - Instafleet Bookings

**Project**: Instafleet Bookings  
**Ticket**: PRO-2959 - Add filters in Bookings  
**Design File**: [Instafleet DS](https://www.figma.com/design/DzJ17Kk2eyyTBGndp4qrAx/Instafleet-DS?node-id=20570-260881)  
**Date**: 2026-04-23

---

## Overview

This document outlines comprehensive edge cases and stress testing scenarios for the filter system being added to the Bookings page. It covers all filter types: date ranges, value ranges, multiple selections, and free text inputs.

---

## 🔴 Critical Edge Cases

### 1. Free Text Filters (Comments, Email, Phone, etc.)

#### 2-Letter Minimum Rule
- [ ] User types 1 letter then waits — no results shown? Or "keep typing"?
- [ ] User types 2 letters, results appear, then deletes back to 1 letter — results hidden immediately?
- [ ] Debounce timing: results appear instantly or after 300ms? Consistent across all fields?

#### Special Characters & Security
- [ ] Emoji input: "😀😀😀" — search works? Doesn't break UI?
- [ ] SQL injection attempt: "'; DROP TABLE bookings--" — safely escaped?
- [ ] Quotes and escapes: "test\"quote", "test'quote" — handled?
- [ ] Newlines in paste: User pastes multi-line text into single-line field — rejected or stripped?
- [ ] RTL text: Arabic/Hebrew input — display and search work?

#### Length & Performance
- [ ] Very long input: 1000+ characters in Comments field — input box expands or scrolls?
- [ ] Very long input: Does filtering still execute or timeout?
- [ ] Rapid character input: User types very fast — any lost keystrokes?

#### Whitespace Handling
- [ ] Leading spaces: "  email@test.com" vs "email@test.com" — treated same or different?
- [ ] Trailing spaces: "john.doe@test.com  " — search works?
- [ ] Multiple spaces: "john    doe" — matches "john doe"?
- [ ] Tabs and special whitespace: Pasted content with non-standard spaces

#### Search Result Ordering
- [ ] Design states: "Results starting with text first, then results containing text"
- [ ] Test: Search "car" in list ["car", "sports car", "electric car", "carpet"]
- [ ] Expected: ["car", "carpet", "electric car", "sports car"]
- [ ] Actual matches requirement?

---

### 2. Value Range Filters (numeric: Discount, Value, Deposit, Price, etc.)

#### Decimal Handling
- [ ] Field accepts decimals: "5.5"? or integers only: "5"?
- [ ] Decimal precision: "5.123456789" — truncated or rounded?
- [ ] From: 5.5, To: 10.7 — range correctly inclusive/exclusive?

#### Negative Numbers
- [ ] Data contains negative values: "Discount: -10%" — can user filter by range including negatives?
- [ ] From: -100, To: 0 — works or error?
- [ ] Display: Shows "-100" clearly or ambiguous?

#### Edge Value Combinations
- [ ] From: 5, To: 5 → "exactly 5" — is this clear in UI?
- [ ] From: 5, To: blank → "≥ 5" — label clear?
- [ ] From: blank, To: 5 → "≤ 5" — label clear?
- [ ] From: blank, To: blank → no filter applied? Or error?

#### Invalid Input
- [ ] From: 100, To: 10 (backwards) — auto-swap? Error? Silent fail?
- [ ] From: "abc", To: "123" — validation error shown?
- [ ] User types: "5-10" (range in single field) — parsed or rejected?

#### Extreme Values
- [ ] From: 999999999999 (very large) — formatting with commas or unreadable?
- [ ] From: -999999999999 — handled?
- [ ] Floating point precision: 0.1 + 0.2 ≠ 0.3 — any rounding errors?

#### Display & UX
- [ ] Input field width: Can user see what they typed?
- [ ] Placeholder text: "e.g., 0" or "Min" vs "From"? Consistent?
- [ ] Number formatting: "1234567" shows as "1,234,567"? Or confusing wall of digits?

---

### 3. Date Range Filters

#### Date Interpretation
- [ ] Timezone: "From: 2026-04-23" — is that 00:00 UTC or user's local midnight?
- [ ] If user in Athens (UTC+3) selects April 23 → does data include Athens midnight or UTC midnight?
- [ ] Result: off-by-one day bugs possible?

#### Invalid Dates
- [ ] Feb 30 (doesn't exist) — rejected or error?
- [ ] Year 9999 — accepted or capped?
- [ ] Leap second (23:59:60) — handled?

#### Date Range Logic
- [ ] From: 2026-04-23, To: 2026-04-23 → shows 1 full day of data? Or technically 0 (start to start)?
- [ ] Design notes mention same component as Generic Tickets — verify behavior is documented

#### Backwards Dates
- [ ] From: 2026-04-23, To: 2026-04-01 (future to past) — auto-swap? Error? Silent no results?

#### Relative Dates (if supported)
- [ ] Design shows absolute dates, but does implementation support "Last 7 days"?
- [ ] If added later: "Last 30 days from TODAY" — does it recalculate daily or fixed?

#### Timezone Edge Cases
- [ ] User creates filter in Athens, data queried from NYC server — any drift?
- [ ] DST (Daylight Saving Time): Filter around March 31, 2026 (when DST changes in EU) — off-by-one errors?

---

### 4. Multiple Selection Filters (Origin, Contract Type, Stage, Assignee, Labels)

#### Large Datasets
- [ ] 1000+ options in dropdown — does it lag or virtualize?
- [ ] User scrolls through 500-item list — smooth or janky?
- [ ] Search within dropdown: User types to filter options — works instantly?

#### Empty Search Results
- [ ] User searches "xyz" in dropdown, 0 matches — blank state? "No results"? Error message?
- [ ] After no results, user clears search — previous options reappear?

#### Selection Logic
- [ ] Select all 100 items — performance hit?
- [ ] Select all, then deselect 1 — UI updates correctly?
- [ ] Max selections: Any limit? Or can select all 1000?
- [ ] Deselect all: Can leave filter empty or must select ≥1?

#### Selected Count & Display
- [ ] 47 items selected — shows "47 selected"?
- [ ] 47 items selected but space for "12 selected" — truncates, wraps, or overflows?
- [ ] Selected items still visible in dropdown while searching?

#### State Persistence
- [ ] User selects 5 items, closes dropdown, reopens — same 5 still selected?
- [ ] User applies filter with 5 selections, page reloads — selections persist?

#### Search Ranking
- [ ] If dropdown supports search: does exact match appear first or alphabetically?
- [ ] Selecting an item: Does it move to top? Or stay in original position?

---

### 5. Filter Panel Interactions & Layout

#### Pinning Filters
- [ ] User pins "Origin" filter — does it move to top? Stays pinned on reload?
- [ ] User pins 15+ filters — does panel overflow? Horizontal scroll? Wrapping?
- [ ] Pinned filters collapse/expand — state saved?

#### Column Visibility
- [ ] User hides all columns except 1 — page still usable or data unreadable?
- [ ] Show/hide column: Updates instantly or requires page reload?
- [ ] Column visibility saved per user session? Permanently?

#### Pin/Unpin While Filtering
- [ ] User pins a filter that's actively filtering results — no data loss?
- [ ] User unpins a filter mid-filter — results stay filtered or update?

#### Filter Panel Overflow
- [ ] 20+ filters in panel + pinned items — scrollable? Wraps?
- [ ] Filters panel on mobile (375px width) — horizontal scroll hell or responsive layout?

#### Drag & Reorder
- [ ] User reorders pinned filters — smooth animation or janky?
- [ ] User drags while filter is applying — pause filter or reapply after?
- [ ] Reorder persisted on reload?

---

### 6. Filter Application & Results

#### Empty Results
- [ ] Origin=Greece + Contract Type=International (no data matches) — shown?
- [ ] Empty state messaging: "No bookings match these filters. Clear filters?" available?
- [ ] User-friendly or confusing?

#### Result Count & Accuracy
- [ ] "Showing 1-50 of 10,234 results" — count accurate after applying new filter?
- [ ] Updates immediately or after 1s delay?
- [ ] If no results: shows "0 of 0" clearly?

#### Performance with Large Datasets
- [ ] Filtering 1M+ bookings — UI freezes or shows loading state?
- [ ] Loading spinner + debounce: Does it appear for "too slow" filters?
- [ ] Timeout: If filter takes >5s, error message?

#### Filter Removal
- [ ] User removes one filter from 5 applied → results update instantly?
- [ ] User clears all filters → page resets or keeps sort/pagination?

#### Conflicting Filters
- [ ] Multiple filters applied simultaneously — all work together (AND logic)?
- [ ] OR logic for same field: Select multiple Origins — "Greece OR Spain"?
- [ ] Clear indication of AND vs OR in UI?

---

### 7. Column Display & Management

#### Reordering Columns
- [ ] After hiding/showing columns, can user drag to reorder?
- [ ] Reorder saved for session? Permanently?
- [ ] Keyboard navigation: Can user reorder via Tab + Arrow keys?

#### Column Width & Text Overflow
- [ ] Long header: "Contract Value (EUR) from 2026-04-20 to 2026-04-30"
- [ ] Truncates? Wraps? Overflows into next column?
- [ ] Hover tooltip shows full text?

#### Frozen/Sticky Columns
- [ ] If many columns visible (horizontal scroll), are key columns (ID, Name) frozen?
- [ ] User scrolls right — ID column still visible? Or scrolls away?

#### Mobile Column Display
- [ ] On 375px width: All columns hidden except 1-2? Horizontal scroll? Stacked cards?
- [ ] User experience: Is data readable on mobile or design desktop-only?

---

### 8. Data Type Mismatches & Format Challenges

#### Phone Filter (Numbers Only)
- [ ] Database has: "+30 210 123 4567", "2101234567", "+30-210-123-4567"
- [ ] User searches: "2101234567" — finds all variants?
- [ ] Or does "numbers only" restriction prevent "+", "-", " "?

#### IBAN Field (Free Text)
- [ ] IBAN format: 27 characters, country code + check digits + account
- [ ] Design allows any free text — no format validation?
- [ ] Search for partial IBAN: "GR9410900770099" — finds "GR9410900770099120000123"?

#### TIN / AFM (Greek Tax ID)
- [ ] Format: 9 digits, specific validation
- [ ] Does filter validate or accept any 9-digit number?
- [ ] User enters "12345678" (8 digits) — rejected or accepted?

#### Coupon & Offer ID Formats
- [ ] Coupon: "SUMMER2026PROMO" — case-sensitive search?
- [ ] User searches "summer2026" — finds "SUMMER2026PROMO"?

#### SKU & Product Name
- [ ] SKU often numeric codes — does system preserve leading zeros?
- [ ] SKU "00123" vs "123" — treated same or different?
- [ ] Product name with special chars: "Dell XPS 15\" (2026)" — search handles quotes?

---

### 9. Filter Drag, Reorder & Animation State

#### Drag During Active Filter
- [ ] User is filtering results, then drags to reorder filters
- [ ] Does filter pause? Reapply after drag? Stay applied?
- [ ] Result count: Accurate after drag?

#### Drag/Drop Performance
- [ ] Smooth animation at 60fps or noticeable lag?
- [ ] With 20+ filters in panel, drag smooth or janky?

#### Ghost Element During Drag
- [ ] User drags filter — does placeholder appear?
- [ ] Or is it confusing where item will drop?

---

### 10. Accessibility & Keyboard Navigation

#### Keyboard-Only Navigation
- [ ] Tab: Navigate through all filters without mouse?
- [ ] Focus visible: Clear outline/highlight on focused element?
- [ ] Enter: Open dropdown? Select item? Clear?
- [ ] Escape: Close dropdown? Cancel edit?
- [ ] Arrow keys: Navigate dropdown options? Reorder filters?

#### Screen Reader
- [ ] "5 filters applied" — announced clearly?
- [ ] Dropdown options: "Option 1 of 50, not selected" — clear?
- [ ] Applied filter chip: "Origin: Greece, remove with Delete key" — instructions?

#### Focus Management
- [ ] Date picker opens (modal) — focus moves inside it?
- [ ] Tab within date picker — focus trap or can tab out?
- [ ] Escape closes date picker and returns focus to trigger button?

#### Color Contrast
- [ ] Filter chips: Text contrast ≥ 4.5:1?
- [ ] Disabled filter field: Visible or disappears into background?
- [ ] Error messages: Red text on light background — readable?

#### Focus Order
- [ ] Is focus order logical (left-to-right, top-to-bottom)?
- [ ] Or does tabbing jump around confusingly?

---

## Design Observations from Screenshots

Based on the 4 filter states shown in Figma:

### Filter Chip Display
- [ ] If 10+ filters applied, do chips wrap to 2+ lines?
- [ ] Or scroll horizontally in single line?
- [ ] Responsive design: At 1024px width, still okay?

### Chip Interaction
- [ ] Close icon (X) visible on each chip? Easy to hit on mobile (40px min)?
- [ ] Clicking chip — edit inline or scroll panel to filter?
- [ ] Visual feedback on click — ripple effect? Color change?

### Filter Summary & Clear All
- [ ] Is there a "Clear all filters" button separate from individual chip removal?
- [ ] Or does user have to remove each chip individually?
- [ ] "Clear all" confirmation needed? Or instant?

### Applied Filters Overview
- [ ] Total count: "12 filters applied" shown prominently?
- [ ] Or need to count chips manually?

---

## Recommended Test Scenarios

Before shipping, test these in order:

### Priority 1 (Critical)
1. [ ] Apply 20+ filters simultaneously → UI responsive?
2. [ ] Type emoji, quotes, special chars in free text → no crash?
3. [ ] Set From: 1000000, To: -500 in value range → error or swap?
4. [ ] Filter with 0 matching results → user experience okay?
5. [ ] On mobile (375px width) → all readable without horizontal scroll?

### Priority 2 (High)
6. [ ] Keyboard navigation: Tab through all filters → all reachable?
7. [ ] Pin 15+ filters → layout doesn't break?
8. [ ] Drag filters while results are filtering → state correct?
9. [ ] Hide all columns → page still usable?
10. [ ] Select all 1000 options in dropdown → performance acceptable?

### Priority 3 (Medium)
11. [ ] Screen reader: Filter announcements clear?
12. [ ] Zoom to 200% → filters still accessible?
13. [ ] RTL text (Arabic/Hebrew) in free text field → display correct?
14. [ ] Very long input (1000 chars) → input box handling?
15. [ ] Date filter around DST change → off-by-one errors?

### Priority 4 (Nice-to-Have)
16. [ ] Copy/paste multi-line text into single-line filter
17. [ ] Rapidly apply/remove filters → any race conditions?
18. [ ] Filter persistence on page reload → state saved?
19. [ ] Reorder columns while filters active → results stay filtered?
20. [ ] Timezone edge cases (UTC vs local time)

---

## Functional Requirements Checklist

From PRO-2959, verify these are implemented:

### Filter Types
- [ ] Date range (Created at, Won time)
- [ ] Value range (Value, Discount, Deposit, Prices, Contract value)
- [ ] Multiple selections (Origin, Contract Type, Contract Period, Stage, Assignee, Labels)
- [ ] Free text (Comments, Email, Referral ID, Plate, Car ID, SKU, Coupon, TIN/AFM, Internal ID, Offer ID, IBAN, Invoice type, Product name, Booking creator)
- [ ] Numbers only (Phone)

### Interactions
- [ ] Delete search bar from booking page ✓
- [ ] Add filters in triangle menu (top right) ✓
- [ ] Users can pin filters ✓
- [ ] Users can hide/display columns ✓
- [ ] Filters accept multiple values (Origin, Contract Type, etc.) ✓

### Search Behavior (Free Text)
- [ ] Filtering starts after 2nd letter ✓
- [ ] Results: Prefix matches first, then contains matches ✓
- [ ] Sorting example: "test" in ["test", "another test", "testing"] → ["test", "testing", "another test"]

### Value Range Behavior
- [ ] From: 5, To: blank → ≥ 5 ✓
- [ ] From: blank, To: 5 → ≤ 5 ✓
- [ ] From: 5, To: 5 → = 5 ✓
- [ ] From: 5, To: 10 → 5 ≤ x ≤ 10 ✓

---

## Notes for Developers

- **Debounce Strategy**: Free text filters should debounce at 300-500ms to avoid performance issues
- **Accessibility**: ARIA labels, focus management, keyboard navigation are critical
- **Mobile-First**: Ensure filter panel is usable at 375px width (iPhone SE)
- **Error Handling**: Show user-friendly messages for invalid input, not technical errors
- **Persistence**: Decide scope: session-only, localStorage, or server-side save
- **Loading States**: Add spinners/skeleton screens if filtering takes >500ms
- **Performance**: Virtualize large dropdown lists (1000+ items)

---

## Sign-Off

- [ ] QA: All edge cases tested
- [ ] Design: UI matches Figma comps under edge cases
- [ ] Accessibility: WCAG 2.1 AA compliance verified
- [ ] Performance: Filtering 1M+ records acceptable (<2s)
- [ ] Mobile: Tested on real devices, not just browser emulation

---

**Document Version**: 1.0  
**Last Updated**: 2026-04-23  
**Owner**: QA / Product
