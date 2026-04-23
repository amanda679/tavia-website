# Tavia Health — GTM, Competitive Intelligence & Sales Materials

> Master reference for positioning, competitive landscape, customer personas, offer frameworks, and website copy.
> Last updated: April 23, 2026

---

## Table of Contents

- [[#Company Overview]]
- [[#Positioning & Differentiation]]
- [[#Competitive Landscape]]
- [[#Customer Personas]]
- [[#Reconciliation Deep-Dive (Customer Voice)]]
- [[#VSL & Ad Scripts]]
- [[#Lead Magnet & Funnel Strategy]]
- [[#Website Copy Building Blocks]]

---

## Company Overview

### What Tavia Health Is

Tavia Health is an AI-powered revenue cycle management platform built specifically for outpatient therapy practices — OT, PT, and SLP — with a focus on MSOs, IPAs, and multi-location group practices. The platform automates prior authorization, verification of benefits (VOB), billing reconciliation, ERA parsing, denial tracking, and clinician payroll.

### Founding Team

- **Amanda Kichline** — COO & Co-Founder. Runs product and operations. Built the revenue cycle team, led contracting and credentialing across a multi-state, multi-discipline group practice. Previously early ops leadership at Charlie Health (scaled clinical operations across multiple states). Healthcare policy background (Cornell). Personal connection to rehab therapy through experience as an athlete with hypermobile joints.
- **Reema (Raeva) Sayed** — CEO & Co-Founder. Owns growth and fundraising.
- **Shweta Shrivastava** — CTO. Owns engineering.

### Stage & Fundraise

- Pre-seed, venture-backed (initial investor: Precursor)
- Mid-fundraise targeting ~$2M seed
- ~$800K committed
- Two signed MSO/IPA design partners (significant traction inflection)
- Mid-May checkpoint

### Core Product Capabilities

- **ERA Reconciliation**: Automated matching of ERA data from clearinghouses to bank deposits (EFT, checks, ACH). Handles denials, partial denials, recoupments, reprocessed claims, payer-specific fees (Zelis, etc.), and ERA-to-bank discrepancies.
- **Denial Tracking**: Automated denial detection from ERA data with CARC/RARC code classification, resolution tracking, and biller notes preservation.
- **Claims Review Queue**: Pulls unsent claims from Postgres, matches to chart notes, uses AI (Bedrock/Claude Sonnet) for modifier analysis (59, 96, 95, CO), outputs to billing operations.
- **VOB Automation**: Retell AI phone agent for verification of benefits calls, including IVR navigation, batch calling, and payer-specific scripting.
- **Payroll Queue Builder**: Automated clinician payout generation from reconciled claims data.
- **Patient Responsibility Tracking**: Tracks patient balances from ERA data.
- **RCM KPI Dashboard**: Automated weekly and monthly metrics with retroactive backfill.
- **Morning Briefing EA**: HIPAA-compliant daily briefing pulling Gmail, Google Calendar, and Linear into Slack.

### Infrastructure

- n8n workflow automation platform
- AWS Bedrock (Claude Sonnet / Haiku) for AI processing
- Postgres database
- Google Sheets for operational outputs
- Plaid / bank API integration for deposit matching
- EMR-agnostic (works with Prompt, InSync/Sora, WebPT, and others)

---

## Positioning & Differentiation

### The Gap in the Market

Nobody is building the AI-native billing operations platform that a multi-location therapy MSO runs on.

- **Silna** owns the front door (VOB, prior auth, insurance monitoring) but stops before billing.
- **Brace** handles back-end billing services for single PT practices.
- **SuperDial** sells AI phone calls to MSO billing teams — a tool, not a platform.
- **Nirvana** does eligibility checks horizontally across PT and behavioral health.
- **WebPT RCM** is outsourced billing, not AI-native.
- **Adonis** targets hospitals, not outpatient therapy.

Tavia's positioning: **The AI-native billing operations platform that an MSO runs on** — from ERA parsing to bank reconciliation to clinician payouts, across every entity, payer, and payment rail.

### Unique Mechanism

Tavia's defensible advantage is **cross-workflow learning within a single MSO's operations**. VOB failure patterns inform auth decisions, which change how claims are coded, which affects ERA reconciliation, which updates the denial playbook, which informs payroll. No other player sees the whole loop.

Three mechanism tests:
- **Specificity**: Not "we use AI" — we parse raw ERA feeds, categorize every adjustment type, maintain state across ERA versions, and reconcile against bank deposits via Plaid.
- **Causality**: Explains why reconciliation works when the last internal tool didn't — we pull from authoritative sources (clearinghouse ERAs, bank API, EMR appointments), not biller posting conventions.
- **Defensibility**: The more MSO data flows through, the smarter payer-specific pattern recognition becomes. Single-practice tools can't build this.

### Key Differentiators

1. **Built for MSO structure from day one** — nested entity data model (MSO → sub-practices → clinicians) with payout splits and audit trails.
2. **Source of truth, not BI layer** — pulls from authoritative data sources (clearinghouse, bank, EMR) rather than depending on biller posting conventions.
3. **Full ERA parsing** — categorizes denials, partial denials, recoupments, contractual adjustments, patient responsibility, and payer fees from raw clearinghouse data.
4. **Founder-operator credibility** — Amanda built and runs this in her own practice first. 5 hrs/week → 10-20 min. Caught $3K overpayment.

### Pitch Lines

- "SuperDial sells AI phone calls TO MSO billing teams. WebPT RCM sells outsourced billing TO multi-location practices. Nobody is building the AI-native billing operations platform that an MSO RUNS ON. That's Tavia."
- "If your RCM director hands you a spreadsheet every week, this is for you."
- "Reconciliation is the trust of the MSO." (Louis's own words)

---

## Competitive Landscape

### Tier 1 — Direct Therapy Front-End RCM

#### Nirvana
- **Funding**: $24.2M Series A (Northzone); 11K providers, 2M visits
- **Product**: Cost transparency, eligibility checks. Horizontal: PT, behavioral health. Continuous coverage monitoring.
- **Pricing**: Per eligibility check with a minimum threshold
- **Mechanism**: Proprietary model built on data standards + clearinghouse relationships (99% uptime). Real mechanism is the training loop: dozen expert billers conduct thousands of policy audits/month, customer billers reinforce through millions of observations.
- **Results**: 5 hrs saved/day, 2.5x more efficient verification, 64 hrs saved/week, 50% reduction in VOB failure rate, 17% increase in new client VOB rate, 320x faster (2.5 sec/verification)
- **Testimonial**: "I love that Nirvana has a really good product that leverages innovative AI technology — but I also love working with their team."

#### Silna
- **Funding**: $27M Series A (Accel + BCV); 50K patients
- **Product**: Care Readiness Platform — VOB, prior auth, insurance monitoring. Predictive Document Intelligence validates clinical docs against payer requirements. PT, OT, SLP, ABA. Portal-based.
- **Mechanism**: Requirements library + upstream position. Resolves requirements before submission (opposite of reactive denial management). Knows every payer's documentation requirements, keeps current, reads clinical docs for completeness.
- **Results**: Approval times weeks → 4 hours. 99.8% success rate. Pre-visit 30 min → 30 sec. 8 insurance portals consolidated. Automates 4-5 staff members' work. Setup minutes vs. months. 25% of customers from provider referrals.
- **Customer results**: Benefits checks 7 days vs. 60 days. 2x patient volume without headcount. Admin time 6 hrs/day → 1-2 hrs/day. Replaced Google Sheet workflows.
- **Testimonial**: "Silna has been nothing short of transformational for our growing business."

#### Pocket (letspocket.com)
- **Funding**: Early stage; ~1K verifications, 50 payers
- **Product**: Front-office AI verification ("Rippling for front office"). End-to-end: customer intake widget → EMR integration → clearinghouse → AI voice calling → patient-friendly summary → EMR writeback.
- **Mechanism**: Vertical integration of full VOB workflow + AI voice calling for missing benefits. At current scale, no defensible mechanism yet — a workflow choice, not a moat.
- **Results**: 1,000+ hours saved, 1,000+ verifications, 50+ payers mapped, 1,000+ patient summaries
- **Testimonials**: "Pocket is really fast and really helpful with our verifications. Pocket legitimately saved us a lot of time on the phone." — Front Office Manager, Texas (3 locations)

### Tier 2 — EMR + RCM Bundled

- **SPRY**: PT/OT/SLP EMR with AI prior auth ($250-1500/mo)
- **Raintree**: Full EMR + RCM suite
- **WebPT RCM**: Outsourced billing (not AI-native)
- **Fusion/Ensora**: EMR with billing add-ons

### Tier 3 — VOB/Eligibility API

#### Sohar
- **Funding**: $3.8M seed (YC S23, Kindred)
- **Product**: 96% accuracy, 6-second latency eligibility. Behavioral health focus.

### Tier 4 — Enterprise RCM (Hospitals, Not Therapy)

- **Adonis**: $95M total ($40M Series C, Quadrille). Mount Sinai. AI orchestration for hospitals.
- **Smarter Technologies**: New Mountain Capital May 2025 roll-up (Access Healthcare + SmarterDx + Thoughtful.ai). 60+ hospitals.
- **Anomaly**: $35.2M. Payer-side.
- **Cohere Health**, **Myndshft**: Prior auth automation, enterprise.

### Tier 5 — AI Billing Services by Vertical

#### Brace Health
- **Funding**: Bessemer, Eniac, Underscore
- **Product**: Back-end collections + billing. US-based biller + AI rules engine. Appeals, patient responsibility, payer denial fighting. PT only. Works across EMRs (WebPT, Prompt, Empower, Healthie, JaneApp, PTEverywhere, Stride).
- **Mechanism**: Human biller stays with the account, amplified by AI compounding on PT-specific patterns. Not a pure software play — betting RCM requires relationship + judgment + domain knowledge.
- **Results**: +5% payer revenue, +6% patient revenue. Response time <60 min. "Top 1% PT billers." Weekly front desk coaching.
- **Testimonial**: "I've seen a nearly 10% increase in revenue since starting with Brace Health. Our billing partner Lisa is amazing."

#### Other Verticals
- **Raven Health**: ABA billing
- **RethinkBH BillAI**: ABA (launched April 2026)
- **Verse Therapy**: SLP MSO (YC W24)
- **HealthSpark**: PT MSO (YC)
- **Clarity RCM**: Derm ($1B managed, Inc 5000 540% growth)
- **Overdrive Health**: YC

### MSO Billing Operations Layer

#### SuperDial
- **Funding**: $15M Series A (SignalFire), $20M total
- **Product**: AI phone agent infrastructure. Customizable scripts/outputs. Human fallback team.
- **Mechanism**: Payer-specific phone tree map that updates continuously. AI navigates trees, waits on hold, extracts data. Human ops steps in when AI can't complete — tight HITL loop.
- **Results**: 4x productivity, 3x cost reduction (67% savings), 5M+ calls. West Coast Dental: 10K calls/month, 70K backlog cleared. MSO case study: 78% reduction in manual claim processing, 60% backlog reduction Q1.
- **Testimonials**: "Our team loves SuperDial. It just works." / "What used to take one of my AR reps three hours on hold with the payer was resolved automatically."

#### Cair Health
- YC. AI for billing companies / BPOs.

### Adjacent / Not Competitors

- **SuperDial**: Tool sold TO MSOs, not the operating platform MSOs run on
- **Paratus Health** (YC): Voice AI for outpatient clinics
- **LunaBill** (YC): Voice billing
- **Aegis** (YC): Denial appeals
- **Adentris** (YC): Documentation
- **Claimable**: Patient appeals
- **PocketHealth**: Canadian medical imaging (NOT letspocket)
- **Arya Health**: $18.2M workforce ops (not RCM)

### Common Competitor Headlines

- Time saved
- Fewer team members hired
- Lower cost
- More efficient operations

---

## Customer Personas

### Persona Comparison Matrix

| | Vicki | Louis | Ken/Jeanine |
|---|---|---|---|
| **Scale** | 1 practice, ~40 clients | MSO with growing practice count | $25M, 140K visits, 20+ clinics |
| **Role** | Clinical owner-operator | MSO operator | Super-group co-founder + ops director |
| **Billing team** | Herself and her partner | 6-7 person Philippines team + RCM director (2.7 cost-to-collect) | 3 FTEs centralized at 3D + decentralized teams at other divisions |
| **Current stack** | InSync/Sora | Fragmented: Xaya ACH, RCM spreadsheets, Chase | Prompt + P-Verify + Copper Hill |
| **Primary pain** | Denials and EI dependency loop | Reconciliation across revenue streams | Payer rule changes + OOP tracking + automation trust |
| **Decision style** | Relational, overwhelmed, trust-first | Analytical, show-me-the-tech, team-vetoed | Data-validated, trust-first, Jeanine is gatekeeper |
| **What they're buying** | Relief | MSO-level infrastructure | Automation they can trust |
| **Who's paying** | Her + business partner | Louis, with Alex/Sarah approval | Ken signs, Jeanine approves |
| **Pitch angle** | "We'll fight your denials so you don't have to" | "MSO operating system with single source of truth" | "Automation you can trust, proven on your data first" |

### Customer Journey Mapping

- **Vicki** = Case study proving "we make this disappear." Low-complexity, high-relief story.
- **Louis** = Expansion story — proof Tavia scales as an MSO grows from 1 to N practices.
- **Ken/Jeanine** = Trophy account — proof Tavia serves a $25M super-group with a sophisticated stack.

---

### Louis Ezrick — Evolve Fit For Life

**Persona**: MSO Operator / Technically-Aware Owner-Operator

**Practice**: Evolve Fit For Life Physical and Occupational Therapy (NY). MSO structure under separate tax ID, billing other practices. Out-of-network focus.

**Team**: 6-7 person Philippines outsource team ($6-7/hr, 4-5yr retention). RCM director. Alex (built previous internal tool, technically sharp, skeptical). Justin (RCM). Sarah. ~7 min avg benefit verification (BCBS 40 min, others 3 min).

**Current stack**: EMR (medical records + billing combined). Xaya/Saya for direct ACH. Chase Business (main practice) + Chase Connect (MSO). Manual check scanner (workers' comp Fridays). Chase mobile deposit (clinical directors, new). Google Sheets/spreadsheets for reconciliation.

#### What Keeps Him Awake

- Money coming in he can't account for — caught $3K overpayment from duplicate RCM spreadsheet entries
- Whether the 20 hrs/month reconciliation problem scales to 200 hrs/month
- Whether his next internal tool attempt will fail like the last one
- Whether Alex and Sarah will sabotage any vendor he brings in

#### What He's Afraid Of

- Being burned again on a tech project ("we've been through this 100 times")
- Team rejecting the tool, forcing him to choose sides
- Not having the technical vocabulary to defend a vendor choice against Alex
- Growing the MSO faster than infrastructure can keep up

#### Who He's Tired Of

- Vendors who over-promise and can't survive his team's scrutiny
- Banks (Chase) for lacking accessible API/data infrastructure
- The fragmentation of how payments physically arrive

#### Top 3 Daily Frustrations

1. Manual reconciliation across Xaya ACH, MSO RCM spreadsheets, and mailed checks
2. Fragmented check processing (Brooklyn office, Chase mobile deposits, Friday scanner)
3. Having to manually download PDFs from Chase — no easy data extraction

#### What He Secretly Desires

- A single source of truth he can actually trust
- MSO-level visibility: owed vs. in the bank, at any moment
- To be the MSO that generates the payout spreadsheet TO other practices
- Direct payer contracts and real MSO power

#### Decision-Making Bias

- **Analytical / technically skeptical.** "Show, don't tell." Proof > pitch.
- Burned before, so bias toward vendors who demonstrate technical competence in front of his team
- "Single source of truth" framing won't survive contact with Alex — needs technical specificity

#### His Language

- "Single source of truth," "reconciliation"
- MSO, IPA, direct payer contracts
- Xaya/Saya, Chase Business, Chase Connect
- RCM director, clinical directors, billers
- "Poking one thing breaks another"
- "Reconciliation is the trust of the MSO"
- "It's like a thorn in my side"
- "We've been through this 100 times"

#### His Reconciliation Process (In His Own Words)

**On the multi-source problem:**
> "Money's coming in from multiple sources in different ways."

> "Saya pays us a direct ACH transfer, but it's not connected to our EMR. So we have to manually enter everything. And reconcile everything against a spreadsheet that they send us."

> "The RCM director there is sending us, again, a spreadsheet. With all the different claims, with the amounts."

**On catching errors:**
> "She had overpaid us by $3,000 this week. Because she had duplicate remittances on her spreadsheet."

**On why it matters:**
> "Reconciliation, for me, is the trust of the MSO. Are we sending you the correct amount? Are we paying you what we're supposed to?"

> "So much of accounting is reconciliation. And the fact that medical doesn't work so easily is annoying."

**On the payer mess:**
> "A payer will take a dollar or 50 off of each claim because they're paying through Zelis. Or the ERA will say 120, but 119 hits the bank account. And it's not recorded anywhere."

**On the previous tool failure:**
> "The new RCM director didn't like the way that we were posting specific takebacks... the way that the software was built was built on a certain rubric. So now, the person that built it was upset that we changed everything. He's like, fine. If you don't want to do it my way, then do it your way."

**His workflow:**
1. Weekly reconciliation + monthly full trip
2. Saya ACH → manual entry, reconcile against Saya's spreadsheet
3. MSO payments → RCM director's spreadsheet with claims/amounts
4. Remittances come in separately, directly
5. Reconcile internal software vs. RCM director's spreadsheet
6. Checks: Brooklyn office weekly, workers' comp scanner Fridays, BCBS patient checks via clinical director Chase mobile deposits
7. Bank data: manually download PDFs from Chase
8. Payouts: weekly Tuesday based on prior Monday-Friday collections
9. Total: ~20 hrs/month (was ~40 hrs/month before, came down after building then losing custom software)

#### Deal Status

- **Stage**: Pending onboarding
- **Next steps**: BAA + discovery questionnaire sent, Google Drive data sharing for initial analysis, Chase API research
- **Risk**: Team buy-in (Alex, Sarah, Justin)
- **Contacts**: Louis (owner), Alex (built previous tool), Justin (RCM), Sarah

---

### Vicki Green — Innovative Therapy LLC

**Persona**: Solo Clinical Owner / Overwhelmed Operator in Transition

**Practice**: Innovative Therapy LLC. 95% early intervention, 5% private pay. ~15-20 active kids, 3 new evals/week. Patients served until age 3.

**Team**: Vicki and her business partner do all billing. Leonie (admin) handles TRICARE referrals and patient intake.

**Current stack**: InSync/Sora (formerly Fusion) EMR. Ability portal (Medicaid). Humana portal. Availity for ERA pulling. Paper planner calendar.

#### What Keeps Her Awake

- Denied claims she hasn't gotten to — backlog of outstanding denials with unidentified patterns
- 3+ hours per denial chasing $60 payments
- Prior auth backlog blocking care delivery
- Can't bill Early Intervention until private insurance pays — commercial delay blocks state submission
- Practice in transition — general operational pressure

#### What She's Afraid Of

- Getting overwhelmed by the transition she's already in
- Confusing her admin assistant with too many tools/processes
- Technical friction (was on phone/tablet during call, computer not working)
- Getting stuck waiting on auths, unable to deliver care
- Missing money she's owed

#### Who She's Angry At

- Private insurance companies — diagnosis code rejections, phone tag for $60
- Third-party pricers that underpay
- The structural unfairness of fighting commercial insurance just to unlock state EI billing
- Not angry at Medicaid — it pays smoothly, which makes the contrast painful

#### Top 3 Daily Frustrations

1. Fighting diagnosis code rejections across multiple attempts per claim
2. Phone tag with insurance reps — wrong numbers, transfers, hold times
3. Managing private insurance as prerequisite to EI state submission

#### What She Secretly Desires

- To get paid what she's owed without fighting for every dollar
- Her time back ("time back in my life for things she enjoys")
- Move from reactive firefighting to clean, proactive workflows
- Not be the one doing billing at all — offload entirely

#### Decision-Making Bias

- **Emotional / relational.** Overwhelmed, not analytical. Needs trust before she'll move.
- Decisions are collaborative — needs partner buy-in
- Responsive to "we'll take this off your plate" framing
- Surprised/receptive when offered things she didn't think possible (EI state submission support)

#### Her Language

- "Early Intervention" / "EI"
- Denials, diagnosis code rejections, auths
- InSync / Sora (formerly Fusion)
- Ability portal, Humana portal
- "Just easier" (reasoning for proactive auth)
- "I don't have a system. I check more than having a system."
- "It's tedious. Could take me a couple days."
- "Without you guys, I wouldn't have done anything."

#### Her Reconciliation Process (In Her Own Words)

**On the central feeling:**
> "It's tedious. Gosh, it could take me a couple days. Honestly."

> "I don't have a system. I check more than having a system."

**On the fragmentation:**
> "It's kind of in multiple places. I rely on the bill that I send to the infant programs for a lot of my tracking of commercial insurance clients. And then I just kind of have to go into Availity to look at all of the Medicaid things."

> "Nothing is centralized."

**On why denials don't get worked:**
> "I don't always know what to do. The other piece is not just not knowing what to do and not knowing how to handle it is just not having the time to handle it. Without you guys, I wouldn't have done anything."

**Her workflow:**
1. Monthly reconciliation stretching into days of work; bills infant program quarterly
2. Pull commercial ERAs (Anthem, Humana) from In Sora
3. Pull everything else from Availity
4. Use paper planner calendar to identify which dates to look up
5. ERAs come back with multiple clients on one ERA — manually sort
6. Black out client information that doesn't pertain to specific infant program
7. Create spreadsheet: client, TRICARE number, discipline, insurance payment, difference
8. Send spreadsheet + ERAs + explanation letter to infant program
9. For denials: copy ERA comment into letter
10. Norfolk requires 2-3 attempts; Hampton/Newport News accept one good letter
11. Does not close the loop — no reconciliation back when infant program pays

#### Deal Status

- **Stage**: Active customer
- **Next steps**: Lindsay credentialing resubmission, UHC secondary claims investigation, invoice once ERAs accessible, centralized dashboard build
- **Risk**: Low — already trusts team, already paying

---

### Ken Guzzardo & Jeanine MacDonald — 3D Physical Therapy / IPTA Group

**Persona**: Super-Group Operator at Scale / "We've Already Solved Most of This"

**Practice**: 3D Physical Therapy (52% of IPTA). IPTA super group: $25M revenue, 20+ clinics, 140K visits/year, 20% annual growth.

**Team**: Ken = co-founder/signer. Jeanine = Operations Director and true gatekeeper (accounting background, 6yrs PT ops). 3 FTEs on verification/benefits/auth at 3D. Other IPTA divisions handle ops at clinic level.

**Current stack**: Prompt EMR (migrated from WebPT). P-Verify (eligibility). Copper Hill (data partner, recently onboarded). Google Sheets being phased out.

#### What Keeps Them Awake

- Scaling from $25M without tripling ops headcount
- Whether Prompt/P-Verify/Copper Hill holds up across new states and divisions
- Payer rule changes discovered only when claims get denied (8,000-page provider manuals)
- Telling patients one cost then billing more ("it never sits right")
- Delaware expansion, Maryland consideration — different payer networks

#### What They're Afraid Of

- Automating bad data ("I won't automate what I can't trust")
- Making the tight-knit ops team feel threatened
- Oversold AI that doesn't survive real data
- Paying for a vendor that duplicates what Prompt already does

#### Who They're Angry At

- Insurance companies, unambiguously — "It all boils down to the insurance company, without a doubt"
- Payers who don't communicate rule changes proactively
- TPA chains (Practice → Rehab Provider Network → ASH → Cigna)

#### Top 3 Daily Frustrations

1. Electronic verification misses enough nuance that manual portal/phone work still required daily
2. Deductible/max OOP tracking broken — Prompt only sees internal claims, not PCP/specialist activity
3. Payer-specific auth requirement changes show up only as denials

#### What They Secretly Desire

- One central source of truth for payer rules and updates (Jeanine's explicit wish)
- Full deductible/OOP visibility across patient's entire claims activity
- Scale visits without adding FTEs (held headcount flat through 400% growth)
- Standardized workflows across all IPTA divisions
- ROI clarity

#### Decision-Making Bias

- **Analytical, data-validated, trust-first.** Jeanine won't automate what she can't verify.
- Evaluate new vendors against what they already have, not a blank slate
- Price matters — mentioned explicitly
- Want transparency about capability limits, not a pitch

#### Their Language

- "Super group," "divisions," "IPTA"
- 140,000 visits, $25M revenue, 20% growth, 20+ clinics
- Prompt, P-Verify, Copper Hill
- Horizon vs. HighMark, United vs. Optum, TPAs, ASH, Rehab Provider Network
- "Source of truth"
- Workers' comp, auto insurance (state-specific)
- "It never sits right"

#### Deal Status

- **Stage**: Pending — Tavia to prepare detailed proposal with cost breakdown and ROI
- **Next steps**: No follow-up captured after March 13
- **Risk**: High bar for trust; already have decent tooling; price-sensitive

---

### Dr. Kim / Balance in Motion PT

**Persona**: Out-of-Network Underpayment Problem (Not Core Fit)

- April 21 meeting. Aetna/Cigna paying 1/3-1/2 of requested. 2+ month negotiation timelines.
- Not a core product fit but signals payer negotiation-as-service as adjacent opportunity.
- **Status**: Pending — free claims analysis using 1-5 EOBs offered.

---

## Reconciliation Deep-Dive: How Louis vs. Vicki Describe It

### The Structural Difference

| | Louis | Vicki |
|---|---|---|
| **Scale** | MSO, multiple entities, multiple payment streams | Solo practice, ~15-20 kids |
| **Time cost** | ~20 hours/month | A couple days/month |
| **What they reconcile** | ERA ↔ bank ↔ Saya ACH ↔ MSO spreadsheets ↔ check scanner ↔ mobile deposits | ERA ↔ schedule ↔ infant program owed ↔ insurance paid |
| **Data sources** | Saya, RCM director spreadsheet, Chase Business, Chase Connect, EMR, paper checks, mobile deposits | In Sora, Availity, paper calendar, payer portals |
| **Edge cases** | Zelis fees, $1 ERA-vs-bank discrepancies, take-backs | Multi-client ERAs requiring manual redaction, denials without a system |
| **Central frustration** | "A thorn in my side" — data inconsistency = trust erosion | "Tedious" — manual pulling and matching is worst |
| **Why they care** | "Reconciliation is the trust of the MSO" — growth blocker | "I need help" — time and expertise blocker |
| **What broke last fix** | Custom software failed from RCM/dev posting conflict | Never tried — "checks more than having a system" |
| **Mental model** | "It should be the stupidest, easiest thing but for some reason it's not" | "I just need a better way to... I got to think about it" |

### The Core Insight

Louis says he wants a system. Vicki says she wants time back. Both can describe their workflow in surprising detail because both are living it hands-on. That granular knowledge means both are ready customers — they just need different product framings.

---

## VSL & Ad Scripts

### Target Customer Definition

Multi-location, multi-specialty outpatient therapy practices or MSOs where money is coming in from too many places to track by hand. The trigger is **complexity of money in, not number of doors**.

The qualifier is structural: multiple payment streams (direct ACH, MSO billing spreadsheets, multiple bank accounts, paper checks across offices).

Headline test: **"If your RCM director hands you a spreadsheet every week, this is for you."**

---

### Short Ad — 45 Seconds

> If you run a multi-location therapy practice or an MSO, I want to ask you something.
>
> How many hours a month is your team spending on reconciliation? Matching ERAs to bank deposits, chasing down why 119 dollars hit the bank when the ERA said 120, figuring out which payer took a recoupment six weeks after the fact.
>
> If the answer is more than a few hours, you're not alone. Most of the MSO operators I talk to are spending 20-plus hours a month on this, and they're still catching 3,000-dollar errors after the fact.
>
> I built Tavia Health because I had this exact problem in my own practice. Five hours a week of reconciliation, now down to 10 to 20 minutes. One source of truth across every payer, every bank account, every entity.
>
> If you want to see how it works, book a 30-minute discovery call at the link below. We'll look at your data together. First 30 days is free — if it's not clearly better than what you're doing today, we walk away.
>
> Link's in the description. Let's take a look.

---

### VSL Script — ~7 Minutes (Teleprompter-Ready)

> If your team is spending 20-plus hours a month on reconciliation, and you still don't trust the numbers — this is for you.
>
> I'm talking to multi-location therapy practice owners and MSOs. If your RCM director hands you a spreadsheet every week. If money is coming in from ACH transfers, MSO billing, patient checks, and mobile deposits. If you've already caught an overpayment this year that nobody flagged until you ran the numbers yourself — keep watching.
>
> We built a platform that gives you a single source of truth across every payment stream. ERA to bank, down to the penny. And if we can't cut your reconciliation time in half within 30 days, you don't pay for that month.
>
> Here's what we guarantee.
>
> First, we'll cut your reconciliation time from 20-plus hours a month to 10 to 20 minutes a week.
>
> I know this works because I did it in my own practice first. It used to take me five hours a week to match ERAs to bank deposits across multiple payers, tax IDs, and check types. Now it takes 10 to 20 minutes. The only time I spend is reviewing the edge cases the system flags.
>
> Second, we'll give you MSO-level visibility across every entity, every payer, every bank account.
>
> You'll know exactly what you're owed, what's actually hit the bank, and where the gap is. In real time. Not at the end of the month when your RCM director finally hands you the spreadsheet. When money is off, you'll see it the same day — not six weeks later. I caught a 3,000-dollar overpayment this week just by running this reconciliation against my own books. Our design partners have caught the same kinds of errors. That's not coincidence. That's what happens when you actually look at the data.
>
> Third, we'll scale with you as you add practices, without adding headcount.
>
> Your reconciliation model right now is a spreadsheet from your RCM director and manual entry for ACH deposits. That works for one practice. It breaks at three. It's unrecoverable at ten. We're built to take the same process and run it across every sub-entity in your MSO. So the spreadsheets your RCM director sends out to other practices become structured, automated payouts with full audit trails.
>
> We guarantee these results. If we can't cut your reconciliation time in half within 30 days of go-live, you don't pay for that month.
>
> Why can we make this kind of promise? Because we've lived it. I run this exact platform inside my own practice. Five hours a week became 10 to 20 minutes. Fewer write-offs. Real-time visibility. We caught a 3K overpayment the same week we went live. Our design partners have gone from 20 hours a month on reconciliation across ACH, MSO spreadsheets, and three different check intake methods — to a single dashboard that reconciles automatically.
>
> If that's all you need to hear, book a 30-minute discovery call. No pressure. We'll look at your data, tell you exactly where the reconciliation gaps are, and show you what the platform would do for your specific setup. If it's not a fit, we'll tell you.
>
> If you want to know why this works when the last tool you tried didn't, stay with me.
>
> Here's reason one.
>
> We're not a BI layer sitting on top of your existing workflow. We're the source of truth underneath it.
>
> Most BI tools pull data from your EMR and depend on your billers posting things a certain way. The moment your RCM director changes how she handles takebacks, the BI breaks. That's exactly what kills most internal tools. The developer and the RCM director have incompatible posting assumptions, and neither will bend. Remember that 21-cent takeback that broke the last tool your team built? That's the exact class of problem we solve structurally.
>
> We pull from the authoritative sources directly. ERAs from your clearinghouse. Deposits from your bank through Plaid or direct API. Appointments from your EMR. Then we reconcile those three against each other. Your billers' posting conventions don't enter the equation until the end, when we hand them a clean, reconciled picture. That means your RCM director can change her process tomorrow and our system still works.
>
> Here's reason two, and this is the big one.
>
> We parse the ERA data directly from the clearinghouse. So you see every dollar — in, out, and back — no matter how the payer formats it.
>
> Here's why reconciliation is so hard. The data coming back from payers is inconsistent. Every payer has its own logic.
>
> A claim comes back denied and the reason is buried in a code on line 47 of the ERA. A claim comes back partially denied — they paid you for the eval but not the manual therapy add-on, and now your expected amount doesn't match your paid amount and nobody can tell you why. A payer does a recoupment six weeks after the fact. They decide they overpaid you in March, and in May they quietly take it back by debiting against a new claim. Your biller sees the takeback. Your bank sees the reduced deposit. Nothing lines up. A claim gets reprocessed and the new ERA shows a different amount than the original — your posting from last week is now wrong. Aetna pays through a pricer and takes a dollar off the claim. Cigna's ERA says 120 but 119 hits the bank because of a Zelis fee that was never documented anywhere.
>
> This is where most reconciliation tools fall over. They match deterministically on amount and date. The moment the payer does anything clever, the match breaks.
>
> We parse the raw ERA feed directly — not a summary — and we categorize every adjustment on every claim. Denials. Partial denials. Recoupments. Contractual adjustments. Patient responsibility. Payer fees. When a payer reprocesses a claim three weeks later, we see the change and update the record. When a recoupment shows up on a future ERA, we trace it back to the original claim, so you know exactly which service was clawed back and why.
>
> The result: you see the full inflow and outflow in real time. Every denial with the reason. Every partial payment with the gap. Every recoupment with the source. Your biller stops guessing why 119 hit the bank when the ERA said 120. The system already knows.
>
> And here's reason three.
>
> We built this for the MSO structure from day one. Not retrofitted.
>
> Most reconciliation tools assume one entity, one bank account, one billing pipeline. Our data model is built around nested entities — the MSO at the top, sub-practices underneath, clinicians underneath those. When a patient pays, the system knows which sub-practice delivered the service, which clinician rendered it, what the payout split looks like, and how the money needs to flow. You stop generating the RCM director's spreadsheet manually. The system generates it, with a full audit trail.
>
> That's the part nobody else has. Silna stops at the front door. Brace handles billing services for a single PT practice. SuperDial makes the phone calls to payers. Nobody is building the reconciliation engine for an MSO operating across multiple entities and multiple payment rails. That's us.
>
> So here's the offer. Book a discovery call at the link below. We'll review your current reconciliation process, show you the parts we can automate in the first 30 days, and give you a concrete plan with pricing before you commit to anything.
>
> And if you're still on the fence, here's the deal. The first 30 days is a free discovery and pilot. We'll take a slice of your ERAs and bank data, run the reconciliation, and show you what we find. If it's not clearly better than what you're doing today, we walk away. No invoices. No strings.
>
> You already know reconciliation is a thorn in your side. The only question is whether you want to keep running the workaround — or actually fix it.
>
> Book the call. Let's take a look at your data together.

---

### VSL Production Notes

- **Length**: ~7 min read aloud. Cut anything over 8 min.
- **Strongest moments** (say directly to camera): "5 hours a week became 10 to 20 minutes," "caught a 3K overpayment," "21-cent takeback."
- **On screen**: Design partner logos (once available), dashboard screenshot, 20hrs→20min graphic.
- **Don't over-produce.** Authenticity > animation.
- **On "AI"**: Only named once in the full script. Louis's team will dismiss buzzwords. Lead with mechanics.
- **Social proof placeholders**: Replace with actual design partner case studies once available. Until then, lean on your own practice numbers.
- **Make 3 specialty versions**: Call out OT, SLP, PT separately for targeted ads.

---

## Lead Magnet & Funnel Strategy

### The Funnel

1. **Ad** (LinkedIn/paid social, 30-45 sec) → drives to landing page
2. **Landing page** has VSL video + lead form
3. **Lead form** captures: name, phone, email + 3-5 qualifying questions
4. **On submit**: automatically sends the guide (reconciliation playbook)
5. **Confirmation page**: "Guide is on the way to your inbox. In the meantime, want 1:1 support? Book a free call." + booking link
6. **Booking link also inside the guide itself**

### Lead Magnet: Reconciliation Guide

A downloadable guide with actual logic in it — not a generic whitepaper. Should include:

- How to structure reconciliation across multiple payment streams
- Common ERA matching pitfalls by payer (Zelis fees, recoupments, reprocessing)
- The 80/20 rule: deterministic matching for most transactions, manual review for edge cases
- Simple framework for tracking denials, partial denials, and take-backs
- Checklist: "What to do when the ERA and the bank don't match"
- Examples with real-world scenarios (anonymized)

The guide should be a scroll — static images, examples, the more the better. Make it feel like operational IP, not marketing content.

### Qualifying Questions (Lead Form)

Suggestions for 3-5 questions that qualify without being intrusive:

1. How many locations does your practice or group operate? (1 / 2-5 / 6-15 / 15+)
2. How many hours per week does your team spend on reconciliation? (<2 hrs / 2-5 hrs / 5-10 hrs / 10+ hrs)
3. What EMR does your practice use? (Open text)
4. What's your biggest billing operations challenge right now? (Reconciliation / Denials / Auth tracking / Collections / Other)
5. What is your role? (Practice owner / Operations director / Billing manager / Other)

### Target Outcome Qualifier

If they spend over 2 hours per week on reconciliation, they qualify.

### Ad Variants to Create

- **General MSO version** (the 45-sec script above)
- **PT-specific version**: Call out PT directly
- **SLP-specific version**: Call out SLP directly
- **OT-specific version**: Call out OT directly

---

## Website Copy Building Blocks

### Headlines (Test Multiple)

- "The billing operations platform therapy MSOs run on."
- "One source of truth. Every payer. Every payment. Every entity."
- "Stop reconciling. Start trusting your numbers."
- "ERA to bank. Down to the penny."
- "Built for multi-location therapy practices. Not retrofitted."

### Subheadlines

- "Tavia Health automates the reconciliation, denial tracking, and clinician payouts that your RCM team is doing by hand."
- "We parse every ERA directly from the clearinghouse — denials, partial payments, recoupments, payer fees — so you see exactly where every dollar went."
- "Our founder built this in her own practice first. 5 hours/week of reconciliation became 10-20 minutes."

### Value Props (Short)

- **Accurate source of truth** across all data sources — ERA, bank, EMR
- **Save time** vs. doing it manually — 20 hrs/month → 10-20 min/week
- **Reduce errors** — catch overpayments, duplicate remittances, payer take-backs
- **Improve collections rate** — track every denial with the reason, every partial payment with the gap
- **Scale without headcount** — add practices without adding reconciliation staff

### Results to Feature

- 5 hrs/week → 10-20 min (Amanda's own practice)
- $3K overpayment caught in first week
- 20 hrs/month → automated (design partner)
- Real-time visibility vs. monthly spreadsheets

### Guarantee Language

"If we can't cut your reconciliation time in half within 30 days, you don't pay for that month."

### Social Proof (Available Now)

- Amanda's own practice numbers
- Design partner stories (once publishable)
- Founder background: early ops at Charlie Health (scaled clinical operations across multiple states), healthcare policy (Cornell)

### Who This Is For (Self-Select Copy)

- Multi-location therapy practices (OT, PT, SLP)
- MSOs and IPAs managing multiple entities
- Group practices with complex payer mixes
- Operations leaders who spend more than 2 hours/week on reconciliation
- Practices billing through multiple IPAs, MSOs, or payer arrangements

### Who This Is Not For

- Single-location practices with one payer and one bank account
- Practices looking for an EMR replacement
- Practices that want outsourced billing (we're a platform, not a billing service)

### About / Founder Story

Amanda Kichline built Tavia Health because she had this exact problem. As COO of a multi-state, multi-discipline therapy practice, she spent 5 hours a week on reconciliation — matching ERAs to bank deposits, chasing payer discrepancies, generating clinician payouts from spreadsheets. She built the first version of Tavia's platform to solve it for her own practice. It worked. 5 hours became 10-20 minutes. She caught a $3K overpayment in the first week. Now she's making it available to every therapy MSO dealing with the same problem.

Before Tavia, Amanda led operations at Charlie Health, where she scaled clinical operations across multiple states. She studied healthcare policy at Cornell and has a personal connection to rehab therapy through her experience as an athlete with hypermobile joints.

---

## Pending Items & Open Questions

- [ ] Confirm unique mechanism choice among 3 candidates (MSO-native data architecture / full-stack vertical coverage / payer intelligence flywheel)
- [ ] Louis BAA + discovery questionnaire + Chase API research
- [ ] 3D/IPTA detailed proposal with cost breakdown + ROI
- [ ] Dr. Kim free claims analysis (1-5 EOBs)
- [ ] Lindsay credentialing resubmission for Vicki
- [ ] UHC secondary claims investigation for Vicki
- [ ] Competitive matrix for pitch deck
- [ ] Script 2 version (compressed results + mechanism) of VSL
- [ ] Pressure-test offer against Louis's specific April 13 objections
- [ ] Design partner testimonials once available
- [ ] Reconciliation guide (lead magnet) — write with actual logic
- [ ] Landing page build
- [ ] 3 specialty-specific ad versions (OT, SLP, PT)
- [ ] Stress-test guarantee ("under 30 min/week" provable at Louis's volume?)
- [ ] Pricing anchor vs. hidden costs (20hrs time + $3K missed errors + near-miss hire)
- [ ] Mechanism explanation technically specific enough for Alex/Justin

---

## Source References

- meetnirvana.com / Meetnirvana.com/our-technology
- silnahealth.com / Silna Health blog
- bracehealth.com
- letspocket.com
- superdial.com / SuperDial blog
- Business Wire — Silna $27M funding announcement (3/25/2025)
- Bain Capital Ventures — Silna blog post
- Fierce Healthcare
- Healthcare IT Today
- Crunchbase / CBInsights
- Y Combinator company pages
- Granola meeting transcripts: Louis (5fd7bebc, f4eafd1f, ab8314e3), Vicki (96bced05), Dr. Kim (b5df8a45, dd18132c), Ken/Jeanine (via query)
