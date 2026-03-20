# Trigr 🛵⚡
### *When disruptions stop your deliveries, we start your payout.*

> **Guidewire DEVTrails 2026** | AI-Powered Parametric Income Insurance for India's Food Delivery Partners
> Persona: Zomato / Swiggy | Platform: Web App

---

## The Problem Nobody Is Solving

India has over 5 million food delivery partners working for Zomato and Swiggy. On a good day, a partner in Hyderabad earns ₹800–₹1,200. On a day when a storm hits, or the AQI crosses 250, or a sudden curfew is declared, or a local bandh shuts the streets? They earn nothing.

Heavy rain slows orders. Extreme heat makes outdoor work unsafe. Severe pollution forces workers off the road. A flood blocks every route. A curfew or local strike brings deliveries to a complete halt.

These are not rare events — they are the lived reality of every gig worker in India. A disruption week can erase 30-40% of a Zomato partner's monthly income. And when it happens, they have absolutely nothing to fall back on. No sick leave. No employer liability. No safety net.

**Trigr changes that.**

We are building an AI-powered parametric insurance platform that monitors real-world disruptions in real time — weather, pollution, floods, curfews, and strikes — and when a trigger fires, sends the payout automatically. No claim form. No waiting. No friction.

---

## 📌 Table of Contents

