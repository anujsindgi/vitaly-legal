# Vitaly — Privacy Policy

_Last updated: 22 July 2026_

Vitaly is a personal health dashboard for iOS. This policy explains what data
the app collects, where it lives, who else sees it, and the controls you have.

We wrote it to be readable, not defensive. If anything is unclear, email
**sindgi.anuj@gmail.com** and we will fix it.

---

## The short version

- **Most of your data stays on your phone.** Journal, medications, water, habit
  logs, muscle-group tags, and score history never leave your device.
- **Some data lives on our server so it can be synced and analysed.** Your
  Swiggy identity and order history, uploaded blood reports, and the extracted
  test results are stored in our Postgres database on Railway.
- **We do not sell your data, run ads, or use third-party analytics or
  tracking SDKs.**
- **You can delete your account and everything the server holds at any time**
  from Settings → Delete Account & All Data.

---

## What Vitaly collects, and where it lives

### 1. Stays on your device only

The following are stored locally on your iPhone in Vitaly's private storage
and are **never sent to our server or any third party**:

- Daily check-ins (mood, energy, journal answers)
- Medications you add and the days you mark them as taken
- Water intake logs and daily targets
- Habit logs (cigarettes, alcoholic drinks)
- Muscle-group tags you apply to workouts
- Digital-detox app selections and completed sessions
- Daily overall-score snapshots (for the trend sparkline)
- Cached copies of server data so tabs work offline

If you delete the app from your phone, this data is deleted along with it.

### 2. Read live from Apple Health

Vitaly reads the following from Apple Health each time you open the app and
processes them on-device:

- Sleep sessions and stages
- Resting heart rate
- VO₂ max
- Recorded workouts (type, duration, calories)

We do not copy this data to our server. Apple Health remains the authoritative
store; you can revoke Vitaly's Health access at any time in **iOS Settings →
Privacy & Security → Health → Vitaly**.

### 3. Stored on our server

The following are sent to and stored in Vitaly's backend (Postgres database
hosted on Railway):

- **Your Swiggy account details** — user ID, mobile number, and name from the
  Swiggy OAuth login; the access token used to fetch your order history
- **Your Swiggy orders** — item names, quantities, prices, order timestamps,
  restaurant or Instamart source, and computed health/nutrition scores
- **Blood reports you upload** — the original PDF plus the extracted test
  results (test name, value, unit, reference range, category)
- **A per-user identifier** (UUID) that ties the above together

We keep this data so the app can sync across sessions, compute long-term
trends, and generate insights.

### 4. Sent to OpenAI when a feature calls for it

When you upload a blood report, or when the AI Coach generates recommendations,
Vitaly sends the relevant data to OpenAI's Chat Completions API:

- **Blood report parsing** — the raw text extracted from your uploaded PDF
- **AI Coach** — a compact snapshot of your abnormal biomarkers, aggregate
  order stats (30-day averages, not individual items), sleep and exercise
  totals, habit counts, and active medications

