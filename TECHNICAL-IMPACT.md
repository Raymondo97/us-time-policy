# Technical impact of civil-time changes

**Reviewed October 26, 2026.** This document explains mechanisms and testable risks; it does not predict outages.

## Four different concepts

| Concept | Example | Implication |
| --- | --- | --- |
| Instant | `2027-03-20T13:00:00Z` | Identifies one moment regardless of legislation |
| Wall time | `09:00` | Requires place and date for conversion |
| UTC offset | `-04:00` | May differ when legislation changes |
| Named zone | `America/New_York` | Identifies a geographic rule set that may change over time |

A fixed UTC instant is not the same as a future appointment whose intent is *9:00 AM local time in New York*. A future rule change can alter which UTC instant represents that appointment.

## Example: March 2007

Under pre-2007 U.S. rules, **March 20, 2007, 9:00 AM New York** was UTC−05:00, corresponding to **14:00 UTC**. Under the enacted 2007 rules, it was UTC−04:00, corresponding to **13:00 UTC**. The local meeting time was unchanged, but its correct instant moved.

This does not mean every historical calendar entry shifted; systems preserving local intent or applying migrations could avoid the problem.

## Example: inconsistent time-zone data

If service A uses older zone data and service B uses newer data for a future date affected by law, they may compute different instants for the same local meeting. Updating a host OS does not guarantee that every embedded runtime, container image, mobile device, or calendar library has the new data. Consult [IANA's distribution guidance](https://data.iana.org/time-zones/tz-link.html).

## Nonexistent and repeated times

Spring-forward transitions skip some wall-clock times; fall-back transitions repeat some. A fixed year-round offset removes **recurring seasonal** gaps and overlaps in that jurisdiction after the change, but historical transitions and any initial transition still require attention.

## Systems worth auditing

- **Calendars and reservations:** Future and recurring appointments, invitations, cancellations, notifications.
- **Workforce and payroll:** Shift schedules, cutoffs, local business-day definitions, overtime calculations.
- **APIs and databases:** Explicit instant-vs-local-time semantics; do not infer named zones from raw numeric offsets.
- **Scheduled tasks:** “Every 24 hours” is different from “every day at 02:00 local.”
- **Platforms and devices:** Container tzdata, language-runtime bundles, embedded devices, offline clients.
- **Integrations:** Producer and consumer may interpret an event with different rules or different semantics.

These are inspection areas, not assertions that specific products are broken.

## Permanent standard time versus permanent DST

| Dimension | Permanent standard time | Permanent DST |
| --- | --- | --- |
| Seasonal transitions after implementation | Removed | Removed |
| Stable future offset | Yes | Yes |
| Time-zone database updates | Generally needed | Generally needed |
| Historical transitions remain relevant | Yes | Yes |
| Computational complexity | Comparable | Comparable |
| Present winter UTC offset in most DST-observing regions | Generally retained | Advanced one hour |
| Regional exceptions | Depend on legislation | Depend on legislation |

**Engineering inference:** Independently changing seasonal schedules increase coordination and regression testing. Different geographic permanent offsets are already routinely supported by mature libraries.

## Suggested reproducible tests

1. Convert historical instants with correct historical zone rules.
2. Recompute a future local event under explicit old and new rules.
3. Exercise recurrence across a skipped or repeated hour.
4. Demonstrate two services using deliberately different time-zone data.
5. Confirm fixed-instant jobs versus local-wall-clock jobs.
6. Include a non-seasonal zone such as `America/Phoenix`.

Tests should pin or simulate the relevant zone rules rather than depending on an unrecorded installed tzdata version.

## Sources and boundaries

- [IANA time-zone guidance](https://data.iana.org/time-zones/tz-link.html)
- [RFC 9557 — Timestamps with Additional Information](https://www.rfc-editor.org/rfc/rfc9557.html). **Important:** RFC 9557 explicitly does not provide a complete representation for future floating local schedules.
- [RFC 5545 — iCalendar](https://www.rfc-editor.org/rfc/rfc5545.html)
- [Energy Policy Act of 2005](https://www.congress.gov/bill/109th-congress/house-bill/6)