1. [Why Food Delivery, Why Now](#1-why-food-delivery-why-now)
2. [How Trigr Works — The Big Picture](#2-how-gigshield-works--the-big-picture)
3. [Persona Scenarios & Workflow](#3-persona-scenarios--workflow)
4. [Weekly Premium Model & Parametric Triggers](#4-weekly-premium-model--parametric-triggers)
5. [AI/ML Architecture](#5-aiml-architecture)
6. [Fraud Detection & Anti-Spoofing Strategy](#6-fraud-detection--anti-spoofing-strategy)
7. [Risk Scoring & Pricing Engine](#7-risk-scoring--pricing-engine)
8. [Tech Stack & System Design](#8-tech-stack--system-design)
9. [Development Roadmap](#9-development-roadmap)
10. [Team](#10-team)

---

## 1. Why Food Delivery, Why Now

### Food Delivery Partners Are the Most Disruption-Exposed Gig Workers in India

Unlike e-commerce delivery (longer windows, some indoor time) or grocery Q-commerce (hyper-local, indoor dark store access), food delivery is entirely real-time, entirely outdoor, and entirely dependent on weather.

A Zomato partner cannot delay an order by 3 hours. They cannot wait out a storm in a warehouse. They are on a bike, in the rain, against the clock — or they are earning nothing.

| Factor | E-Commerce Delivery | Grocery / Q-Commerce | **Food Delivery (Zomato/Swiggy)** |
|---|---|---|---|
| Delivery window | Hours to days | 10–20 minutes | 30–45 minutes |
| Weather sensitivity | Low–Moderate | Moderate | **High** |
| Peak hour dependency | Low | Moderate | **Critical** |
| Income drop during disruption | 10–15% | 20–25% | **30–40%** |
| Daily earnings (Tier 1 city) | ₹700–₹1,000 | ₹600–₹900 | **₹900–₹1,500** |

This is why food delivery is the right first persona. The income loss is significant, the disruption triggers are measurable, and the urgency of payout is real.

### City-Tier Reality

Income and disruption impact are not uniform across India. Trigr accounts for where a partner works:

| City Tier | Examples | Daily Income (Normal Day) | Income Loss During Disruption |
|---|---|---|---|
| Tier 1 (Metro) | Bengaluru, Hyderabad | ₹900–₹1,500 (20–30 orders) | 30–40% |
| Tier 2 | Vijayawada, Vizag | ₹600–₹1,000 (15–22 orders) | 25–30% |
| Tier 3 | Smaller cities | ₹300–₹700 (8–15 orders) | 20–25% |

> A key insight: higher-tier cities have more income at stake, but Tier 3 workers are more financially vulnerable because they have far less buffer.

---

## 2. How Trigr Works — The Big Picture

Trigr is built on a simple but powerful principle: **parametric insurance**. Instead of asking a worker to prove their loss, the system watches the world for them.

When rainfall exceeds our threshold in a worker's zone, a trigger fires. The system checks whether the worker was active, validates against fraud signals, and releases a payout — directly to their UPI ID. No claim form. No waiting. No friction.

```
┌─────────────────────────────────────────────────────────────────┐
│                    WORKER JOURNEY                               │
│─────────────────────────────────────────────────────────────────│
│  [Every Monday]  Worker opts into weekly coverage               │
│       ↓                                                         │
│  Premium calculated (based on zone risk, history, forecast)     │
│       ↓                                                         │
│  [During Week]  Trigger Monitor checks every 15 minutes         │
│  Weather API + AQI API + Admin Panel (for curfew/strike)        │
│       ↓                                                         │
│  Disruption detected → Severity assessed → Location validated   │
│       ↓                                                         │
│  Fraud Engine runs multi-layer check                            │
│       ↓                            ↓                            │
│  Risk Score < 30 → Auto-approve    Risk Score > 65 → Freeze     │
│       ↓                                                         │
│  Payout calculated (based on affected hours + severity)         │
│  UPI transfer → Worker notified via app/SMS                     │
└─────────────────────────────────────────────────────────────────┘
```

---

## 3. Persona Scenarios & Workflow

### Understanding Our Two Core Personas

**Persona A — The Normal Day (Rajan, Zomato, Bengaluru)**

Rajan works 8 hours a day in Indiranagar. He earns roughly ₹100/hour — about ₹800 for a full day. He accepts orders, picks up food from restaurants, and delivers to customers in a defined zone. His earnings come from per-order pay, distance-based pay, and surge pricing during peak hours (lunch: 12–2 PM, dinner: 7–9 PM).

Trigr tracks Rajan's expected income baseline using his last-4-week average earnings, his declared working hours, and his operating zone's historical activity patterns.

**Persona B — The Disrupted Day (Rajan, same city, bad Tuesday)**

Rainfall hits 18mm/hr at 2 PM — right in the middle of peak earning hours. Road speeds drop. Restaurant pickup times double. Customers cancel. But it's not always rain. Some days it's a heat wave pushing 43°C that makes riding unsafe. Other days it's an AQI alert that keeps customers indoors. Occasionally it's a local strike that shuts down the entire zone.

Whatever the disruption, the result is the same: Rajan's order count falls from his average of 5 per hour to 1 — or zero.

Trigr detects: rainfall threshold crossed ✅, continuous for 2+ hours ✅, Rajan's GPS is in his declared zone ✅, his account has been active today ✅.

**Result:** Fraud score = Low. Payout automatically calculated and sent to his UPI. Trigr covers the income gap — whatever caused it.

---

### Scenario A — The 3 PM Monsoon Halt, Hyderabad

**Meera**, Swiggy partner, Banjara Hills. Thursday, 3:00 PM.

Rainfall crosses 22mm/hr. Trigr's continuous trigger activates (rain above threshold for 2+ hours). Meera has been online since 10 AM — her activity log is clean.

- Trigger threshold crossed ✅
- Continuous rain validated for 2 hours ✅
- Meera's GPS matches her declared delivery zone ✅
- No fraud signals detected ✅

**Result:** Payout = ₹350 (3 disrupted hours × expected hourly income × severity factor). Sent to UPI within 22 hours. Meera didn't file anything.

---

### Scenario B — The Delhi AQI Shutdown

**Arjun**, Zomato partner, Dwarka, Delhi. November, 8 AM.

AQI crosses 260. Health risk makes extended outdoor work unsafe. Arjun has been logged in, but platform activity shows a visible slowdown.

- AQI trigger crosses 250 threshold ✅
- Continuous for 6+ hours ✅
- Arjun is in his declared operating zone ✅

**Result:** Medium severity payout (50% income loss rate) for the disrupted hours. Arjun's weekly premium was ₹68 — this week, Trigr covers what Delhi's air quality took from him.

---

### Scenario C — The Curfew (Social Disruption)

**Priya**, Zomato partner, Vijayawada. An unplanned curfew is declared at 6 PM.

Unlike weather, curfews don't have a real-time API. Trigr handles this through an **admin-verified trigger** — an admin marks the affected city/zone as curfew-active on the dashboard. The system then cross-validates: is Priya active in that zone? Was she working in those hours?

- Curfew = TRUE, zone confirmed ✅
- Priya's activity log confirms she was active before the curfew ✅
- Disruption hours = 6 PM to declared end of working day ✅

**Result:** 100% income loss rate for the curfew duration. Instant trigger. Payout = full estimated earnings for those hours.

---

### Full Application Workflow

```
╔═══════════════════════════════════════════════════════════════╗
║                    WORKER ONBOARDING                          ║
╠═══════════════════════════════════════════════════════════════╣
║  Register → Verify phone → Declare zone + weekly hours        ║
║  Platform income verified via API (or self-declared × 0.8)   ║
║  Weekly opt-in every Monday → Premium auto-deducted           ║
╠═══════════════════════════════════════════════════════════════╣
║                    TRIGGER MONITORING                         ║
╠═══════════════════════════════════════════════════════════════╣
║  Every 15 minutes per zone:                                   ║
║  OpenWeatherMap API → Rainfall, Temperature                   ║
║  AQI API (AQICN / OpenWeather Air) → AQI reading              ║
║  Admin Panel → Curfew / Strike status                         ║
║  IMD alerts → Flood advisory (Red/Orange/Green)               ║
╠═══════════════════════════════════════════════════════════════╣
║                    TRIGGER ACTIVATED                          ║
╠═══════════════════════════════════════════════════════════════╣
║  Severity assigned (Low / Medium / High / Extreme)            ║
║  Trigger type checked (Instant vs. Continuous)                ║
║  Location validated: worker must be in affected zone          ║
║  Time validated: must be within active working hours          ║
╠═══════════════════════════════════════════════════════════════╣
║                    FRAUD ENGINE                               ║
╠═══════════════════════════════════════════════════════════════╣
║  5-layer fraud check runs in parallel:                        ║
║  GPS integrity + Network anchoring + Device fingerprint       ║
║  Behavioral baseline + Cluster detection                      ║
║  Risk Score calculated (0–100)                                ║
╠═══════════════════════════════════════════════════════════════╣
║                    PAYOUT DECISION                            ║
╠═══════════════════════════════════════════════════════════════╣
║  Score 0–30  → Auto-approved, UPI in 22 hours                 ║
║  Score 31–65 → Held for OTP / identity verification           ║
║  Score 66+   → Frozen, manual review, appeal path open        ║
╠═══════════════════════════════════════════════════════════════╣
║                    INSURER DASHBOARD                          ║
╠═══════════════════════════════════════════════════════════════╣
║  Active policies by zone → Live trigger feed                  ║
║  Loss ratio analytics → Fraud alert centre                    ║
║  7-day weather exposure forecast → Zone risk heatmap          ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 4. Weekly Premium Model & Parametric Triggers

### Why Weekly?

Food delivery workers live week to week. A daily premium feels like a hidden tax they can't control. A monthly premium is a large upfront commitment they can't afford. Weekly is the natural rhythm — just like their earnings, just like their expenses.

Trigr's weekly opt-in model lets workers skip a week with no penalty. No lock-in. No fine print. They pay ₹X on Monday morning, and from that moment until Sunday night, they are covered.

---

### The 6 Parametric Triggers

| # | Trigger | Threshold | Trigger Type | Data Source | Severity |
|---|---|---|---|---|---|
| 1 | **Heavy Rain** | > 5mm/hr (Low), > 15mm/hr (High) | Continuous (2+ hrs) | OpenWeatherMap API | Low / Medium / High |
| 2 | **Extreme Heat** | > 38°C (Low), > 42°C (High) | Continuous | OpenWeatherMap API | Low / Medium / High |
| 3 | **Severe AQI** | > 150 (Medium), > 250 (High) | Continuous | AQICN / OpenWeather Air API | Medium / High |
| 4 | **Flood Alert** | IMD Flood Alert = TRUE | Instant | IMD / NDMA (or simulated) | High / Extreme |
| 5 | **Curfew** | Curfew Status = TRUE | Instant | Admin-verified panel | Extreme (100%) |
| 6 | **Local Strike / Bandh** | Strike Status = TRUE | Instant | Admin-verified / News API | Extreme (100%) |

**Key design decisions:**

- **Instant triggers** (Flood, Curfew, Strike): These cause complete, immediate disruption. No duration check needed — the moment they are confirmed, a claim activates.
- **Continuous triggers** (Rain, Heat, AQI): A 10-minute rain spike should not cause a payout. The condition must persist for 2+ hours to confirm genuine income impact.
- **Multi-disruption rule:** If multiple triggers fire simultaneously, only the highest severity is used. No double payouts.

---

### Severity → Income Loss Mapping

| Severity | Income Loss % | When It Applies |
|---|---|---|
| Low | 20% | Light disruption — worker can still operate, just slower |
| Medium | 50% | Significant disruption — reduced hours, fewer orders |
| High | 80% | Major disruption — minimal work possible |
| Extreme | 100% | Complete shutdown — Flood, Curfew, or Strike |

---

### Income Loss Calculation

```
Expected Income  =  Average hourly income × Working hours in disruption window

Actual Income    =  What the worker earned during that period

Income Loss      =  Expected Income − Actual Income

Payout           =  Income Loss × Severity %
```

**Worked example — Rajan, Bengaluru, Medium rain (50% severity), 3 disrupted hours:**
```
Expected Income  = ₹100/hr × 3 hrs = ₹300
Actual Income    = ₹100 (earned only 1 order worth)
Income Loss      = ₹300 − ₹100 = ₹200
Payout           = ₹200 × 50% = ₹100
```

**Payout formula used in the system:**
```
Payout = (DWI / 7) × (affected_hours / 9) × DSF × trigger_rate

where:
  DWI          = Declared Weekly Income (platform-verified)
  DSF          = Disruption Severity Factor (0.50 / 0.75 / 1.00)
  trigger_rate = 1.00 (primary) | 0.70 (secondary triggers like curfew/strike)
```

---

### Weekly Premium Formula

```
Weekly Premium = EL × (1 + 0.35) × City Tier Multiplier

where:
  EL  = Expected Loss = DWI × ELR (Expected Loss Rate from CRS band)
  0.35 = 35% loading (operations + reinsurance + margin)

City Tier Multipliers:
  Tier A (Mumbai, Delhi, Bengaluru)  →  1.00
  Tier B (Hyderabad, Chennai, Pune)  →  0.92
  Tier C (all other cities)          →  0.85

Weekly change cap: ±25% (IRDAI micro-insurance alignment)
```

### Sample Weekly Premiums

| Worker | City | Zone Risk | DWI | CRS | Est. Premium | Max Weekly Payout |
|---|---|---|---|---|---|---|
| Rajan | Bengaluru | High (flood-prone) | ₹5,600 | 56 (Moderate) | ₹68 | ₹4,760 |
| Meera | Hyderabad | Moderate | ₹4,800 | 30 (Low) | ₹42 | ₹4,080 |
| Arjun | Delhi | High (AQI season) | ₹6,000 | 70 (High) | ₹110 | ₹5,100 |
| Priya | Vijayawada | Low | ₹3,800 | 22 (Low) | ₹35 | ₹3,230 |

> **Payout cap:** Max payout per week = 85% of DWI. This prevents over-insurance and moral hazard while still providing meaningful protection.

---

## 5. AI/ML Architecture

### Model 1 — Composite Risk Scorer (CRS)

**Purpose:** Compute a single risk score (0–100) per worker per week. This drives both premium and payout calculations.

**Four risk dimensions combined:**

```
CRS = (0.55 × R_env + 0.15 × R_loc + 0.15 × R_act + 0.15 × R_usr) × 100

R_env  = Environmental risk (live weather + AQI conditions)         — updated every 3 hrs
R_loc  = Location risk (historical disruption frequency of zone)    — updated weekly
R_act  = Activity risk (how many hours the worker is exposed)       — updated daily
R_usr  = User history risk (claim frequency + tenure)               — updated weekly
```

**Why 55% weight on R_env?** Because bad weather is the primary cause of income loss. It is the reason this product exists. The other three dimensions provide important modulation — zone history, personal exposure, and individual claim behaviour — but no other factor comes close to real-time weather in determining weekly risk.

**CRS Risk Bands:**

| CRS Range | Risk Level | Expected Loss Rate | Premium Signal |
|---|---|---|---|
| 0–20 | Very Low | 3% | Near-floor premium |
| 21–40 | Low | 7% | Below-average premium |
| 41–60 | Moderate | 14% | Average premium |
| 61–80 | High | 22% | Above-average premium |
| 81–100 | Very High | 30% | Capped premium |

---

### Model 2 — Dynamic Premium Adjuster

**Purpose:** Update each worker's weekly premium every Sunday night for the coming week.

**Inputs:**
- 7-day weather forecast (Open-Meteo free tier)
- 7-day AQI trend
- Worker's activity data from the past week
- Any new claims in the past week

**Logic:** The ±25% weekly cap ensures workers are never hit with a sudden 2× premium spike during disruption season. Instead, if their risk profile jumps dramatically, the premium rises by at most 25% in week 1, then another 25% in week 2 if conditions persist — a smooth, predictable ramp.

---

### Model 3 — Fraud Detection Engine

Detailed in [Section 6](#6-fraud-detection--anti-spoofing-strategy).

---

### Model 4 — Predictive Disruption Forecaster (Insurer Dashboard)

**Purpose:** Give insurers a 7-day forward view of likely claims exposure by zone.

```
Expected Claim Exposure (zone) =
    P(trigger fires this week)
    × active_policies_in_zone
    × avg_payout_per_event

P(trigger) = weighted combination of:
    7-day rainfall probability (OpenWeatherMap forecast)
    AQI trend projection (5-day CPCB data)
    Civil event calendar lookup (curfews, festivals, elections)
    Historical same-week-of-year disruption rate
```

Dashboard output: *"Zone: Banjara Hills, Hyderabad — 62% disruption probability — Estimated exposure: ₹28,400"*

---

## 6. Fraud Detection & Anti-Spoofing Strategy

> 🚨 **Market Crash Incident:** A coordinated ring of 500 delivery partners used GPS-spoofing apps to fake their presence inside weather-alert zones. Dormant accounts were activated minutes before the trigger fired. Payouts were drained before any alert could be raised. Trigr was designed to make this attack impossible.

---

### How We Tell a Real Worker from a GPS Spoofer

Both a genuine stranded worker and a GPS spoofer will appear in the same zone at the same time. Weather data alone cannot tell them apart. Only behavioral, physical, and network signals can.

| Signal | What a Genuine Worker Shows | What a GPS Spoofer Cannot Fake |
|---|---|---|
| **Movement Entropy** | Erratic, real-world movement — short bursts, stops, turns | Static GPS or impossibly smooth movement paths — mock app artifacts |
| **Cell Tower Drift** | Tower IDs change naturally as worker moves through streets | Tower ID unchanged for 20+ minutes — still pinging home base |
| **Platform Activity** | Order checks, map interactions, restaurant pings visible in logs | Flat login — no app interactions whatsoever |
| **Historical Activity** | 30+ days of continuous delivery zone presence | Dormant account activated within 2 hours of a trigger announcement |
| **Network Anchoring** | WiFi BSSID absent (outdoor, mobile) — IP consistent with carrier subnet | WiFi BSSID active (sitting at home) — IP from VPN |

**The core rule:** If any 3 of the following 5 signals are simultaneously true, the claim is auto-escalated to HIGH RISK and frozen:

```
S1: GPS coordinate shows near-zero variance for the entire shift
S2: Cell tower ID unchanged for > 20 minutes in a multi-tower area
S3: Account logged in within 15 minutes of trigger announcement
S4: Zero delivery platform interactions during claimed active window
S5: Device WiFi is connected (genuine delivery workers are mobile)
```

---

### The 5-Layer Detection System

**Layer 1 — GPS Integrity Check**
- Verify movement entropy: real workers show irregular movement patterns
- Cross-check GPS coordinates against cell tower triangulation (±300m tolerance)
- Detect mock app artifacts: teleportation, perfectly smooth paths, sub-meter precision

**Layer 2 — Network & Device Anchoring**
- Each login is associated with a primary home WiFi BSSID and device fingerprint
- Two accounts sharing the same BSSID → immediate duplicate account flag
- Emulator detection: certain device + OS combinations indicate virtual environments

**Layer 3 — Behavioral Baseline**
- Every worker builds a rolling 30-day profile: active hours, zone history, order count
- A user dormant for 7+ days who suddenly activates during a disruption window → anomaly flag
- Users who only ever claim during disruptions (never show normal-day activity) → flagged

**Layer 4 — External Disruption Validation**
- Claim is cross-validated against the official parametric trigger from our engine
- If the worker's GPS zone did NOT receive a confirmed trigger → auto-rejected
- Prevents opportunistic claims from workers in unaffected areas

**Layer 5 — Cluster & Pattern Detection**
- Real-time monitoring of claim density per 1km × 1km geographic grid cell
- If a zone receives > 3× its expected claim rate within a 2-hour window → Cluster Alert
- Cross-check: are flagged accounts newly created? Do they share device signals?

---

### Risk Score Formula

```
Risk Score = (GPS_score × 0.30) + (Network_score × 0.25) +
             (Device_score × 0.20) + (Behavior_score × 0.15) +
             (Cluster_score × 0.10)

Each sub-score: 0–100 (0 = clean, 100 = high suspicion)
```

| Risk Tier | Score | System Action | Worker Experience |
|---|---|---|---|
| **LOW** | 0–30 | Auto-approve | Seamless — payout within 22 hours |
| **MEDIUM** | 31–65 | Hold — OTP + identity verification | Delayed 24–48 hrs — prompted to verify |
| **HIGH** | 66–100 | Freeze — manual review | Claim blocked — appeal path opened |

---

### Defending Against a Coordinated Fraud Ring

Individual spoofers are caught by the 5-layer check. Coordinated rings require network-level detection — looking at the group, not just the individual.

**Ring Detection Signals:**

- **Synchronized login storm:** 50+ accounts logging in within a 10-minute window after a trigger fires — genuine workers are already logged in before the trigger
- **Device fingerprint clustering:** Ring members often share device models, OS versions, and app builds because they register accounts in batches
- **BSSID collision graph:** Multiple accounts sharing the same home WiFi BSSID — physically in the same room
- **UPI destination clustering:** If 5+ accounts route payouts to the same UPI ID, that is a confirmed ring operating under central control
- **Claim velocity spike:** Genuine disruptions show a gradual claim rise. Ring attacks produce a vertical spike — 500 claims in 30 minutes

**The Zone Radar:**

| Claim Rate vs. Expected | Status | Action |
|---|---|---|
| 1× – 2× normal | Normal | Auto-process |
| 2× – 3× normal | Watch | Slow-track, verify top 20% |
| > 3× normal | Alert | Freeze zone payouts, ring investigation |
| Vertical spike (< 30 min) | Ring Detected | Full zone freeze + escalation |

---

### Adversarial Defense Walls

**Wall 1 — Pre-Trigger Baseline Lock**
Every account's behavioral baseline is snapshotted when a trigger fires. Accounts that came online within 2 hours of the trigger get a Suspicious Activation Flag — they had no prior signal of being in the field.

**Wall 2 — Multi-Signal GPS Verification**
Simple GPS is dead. Trigr requires GPS + cell tower + WiFi BSSID status + IP geolocation to all agree. 3 out of 4 → MEDIUM risk. 2 or fewer → HIGH risk, claim frozen.

**Wall 3 — Behavioral Liveness Proof**
The system looks for at least one delivery platform interaction during the disruption window: order view, map route load, restaurant ping, or order cancellation. A genuine worker always leaves a digital footprint. A fraudster at home shows a flat login with no activity.

**Wall 4 — Real-Time Cluster Firewall**
The payout engine enforces a per-zone velocity limit: max payouts per zone per hour = 2× the registered active worker density. When this is hit, remaining claims enter a review queue — not rejected, just held. This stops liquidity drain before it starts.

**Wall 5 — Post-Payout Graph Audit**
Every payout is mapped to its UPI ID. If 3+ worker accounts route to the same payment destination, it is flagged as a payout ring. Clawback mechanism: confirmed fraud triggers UPI blacklisting and account suspension.

---

### Protecting Genuine Workers

Aggressive fraud detection cannot punish real workers. A genuine partner in a flooded zone may have weak GPS, patchy cell signal, and zero app activity — the same signals that look suspicious.

**Trusted Tier (Score 0–30 for 3+ months):**
Workers with a long clean history are given Trusted status. Their claims are auto-approved regardless of cluster alerts in their zone. Trusted workers skip OTP verification for low-severity claims.

**Appeal Mechanism:**
Every frozen claim generates an SMS appeal token within 15 minutes. The worker can submit: a delivery platform screenshot, a short video of their surroundings, or a partner app activity log. Human review SLA: 48 hours. If upheld, payout is released. Three successful appeals → Trusted tier fast-track.

**Score Decay:**
Risk Score decays by 5 points per clean claim week. A worker who was once flagged can fully recover their standing over time. Score never decays during an active investigation.

**The Core Principle:**
> Trigr never accuses a worker. It validates a situation. An honest worker in a genuine disruption will have corroborating signals from their environment — even if their own device is unreliable. The fraud ring cannot manufacture those environmental signals.

---

## 7. Risk Scoring & Pricing Engine

### Environmental Risk (R_env)

R_env captures real-time severity of weather and air quality at the worker's zone. It is the most important input — directly correlated with order cancellations and halted earnings.

```
R_env = (w_rain × S_rain) + (w_heat × S_heat) + (w_aqi × S_aqi) + (w_flood × S_flood)

Signal normalization:
  S_rain  = min((mm_per_day − 15) / 100, 1.0)    [threshold: 15mm/day]
  S_heat  = min((°C − 38) / 10, 1.0)             [threshold: 38°C]
  S_aqi   = min((AQI − 150) / 250, 1.0)          [threshold: AQI 150]
  S_flood = 0 / 0.5 / 1.0                        [Green / Orange / Red alert]
```

**City-specific environmental weights** (derived from 10-year IMD historical data):

| City | w_rain | w_heat | w_aqi | w_flood | Dominant Hazard |
|---|---|---|---|---|---|
| Mumbai | 0.50 | 0.10 | 0.15 | 0.25 | Heavy monsoon + coastal flood |
| Delhi | 0.10 | 0.30 | 0.45 | 0.15 | Severe winter AQI + summer heat |
| Bengaluru | 0.50 | 0.20 | 0.20 | 0.10 | Year-round rain + waterlogging |
| Hyderabad | 0.40 | 0.35 | 0.15 | 0.10 | Heat waves + erratic rain |
| Chennai | 0.45 | 0.30 | 0.10 | 0.15 | NE monsoon + high heat |

---

### Location Risk (R_loc)

R_loc reflects how historically disruption-prone a worker's zone is — independent of what the weather is doing right now.

```
R_loc = (zone_flood_index × 0.5) + (zone_disruption_frequency × 0.5)
```

Workers who operate in multiple zones in a week get the highest R_loc among their active zones. This updates weekly.

---

### Activity Risk (R_act)

R_act captures outdoor exposure. A worker clocking 70 hours/week in peak summer Delhi faces more income-loss risk than one working 20 hours. This also prevents over-charging workers who naturally reduce hours during bad weather.

```
R_act = min((hours_this_week / 60) × zone_exposure_factor × segment_multiplier, 1.0)

segment_multiplier (Food Delivery) = 1.10
  [Outdoor, time-sensitive, cannot skip or delay orders]
```

---

### User History Risk (R_usr)

R_usr is the only sub-score a worker directly controls. Workers who stay claim-free over time earn progressively lower premiums. New workers start with a moderate unknown-history score that decays toward zero as they build a clean record.

```
R_usr = (claim_frequency_score × 0.60) + (low_tenure_score × 0.40)

claim_frequency_score = min(claims_past_6_weeks / 4, 1.0)
low_tenure_score      = max(0, 1 − (tenure_weeks / 26))
```

---

### Full Worked Example — Rajan, Bengaluru, Week 3 of Monsoon

| Input | Value | Normalized Score |
|---|---|---|
| Rainfall (Mumbai weights) | 82mm/day | S_rain = 0.67 |
| Temperature | 33°C | S_heat = 0.00 (below threshold) |
| AQI | 95 | S_aqi = 0.00 (below threshold) |
| Flood alert | Orange | S_flood = 0.50 |
| R_env (Bengaluru weights) | — | **0.46** |
| R_loc (flood-prone zone) | — | **0.62** |
| R_act (52 hrs, food delivery) | — | **0.96** |
| R_usr (1 claim in 6 wks, 14 wk tenure) | — | **0.49** |

```
CRS = (0.55 × 0.46 + 0.15 × 0.62 + 0.15 × 0.96 + 0.15 × 0.49) × 100
    = (0.253 + 0.093 + 0.144 + 0.074) × 100
    = 56.4 → Moderate Risk Band
```

```
EL  = DWI × ELR = ₹5,600 × 14% = ₹784
P   = ₹784 × 1.35 × 1.00 (Tier A) = ₹1,058

With ±25% cap applied from previous week: final premium = ~₹1,058
```

---

## 8. Tech Stack & System Design

### Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    WEB FRONTEND                             │
│   React 18 + TypeScript + Vite                              │
│   Tailwind CSS + shadcn/ui                                  │
│   Recharts (analytics) + Leaflet.js (zone heatmaps)         │
└──────────────────────┬──────────────────────────────────────┘
                       │ REST + WebSocket
┌──────────────────────▼──────────────────────────────────────┐
│                    BACKEND CORE                             │
│   Python FastAPI (async)                                    │
│   APScheduler — trigger monitor every 15 min per zone      │
│   JWT Auth + phone OTP (workers) + email (insurers)         │
└──────────┬──────────────┬────────────────┬──────────────────┘
           │              │                │
┌──────────▼────┐ ┌───────▼──────┐ ┌──────▼──────────────────┐
│  PostgreSQL   │ │    Redis     │ │     ML Microservice      │
│  (Supabase)   │ │  session +   │ │  FastAPI + XGBoost       │
│  workers      │ │  trigger     │ │  + scikit-learn          │
│  policies     │ │  state +     │ │                          │
│  claims       │ │  queue       │ │  CRS Risk Scorer         │
│  payouts      │ └──────────────┘ │  Dynamic Premium Engine  │
│  zones        │                  │  Fraud Detection Engine  │
└───────────────┘                  │  Disruption Forecaster   │
                                   └─────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│                 EXTERNAL INTEGRATIONS                       │
│  OpenWeatherMap API     — rainfall + temperature triggers   │
│  AQICN / OpenWeather Air — AQI triggers                     │
│  IMD / NDMA             — flood alerts (mock in Phase 1)    │
│  Admin Panel            — curfew / strike activation        │
│  Razorpay Test Mode     — UPI payout simulation             │
│  Platform Mock API      — worker activity + GPS data        │
└─────────────────────────────────────────────────────────────┘
```

### Core Database Schema

```sql
-- Workers
workers (
  id, phone_hash VARCHAR UNIQUE,   -- hashed for privacy
  name, zone_id FK,
  platform ENUM(zomato, swiggy),
  declared_weekly_hours INT,
  avg_hourly_income DECIMAL,
  crs_score DECIMAL,
  upi_id_encrypted VARCHAR,
  tenure_weeks INT,
  trusted_status BOOLEAN
)

-- Policies (weekly)
policies (
  id, worker_id FK, zone_id FK,
  week_start DATE, week_end DATE,
  premium_paid DECIMAL,
  coverage_cap DECIMAL,
  status ENUM(active, expired, skipped)
)

-- Trigger events (zone-level)
trigger_events (
  id, zone_id FK,
  trigger_type ENUM(rain, heat, aqi, flood, curfew, strike),
  severity ENUM(low, medium, high, extreme),
  start_time TIMESTAMP, end_time TIMESTAMP,
  trigger_type_logic ENUM(instant, continuous),
  data_sources JSONB,    -- full audit trail of API sources used
  verified BOOLEAN
)

-- Claims (auto-generated — never manually filed)
claims (
  id, policy_id FK, trigger_event_id FK,
  disrupted_hours DECIMAL,
  expected_income DECIMAL,
  actual_income DECIMAL,
  payout_amount DECIMAL,
  fraud_score DECIMAL,
  fraud_flags JSONB,
  status ENUM(auto_approved, review, rejected, paid)
)

-- Payouts
payouts (
  id, claim_id FK, worker_id FK,
  amount DECIMAL,
  razorpay_ref VARCHAR,
  status ENUM(initiated, success, failed),
  paid_at TIMESTAMP
)

-- Zones
zones (
  id, pincode, city, city_tier,
  flood_incident_count INT,
  disruption_frequency DECIMAL,
  r_loc_score DECIMAL,
  env_weights JSONB,    -- city-specific R_env weights
  last_updated TIMESTAMP
)
```

### Why These Technology Choices

**FastAPI (Python):** Async-first, perfect for a trigger monitor that runs concurrent zone checks every 15 minutes. Integrates naturally with our Python ML models.

**Supabase (PostgreSQL):** Built-in phone OTP auth for worker onboarding, Realtime subscriptions for the insurer's live trigger feed, and auto-generated REST APIs — significantly reduces backend boilerplate.

**Redis:** Handles trigger state (has rain been continuous for 2+ hours in zone X?) and claim queuing without database round-trips.

**XGBoost / scikit-learn:** Gradient Boosted Regressors for the dynamic premium adjuster; Isolation Forest for Phase 3 fraud ring detection at the cluster level.

---

## 9. Development Roadmap

### Phase 1 — Seed (Weeks 1–2, March 20 deadline) ← *Current*

```
✅ Problem analysis + food delivery persona research
✅ 6 parametric triggers defined with exact thresholds
✅ Severity × income loss mapping documented
✅ CRS formula and all 4 risk dimensions designed
✅ Premium model (linear + geometric) documented
✅ 5-layer fraud detection system designed
✅ Market Crash adversarial defense documented
✅ Full payout formula with eligibility gates defined
[ ] GitHub repo setup + project scaffold (FastAPI + React)
[ ] OpenWeatherMap + AQICN API connection (mock data layer)
[ ] CRS computation module (Phase 1: mock inputs)
[ ] Basic premium calculation function
[ ] Supabase project setup — schema creation + seed data
[ ] 2-minute strategy video
```

### Phase 2 — Scale (Weeks 3–4, April 4 deadline)

```
[ ] Worker registration + onboarding flow
[ ] Weekly opt-in flow with premium deduction
[ ] All 6 triggers wired to real + mock APIs
[ ] Dynamic premium calculation (all 4 CRS components live)
[ ] Auto-claim generation engine (zero manual filing)
[ ] Layer 1–3 Fraud Detection (GPS + network + behavioral)
[ ] Razorpay test mode payout
[ ] Insurer dashboard v1 (active policies, live trigger feed)
[ ] 2-minute demo video
```

### Phase 3 — Soar (Weeks 5–6, April 17 deadline)

```
[ ] Layer 4–5 Fraud Detection (cluster detection + post-payout graph audit)
[ ] 7-Day Disruption Forecaster on insurer dashboard
[ ] Zone risk heatmap (Leaflet.js)
[ ] Advanced fraud: GPS spoofing fingerprint detection
[ ] End-to-end disruption simulation demo (rainstorm → trigger → payout)
[ ] Worker dashboard: earnings protected, active coverage summary
[ ] Insurer dashboard: loss ratios + predictive analytics
[ ] Final pitch deck (PDF)
[ ] 5-minute demo video
```

---

## Why Trigr Wins

| What Generic Insurance Offers | What Trigr Builds |
|---|---|
| Workers must file a claim | Workers receive a payout before they ask |
| City-level weather data | Zone-level CRS with city-specific environmental weights |
| Static monthly premiums | Dynamic weekly premiums that adjust for next week's forecast |
| Weather API only | Weather + AQI + Flood alerts + Admin-verified social triggers |
| Binary payout or nothing | Proportional payouts tied to disruption severity and actual hours lost |
| GPS check only | 5-layer multi-signal fraud detection + coordinated ring radar |
| One-size-fits-all pricing | City tier multipliers + user history rewards for clean claimants |

> *Trigr doesn't ask delivery partners to prove they lost income. It watches the world on their behalf — and pays before they even think to ask.*

---

## 10. Team

| Member | Role | Contribution |
|---|---|---|
| Member 1 | Persona & Activity | Delivery partner identity, daily workflow, income model, city-tier analysis, activity tracking |
| Member 2 | Disruption Modeling | Parametric triggers, severity thresholds, income loss mapping, trigger logic |
| Member 3 | Fraud & Fairness | 5-layer fraud detection, adversarial defense walls, Market Crash response, risk scoring |
| Member 4 | Risk & Pricing | CRS formula, premium model, payout engine, eligibility gates, regulatory alignment |

---

## 🔗 Links

| Resource | Link |
|---|---|
| GitHub Repository | *[Link to be added]* |
| Phase 1 Demo Video | *[Link to be added]* |
| Live Demo | *[Phase 2]* |
| Insurer Dashboard | *[Phase 2]* |

---

<div align="center">

**Trigr** — Built for Guidewire DEVTrails 2026

*Seed. Scale. Soar.*

*When disruptions stop your deliveries, we start your payout.*

</div>
