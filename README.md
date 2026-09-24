# PagePilot — Facebook Page Automation Demo

[![Static Website](https://img.shields.io/badge/type-static%20demo-1b63b7)](#current-scope)
[![Responsive](https://img.shields.io/badge/layout-responsive-10b981)](#features)
[![License](https://img.shields.io/badge/license-not%20specified-lightgrey)](#license)

PagePilot is a polished, interactive product demo for a single Facebook Page automation system. It is designed for presenting the product concept to clients and demonstrating how Messenger conversations, automatic replies, orders, rules, FAQs, and safety controls could work from one admin workspace.

The current repository contains a browser-based frontend demo. It does **not** connect to Facebook, an AI provider, or a production database yet.

## Features

### Operations dashboard

- Daily conversation and reply metrics
- Conversation activity chart
- Priority queue for human attention
- Reply-source breakdown
- Facebook Page, product catalogue, and AI health indicators

### Inbox

- Messenger-style conversation list
- Needs-human and order filters
- Conversation search
- Manual reply interaction
- Human takeover workflow
- Responsive mobile conversation navigation

### Orders

- Messenger order pipeline
- Search and status filtering
- Placed, confirming, and cancelled states
- CSV export

### Rules and FAQ

- Add reply rules
- Enable or pause individual rules
- Add approved FAQ answers
- View FAQ categories and match counts

### Settings

- Off, Shadow, and Live operating modes
- Business hours
- AI provider, model, confidence, and system instructions
- Protected demo input for an API key
- Delivery charges and order-confirmation vocabulary
- Complaint escalation, approval, reply-cap, and fallback controls
- Emergency kill-switch interaction

Settings entered in the demo are stored in the current browser where appropriate. The API-key field is excluded from browser storage and cleared immediately after submission.

## Run locally

### Requirements

- Git
- Python 3, or any static HTTP server

### Setup

```bash
git clone https://github.com/thowfique041/facebook-page-automation-demo.git
cd facebook-page-automation-demo
python3 -m http.server 4173 --directory dist
```

Open [http://localhost:4173](http://localhost:4173) in a browser.

Stop the local server with `Ctrl + C`.

### Update an existing local copy

```bash
cd facebook-page-automation-demo
git pull origin main
python3 -m http.server 4173 --directory dist
```

If the browser still displays an older version, use a hard refresh:

- Windows/Linux: `Ctrl + Shift + R`
- macOS: `Cmd + Shift + R`

## Project structure

```text
facebook-page-automation-demo/
├── .openai/
│   └── hosting.json
├── dist/
│   ├── index.html
│   ├── styles.css
│   └── app.js
└── README.md
```

The project has no build step and no package dependencies. The `dist` directory is the complete static website.

## Current scope

This repository is a client-facing interactive prototype. The conversations, orders, rules, FAQs, metrics, and system-health data are illustrative. No real customer data is included.

The following production capabilities are not implemented yet:

- Meta webhook verification and event processing
- Sending Messenger and comment replies through the Graph API
- Secure authentication and staff permissions
- PostgreSQL persistence
- Server-side AI-provider integration
- Product, price, and stock synchronization
- Durable outbox, retries, and delivery tracking
- Real order creation and duplicate protection
- Audit logs and history import
- Health checks, rate limiting, and scheduled cleanup

## Security notes

Never place a real API key, Facebook Page token, app secret, password, or customer data in this static repository.

The API-key field demonstrates the intended user experience only. It masks the typed value, blocks normal copy/cut actions, does not write the value to browser storage, and clears it after Save. A browser-only application cannot guarantee secret confidentiality because users with access to the browser can inspect runtime memory and network traffic.

A production implementation must:

1. Receive credentials through an authenticated backend.
2. Encrypt secrets at rest or use a managed secret store.
3. Make AI and Meta API requests only from the server.
4. Keep secrets out of frontend code, browser storage, logs, and Git history.

## Production roadmap

1. Add a TypeScript backend and PostgreSQL database.
2. Implement authentication, roles, and audit logging.
3. Connect Meta webhooks and the Graph API.
4. Add durable conversations, messages, orders, rules, and FAQs.
5. Integrate AI providers through server-side secrets.
6. Test in Shadow mode before enabling live replies.

## Browser support

The demo targets current versions of Chrome, Edge, Firefox, and Safari. It supports desktop, tablet, and mobile layouts.

## License

No open-source license has been added. Unless a license is provided later, the repository remains publicly viewable but all rights are reserved by the repository owner.
