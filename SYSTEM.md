# RocketRush Proposal System

## Repository Structure
```
rr-proposals/
├── template.html          ← Master template with {{VARIABLES}}
├── proposals.json         ← Database of all proposals
├── SYSTEM.md              ← This file
└── proposals/
    └── {client-key}.html  ← Individual client proposals
```

## Tech Stack
| Layer | Service | Purpose |
|---|---|---|
| Hosting | GitHub Pages | Serves proposal HTML files |
| Database | Firebase Firestore | Stores signed state universally |
| Images | Cloudinary | Stores client signature images |
| Notifications | Formspree | Emails team on signing |

## Template Variables
| Variable | Description | Example |
|---|---|---|
| {{CLIENT_COMPANY}} | Company name | Alphastar Technologies Private Limited |
| {{CLIENT_GSTIN}} | GSTIN | 06AAWCA0898H1Z4 |
| {{CLIENT_SIGNATORY}} | Signatory name | Ujwal Kalra |
| {{MONTHLY_FEE}} | Fee excl. GST | ₹55,000 |
| {{TOTAL_FEE}} | Fee incl. GST | ₹64,900 |
| {{ENGAGEMENT_LABEL}} | Pilot or Tenure | Pilot |
| {{ENGAGEMENT_CLASS}} | CSS class | pilot |
| {{DURATION_LABEL}} | Period label | Pilot Period |
| {{DURATION_VALUE}} | Duration | 3 months |
| {{NUM_POSTS}} | Monthly posts | 10–12 |
| {{NUM_CONNECTIONS}} | Connection requests | 150 |
| {{CLIENT_COMPANY_KEY}} | URL-safe key | alphastar-technologies |
| {{SPECIAL_NOTE_ROW}} | Extra pricing row | <tr><td>Note</td><td>Text</td></tr> |

## GitHub Pages URL Pattern
https://teamrocketrush-ui.github.io/rr-proposals/proposals/{client-key}.html

## Firebase Config
- Project: rocketrush-proposals
- Collection: signatures
- Document ID: {client-key}
- Fields: signed, date, sigUrl, client, signatory, proposal, timestamp

## Cloudinary Config
- Cloud Name: dsjpiafaa
- Upload Preset: rocketrush_signatures
- Folder: signatures/{client-key}/
- Public ID: {client-key}_client_sig

## Formspree Endpoint
https://formspree.io/f/meebzlwo

## Delete Proposal — Full Cleanup
When deleting a proposal, do ALL THREE:
1. Delete HTML file from GitHub: proposals/{client-key}.html
2. Delete Firestore document: signatures/{client-key}
3. Delete Cloudinary image: signatures/{client-key}/{client-key}_client_sig
