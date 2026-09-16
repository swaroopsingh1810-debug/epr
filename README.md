# Non-Ferrous Metal EPR — obligation calculator and rules config

Live: https://epr.cognispike.com

Tooling for Extended Producer Responsibility on scrap of non-ferrous metals
(aluminium, copper, zinc and their alloys) in India, under **Chapter VIII** of the
Hazardous and Other Wastes (Management and Transboundary Movement) Rules, 2016,
as inserted by **G.S.R. 438(E)** dated 1 July 2025, in force from 1 April 2026.

Maintained by Cognispike AI Solutions.

## Contents

| Path | What it is |
|---|---|
| `index.html` | The calculator. Self-contained, no dependencies, no build step. |
| `data/nonferrous-epr-rules.yaml` | Machine-readable extraction of Schedules X–XIII and the operative rules. |

## Sourcing rule

Every value in the YAML carries a `src` field pointing at the rule or schedule it
came from. Nothing is taken from a secondary summary, a consultancy blog or a
press note. Where the gazette delegates a value to CPCB, it is recorded under
`cpcb_pending` rather than guessed.

This matters because published guidance on these rules is not reliable. At least
one vendor guide states the FY 2026-27 target as 20% of prior-year sales weight.
Schedule XI says 10%, and the base is not prior-year sales at all.

## Why the calculator returns a range

Schedule XI sets the target as a percentage of the quantity placed on market in
year `Y − X`, where `X` is the average life of the product. Note 2 to Schedule XI
delegates average life to CPCB, which has not published it. No exact FY 2026-27
obligation can be computed by anyone today. The calculator takes a user-supplied
range for `X` and returns bounded output plus the list of outstanding parameters.

## Findings recorded here

- Targets step 10 / 10 / 30 / 30 / 50 / 50 / 75 — a 3x jump in FY 2028-29, not a smooth ramp.
- Seven parameters are delegated to CPCB; three block computation outright.
- Rule 51(3) and the Schedule XIII footnote give different denominators for
  minimum recycled content. For a product 30% aluminium by weight the readings
  differ by more than 6x.
- Rule 49(2): the English text says half-yearly, the Hindi says तिमाही (quarterly).
  The same notification uses अर्धवार्षिक correctly elsewhere, so this is a drafting
  divergence rather than a transcription artefact.
- Schedule XI(ix) puts importers of used goods or scrap at 100% of prior-year
  imports — no average-life lag, and 10x the producer rate in FY 2026-27.
- Verified 16 September 2026: the CPCB Common EPR Portal lists "Scrap of
  Non-Ferrous Metals" as COMING SOON. Rule 45(2) requires online registration on
  that portal, rule 45(5) bars business without registration, rule 46(3) permits
  fulfilment only through it. Rule 50(3)'s six-month deadline falls on
  1 October 2026; the first half-yearly return is due 31 October 2026.

## Updating after a CPCB notification

1. Edit `data/nonferrous-epr-rules.yaml`. Keep the `src` discipline.
2. Bump `meta.config_version`.
3. Mirror any change into `index.html` (target table, pending list, banner).
4. Commit and push. Netlify redeploys automatically.

## Disclaimer

An engineering aid, not legal advice.
