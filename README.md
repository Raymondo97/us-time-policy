# U.S. Time Policy: A Software Engineering Perspective

**A public, evidence-based discussion of how U.S. civil-time legislation affects software, scheduling, and infrastructure.**

This project advocates **permanent standard time** while keeping its engineering analysis separate from its public-health and policy preferences. Our technical asks apply regardless of which time policy Congress adopts: clear legal rules, predictable transitions, adequate advance notice, and limited unnecessary fragmentation.

> **Status:** Early public draft, October 26, 2026. Not affiliated with IANA, the IETF, any standards body, or a medical organization. This is not a claim of industry consensus.

## Why this exists

Time-zone policy affects more than the clock on a wall. Changes must propagate through operating systems, programming runtimes, mobile devices, servers, databases, container images, calendar applications, and integrations. Previously scheduled future events can require special handling when the rules change.

The 2007 U.S. DST extension illustrates the coordination burden. Vendors and organizations prepared patches and calendar-migration procedures after the Energy Policy Act of 2005 changed the transition dates. The transition was not a nationwide software catastrophe; it nevertheless required substantial preparation and exposed real compatibility problems.

Our goal is to document those issues precisely, explain the trade-offs, and propose policy requirements that engineers can evaluate independently of their preferred clock setting.

## Our position

1. **Policy preference:** We support permanent standard time, informed by sleep and circadian-health research. This is a public-policy position, not a conclusion derived from computational complexity.
2. **Engineering requirement:** Any enacted rule should define exactly which jurisdictions are affected, their offsets and transition instants, and the effective date.
3. **Engineering recommendation:** Provide **at least 12 months between finalized rules and the first affected clock transition**, allowing time for updates, testing, and distribution. Longer notice may be necessary for some deployments.
4. **Engineering recommendation:** Avoid unnecessary jurisdiction-specific and seasonal exceptions. Existing regional time zones are normal and supported; the concern is multiplying independently changing rules and transitions.
5. **Technical accuracy:** Permanent standard time and permanent DST are both representable in time-zone databases. Neither eliminates the need to maintain historical data or account for other countries' rules.

Read the detailed [manifesto](MANIFESTO.md).

## Legislation being tracked

**As checked October 26, 2026:**

- **H.R. 139, Sunshine Protection Act of 2025:** Passed the House on July 14, 2026; referred to the Senate Committee on Commerce, Science, and Transportation on July 15. [Official House vote](https://clerk.house.gov/Votes/2026238) · [GovInfo Senate-referred bill record](https://www.govinfo.gov/app/details/BILLS-119hr139rfs)
- **H.R. 9638, Sunshine for Our Kids Act of 2026:** Introduced July 9, 2026 and referred to the House Energy and Commerce Committee. Its introduced text would make standard time the default while allowing states to elect daylight saving time under specified conditions. [GovInfo official introduced text](https://www.govinfo.gov/content/pkg/BILLS-119hr9638ih/pdf/BILLS-119hr9638ih.pdf) · [Bill record](https://www.govinfo.gov/app/details/BILLS-119hr9638ih)

**Bill status can change.** Verify the latest official record before quoting these descriptions publicly.

## The core engineering distinction

| Question | What we can support |
| --- | --- |
| Are law changes risky to deploy? | Yes. Time-zone data and dependent applications do not necessarily update together. |
| Can a future appointment move by an hour? | Yes, if the time-zone rules for its intended local time change. |
| Does UTC solve every scheduling issue? | No. A future *local* appointment must preserve its geographic and civil-time intent. |
| Is permanent standard time inherently easier to compute than permanent DST? | No. After the transition, both can use stable offsets. |
| Do state-level rules necessarily break software? | No. Location-specific rules are already supported; additional independent changes increase coordination and testing work. |

## References to start with

- [IANA: Time Zone and Daylight Saving Time Data](https://data.iana.org/time-zones/tz-link.html) — distribution, updates, and coordination with governments.
- [IETF RFC 9557](https://www.rfc-editor.org/rfc/rfc9557.html) — time-zone annotations, rule changes, and inconsistent timestamp interpretations.
- [IETF RFC 5545](https://www.rfc-editor.org/rfc/rfc5545.html) — calendaring and recurring-event representations.
- [House Clerk H.R. 139 vote](https://clerk.house.gov/Votes/2026238) and [GovInfo H.R. 9638 text](https://www.govinfo.gov/content/pkg/BILLS-119hr9638ih/pdf/BILLS-119hr9638ih.pdf) — primary legislative records.

## Contributing

The initial release consists of this README and [MANIFESTO.md](MANIFESTO.md). We welcome factual corrections, reproducible engineering examples, sources supporting or challenging individual claims, and discussion of alternative time policies.

Please distinguish **documented facts**, **engineering inferences**, and **policy preferences**. Do not claim endorsement by standards maintainers, medical groups, or the developer community without explicit permission. Keep discussion about trade-offs and evidence rather than personal attacks.

**Planned next additions:** `EVIDENCE.md`, `LEGISLATION.md`, `TECHNICAL-IMPACT.md`, contributor guidance, and small independently runnable examples.

## Scope and independence

This is a civic and technical advocacy project, not a software package, a replacement time-zone database, or an official standards process. Nothing here guarantees that a particular law will cause a given outage. The repository's positions and evidence are intended to remain open to correction.
