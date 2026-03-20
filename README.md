# Trigr ⚡
### Parametric Income Insurance for India's Food Delivery Partners

> **Guidewire DEVTrails 2026** — AI-Powered Parametric Insurance Platform
> Persona: Food Delivery (Zomato / Swiggy) | Platform: Web Application

---

*When disruptions stop your deliveries, we start your payout.*

---

## The Problem

Every morning, millions of food delivery partners across India log onto Zomato or Swiggy with one goal — earn enough to get through the week. They are not employees. There is no salary, no sick leave, no employer liability. Their income is entirely tied to the number of orders they complete.

Now imagine it starts raining heavily at 2 PM on a Wednesday — the middle of peak lunch hour. Orders stop coming. Customers cancel. The roads become unsafe. A partner who would have earned ₹400 in those three hours earns almost nothing. That loss is permanent. No one compensates them for it. No one even acknowledges it happened.

This is not a rare edge case. Disruptions — heavy rain, extreme heat, severe pollution, floods, sudden curfews — hit Indian cities regularly and predictably. The income loss is real, measurable, and currently uninsured.

**Trigr is built to fix that.**

---

## What Trigr Does

Trigr monitors real-world disruption events continuously across delivery zones. When a qualifying event occurs — rainfall crossing a threshold, AQI spiking, a flood alert activating — the system identifies which enrolled workers were active in the affected area, runs a fraud check, calculates how much income they likely lost, and transfers a proportional payout to their UPI account. Automatically. Without the worker filing anything.

This is parametric insurance. The trigger is the claim. The data does the work.

---

## Table of Contents

