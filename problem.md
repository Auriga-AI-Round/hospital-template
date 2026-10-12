# Hospital Management System — Take-Home Task

Build a small **Hospital Management System** backend (with a minimal UI) that manages
patients, doctors, and appointments. Keep it simple, correct, and well-structured.

You have the starter repo (this one). Read this file fully before you start — it is the
**only** spec. Commit and push your work to the default branch; pushes are captured
automatically.

---

## Tech constraints

- **Language/framework:** your choice (Django, FastAPI, Flask, Express, Spring, …).
- **Database:** use a **real database server** (PostgreSQL or MySQL). A file-based
  SQLite database is **not** acceptable for the final submission — it is one of the
  mandatory requirements below.
- Provide a `README.md` with setup steps and a `## Submission` section (see the end).

---

## Core features (required)

### 1. Patient management (simple)
- Register a patient: full name, date of birth, gender, phone, email.
- List patients and view a single patient.
- Edit and soft-delete a patient.

### 2. Doctor management (simple)
- Register a doctor: full name, specialization, phone, email, consultation fee.
- List doctors and view a single doctor.

### 3. Appointment booking (complex)
- Book an appointment between a patient and a doctor for a given date + time slot.
- **A doctor cannot be double-booked** for the same slot — reject the overlap with a
  clear error (this is the core correctness rule).
- List a doctor's appointments for a given day.
- Cancel an appointment.

### 4. Search (implicit requirement)
- Search patients by name or phone (partial match).
- Search doctors by specialization.
> Search is **mandatory** even though it is only stated here once.

### 5. Billing / analytics (complex)
- For a doctor, compute total billed = (number of completed appointments × fee).
- A simple analytics endpoint: appointments per doctor for a date range.

---

## The twist (read carefully)

Appointment slots are **30 minutes**. When booking, the system must reject **any
overlap**, not just an exact-time clash: an appointment at 10:00–10:30 must block a
new booking at 10:15–10:45 for the **same doctor**. Handle this at the data layer
(a time-range overlap check), not only in the UI.

---

## Mandatory requirements (you will be marked down hard if missing)

1. **Real DB server** (Postgres/MySQL) — not SQLite.
2. **Search** (feature 4) must work.
3. **No double-booking** including the 30-minute **overlap** twist.
4. Input validation + sensible error responses (no 500s on bad input).

---

## Bonus (optional, scored separately)

- **Analytics dashboard page**: a simple landing/analytics UI page showing
  appointments-per-doctor and total billings. (This is the "bonus problem".)
- A seed script and a few automated tests.

---

## What we evaluate

| Area | What we look for |
|---|---|
| Feature coverage | patient/doctor/appointment CRUD, search, billing |
| The twist | 30-min overlap rejection at the data layer |
| Robustness | validation, error handling, no crashes on bad input |
| DB hygiene | real DB server, migrations, sane schema (not SQLite) |
| Testing | any automated tests present |
| Docs & reasoning | clear README, setup steps, design notes |
| Landing page | the bonus analytics/landing UI |

---

## Submission

Fill this in your repo's `README.md` so reviewers (and the automated live-check) can
reach your running app:

```
## Submission
App URL: https://your-deployed-app.example.com
API base: https://your-deployed-app.example.com/api
Username: reviewer@example.com
Password: review-pass-123
Endpoints:
  - GET /api/patients
  - GET /api/doctors
  - GET /api/appointments
```
