# RocketRush Proposal System — SYSTEM.md

## Repository
- Owner: teamrocketrush-ui
- Repo: rr-proposals
- GitHub Pages: https://teamrocketrush-ui.github.io/rr-proposals

## File Structure
```
rr-proposals/
├── template.html              <- Master proposal template with {{VARIABLES}}
├── proposals.json             <- Database of all proposals
├── SYSTEM.md                  <- This file
└── proposals/
    └── {client-key}.html      <- Individual client proposal pages
```

## Tech Stack
| Layer | Service | Purpose |
|---|---|---|
| Hosting | GitHub Pages | Serves proposal HTML files |
| Signed State | Firebase Firestore | Universal signed state across all devices |
| Signature Images | Cloudinary | Permanent signature image storage |
| Notifications | Formspree | Emails team when proposal is signed |

## Template Variables
| Variable | Description | Example |
|---|---|---|
| CLIENT_COMPANY | Full company name | Alphastar Technologies Private Limited |
| CLIENT_GSTIN | Client GSTIN | 06AAWCA0898H1Z4 |
| CLIENT_SIGNATORY | Signatory full name | Ujwal Kalra |
| MONTHLY_FEE | Fee excl. GST | Rs.55,000 |
| TOTAL_FEE | Fee incl. 18% GST | Rs.64,900 |
| ENGAGEMENT_LABEL | Pilot or Tenure | Pilot |
| ENGAGEMENT_CLASS | CSS class | pilot or tenure |
| DURATION_LABEL | Label for duration | Pilot Period or Contract Duration |
| DURATION_VALUE | Duration value | 3 months or 12 months |
| NUM_POSTS | Monthly posts | 10-12 |
| NUM_CONNECTIONS | Connection requests | 150 |
| CLIENT_COMPANY_KEY | URL-safe key | alphastar-technologies |
| SPECIAL_NOTE_ROW | Extra pricing row | HTML table row or empty string |

## Client Key Format
- Lowercase company name, spaces to hyphens
- Examples:
  - "Alphastar Technologies Private Limited" -> alphastar-technologies
  - "TechCorp India Pvt. Ltd." -> techcorp-india
  - "ABC Solutions" -> abc-solutions

## Proposal URL Pattern
https://teamrocketrush-ui.github.io/rr-proposals/proposals/{client-key}.html

## Firebase Firestore Structure
Collection: signatures
Document ID: {client-key}
Fields: signed, date, sigUrl, client, signatory, proposal, timestamp

## Cloudinary Storage Structure
Folder: signatures/{client-key}/
Public ID: {client-key}_client_sig

## proposals.json Structure
[
  {
    "id": "alphastar-technologies",
    "client_name": "Alphastar Technologies Private Limited",
    "signatory": "Ujwal Kalra",
    "gstin": "06AAWCA0898H1Z4",
    "monthly_fee": "55000",
    "total_fee": "64900",
    "engagement": "Pilot",
    "duration": "3 months",
    "num_posts": "10-12",
    "num_connections": "150",
    "created_date": "29 June 2026",
    "url": "https://teamrocketrush-ui.github.io/rr-proposals/proposals/alphastar-technologies.html"
  }
]

## Delete Proposal - Full Cleanup (always do all 3)
1. Delete HTML from GitHub: proposals/{client-key}.html
2. Delete Firestore document: collection=signatures, doc={client-key}
3. Delete Cloudinary image: public_id=signatures/{client-key}/{client-key}_client_sig