OpenAI processes this to return structured data and returns it to us. Per
[OpenAI's API terms](https://openai.com/policies/api-data-usage-policies),
API inputs are not used to train their models and are retained by OpenAI for
up to 30 days for abuse monitoring before deletion.

We do not send OpenAI your name, Swiggy identity, or any direct identifier —
the request is anonymous from OpenAI's perspective.

---

## What we do **not** collect

- **No advertising identifiers**, no IDFA, no fingerprinting
- **No third-party analytics SDKs** (no Firebase, Mixpanel, Amplitude, Segment,
  etc.)
- **No crash-reporting SDKs** beyond Apple's own opt-in reporting
- **No location** beyond what's implicit in Swiggy order delivery addresses
  (we do not read your phone's GPS)
- **No contacts, photos, microphone, or camera** access

The app does not include social sharing, and does not upload anything to
Vitaly's server unless it is listed in section 3 above.

---

## Third parties who process your data

| Service | What we send them | Why |
|---|---|---|
| **Swiggy** ([privacy](https://www.swiggy.com/privacy-policy)) | OAuth login; the access token they issued | To fetch your order history on your behalf |
| **OpenAI** ([API data policy](https://openai.com/policies/api-data-usage-policies)) | Blood report text; anonymised health snapshot | To parse reports and generate insights |
| **Railway** ([privacy](https://railway.app/legal/privacy)) | Everything in section 3 (as our infrastructure host) | To run the backend and database |
| **Apple** ([privacy](https://www.apple.com/legal/privacy/)) | Nothing from us — Apple Health data stays on-device | HealthKit, push notifications, and TestFlight distribution operate under Apple's policies |

We do not have any other data-sharing arrangements. We do not sell your data
to anyone.

---

## Your rights and how to exercise them

**Delete your account and all server-side data.**
Settings → Delete Account & All Data. This immediately removes your Swiggy
tokens, orders, blood reports, and extracted results from our database. It
cannot be undone.

**Delete on-device data.**
Delete the Vitaly app from your phone. All local data (journal, meds, water,
habits, cached copies) is removed with it.

**Revoke Apple Health access.**
iOS Settings → Privacy & Security → Health → Vitaly. This immediately stops
Vitaly from reading any Health data.

**Disconnect Swiggy without deleting the account.**
Settings → Sign out. Your data remains on our server (in case you want to
sign back in), but no further sync happens. Use Delete Account if you also
want the historical data gone.

**Access a copy of your data.**
Email us at sindgi.anuj@gmail.com from the address associated with your
account and we will send you a JSON export within 30 days.

**Correct your data.**
Blood report extractions can occasionally misread values. If you spot an error,
delete and re-upload the report; if the issue persists, email us.

---

## Data security

- All app-to-server traffic uses HTTPS (TLS 1.2+).
- Passwords are not applicable — you sign in with Swiggy's OAuth flow; we
  never see or store your Swiggy password.
- Access to the production database is restricted to the developer.
- We do not encrypt your data at rest beyond the standard disk encryption
  provided by Railway's infrastructure.

Vitaly is currently a small independent project. If you are handling
particularly sensitive data (for example, unusual medical conditions you would
not want in any third-party system), please weigh that against the security
posture described here.

---

## Data retention

- **Server data** (section 3) is retained until you delete your account, at
  which point it is removed within 24 hours from our primary database.
  Encrypted database backups are rotated within 30 days.
- **OpenAI** retains API inputs for up to 30 days for abuse monitoring, then
  deletes them.
- **On-device data** is retained until you delete the app.

If you stop using Vitaly without deleting your account, your data remains on
our server indefinitely so you can pick up where you left off. You can force
deletion at any time from the app or by email.

---

## Children

Vitaly is not intended for users under 18. We do not knowingly collect data
from anyone under 18. If you believe a child has provided data to Vitaly,
email sindgi.anuj@gmail.com and we will delete it.

---

## Where your data is processed

Vitaly's backend and database are hosted on Railway. Railway operates
worldwide; your data may be processed in the region Railway assigns your
project (typically the US or the EU). OpenAI processes API requests in the
United States.

If you are in the European Economic Area, the United Kingdom, or another
region with data-transfer restrictions, using Vitaly involves your data being
transferred to and processed in those regions.

---

## Medical disclaimer

Vitaly is a personal tracking tool, not a medical device or a substitute for
professional medical advice. The health score, insights, and food
recommendations are informational and generated automatically. Always consult
a qualified doctor for medical decisions, especially about abnormal blood
test results or changes to medication.

---

## Changes to this policy

We may update this policy as Vitaly evolves. Material changes will be shown
in the app before they take effect. The "Last updated" date at the top of
this page always reflects the current version.

---

## Contact

Questions, requests, or complaints:

**sindgi.anuj@gmail.com**

Vitaly is developed by Anuj Sindgi.
