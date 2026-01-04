# PROJECT_SPEC.md

## Project Name
QuickQueue

## Vision
QuickQueue is a lightweight, mobile-first virtual queue management application designed for small businesses to replace physical waiting lines. The platform allows customers to join queues using QR codes or shareable links and provides real-time position updates to improve the waiting experience while helping businesses manage customer flow more efficiently.

## Non-Goals
- No support for payments or monetization in Phase 1.
- No advanced analytics dashboards.
- No multi-location management or organization-level aggregation.

## Functional Requirements
- **Customer Queue Interaction:**
  - Join queue via QR code or unique link.
  - View real-time queue position and estimated waiting time.
  - Receive optional browser push notification when next in line.
- **Business Management Interface:**
  - Staff dashboard to view and manage active queues.
  - Simple authentication via magic link (email-based, no passwords).
  - Ability to mark customers as “served” or “no-show.”
- **Queue Configuration:**
  - Create and name queues.
  - Define service type and optional estimated service duration.
  - Set maximum queue capacity (optional).
- **System Behavior:**
  - Real-time updates using WebSockets or long polling.
  - Mobile-first responsive design.
  - Basic metrics (active queue length, average wait time).

## Non-Functional Requirements
- **Performance:** Queue updates must propagate to clients within 2 seconds.
- **Availability:** Target 99.5% uptime.
- **Scalability:** Support up to 100 concurrent queues per small business.
- **Security:** Magic link tokens expire within 15 minutes; enforce HTTPS.
- **Privacy:** No user accounts or persistent personal data storage.

## Constraints
- Web-only MVP (no native app in Phase 1).
- Hosted on a managed cloud (e.g., Firebase, Vercel, or AWS Amplify).
- Relies on browser-based notifications (no SMS).

## Architecture Assumptions
- Frontend: React (Next.js or Vite) + TailwindCSS.
- Backend: Serverless functions (Node.js runtime).
- Data store: Firestore or DynamoDB (for queues and session state).
- Realtime updates via Firebase Realtime DB or WebSocket gateway.
- Auth: Magic link implemented via Firebase Authentication or Magic.link API.

## Quality Bars
- Fully functional queue creation and joining flow tested on mobile browsers.
- Latency for real-time updates under 2 seconds.
- 95% of user interactions must be successful without page reloads.
- Simple, intuitive UX requiring <2 taps to join queue.

## Configurability
- Businesses can rename queues and define queue capacity.
- Estimated service duration adjustable per queue.
- Push notifications toggle for customers.

## Observability & Debugging
- Centralized logging for queue events (create, join, serve).
- Client event logs stored locally for debugging.
- Health checks for backend functions.

## Future Phases
- Phase 2: Multi-location management and analytics dashboard.
- Phase 3: Payment integrations and business insights.
- Phase 4: Native mobile apps.

## Open Assumptions
- Small businesses will be comfortable using magic links over traditional login.
- Customer browsers will allow push notifications.
- Businesses are expected to operate single queues per physical location.

## Summary
QuickQueue aims to deliver a minimal yet robust MVP that eliminates physical waiting lines with real-time digital queues, focusing on simplicity, speed, and reliability for small business adoption.
