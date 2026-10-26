# Evidence register

**Reviewed October 26, 2026.** This is a living collection of sources and the specific claims they support, not a comprehensive systematic review.

## Evidence labels

- **Documented:** Directly supported by a cited primary source.
- **Engineering inference:** A consequence drawn from documented system behavior; the assumptions must be stated.
- **Policy position:** An explicit preference or recommendation.
- **Unverified:** Not appropriate to present as established fact.

## Engineering and historical sources

### E-01: IANA time-zone updates

**Source:** [IANA time-zone documentation](https://data.iana.org/time-zones/tz-link.html).

**Documented:** Rule changes pass through database maintenance, downstream vendors, testing, and distribution. Devices may run outdated data indefinitely. IANA recommends that governments announce changes at least a year before they affect clocks.

**Limit:** One year is guidance, not a guarantee of safe deployment everywhere.

### E-02: IETF time-zone annotation standard

**Source:** [RFC 9557](https://www.rfc-editor.org/rfc/rfc9557.html) (2024).

**Documented:** Geographic time-zone rules and numeric UTC offsets differ. An offset and named-zone annotation can disagree after the rules change or when systems use different data. The RFC does not define a full model for future floating civil-time schedules.

**Limit:** This does not establish that every calendar application is vulnerable.

### E-03: Calendar interoperability

**Source:** [RFC 5545 (iCalendar)](https://www.rfc-editor.org/rfc/rfc5545.html) (2009).

**Documented:** Recurring events and local timestamps require explicit calendaring and zone rules, including transitions.

### E-04: The 2007 DST extension

**Source:** [Energy Policy Act of 2005](https://www.congress.gov/bill/109th-congress/house-bill/6); see archived Microsoft guidance and contemporaneous institutional reports for migration details.

**Documented:** Congress changed the seasonal transition dates effective in 2007, and organizations prepared OS, application, and calendar updates with substantial advance notice. Outlook/Exchange calendar rebasing illustrates coordination work.

**Limit:** The transition was not a nationwide software collapse. Contemporary industry cost forecasts should not be stated as realized losses.

## Health and science

### S-01: Sleep medicine position

**Source:** [American Academy of Sleep Medicine position statement](https://pubmed.ncbi.nlm.nih.gov/37904574/) (2024), *Permanent standard time is the optimal choice for health and safety*.

**Documented:** The authors recommend permanent standard time based on sleep and circadian-health considerations including morning light.

**Limit:** Separate an expert organization's position from the quantitative findings of individual underlying studies. Avoid treating forecasts of permanent-DST effects as already observed national outcomes.

## Legislative primary sources

### L-01: Sunshine Protection Act, H.R. 139

**Sources:** [Senate-referred text](https://www.govinfo.gov/content/pkg/BILLS-119hr139rfs/html/BILLS-119hr139rfs.htm) and [House vote 238](https://clerk.house.gov/Votes/2026238).

**Documented:** The House passed the bill July 14, 2026 (308–117). The Senate received it July 15. It advances statutory offsets, with choices for previously exempt jurisdictions. No explicit postponed effective date appears in the referred text.

### L-02: Sunshine for Our Kids Act, H.R. 9638

**Source:** [Introduced House text](https://www.govinfo.gov/content/pkg/BILLS-119hr9638ih/html/BILLS-119hr9638ih.htm).

**Documented:** The proposal makes standard time the default but lets states advance their clocks by an hour, year-round **or for part of a year**, under geographic conditions. The amendment takes effect on the first Sunday in November after enactment.

**Limit:** Introduced bill text is not law and may be amended.

## Claims we do not make

- Permanent standard time is inherently simpler for computers to calculate than permanent DST.
- State differences necessarily cause outages or database corruption.
- UTC alone preserves the intent of every future local appointment.
- The 2007 change caused universal failures or a verified multibillion-dollar loss.
- IANA, IETF, AASM, or the software industry endorses this project.

## Adding evidence

Record the claim, original source URL, author or publisher, publication date, relevant section, direct support, limitations, and any credible counterevidence. Distinguish observed incidents from projections and policy preferences.
