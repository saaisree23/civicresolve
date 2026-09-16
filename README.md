# CivicResolve

**From Community Challenges to Collaborative Solutions**
Prototype built for Smart India Hackathon 2026 — Problem Statement: "A digital platform to crowdsource societal challenges and facilitate collaborative problem solving through universities and industry partnerships."

This is a fully clickable, working prototype. There is no real backend — data is
held in a central React context and persisted to the browser's `localStorage`,
so the workflow stays consistent as you navigate and even survives a page refresh.

## Tech stack

- React 19 + Vite
- React Router
- Tailwind CSS v4
- lucide-react icons
- Mock auth, mock AI classification, mock notifications — all client-side

## Getting started

```bash
npm install
npm run dev
```

Then open the URL Vite prints (typically http://localhost:5173).

To create a production build:

```bash
npm run build
npm run preview
```

## Demo script (2-3 minutes)

1. On the landing page, click Get Started -> choose Citizen -> Login as Citizen.
2. Click Report New Challenge, fill in a title/description (try mentioning
   "repeatedly" or "recurring" to trigger a Complex classification, or leave
   it simple for a Routine one), add a photo, set a location, submit.
3. Watch the AI Classification animation, review the category/priority/
   complexity result, then continue to Smart Matching -- you'll see it branch
   to either the Municipality or the University & Industry Dashboard.
4. Logout, then Login as Student / Faculty / Industry Expert (for a complex
   challenge) or Login as Municipality (for a routine one).
5. Open the new challenge:
   - Municipality: Assign to my team -> In Progress -> Resolved.
   - University/Industry: Claim Challenge / Join Team -> open the
     Collaboration Workspace (discussion, ideas, documents, tasks, progress)
     -> Submit Proposed Solution -> Mark as In Progress -> Mark as Resolved.
6. Logout and log back in as Citizen -> open My Challenges -> see the
   updated timeline and status -> leave a star rating + feedback once resolved.
7. Check the notification bell at any point -- every action above fires a
   mock notification to the relevant role.

Three realistic sample challenges are preloaded on first run (one routine,
two complex, one of which already has an active collaboration) so the
dashboards aren't empty even before you submit anything yourself.

## Project structure

```
src/
  store/             Central state (AppContext), seed data, AI classification logic
  components/        Shared UI: Navbar, DashboardLayout, ChallengeCard, Timeline,
                      Badges, Modal, FileUpload, LocationPicker, NotificationBell, etc.
  pages/
    Landing.jsx, Login.jsx, Explore.jsx, FutureScope.jsx
    citizen/          Dashboard, Submit form, AI/matching screen, tracking, feedback
    municipality/      Dashboard, challenge details + status updates
    uni/               Combined University & Industry dashboard, claim/collaborate,
                       solution submission
```

## Notes for judges

- AI classification is a transparent rule-based simulation (see
  `src/store/classify.js`) -- it is explicitly not presented as a trained model,
  in line with the project's "AI classifies and matches, it does not solve"
  principle.
- The Future Scope page (linked from the landing page About section)
  lists ideas that are intentionally not implemented in this build, such as
  automatic escalation of overdue challenges.
- Photos are compressed client-side before being stored, and demo seed
  photos are pulled from picsum.photos placeholders -- an internet connection
  is needed to see those images.
