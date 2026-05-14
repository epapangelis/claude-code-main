# Subscriptions Data Model

**Summary**: Schema and field definitions for the subscription entity in instacar, derived from the subscriptions export and report CSVs.
**Context**: [instacar]
**Sources**: subs export.csv, subs report.csv
**Last updated**: 2026-04-15

---

## Subscription ID Formats

Subscriptions use prefixed internal IDs:
- `SUB-XXXXXXXX` -- Standard / Closed Contract subscriptions
- `SUBP-XXXXXXXX` -- Predel (pre-delivery) subscriptions
- `SUBT-XXXXXXXX` -- Temp (temporary vehicle) subscriptions

---

## Core Fields

| Field | Description | Example Values |
|-------|-------------|----------------|
| ID | MongoDB ObjectID | 69c671db... |
| Internal ID | Human-readable ID | SUB-0GP29Y77BQ |
| Car ID / VehicleInternalID | Vehicle identifier | 2024111500073 |
| Type | Subscription category | Standard, Predel, Temp, Closed Contract |
| Status | Active or Ended | Active, Ended |
| Vehicle | Make + model | PEUGEOT - 2008 |
| Plate | License plate | XHY1325 |
| Owner / Email | Customer email | customer@email.com |
| Amount | Monthly amount (EUR) | 416.00 |
| Pipedrive ID | Linked Pipedrive deal (being phased out) | 248123 |
| Referral ID | Referral source if any | |
| Tags | Customer journey classification | new_customer, existing_changing_vehicle, returning_customer, existing_customer_extra_car, existing_pre_del, existing_contract_renewal, existing_changing_contract, new_customer_daily_deal, marketing |

---

## Delivery Fields

| Field | Description |
|-------|-------------|
| Promised Delivery Date Range | Date window offered to customer |
| Delivery Date | Actual delivery date |
| Delivery Status | Delivery Ready, Delivery Planned, Delivery Option Selected |
| Assignee | Responsible agent/location |

---

## Return and Contract Fields

| Field | Description |
|-------|-------------|
| Promised Returned Date | Expected return date |
| Return Date | Actual return date |
| End Contract Date | Contract end date |
| Planned Downpayment Date | When downpayment was/is due |

---

## Vehicle Status Fields

| Field | Description | Known Values |
|-------|-------------|--------------|
| Location | Branch/location | instacar-hq, instacar-anoixh, instacar-pigasou, thessaloniki-cars-airport, 653a59b7... (ID) |
| Stage | Vehicle lifecycle stage | Fleet, Payment Process, Ordered, Defleeted |
| Reservation Type | Booking type | Booked, Predel Temp, Seasonal Cars, Permanent Temp, For Sale |
| Availability Status | Current availability | For Delivery, On Lease ARM, Available, ARM |

---

## Customer Tags Reference

| Tag | Meaning |
|-----|---------|
| new_customer | First-time customer |
| returning_customer | Customer who has leased before |
| existing_customer_extra_car | Existing customer adding a second car |
| existing_changing_vehicle | Customer swapping to a different vehicle |
| existing_changing_contract | Customer changing contract terms |
| existing_pre_del | Customer in pre-delivery phase |
| existing_contract_renewal | Renewing an existing contract |
| new_customer_daily_deal | New customer via daily deal/promo |
| marketing | Marketing-sourced lead |

---

## Related pages
- [[instafleet-subscriptions]]
- [[instafleet]]
- [[instacar-api]]
- [[defleet]]
