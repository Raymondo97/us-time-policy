# U.S. civil-time legislation

**Status snapshot: October 26, 2026.** This page describes versions of proposed bills, not enacted federal law. Check current records before quoting it.

| | H.R. 139 | H.R. 9638 |
| --- | --- | --- |
| Name | Sunshine Protection Act of 2025 | Sunshine for Our Kids Act of 2026 |
| Version reviewed | [Senate-referred](https://www.govinfo.gov/content/pkg/BILLS-119hr139rfs/html/BILLS-119hr139rfs.htm) | [Introduced in House](https://www.govinfo.gov/content/pkg/BILLS-119hr9638ih/html/BILLS-119hr9638ih.htm) |
| Status | House passed July 14, 2026; Senate committee referral July 15 | Introduced and referred to House committee July 9, 2026 |
| Main proposal | Advance the statutory standard-time offsets, producing year-round advanced clock settings | Retain standard-time default, with state elections to advance clocks |
| Exceptions | Previously exempt jurisdictions can choose offsets as specified | Eligible states can advance time year-round **or for part of a year** |
| Timing | No express delayed effective date in reviewed text | First Sunday in November after enactment |

Sources: [House Clerk vote](https://clerk.house.gov/Votes/2026238), [H.R. 139 official text](https://www.govinfo.gov/app/details/BILLS-119hr139rfs), [H.R. 9638 official text](https://www.govinfo.gov/app/details/BILLS-119hr9638ih).

## H.R. 139: implementation considerations

Section 2 repeals the federal seasonal rule and advances enumerated statutory time-zone offsets. It preserves a choice for jurisdictions **already exempt** under the prior law; this is not a new, unrestricted state election. The reviewed text does not specify a delayed effective date.

Questions for implementers: Which exact UTC instant starts each new offset? How are existing exceptions communicated? How much lead time will database and platform maintainers receive? What guidance will accompany new future schedules?

## H.R. 9638: implementation considerations

The introduced text permits eligible states to advance clocks by an hour year-round or for part of the year. For states with one time zone, the state-wide rule applies; for multi-zone states, elections are constrained to the entire state or relevant entire time-zone portions. **It does not authorize arbitrary county-by-county choices.** Nevertheless, separately changing seasonal rules could remain possible.

Its specified November effective date may provide differing lead times depending on enactment date. Later state elections would create their own notification and distribution questions.

## What both policies have in common

Both require time-zone data updates for affected jurisdictions. Both can be represented in ordinary geographic time-zone databases. Both require historical time-zone rules to remain available. Additional independent changes can increase testing and coordination work, but do not inherently break well-designed software.

## Repository positions

- **Policy:** Prefer permanent standard time.
- **Implementation:** Publish unambiguous jurisdictional scope, offsets, and transition instants.
- **Notice:** Allow at least 12 months from finalized, implementable rules to first affected clock change, consistent with [IANA's general recommendation](https://data.iana.org/time-zones/tz-link.html).
- **Exceptions:** Minimize independently changing seasonal rules while recognizing normal geographic time-zone distinctions.

## Updating this document

Consult [H.R. 139 on Congress.gov](https://www.congress.gov/bill/119th-congress/house-bill/139) and [H.R. 9638 on Congress.gov](https://www.congress.gov/bill/119th-congress/house-bill/9638). Record the **bill version**, action date, chamber, updated exceptions and effective date. Never silently apply language from one bill version to another.
