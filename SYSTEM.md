# RocketRush Proposal System

## Repository Structure
- `template.html` — Master proposal template with {{VARIABLES}}
- `proposals.json` — Database of all created proposals
- `proposals/` — Individual client proposal HTML files

## Template Variables
| Variable | Description |
|---|---|
| {{CLIENT_COMPANY}} | Client company name |
| {{CLIENT_GSTIN}} | Client GSTIN number |
| {{CLIENT_SIGNATORY}} | Client signatory full name |
| {{MONTHLY_FEE}} | Monthly fee excl. GST (e.g. ₹55,000) |
| {{TOTAL_FEE}} | Monthly fee incl. GST (e.g. ₹64,900) |
| {{ENGAGEMENT_LABEL}} | Pilot or Tenure |
| {{ENGAGEMENT_CLASS}} | pilot or tenure (CSS class) |
| {{DURATION_LABEL}} | Pilot Period or Contract Duration |
| {{DURATION_VALUE}} | e.g. 3 months or 12 months |
| {{NUM_POSTS}} | Number of monthly posts (e.g. 10-12) |
| {{NUM_CONNECTIONS}} | Number of connection requests (e.g. 150) |
| {{CLIENT_COMPANY_KEY}} | URL-safe client key (e.g. alphastar-technologies) |
| {{SPECIAL_NOTE_ROW}} | Optional extra row in pricing table, or empty string |

## GitHub Pages URL Pattern
https://teamrocketrush-ui.github.io/rr-proposals/proposals/{client-key}.html

## Cloudinary Config
- Cloud Name: dsjpiafaa
- Upload Preset: rocketrush_signatures
- Folder: signatures

## Formspree Endpoint
https://formspree.io/f/meebzlwo
