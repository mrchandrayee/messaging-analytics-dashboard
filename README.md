# Messaging Analytics Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/messaging-analytics-dashboard/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

A runnable frontend reconstruction of the uploaded 5-second screen recording (720 × 1280, 30 fps).

## Run locally
1. Extract `messaging-analytics-dashboard.zip`.
2. Open `index.html` in Chrome, Firefox, Safari or Edge.
3. No npm install or build step is required.

Optional local server:
```bash
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

## What is visible in the video

The video is headed **“Messaging Analytics Dashboard”**. The dashboard greeting reads **“Good afternoon, Noor”** and the subtitle reads **“Here's how your conversations moved today.”** The UI uses a warm ivory canvas, near-black plum sidebar, terracotta/orange audience card, purple accents and rounded white metric cards.

### Overview dashboard
- Audience: 4,853; 315 new in October; LIVE indicator; monthly bar chart.
- Delivery rate: 94.1%; 312 queued; +1.4% indicator.
- Active campaigns: 18 / 40; 6 scheduled; +3 this week.
- Credits: $1,820 balance; $420 of $600 monthly budget; 13 days left.
- Messages sent: 121,506; 1,887 today; +12%; 30d / 7d toggle and line chart.
- Messages by month: Replied / Awaiting reply; 2026 / 2025 toggle.
- Channel mix: SMS, WhatsApp and Email; This month / Last toggle.

The initial video frame shows the dashboard still loading/initializing with values such as Audience 1,583, Delivery 16.7%, Active campaigns 0/40, Credits $0 and Messages sent 0. Values rise as the recording progresses.

### Reports page
The video navigates to **Reports** with subtitle “How your messaging performs over time”. Visible controls include 7d / 30d / 90d / 12m, channel filters All / SMS / WhatsApp / Email, date range Oct 2 – Oct 31 and Export CSV.

Visible report metrics:
- Messages sent: 63,770 (+5.5%)
- Delivery rate: 50.0% (No change)
- Reply rate: 3.6% (+0.3 pts)
- Median first response: 1.7 min (−0.5%)
- Messages by channel chart: SMS, WhatsApp, Email.

### Campaigns page
The video navigates to **Campaigns**, showing “13 campaigns · 3 scheduled”.

Summary metrics:
- Messages sent: 11,360 across 7 campaigns in the last 30 days.
- Average delivery rate: 89.0%.
- Average reply rate: 6.3%.
- Link clicks: 1,451.

The table has All / Sent / Sending / Scheduled / Draft / Paused filters, campaign search, sort, and New campaign. Readable campaign rows include:
- Loyalty points expiring — SMS — Scheduled.
- Holiday gift guide — Email — Scheduled.
- Black Friday teaser — SMS — Scheduled.
- Weekend pop-up reminder — WhatsApp — Sending.

## Readable original source fragment

The lower code preview is titled `src/main.ts`. The video clearly exposes the beginning of a function named `markRail` (lines 1–14). The visible code is transcribed below. The final visible `gsap.to` line is cut off at the bottom edge of the preview, so its missing arguments are not guessed.

```ts
function markRail(name: RouteName, animate: boolean) {
  railLinks.forEach((a) => {
    a.classList.toggle('is-active', a.dataset.route === name);
  });
  const link = railLinks.find((a) => a.dataset.route === name);
  if (!link) return gsap.to(pill, { opacity: 0, scale: 0.6 });
  // Offsets ignore transforms: a pressed icon can't throw the pill
  const icon = link.querySelector<HTMLElement>('.rail__icon');
  let x = 0, y = 0;
  for (let n = icon; n && n !== railList; n = n.offsetParent) {
    x += n.offsetLeft; y += n.offsetTop;
  }
  if (!animate) return gsap.set(pill, { x, y });
  gsap.to(pill, { x, y, opacity: 1, scale: 1, duration: 0.8,
```

This is a partial source transcription, not a complete original source file. The recording does not expose the imports, `RouteName` / `railLinks` / `railList` declarations, the remaining function body, or the original app source repository.

## Interactions included in this reconstruction
- Sidebar navigation between Overview, Inbox, Campaigns, Automations, Contacts, Credits and Templates, plus Reports.
- Overview audience/message counters with lightweight live demo increments.
- 30d / 7d message chart toggle.
- Reports period filters and channel filters update the visible summary metrics.
- Export report summary as CSV.
- Campaign status filters, search and sorting.
- Open a campaign row to inspect it; edit campaign name/channel; pause/resume.
- Create a campaign in the local demo table.
- Add credits demo dialog.
- Sync status button.
- Global search routes to campaign search.
- Responsive layout for tablet and mobile widths.

## Project files
- `index.html` — page markup and views.
- `styles.css` — layout, cards, charts, responsive design and colors.
- `app.js` — dashboard rendering, navigation, filters, campaign interactions and demo values.
- `README.md` — source observations and run guide.

## Accuracy and limitations
The video shows a running application and a small partial source preview, not a complete source editor or repository. The `markRail` fragment above is the readable source transcription; the rest of the app is reconstructed from the visible interface, labels, sample values and interactions. Data is illustrative and live counter changes are simulated in the browser. There is no messaging provider connection, contact database, real delivery status, billing/credits backend, campaign scheduler, authentication or persistence. CSV export is a local report snapshot only.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
