<div align="center">

# Queens Match

**A full-stack mentoring platform that connects women in tech with mentors, schedules sessions, and gives program admins visibility into matching and referrals.**

[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=white)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14+-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Material UI](https://img.shields.io/badge/MUI-v5-007FFF?style=for-the-badge&logo=mui&logoColor=white)](https://mui.com/)
[![JWT](https://img.shields.io/badge/Auth-JWT%20%2B%20httpOnly-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)](https://jwt.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)

React · Express · PostgreSQL · Material UI · Jest · Nodemailer

<br />

<img src="docs/screenshots/01-home.png" alt="Queens Match landing page" width="88%" />

<sub>Landing page — English, Hebrew, and Arabic UI, AppsFlyer × QueenB Bootcamp 2026 branding</sub>

</div>

---

## Overview

Queens Match is a production-style mentoring product: mentees browse mentor profiles, request sessions, and pick a time; mentors propose slots, reschedule, or decline; admins inspect users, matchings, a meeting calendar, and a referral funnel. The stack is a React SPA with an Express REST API, PostgreSQL, cookie-based JWT authentication, and optional email notifications.

This is **not** the original QueenB task-management template. The repository implements a real matching lifecycle, admin analytics, and multilingual UX on top of that bootcamp starter.

---

## Project background

Queens Match was built during the **AppsFlyer × QueenB Bootcamp 2026**.

[QueenB](https://www.queenb.org.il/) is a non-profit that supports women entering technology. [AppsFlyer](https://www.appsflyer.com/) partnered with the bootcamp as an industry host. The product theme — meaningful mentor–mentee connections in tech — is reflected in the landing copy, bilingual/trilingual UI, and the matching workflow.

The footer across authenticated and public pages carries the Bootcamp 2026 partnership branding.

---

## Product gallery

Screenshots below were captured from a local run against **synthetic QA accounts** (`@queenb.test`). They do not contain real user PII.

### Authentication and mentee experience

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/03-sign-in.png" alt="Sign in page" />
      <p align="center"><sub>Cookie-based sign-in with validation and rate limiting on the API</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/02-sign-up.png" alt="Sign up page" />
      <p align="center"><sub>Registration with email, username, and password policy checks</sub></p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/04-dashboard.png" alt="User dashboard" />
      <p align="center"><sub>Post-login dashboard: browse mentors or become a mentor</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/05-mentors-directory.png" alt="Mentors directory" />
      <p align="center"><sub>Active mentor directory with role, stack, and topics</sub></p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/06-mentor-profile.png" alt="Mentor profile" />
      <p align="center"><sub>Mentor profile, share attribution (WhatsApp / LinkedIn / copy link), request session</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/07-my-requests.png" alt="My requests list" />
      <p align="center"><sub>Mentee request list with status filters</sub></p>
    </td>
  </tr>
</table>

<p align="center">
  <img src="docs/screenshots/08-matching-details.png" alt="Matched request details" width="88%" />
  <br />
  <sub>Matched request: confirmed meeting time, one-time reschedule, and cancel</sub>
</p>

### Mentor workflow

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/09-mentor-inbox.png" alt="Mentor inbox" />
      <p align="center"><sub>Mentor inbox: propose slots, reject, reschedule, or cancel</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/10-become-mentor.png" alt="Become a mentor form" />
      <p align="center"><sub>Create or edit a mentor profile (job, stack, topics, capacity)</sub></p>
    </td>
  </tr>
</table>

### Admin operations

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/11-admin-calendar.png" alt="Admin calendar" />
      <p align="center"><sub>Admin calendar of selected meeting times (matched vs cancelled)</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/12-admin-users.png" alt="Admin users table" />
      <p align="center"><sub>Admin user directory with search and matching counts</sub></p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/14-admin-matchings.png" alt="Admin matchings report" />
      <p align="center"><sub>Matchings report with status and participant filters</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/16-admin-analytics.png" alt="Admin analytics dashboard" />
      <p align="center"><sub>Referral funnel KPIs from tracked analytics events</sub></p>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="docs/screenshots/13-admin-user-details.png" alt="Admin user details" />
      <p align="center"><sub>Admin user detail, including mentor profile when present</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="docs/screenshots/15-admin-matching-details.png" alt="Admin matching details" />
      <p align="center"><sub>Read-only matching detail for operations review</sub></p>
    </td>
  </tr>
</table>

---

## Key features

Implemented in this repository (not aspirational):

- **Accounts and sessions** — Register, login, logout; JWT stored in an httpOnly cookie (`SameSite=Lax`); `GET /api/users/me` for session identity; registration/login rate limiting.
- **Role overlap** — A user can be a mentee, a mentor, and an admin at the same time. Admin is a server-side `is_admin` flag, never granted through registration.
- **Mentor directory** — Active profiles with job, company, tech stack, topics, capacity, and optional photo URL.
- **Matching lifecycle** — Request → mentor proposes times → mentee selects a slot → `MATCHED`. Supports extra times, reject, cancel, one-time reschedule, and post-meeting feedback.
- **Smart referral attribution** — Profile share links tagged `whatsapp`, `linkedin`, `copy_link`, or `direct`; client records `mentor_profile_viewed`; lifecycle events are written server-side.
- **Notifications and email** — In-app unread counts plus optional SMTP (Gmail or generic SMTP) for requests, slots, reminders, follow-up, and feedback thank-you. Cron jobs can be disabled with `ENABLE_NOTIFICATION_CRON=false`.
- **Admin console** — Calendar, users, matchings, analytics. Admin APIs are auth + admin middleware; the UI is isolated under `client/src/admin`.
- **Localization** — English, Hebrew, and Arabic, including RTL for Hebrew and Arabic, without mirroring layout structure.
- **Security basics** — Helmet, CORS with credentials, bcrypt password hashing, structured API errors, blocked analytics metadata keys (email, password, bio, and similar).

---

## Technology stack

| Layer | Technologies |
| --- | --- |
| **Frontend** | React 18, React Router 7, Material UI 5, Emotion, Axios, Create React App |
| **Backend** | Node.js, Express 4, `pg`, JWT (`jsonwebtoken`), `bcryptjs`, `cookie-parser`, Helmet, Morgan, `express-rate-limit`, `node-cron`, Nodemailer |
| **Database** | PostgreSQL (users, mentor profiles, matching, slots, notifications, feedback, analytics) |
| **Testing** | Jest + React Testing Library (client), Jest + Supertest (server) |
| **Tooling** | Concurrently (root `npm run dev`), dotenv, nodemon |

---

## System architecture

```mermaid
flowchart LR
  subgraph Client["React SPA :3000"]
    UI[Pages and Admin console]
    AuthCtx[AuthContext]
    Analytics[Attribution client]
  end

  subgraph API["Express API :5001"]
    Routes[REST routes]
    MW[Helmet / CORS / cookies]
    AuthMW[JWT cookie auth]
    AdminMW[Admin capability check]
    Services[Domain services]
    Jobs[Cron notification jobs]
  end

  subgraph Data["PostgreSQL"]
    DB[(mentoring_app)]
  end

  Mail[SMTP / Gmail]

  UI --> AuthCtx
  UI --> Analytics
  AuthCtx -->|proxy /api| MW
  Analytics -->|POST /api/analytics/events| MW
  MW --> Routes
  Routes --> AuthMW
  AuthMW --> AdminMW
  AuthMW --> Services
  AdminMW --> Services
  Services --> DB
  Jobs --> Services
  Services --> Mail
```

The CRA `proxy` in `client/package.json` forwards `/api` to `http://localhost:5001` during development.

---

## Mentor–mentee matching workflow

Statuses stored on `matching.status`:

`PENDING_MENTOR` → `PENDING_MENTEE` → `MATCHED`  
Terminal: `REJECTED`, `CANCELLED`

```mermaid
stateDiagram-v2
  [*] --> PENDING_MENTOR: Mentee requests a mentor
  PENDING_MENTOR --> PENDING_MENTEE: Mentor proposes time slots
  PENDING_MENTOR --> REJECTED: Mentor rejects
  PENDING_MENTEE --> MATCHED: Mentee selects a slot
  PENDING_MENTEE --> PENDING_MENTOR: Mentee asks for more times
  PENDING_MENTEE --> REJECTED: Mentee cancels after extra times
  MATCHED --> PENDING_MENTOR: One-time reschedule
  MATCHED --> CANCELLED: Either party cancels the meeting
  MATCHED --> MATCHED: Post-meeting feedback
```

1. Mentee opens an active mentor profile and sends a request (`POST /api/matching`). Duplicate **active** requests (pending or matched) are rejected with `409`.
2. Mentor sees the request in the inbox (`GET /api/mentor-requests`) and either proposes slots or rejects.
3. Mentee picks a slot (`POST /api/matching/:id/select-slot`). The selected slot is stored as `matching.selected_slot_id`.
4. After match, either side may reschedule **once** (`reschedule_used`) or cancel the meeting.
5. Feedback (`POST /api/matching/:id/feedback`) records attendance, a 1–5 rating, and a comment; a thank-you path exists for the mentor.

---

## Database architecture

Tables are created from `server/db/migrations/*.sql` plus `server/scripts/initMatchingTable.js` (the `matching` table is initialized by script rather than a numbered migration).

```mermaid
erDiagram
  users ||--o| mentor_profiles : "user_id"
  users ||--o{ matching : "mentor_id"
  users ||--o{ matching : "mentee_id"
  matching ||--o{ matching_slots : "matching_id"
  matching ||--o| matching_slots : "selected_slot_id"
  matching ||--o{ notifications : "matching_id"
  matching ||--o{ meeting_feedback : "matching_id"
  users ||--o{ notifications : "receiver / sender"
  users ||--o{ analytics_events : "user_id"
  users ||--o{ analytics_events : "mentor_user_id"

  users {
    int id PK
    varchar email UK
    varchar username UK
    varchar password_hash
    boolean is_admin
  }
  mentor_profiles {
    int id PK
    int user_id UK
    text background
    text[] tech_stack
    varchar job
    varchar company
    int years_experience
    text[] topics
    int max_sessions
    int session_duration
    boolean is_active
  }
  matching {
    int id PK
    int mentor_id FK
    int mentee_id FK
    varchar status
    int selected_slot_id FK
    boolean more_times_requested
    boolean reschedule_used
  }
  matching_slots {
    int id PK
    int matching_id FK
    timestamptz start_time
    timestamptz end_time
    boolean is_selected
  }
  notifications {
    int id PK
    int receiver_id FK
    int sender_id FK
    int matching_id FK
    varchar type
    boolean is_read
  }
  meeting_feedback {
    int id PK
    int matching_id FK
    int user_id FK
    boolean attended
    int rating
  }
  analytics_events {
    int id PK
    varchar event_type
    int user_id FK
    int mentor_user_id FK
    int matching_id
    varchar source
    jsonb metadata
  }
```

---

## REST API overview

Base URL in development: `http://localhost:5001`. JSON errors use `{ error: { code, message } }` on most routes.

| Method | Path | Auth | Description |
| --- | --- | --- | --- |
| `GET` | `/api/health` | Public | Liveness check |
| `POST` | `/api/auth/register` | Public, rate limited | Create account, set auth cookie |
| `POST` | `/api/auth/login` | Public, rate limited | Sign in, set auth cookie |
| `POST` | `/api/auth/logout` | Public | Clear auth cookie |
| `GET` | `/api/users/me` | Cookie JWT | Current user |
| `GET` | `/api/mentors` | Public | Active mentor directory |
| `GET` | `/api/mentors/:id` | Public | Mentor profile by `mentor_profiles.id` |
| `GET` / `POST` | `/api/mentor-profile` | Auth | Read or upsert own mentor profile |
| `GET` | `/api/mentor-requests` | Auth | Incoming requests for the mentor |
| `POST` | `/api/mentor-requests/:id/slots` | Auth | Propose time slots |
| `POST` | `/api/mentor-requests/:id/reject` | Auth | Decline a pending request |
| `POST` | `/api/mentor-requests/:id/request-reschedule` | Auth | Mentor one-time reschedule |
| `POST` | `/api/mentor-requests/:id/cancel-meeting` | Auth | Mentor cancels a matched meeting |
| `GET` | `/api/matching` | Auth | Mentee’s requests |
| `GET` | `/api/matching/:id` | Auth | One request owned by the mentee |
| `POST` | `/api/matching` | Auth | Create request (`mentorId`, optional `source`) |
| `POST` | `/api/matching/:id/select-slot` | Auth | Select a proposed slot |
| `POST` | `/api/matching/:id/request-more-times` | Auth | Ask mentor for additional times |
| `POST` | `/api/matching/:id/cancel` | Auth | Cancel after extra times still fail |
| `POST` | `/api/matching/:id/request-reschedule` | Auth | Mentee one-time reschedule |
| `POST` | `/api/matching/:id/cancel-meeting` | Auth | Mentee cancels a matched meeting |
| `POST` | `/api/matching/:id/feedback` | Auth | Post-meeting feedback |
| `GET` | `/api/notifications/unread-count` | Auth | Unread badge counts |
| `PUT` | `/api/notifications/mark-read` | Auth | Mark notifications read |
| `POST` | `/api/analytics/events` | Auth | Client-trackable events only (`mentor_profile_viewed`) |
| `GET` | `/api/admin/users` | Auth + admin | User list |
| `GET` | `/api/admin/users/:id` | Auth + admin | User detail |
| `GET` | `/api/admin/matchings` | Auth + admin | Matching report (`status`, `participantId`) |
| `GET` | `/api/admin/matchings/:id` | Auth + admin | Matching detail |
| `GET` | `/api/admin/analytics` | Auth + admin | Funnel and referral KPIs |

---

## Project structure

```
queens-match-mentoring-platform/
├── package.json                 # Root scripts: dev, server, client, install-all
├── client/
│   ├── public/                  # index.html, AppsFlyer & QueenB logos
│   └── src/
│       ├── App.js               # Routes and providers
│       ├── admin/               # Admin UI (isolated from shared navbar)
│       ├── analytics/           # Share URLs and profile-view tracking
│       ├── api/                 # Auth and notifications HTTP clients
│       ├── components/          # Home, auth, dashboard, shared chrome
│       ├── context/             # AuthContext
│       ├── matching/            # Mentee requests and matching details
│       └── mentor/              # Directory, profile, inbox, become-mentor
├── server/
│   ├── app.js                   # Express app, middleware, routers
│   ├── index.js                 # HTTP listen + cron start
│   ├── db.js                    # pg Pool
│   ├── db/migrations/           # Numbered SQL (users, profiles, slots, …)
│   ├── routes/                  # HTTP handlers
│   ├── services/                # Auth, matching, mentors, admin, analytics
│   ├── middleware/              # JWT auth, admin gate
│   ├── jobs/                    # Reminder / follow-up / feedback cron
│   ├── scripts/                 # Table init + QA seed / cleanup
│   └── tests/                   # Supertest API tests
└── docs/screenshots/            # README gallery (this documentation)
```

---

## Installation and setup

### Prerequisites

- Node.js 18+ (tested with Node 22)
- npm
- PostgreSQL 14+

### 1. Clone and install

```bash
git clone https://github.com/Janadan-Sbeihat/queens-match-mentoring-platform.git
cd queens-match-mentoring-platform

npm install
npm run install-all
```

`install-all` installs `server/` and `client/` dependencies.

### 2. Create the database

```bash
createdb mentoring_app
```

Use any database name you prefer; it must match `PGDATABASE`.

### 3. Configure environment variables

```bash
cp server/.env.example server/.env
```

Edit `server/.env` with **your** values. Do not commit this file. If the example file contains sample SMTP credentials, replace them — never reuse checked-in secrets.

### 4. Apply schema

From `server/`, in this order (matching slots depend on `matching`; the matching script also adds foreign keys to `matching_slots`):

```bash
cd server

psql "$PGDATABASE" -f db/migrations/001_create_users.sql
psql "$PGDATABASE" -f db/migrations/004_add_users_is_admin.sql
psql "$PGDATABASE" -f db/migrations/005_create_analytics_events.sql

npm run db:init-matching
npm run db:init-mentors
npm run db:init-matching          # retry FKs now that matching_slots exists
npm run db:init-notifications
```

If `db:init-matching` reports that `matching_slots` is missing, run `db:init-mentors` and then `db:init-matching` again.

### 5. Optional: seed synthetic QA data

Development only. Refuses to run when `NODE_ENV=production`.

```bash
npm run seed:admin-qa
```

Cleanup:

```bash
npm run cleanup:admin-qa
```

Seeded accounts use the `@queenb.test` domain and a shared development password defined in `server/scripts/seedAdminQaData.js` (printed by the seed script). Example logins:

| Role | Email |
| --- | --- |
| Admin | `qa_admin@queenb.test` |
| Mentor | `qa_mentor_a@queenb.test` |
| Mentee | `qa_mentee_1@queenb.test` |

### 6. Run the app

From the repository root:

```bash
npm run dev
```

Or separately:

```bash
npm run server    # http://localhost:5001
npm run client    # http://localhost:3000
```

Open [http://localhost:3000](http://localhost:3000).

### 7. Tests

```bash
cd server && npm test
cd ../client && npm test -- --watchAll=false
```

### Production build

```bash
npm run build
npm start
```

`npm start` runs the Express server only; serve the CRA `client/build` output according to your deployment setup.

---

## Environment variables

Set these in `server/.env` (gitignored). Never commit real passwords, JWT secrets, or SMTP app passwords.

| Variable | Purpose |
| --- | --- |
| `PORT` | API port (project default in the example is `5001`; `index.js` falls back to `5000` if unset) |
| `PGHOST` | PostgreSQL host |
| `PGPORT` | PostgreSQL port |
| `PGUSER` | Database user |
| `PGPASSWORD` | Database password |
| `PGDATABASE` | Database name |
| `JWT_SECRET` | Strong secret used to sign session JWTs |
| `NODE_ENV` | `development`, `test`, or `production` |
| `CLIENT_ORIGIN` | CORS origin for the React app (`http://localhost:3000` locally) |
| `SMTP_USER` | Optional. SMTP username |
| `SMTP_PASS` | Optional. SMTP password / app password |
| `SMTP_FROM` | Optional. From header |
| `SMTP_SERVICE` | Optional. e.g. `gmail` |
| `SMTP_HOST` / `SMTP_PORT` / `SMTP_SECURE` | Optional. Non-Gmail SMTP |
| `ENABLE_NOTIFICATION_CRON` | Set `false` to skip reminder/follow-up/feedback jobs |

Email is skipped when `SMTP_USER` or `SMTP_PASS` is unset (`emailService.isEmailConfigured()`).

---

## Team and acknowledgments

Built as a QueenB bootcamp team project. Git history credits:

| Person | Git identity |
| --- | --- |
| Adi Shemesh | `adiShemesh95` |
| Jana Sbeihat | `janadansbeihat` |
| Stav Yemin | `Stav Yemin` |

**Acknowledgments**

- [QueenB](https://www.queenb.org.il/) — bootcamp and community mission
- [AppsFlyer](https://www.appsflyer.com/) — industry partner for Bootcamp 2026
- Shirley Kulbak — AppsFlyer / bootcamp repository setup and early template work in git history

This README documents the product as implemented by the team. It does not assign individual feature ownership.

---

## License

MIT. See the license field in `package.json`.
