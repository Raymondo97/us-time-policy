# A Developer's Case for Better U.S. Time Policy

**Draft position statement — October 26, 2026**

## Our purpose

Civil-time law is an input to software infrastructure. When that law changes, an update may need to travel from government text to the IANA Time Zone Database, operating-system and runtime maintainers, distributors, organizations, devices, and applications. Some systems receive the new rules later than others; some may never receive them.

We support **permanent standard time** for its alignment with the position of sleep and circadian-health experts. Separately, we ask lawmakers to treat implementation safety and clear, consistent time-zone rules as nonpartisan engineering requirements, regardless of the permanent-time policy they ultimately choose.

Our technical position is deliberately narrower than saying that one UTC offset is inherently safer for software. It is not.

## What we ask of lawmakers

### 1. Define the transition unambiguously

Legislation and implementing guidance should specify:

- The affected jurisdictions and treatment of existing exceptions.
- Each jurisdiction's applicable UTC offset after the change.
- The exact date and time the new rules first take effect.
- Whether subsequent seasonal transitions remain legal, including under state elections.
- How future modifications will be announced and coordinated with downstream time-zone data distributors.

An unclear effective date or unspecified exception can become inconsistent software behavior across systems and regions.

### 2. Allow adequate deployment time

We request **at least twelve months between final publication of executable time rules and their first effect**, rather than relying solely on the date a bill is introduced or enacted. This is a policy recommendation informed by [IANA's guidance about advance notice and update propagation](https://data.iana.org/time-zones/tz-link.html), not a guarantee that twelve months is sufficient for every product.

Manufacturers, maintainers, platform vendors, enterprise operators, and organizations must be able to integrate, test, ship, and verify the changes. Some unsupported systems may never be updated.

### 3. Minimize unnecessary fragmentation

We recognize that time zones are geographical, not inherently uniform across the country. Regional distinctions are routinely handled by software, and different permanent offsets are not themselves a programming defect.

The avoidable burden comes from additional independently changing rules, particularly when jurisdictions use different seasonal transition dates. We ask Congress to consider how any state-level exemptions will be administered, published, and maintained, including whether they permit continued seasonal clock changes.

### 4. Protect the meaning of future schedules

A UTC timestamp faithfully identifies an instant. It does not by itself preserve the intent of an event defined as *9:00 AM local time in a particular city next year*. If the city's future civil-time rules change, the corresponding UTC instant may change.

Affected systems include calendars, transportation schedules, payroll and shift scheduling, reservations, automated jobs, and systems that exchange time-sensitive records. Not all such systems will fail; the precise impact depends on stored data, software design, and update timing.

For technical context, see [RFC 9557](https://www.rfc-editor.org/rfc/rfc9557.html) and [RFC 5545](https://www.rfc-editor.org/rfc/rfc5545.html).

## Why the 2007 transition matters

The [Energy Policy Act of 2005](https://www.congress.gov/bill/109th-congress/house-bill/6) moved the U.S. spring and fall DST transition dates starting in 2007. Software vendors and IT organizations had substantial advance notice, yet still needed to distribute updates and, in some cases, correct future calendar entries previously created under old rules.

That history shows the **coordination and migration work** involved in a rule change. It does **not** show that the 2007 transition caused a nationwide technology breakdown, nor does it establish an exact cost for a new law. Any monetary cost estimate should be labeled as an estimate and linked to its original source.

## Our preference for permanent standard time

The human-health question deserves its own evidence, rather than being disguised as an engineering theorem. We support permanent standard time because of research and professional positions concerning sleep, circadian alignment, and morning daylight. We intend to document the relevant research, limitations, and competing considerations in a dedicated evidence file.

We also acknowledge that permanent daylight time would remove recurring seasonal clock changes in participating jurisdictions. After the transition, properly maintained systems can represent either permanent policy. Our engineering requests concerning clarity, testing, update lead time, and rule fragmentation apply to both.

We do **not** claim that permanent standard time solves international coordination: neighboring jurisdictions and other countries may use different offsets or seasonal rules.

## Our commitment to accuracy

We will:

- Separate sourced technical facts from interpretation and policy preference.
- Prefer original legislative text, maintained standards, technical vendor documentation, and peer-reviewed scientific literature.
- Correct or retract claims that overstate costs, incidents, or expected failures.
- Welcome substantive critiques, including from engineers who favor permanent DST or existing arrangements.
- Avoid presenting the views of individual maintainers as endorsements from IANA, the IETF, or other organizations.

## Legislative context (checked October 26, 2026)

- [H.R. 139](https://www.govinfo.gov/app/details/BILLS-119hr139rfs) seeks permanent daylight saving time and passed the House in July 2026; it was subsequently referred to a Senate committee.
- [H.R. 9638](https://www.govinfo.gov/app/details/BILLS-119hr9638ih) proposes a standard-time default but provides for state elections to observe daylight saving time. Any assessment of exemptions must use the actual bill language, not just its short title.

These bills may be amended. This document describes positions and principles rather than claiming any particular text will become law.

## Participate

Help document the real engineering impact. Bring primary sources, independently verifiable examples, corrections, and alternatives. The goal is not to speak for every developer; it is to help lawmakers and the public understand what reliable timekeeping legislation requires.