1. [Why Food Delivery](#1-why-food-delivery)
2. [How It Works](#2-how-it-works)
3. [Real Worker Scenarios](#3-real-worker-scenarios)
4. [Triggers and Premium Model](#4-triggers-and-premium-model)
5. [AI and ML Architecture](#5-ai-and-ml-architecture)
6. [Fraud Detection — The Work Trail Protocol](#6-fraud-detection--the-work-trail-protocol)
7. [Market Crash Defense](#7-market-crash-defense)
8. [Risk Scoring and Pricing Engine](#8-risk-scoring-and-pricing-engine)
9. [Tech Stack](#9-tech-stack)
10. [Development Roadmap](#10-development-roadmap)

---

## 1. Why Food Delivery

Among all gig delivery segments in India, food delivery partners carry the highest income risk during disruptions. The reason is structural, not coincidental.

An e-commerce partner delivering a package from Amazon has a delivery window measured in hours — sometimes days. If it rains, they can pause and resume. A grocery partner on Zepto or Blinkit operates hyper-locally and can shelter nearby. A food delivery partner on Zomato or Swiggy has a 30–45 minute window to pick up a hot meal and deliver it. There is no pausing, no rescheduling, no indoor fallback. When a storm hits, the order cancels, the income disappears, and the partner has no recourse.

This is why food delivery is the right starting persona for a parametric income product. The disruption is sharp, the income loss is immediate, and the triggers are measurable from external data sources that no worker can manipulate.

| Factor | E-Commerce | Grocery Q-Commerce | Food Delivery |
|---|---|---|---|
| Delivery window | Hours to days | 10–20 minutes | 30–45 minutes |
| Weather sensitivity | Low | Moderate | High |
| Peak hour dependency | Low | Moderate | Critical |
| Income loss on disruption day | 10–15% | 20–25% | 30–40% |
| Order deferral flexibility | High | Low | None |

Income also varies significantly by city. A partner in Bengaluru earns more per day than one in Vijayawada, but the Vijayawada partner has far less financial buffer when things go wrong. Trigr accounts for both — higher-income cities are charged at standard rates while Tier 2 and Tier 3 cities receive a community discount built into the premium.

| City Tier | Examples | Normal Daily Income | Income Loss During Disruption |
|---|---|---|---|
| Tier 1 | Bengaluru, Hyderabad | ₹900–₹1,500 | 30–40% |
| Tier 2 | Vijayawada, Vizag | ₹600–₹1,000 | 25–30% |
| Tier 3 | Smaller cities | ₹300–₹700 | 20–25% |

---

## 2. How It Works

The system runs a continuous monitoring loop across all enrolled delivery zones. Every 15 minutes it checks weather conditions, AQI readings, flood alerts, and any admin-verified social events. When a condition crosses a defined threshold, the disruption engine activates.

```
Worker enrolls on Monday
Premium deducted, coverage active until Sunday night

     |
     |  Every 15 minutes
     |  Trigger monitor checks each zone
     |  Weather API + AQI API + Flood alerts + Admin panel
     |
     |  Disruption detected → Severity assessed
     |  Worker location cross-checked with affected zone
     |
     |  Work Trail Protocol runs — 2-dimension individual check + zone check
     |
     |  TDS = 0.0                         → Hard reject (no further evaluation)
     |  ZCS < 0.2                         → Zone freeze (ring attack)
     |  IAS >= 0.65 AND ZCS >= 0.5        → Auto-approved, UPI within 24 hours
     |  IAS >= 0.35 OR  ZCS >= 0.2        → OTP verify, resolved in 24–48 hours
     |  Otherwise                         → Frozen, appeal token by SMS
     |
     |  Payout = (DWI / 7) × (affected hours / 9) × Severity Factor × Coverage Rate
     |
     Worker receives UPI notification
```

No claim form. No waiting. No friction.

---

## 3. Real Worker Scenarios

### Scenario A — Heavy Rain in Hyderabad

Meera is a Swiggy partner operating in Banjara Hills. It is Thursday afternoon. Rainfall crosses 22mm per hour and stays above the threshold for two continuous hours. Trigr's trigger engine activates.

The system checks Meera's GPS log against the disruption zone — she is in the right area. Her activity log shows she has been online since 10 AM with 6 order completions and active map interactions. Work Trail scores: TDS = 1.0, TTI = 1.0, IAS = 1.0. Zone coherent, ZCS = 0.87. Auto-approved.

Her payout — approximately ₹350 — arrives in her UPI account within 24 hours. She did not file anything.

---

### Scenario B — AQI Shutdown in Delhi

Arjun is a Zomato partner in Dwarka, Delhi. In November, the AQI crosses 260 and stays there for six hours, crossing Trigr's medium severity threshold.

The system confirms Arjun was in his declared operating zone, the trigger is valid, and his account shows normal activity patterns across the prior week. IAS = 0.91, ZCS = 0.83. Auto-approved. His weekly premium was ₹68. The payout he receives that week is proportionally larger — that is the point of insurance.

---

### Scenario C — Curfew in Vijayawada

Priya is a Zomato partner in Vijayawada. An unplanned curfew is declared at 6 PM. An admin marks the affected zone as curfew-active on the dashboard. The system checks whether Priya was working in that zone before the curfew was imposed and calculates hours of income lost after it was declared.

Curfews and local strikes are **secondary triggers** — they pay at 50% of calculated daily loss, funded from a dedicated reserve pool made up of 3% of all premiums collected, keeping the main insurance pool stable.

---

## 4. Triggers and Premium Model

### Primary Triggers — Automated, Real-Time

Monitored continuously from external APIs. Pay at **70% of calculated daily loss**.

| Trigger | Threshold | Activation Type | Data Source |
|---|---|---|---|
| Heavy rain | Above 5mm/hr (low) or above 15mm/hr (high) | Continuous — must persist 2+ hours | OpenWeatherMap API |
| Extreme heat | Above 38°C (low) or above 42°C (high) | Continuous — must persist 2+ hours | OpenWeatherMap API |
| Severe AQI | Above 150 (medium) or above 250 (high) | Continuous — must persist 2+ hours | AQICN / OpenWeather Air |
| Flood alert | IMD flood advisory active | Instant | IMD / NDMA (simulated Phase 1) |

The continuous requirement prevents payouts from short spikes. A 10-minute rainfall burst does not meaningfully disrupt a delivery partner's income. Two hours does.

### Secondary Triggers — Admin-Verified

Activate only after a human admin confirms the event. Pay at **50% of calculated daily loss**.

| Trigger | Verification Method | Activation Type |
|---|---|---|
| Curfew | Admin marks zone on dashboard | Instant after verification |
| Local strike or bandh | Admin confirmation, optional news API cross-check | Instant after verification |

If multiple triggers are active simultaneously, only the highest severity is applied — no double payouts.

---

### Payout Calculation

```
Daily loss  =  (DWI / 7)  ×  (affected hours / 9)  ×  Disruption Severity Factor

Payout      =  Daily loss  ×  Coverage rate

Coverage rate:
  Primary triggers    →  0.70   (70% of daily loss)
  Secondary triggers  →  0.50   (50% of daily loss)

Disruption Severity Factor:
  Low severity    →  0.50   threshold barely crossed, worker can partially operate
  Medium severity →  0.75   significant disruption, meaningful income drop
  High severity   →  1.00   severe conditions, near-complete halt
```

**Why not 100% coverage?** Full income replacement creates no incentive to operate during mild disruptions. Trigr's 70% primary rate follows IRDAI-aligned products like PM-FASAL BIMA and WBCIS (60–80% replacement). Workers still receive meaningful compensation — a full disruption day in a Tier 1 city pays out ₹500–₹700.

---

### Payout Caps

| Cap | Value | Purpose |
|---|---|---|
| Maximum per event | DWI daily × 1.10 | Prevents overcompensation on any single event |
| Maximum per week | DWI × 0.60 | Moral hazard buffer |
| Maximum per month | DWI × 2.00 | Prevents exploitation across catastrophic months |
| Auto-payout events per month | 8 events | The 9th triggers a fraud review |
| Payout SLA | 24 hours | UPI transfer after trigger confirmation |

---

### Weekly Premium

```
Weekly Premium  =  Expected Loss  ×  1.35  ×  City Tier Multiplier

City Tier Multipliers:
  Tier 1 — Mumbai, Delhi, Bengaluru    →  1.00
  Tier 2 — Hyderabad, Chennai, Pune    →  0.92
  Tier 3 — all other enrolled cities   →  0.85

Week-on-week change cap:  ±25%
```

---

## 5. AI and ML Architecture

The CRS formula in Phase 1 uses fixed weights based on actuarial assumptions. From Phase 2 onwards, those weights are replaced by outputs from a machine learning model trained on actual claim data.

### Model 1 — Composite Risk Scorer (CRS)

```
CRS  =  (0.55 × R_env  +  0.15 × R_loc  +  0.15 × R_act  +  0.15 × R_usr)  ×  100

R_env  =  Environmental risk — live weather and AQI, updated every 3 hours
R_loc  =  Location risk — historical disruption frequency of the zone, updated weekly
R_act  =  Activity risk — hours worked and outdoor exposure, updated daily
R_usr  =  User history risk — claim frequency and tenure, updated weekly
```

| CRS Range | Risk Level | Expected Loss Rate |
|---|---|---|
| 0–20 | Very low | 3% |
| 21–40 | Low | 7% |
| 41–60 | Moderate | 14% |
| 61–80 | High | 22% |
| 81–100 | Very high | 30% |

### Model 2 — Dynamic Premium Adjuster

Recalculates each worker's premium every Sunday night using the 7-day weather forecast, AQI trends, last week's platform activity, and any new claims. The ±25% cap prevents sudden large jumps.

### Model 3 — Work Trail Protocol (WTP)

Trigr's fraud detection engine. Covered in full in Section 6. The WTP is a legitimacy-first system — it requires proof of prior work rather than attempting to detect fraud after the fact.

### Model 4 — Predictive Disruption Forecaster

```
Expected claim exposure per zone
  =  probability trigger fires this week
     × active policies in zone
     × average payout per event

Inputs: 7-day rainfall probability, AQI trend projection,
        historical disruption rate for same calendar week in prior years
```

---

## 6. Fraud Detection — The Work Trail Protocol

Most parametric fraud systems ask: *"Is this claim suspicious?"* and try to score suspicion after a trigger fires. That is the wrong question. It keeps the system reactive, always one step behind a motivated attacker.

Trigr asks a fundamentally different question: **"Has this worker already proven they were working?"**

This shift is the entire foundation of the **Work Trail Protocol (WTP)**. The WTP does not detect fraud after it happens. It requires every worker to have passively accumulated an unforgeable evidence trail of legitimate work *before* a payout can ever be considered. A fraudster cannot retroactively manufacture a week of delivery history. The fraud problem is eliminated before the fraud attempt can begin.

---

### The Core Insight — Work Leaves Evidence That Cannot Be Faked in Bulk

A genuine delivery partner on any ordinary Tuesday generates hundreds of verifiable data points without thinking about it — GPS movement near restaurants, order completion events, map API calls, active app interactions, zone entry and exit timestamps. These signals are a natural byproduct of doing the job. They accumulate passively over time and cannot be created in bulk on demand.

The WTP treats this as a **passive evidence ledger** — an ongoing record that every worker builds through ordinary work. When a disruption trigger fires, the system does not ask "is this person lying?" It asks: "how deep is their evidence ledger?" A rich, consistent ledger means fast payout. A thin or empty ledger means scrutiny.

The ledger is evaluated at two independent levels: **individual** (did this specific worker actually work?) and **zone** (does the population of claims from this zone look like a genuine disruption?). Both must pass. Neither can compensate for the other.

---

### Individual Level — Two Dimensions, One Multiplicative Score

#### Dimension 1 — Temporal Depth Score (TDS)

*How much legitimate work did this worker do in the 7 days before the trigger?*

TDS does not count raw hours. It counts **verified work-hours** — hours where three independent signals are simultaneously present and corroborating:

```
A verified work-hour requires ALL THREE of the following:

  (a) GPS zone presence during that hour
  (b) At least one active platform interaction during that hour
      — order check, map load, restaurant ping, or ETA query
  (c) GPS movement consistent with active delivery
      — not static, not a single background ping — measurable movement within the zone

Verified work-hours across the 7 days before the trigger event  =  H_verified

TDS  =  min(H_verified / 15,  1.0)     normalized to [0, 1]
        15 verified hours = full score (1.0)
```

Why require all three signals? GPS presence alone can be spoofed. App interactions alone can be automated. GPS movement alone could be a background process cycling coordinates. All three simultaneously, sustained across many individual hours over seven days, requires either genuine delivery work or an attack sophisticated enough to continuously simulate an active delivery worker in real time — which costs far more than any parametric payout is worth, and must be sustained indefinitely since the attacker cannot know when the next trigger will fire.

| TDS | Verified Hours | What It Means | Decision Path |
|---|---|---|---|
| 1.0 | 15+ | Strong trail — consistent working pattern | Proceed to TTI |
| 0.67–0.99 | 10–14 | Adequate trail, minor gaps | Proceed with flag |
| 0.33–0.66 | 5–9 | Thin trail — slow week or new worker | OTP verification required |
| 0.01–0.32 | Under 5 | Very thin — insufficient pre-event evidence | Manual review triggered |
| 0.0 | Zero | Dormant account — no trail exists | Hard reject, no further evaluation |

**TDS = 0.0 is a hard reject.** The payout engine stops immediately. No GPS check, no timing analysis, no zone evaluation, no appeal path except direct human review submission. This single gate stops every dormant-account attack before the system even processes the GPS coordinate.

---

#### Dimension 2 — Trigger Timing Index (TTI)

*Did the disruption find this worker working — or did the worker find the disruption?*

Every fraud ring has an unavoidable timing problem. Fraudsters learn about a trigger from a Telegram group, a weather alert, or a news notification. Then they activate their accounts. This produces a detectable signature: the worker appeared *after* the disruption was known.

Genuine workers are caught by disruptions. The weather deteriorates while they are already on the road. They were in the zone before it was disrupted. These two scenarios produce opposite timing profiles.

```
TTI is built from two timestamps:

  T_trigger   =  the moment weather data first crossed the parametric threshold
  T_presence  =  the worker's earliest verified zone presence on the trigger day

  Gap  =  T_presence − T_trigger    (minutes; negative = worker arrived before threshold)

TTI:
  Gap ≤ −30 min    worker in zone 30+ min before threshold   →  TTI = 1.00  (was already working)
  Gap −30 to 0     worker in zone just before threshold      →  TTI = 0.85  (plausible)
  Gap 0 to +15     entered zone within 15 min of threshold   →  TTI = 0.65  (borderline)
  Gap +15 to +45   entered 15–45 min after threshold         →  TTI = 0.35  (suspicious)
  Gap +45 to +90   entered 45–90 min after threshold         →  TTI = 0.15  (high suspicion)
  Gap > +90 min    entered 90+ min after threshold           →  TTI = 0.00  (fraud pattern)
```

TTI is never used alone — a worker who genuinely started their shift late should not be penalized purely by timing. It combines with TDS multiplicatively to produce the **Individual Authenticity Score (IAS)**:

```
IAS  =  TDS × TTI     range [0, 1]
```

The multiplicative structure is intentional. A strong work history (TDS = 1.0) cannot rescue catastrophic timing (TTI = 0.0) — IAS collapses to 0. Suspicious timing (TTI = 0.15) cannot be rescued by a solid work trail (TDS = 0.8) — IAS = 0.12, frozen. Neither dimension overrides a failure in the other.

| IAS | Decision |
|---|---|
| ≥ 0.65 | Passes to zone-level check |
| 0.35–0.64 | OTP verification required before payout releases |
| < 0.35 | Claim frozen — appeal token sent by SMS within 15 minutes |

---

### Zone Level — Zone Coherence Score (ZCS)

The IAS evaluates one worker. The ZCS evaluates the *population* of claims from a zone in a single trigger event. Even if every individual claim passes IAS, the collective arrival pattern has a statistical signature that sharply distinguishes genuine mass disruptions from coordinated ring attacks.

Genuine disruptions produce a characteristic claim curve: gradual onset, peak during worst conditions, slow tail as workers resume. Fraud rings produce a different signature: vertical spike, tight time window, abnormal financial topology, clustered account creation dates.

ZCS measures three population signals and combines them multiplicatively — any single signal at zero collapses the entire zone score and triggers a freeze.

---

#### ZCS Signal A — Claim Arrival Distribution

```
For each zone, Trigr maintains a rolling baseline:
  expected_rate  =  enrolled_workers × historical_disruption_claim_rate   (per 30-min window)

Ratio of actual claims to expected within any 30-minute window:

  ≤ 2× expected                →  ZCS_A = 1.0   normal disruption curve, process normally
  2× to 3× expected            →  ZCS_A = 0.6   elevated, monitor
  3× to 5× expected            →  ZCS_A = 0.2   abnormal, slow-track all zone claims
  > 5× expected OR             →  ZCS_A = 0.0   zone freeze — no individual IAS evaluated
  vertical spike under 30 min
```

#### ZCS Signal B — Financial Topology

In a genuine disruption, payout destinations are nearly uniformly distributed — each of N workers has a distinct UPI ID. Fraud rings consolidate: the organizer needs to collect, so multiple accounts route to few destinations.

```
Concentration ratio  =  unique UPI IDs in this event / total claims in this event

≥ 0.95               →  ZCS_B = 1.0   healthy dispersion, one ID per worker
0.80–0.94            →  ZCS_B = 0.7   minor clustering, monitor
0.50–0.79            →  ZCS_B = 0.3   significant clustering, all shared IDs flagged
< 0.50               →  ZCS_B = 0.0   ring financial topology confirmed
```

#### ZCS Signal C — Account Age Distribution

Legitimate workers have spread tenure — enrolled across many weeks or months. Fraud rings recruit in batches just before a forecasted event: account creation timestamps cluster in a narrow window.

```
New account ratio  =  accounts registered within 7 days of trigger / total claimants

< 0.10               →  ZCS_C = 1.0   healthy age spread
0.10–0.20            →  ZCS_C = 0.7   mild surge, normal during growth phases
0.20–0.40            →  ZCS_C = 0.3   recruitment spike, all new accounts flagged
> 0.40               →  ZCS_C = 0.0   ring recruitment pattern confirmed
```

#### Zone Coherence Score

```
ZCS  =  ZCS_A × ZCS_B × ZCS_C     range [0, 1]

Multiplicative — any single signal at 0.0 collapses the zone to a full freeze.

ZCS ≥ 0.5     zone coherent — process individual claims by IAS
ZCS 0.2–0.49  zone under review — all claims slow-tracked pending investigation
ZCS < 0.2     zone freeze — no payouts released, insurer dashboard alerted immediately
```

---

### The WTP Decision Matrix

```
Evaluated strictly in order — first match wins:

  1. TDS = 0.0                         →  HARD REJECT    (no further evaluation)
  2. ZCS < 0.2                         →  ZONE FREEZE    (no individual scores evaluated)
  3. IAS ≥ 0.65  AND  ZCS ≥ 0.5       →  AUTO-APPROVE   (UPI payout within 24 hours)
  4. IAS ≥ 0.35  OR   ZCS ≥ 0.2       →  OTP VERIFY     (payout within 48 hours on confirm)
  5. All other                         →  FROZEN          (SMS appeal token, human review 48hrs)
```

| Outcome | Worker Experience | Expected Share of Genuine Claims |
|---|---|---|
| Auto-approve | Payout to UPI within 24 hours, zero action needed | ~78% |
| OTP verify | SMS prompt, confirm identity, payout within 48 hours | ~18% |
| Frozen | SMS appeal token, submit evidence, human review within 48 hours | ~4% |

---

### Verified Carrier Status

Workers who accumulate 90+ days of continuous clean claim history earn **Verified Carrier** status. Their TDS from the prior 90 days acts as a standing baseline — a Verified Carrier who had a genuinely thin week due to illness or personal circumstances is not penalized by that single week, because their longer history provides the evidence their current ledger cannot.

Verified Carriers are processed through a separate trusted queue that is immune to zone-level freezes. When a ring attack triggers a ZCS collapse, Verified Carriers in that zone still receive their payouts within 24 hours.

Status is earned only through sustained legitimate work. It cannot be purchased, transferred, or manufactured.

---

### What the WTP Makes Impossible

To defeat the WTP, a fraud ring must simultaneously satisfy all of the following:

1. **Register accounts well in advance** — not 72 hours before a target event but weeks prior, destroying the ZCS_C leverage
2. **Have those accounts perform genuine delivery work** — 15+ verified hours weekly, ongoing and indefinitely, on the chance a trigger fires in their zone this particular week
3. **Enter the target zone before the threshold crosses** — requiring the ring to predict the exact minute a parametric threshold is breached, not just the general weather forecast
4. **Keep all UPI destinations unique** — abandoning financial consolidation entirely, making the operation economically unviable for any organizer

Satisfying all four conditions simultaneously is operationally indistinguishable from running a legitimate delivery workforce. The attack either becomes real delivery work, or it fails the WTP.

---

## 7. 🚨 Market Crash Defense

### The Attack

500 dormant accounts. GPS spoofed into an active weather-alert zone in Banjara Hills. All 500 claims filed within 18 minutes of the trigger announcement. The goal: drain the zone's insurance pool before the system responds.

---

### How the WTP Stops It — Decision by Decision

**Step 1 — TDS kills all 500 claims before anything else runs.**

Every account is dormant. Zero verified work-hours in the prior 7 days. TDS = 0.0 for all 500. The WTP hard reject fires immediately. The payout engine never reaches GPS validation, timing checks, zone scoring, or ring detection. The insurance pool is never touched.

```
500 accounts  ×  TDS = 0.0  →  500 hard rejects
Computation time: milliseconds
Pool drained: ₹0
```

**Step 2 — TTI confirms the pattern (redundant catch for any account that somehow had TDS > 0).**

All 500 accounts logged in after the trigger threshold crossed and was publicly known. Gap > +90 minutes for all accounts. TTI = 0.0. IAS = TDS × 0.0 = 0.0. Frozen — independently.

**Step 3 — ZCS collapses independently, triggering zone freeze regardless.**

Even if individual IAS scores had somehow passed:

- 500 claims arrive in 18 minutes against an expected baseline of ~35 claims/hour → ZCS_A = 0.0 → zone freeze
- Claims routing to under 30 unique UPI IDs across 500 accounts → concentration ratio = 0.06 → ZCS_B = 0.0
- 340+ accounts registered within 72 hours of trigger → new account ratio = 0.68 → ZCS_C = 0.0

ZCS = 0.0 × 0.0 × 0.0 = 0.0. Full zone freeze. Insurer dashboard receives an immediate ring-attack alert including the complete UPI topology graph — which destination IDs are at the center of the ring and every account linked to each.

**Step 4 — The ring's financial structure becomes permanent evidence.**

Every UPI ID identified in the topology is flagged for blacklisting. Every account connected to those destinations — across all zones, not just Banjara Hills — is suspended pending investigation. The ring is not just stopped; it is identified and dismantled.

---

### Meera Is Not Caught in the Freeze

Meera has been working Banjara Hills for 4 months. She was already online at 10 AM and three orders into her shift when the rainfall threshold crossed at 2 PM.

```
Meera's WTP evaluation:

  H_verified in prior 7 days:  52 hours, all three signals present each hour
  TDS:  min(52 / 15, 1.0) = 1.0

  T_trigger:    2:00 PM (threshold crossed)
  T_presence:   10:00 AM (Meera's first zone presence on trigger day)
  Gap:          −240 minutes (she was in zone 4 hours before trigger)
  TTI:          1.0

  IAS:          1.0 × 1.0  =  1.0

  ZCS:          Zone frozen due to ring attack
  Override:     Meera holds Verified Carrier status (4 months clean record)
                → processed from Trusted queue, isolated from frozen zone batch

Result:  ₹350 payout to UPI within 24 hours.
Ring:    ₹0 paid out. Ring accounts suspended. UPI topology logged.
```

---

### The Adversarial Asymmetry Table

| What the ring must do to defeat WTP | Why it fails |
|---|---|
| Build 500 accounts with TDS ≥ 0.67 | Requires 500 people doing real delivery work 10+ hours/week indefinitely |
| Achieve TTI > 0.35 for all accounts | Requires predicting exact parametric threshold crossing times hours in advance |
| Keep ZCS_B above 0.5 | Requires 250+ unique UPI IDs — destroys consolidation, making the ring uneconomical to operate |
| Avoid ZCS_A spike | Requires spreading 500 claims over several hours — giving the system investigation time |
| Avoid ZCS_C flag | Requires registering accounts weeks in advance — enormous lead time for uncertain payout |

Every countermeasure the ring takes against the WTP makes the ring either more expensive, more operationally complex, or more detectable. The protocol is adversarially robust not because it catches fraud — but because it makes fraud economically irrational before it starts.

---

## 8. Risk Scoring and Pricing Engine

### Environmental Risk — R_env

```
R_env  =  (w_rain × S_rain) + (w_heat × S_heat) + (w_aqi × S_aqi) + (w_flood × S_flood)

Signal normalization:
  S_rain   =  min((rainfall mm/day − 15) / 100,   1.0)
  S_heat   =  min((temperature °C − 38) / 10,     1.0)
  S_aqi    =  min((AQI − 150) / 250,              1.0)
  S_flood  =  0 / 0.5 / 1.0   for Green / Orange / Red alert
```

City-specific weights reflect each city's dominant historical hazard:

| City | w_rain | w_heat | w_aqi | w_flood | Main Hazard |
|---|---|---|---|---|---|
| Mumbai | 0.50 | 0.10 | 0.15 | 0.25 | Monsoon and coastal flooding |
| Delhi | 0.10 | 0.30 | 0.45 | 0.15 | Winter AQI and summer heat |
| Bengaluru | 0.50 | 0.20 | 0.20 | 0.10 | Year-round rain and waterlogging |
| Hyderabad | 0.40 | 0.35 | 0.15 | 0.10 | Heat waves and erratic rainfall |
| Chennai | 0.45 | 0.30 | 0.10 | 0.15 | Northeast monsoon and high heat |

### Location Risk — R_loc

```
R_loc  =  (zone flood index × 0.5) + (zone disruption frequency × 0.5)
```

Workers active in multiple zones during a week take the highest R_loc among those zones.

### Activity Risk — R_act

```
R_act  =  min((hours this week / 60) × zone exposure factor × 1.10,   1.0)

Food delivery segment multiplier: 1.10
Maximum expected weekly hours cap: 60
```

### User History Risk — R_usr

```
R_usr  =  (claim frequency score × 0.60) + (low tenure score × 0.40)

claim frequency score  =  min(claims in past 6 weeks / 4,   1.0)
low tenure score       =  max(0,   1 − tenure weeks / 26)
```

A new worker starts at R_usr of 0.40. After six months of clean claims it approaches zero, visible in the app as a growing loyalty discount.

### Full Worked Example — Rajan, Bengaluru, Monsoon Week

| Input | Raw Value | Normalized Score |
|---|---|---|
| Rainfall | 82mm/day | S_rain = 0.67 |
| Temperature | 33°C | S_heat = 0.00 (below threshold) |
| AQI | 95 | S_aqi = 0.00 (below threshold) |
| Flood alert | Orange | S_flood = 0.50 |
| R_env (Bengaluru weights) | — | 0.46 |
| R_loc (flood-prone zone) | — | 0.62 |
| R_act (52 hours, food delivery) | — | 0.96 |
| R_usr (1 claim in 6 weeks, 14-week tenure) | — | 0.49 |

```
CRS  =  (0.55 × 0.46 + 0.15 × 0.62 + 0.15 × 0.96 + 0.15 × 0.49) × 100
     =  56.4   →  Moderate risk band

Expected Loss   =  ₹5,600 × 14%  =  ₹784
Weekly Premium  =  ₹784 × 1.35 × 1.00  =  ₹1,058
```

---

## 9. Tech Stack

**Frontend**
React 18 with TypeScript and Vite, Tailwind CSS with shadcn/ui, Recharts for analytics, Leaflet.js for zone heatmaps.

**Backend**
Python FastAPI (async), APScheduler running the trigger monitor every 15 minutes per zone, JWT authentication with phone OTP for workers.

**Database and Cache**
PostgreSQL via Supabase, Redis for trigger state management and claim queuing.

**ML Service**
FastAPI microservice running XGBoost for CRS risk weight tuning, scikit-learn for premium regression, and an Isolation Forest model for ZCS anomaly detection on zone-level claim populations.

**External Integrations**
OpenWeatherMap for rainfall and temperature, AQICN and OpenWeather Air for AQI readings, IMD and NDMA for flood alerts (simulated in Phase 1), Razorpay test mode for UPI payout simulation, platform mock API for worker activity and GPS data.

### Core Database Schema

```sql
workers        (id, phone_hash, zone_id, platform, weekly_hours,
                avg_income, crs_score, upi_id_encrypted, tenure_weeks,
                verified_carrier, tds_rolling, last_active_timestamp)

policies       (id, worker_id, week_start, week_end,
                premium_paid, coverage_cap, status)

trigger_events (id, zone_id, trigger_type, trigger_category,
                severity, start_time, end_time, data_sources,
                verified, threshold_crossed_at)

work_ledger    (id, worker_id, date_hour, gps_present,
                app_interaction, movement_confirmed,
                verified_hour, zone_id)

claims         (id, policy_id, trigger_event_id, disrupted_hours,
                expected_income, payout_amount,
                tds_score, tti_score, ias_score, zcs_score,
                decision, freeze_reason)

payouts        (id, claim_id, worker_id, amount, razorpay_ref, paid_at)

zones          (id, pincode, city, tier, flood_index,
                disruption_frequency, r_loc_score, env_weights,
                expected_claim_rate, freeze_active)

fraud_events   (id, zone_id, trigger_event_id,
                zcs_a, zcs_b, zcs_c, zcs_final,
                accounts_flagged, upi_topology_json,
                ring_confirmed, insurer_alerted_at, resolution_status)
```

---

## 10. Development Roadmap

### Phase 1 — Seed (Weeks 1–2, deadline March 20) ✅

- Food delivery persona research and city-tier income analysis
- Six parametric triggers defined with exact thresholds
- Primary vs secondary trigger architecture documented
- CRS formula and all four risk dimensions designed
- Weekly premium model documented
- Payout formula with 70% and 50% coverage rates
- Work Trail Protocol — TDS, TTI, IAS, ZCS architecture fully designed
- Market Crash adversarial defense documented
- Community pricing and zone fairness model defined
- GitHub repository setup and project scaffold
- CRS computation module with mock inputs
- Basic premium calculation function
- Supabase schema creation and seed data
- 2-minute strategy video

### Phase 2 — Scale (Weeks 3–4, deadline April 4)

Worker registration and weekly opt-in flow, all six triggers wired to real and mock APIs, dynamic premium calculation with all four CRS components live, auto-claim generation engine with zero manual filing, WTP Dimensions 1 and 2 live (TDS hard gate + TTI scoring), work ledger table populated from platform mock API, Razorpay test mode payout, insurer dashboard version one, 2-minute demo video.

### Phase 3 — Soar (Weeks 5–6, deadline April 17)

ZCS zone-level coherence scoring with Isolation Forest anomaly detection, Verified Carrier queue and trusted processing path, 7-day disruption forecaster on insurer dashboard, zone risk heatmap, full end-to-end disruption simulation demo, worker dashboard showing earnings protected and active coverage, insurer dashboard with loss ratios and ring-attack alert timeline, final pitch deck, 5-minute demo video.

---

## Links

| Resource | Link |
|---|---|
| GitHub Repository | To be added |
| Phase 1 Demo Video | To be added |
| Live Demo | Phase 2 |
| Insurer Dashboard | Phase 2 |

---

<div align="center">

**Trigr** — Built for Guidewire DEVTrails 2026

*Seed. Scale. Soar.*

*When disruptions stop your deliveries, we start your payout.*

</div>
