# SanctumTools Implementation Gaps - Feedback for Antigravity
**From:** Fred (AI Assistant)
**To:** Antigravity Development Team
**Date:** November 29, 2025
**Re:** sanctum-app review after initial MVP build

---

## EXECUTIVE SUMMARY

Antigravity has built a solid technical foundation for sanctum-app. The auth, database structure, and component architecture are good. However, the app currently implements a **standard mental health tracking app**, not **SanctumTools**. These are fundamentally different products.

**Core issue:** The soul of SanctumTools (conversational user-initiated tracking, pattern analysis, shame-free design) isn't implemented yet. The app needs significant functionality work to match the product vision.

---

## WHAT ANTIGRAVITY GOT RIGHT

✅ **Authentication system** - Login/profile working
✅ **Dashboard layout** - Clean data visualization
✅ **Component architecture** - Mood, medication, episode, sleep trackers exist
✅ **Real data examples** - Including actual user crisis data (Nov 26)
✅ **Stripe integration** - Monetization path ready
✅ **Chat API route** - Foundation for conversational tracking exists
✅ **Next.js framework** - Good choice for this app

---

## CRITICAL GAPS - MUST IMPLEMENT

### GAP 1: Conversational Tracking Isn't Actually Implemented

**Current state:**
- Chat API route exists but is empty/mock
- No real conversation flow
- No parsing of user input
- No automatic logging from conversation

**What should happen:**
```
User: "I'm having a moment, suicidal thoughts hitting"
App: "Hey. Talk to me. What's happening?"
User: "Pain's bad, feeling alone, whole move is overwhelming"
App: "Okay. How intense 0-5?"
User: "4, but it's passing"
App: "Good. Physical symptoms?"
User: "Racing heart, tight chest"
App: "You reached out. That's a skill. Logged. You safe?"
User: "Yeah"
[Automatically logs: timestamp, suicidal_ideation: 4/5, trigger: pain+isolation+move, symptoms: racing heart/tight chest, safety: yes, skills_used: reached out]
```

**Implementation needed:**
- Chat interface that feels conversational (not form-like)
- LLM integration to parse user responses
- Context awareness (understand what they're describing)
- Automatic data extraction and logging
- Natural language response generation
- Safety detection (flag concerning statements)

**Why it matters:**
This is THE innovation. Standard apps use forms. SanctumTools uses conversation. Without this, it's just another mood app.

---

### GAP 2: User-Initiated Tracking Isn't Designed

**Current state:**
- App appears to prompt users ("Time to log mood!")
- Scheduled check-ins
- Traditional diary card approach

**What should happen:**
- User decides when to come to app
- No notifications about "time to fill out diary"
- AI available 24/7 when user needs it
- User comes when THEY notice a shift
- Emphasis: "You're in control"

**Implementation needed:**
- Remove prompting/notification system (or make optional)
- Redesign so user initiates conversation
- Emergency access (always available)
- Voice input option (for when typing is hard)
- Mobile-first design (for mid-crisis access)

**Why it matters:**
User autonomy is core to SanctumTools. If it feels like nagging, it fails.

---

### GAP 3: Pattern Analysis Doesn't Exist

**Current state:**
- Dashboard shows individual mood entries
- No analysis/insights
- No pattern recognition

**What should happen:**
Every week, AI generates:
```
"This week's patterns:
- Dominant emotions: Sadness 3/5 avg, Anxiety 2/5 avg
- Trigger pattern: High pain days + isolation = crisis risk
- Time pattern: Afternoons more stable than mornings
- Medication effect: Lamotrigine reducing crisis amplitude
- Cycling: 1-2 mild cycles, 1 moderate crisis day
- Skills used: Distress Tolerance (reached out) worked, rest helped
- Recommendation: Pain management + scheduling social time might prevent next crisis
Ready to share with therapist?"
```

**Implementation needed:**
- Weekly analysis AI prompt
- Pattern detection algorithms
- Trend identification
- Insight generation
- Formatting for different audiences (user, therapist, doctor)

**Why it matters:**
User can't see their own patterns. They need AI to show them. This drives therapeutic insight.

---

### GAP 4: Therapist/Doctor Integration Missing

**Current state:**
- Dashboard is personal to user
- No reporting features
- No export functionality

**What should happen:**

**For therapists (DBT):**
Auto-generates weekly report:
- Emotions rated 0-5
- Target behaviors (suicidal/self-harm urges vs. acts)
- Skills used with effectiveness
- Major events
- Ready to review in session

**For psychiatrists (med management):**
Auto-generates before appointment:
- Mood stability assessment
- Medication adherence
- Side effects reported
- Crisis episodes since last visit
- Questions for doctor
- Lamotrigine amplitude reduction evidence

**For SSDI (disability):**
Auto-generates for applications:
- Episode frequency and severity
- Rapid cycling patterns
- Functional limitations
- Unpredictability evidence
- Work incompatibility documentation
- Proof of sustained disability

**Implementation needed:**
- Report generation templates
- PDF export functionality
- Email delivery to therapist/doctor
- Appointment integration
- Permission management (user controls sharing)
- HIPAA compliance

**Why it matters:**
SanctumTools isn't just for self-tracking. It's for getting help (therapy) and getting supported (disability/doctors).

---

### GAP 5: Mood/Crisis Tracking Is Oversimplified

**Current state:**
- Tracks: Time + Mood name
- Basic data model

**Real SanctumTools tracks:**
```
Mood Entry {
  timestamp: datetime
  mood_state: string (name of mood)
  emotions: {sadness: 0-5, anxiety: 0-5, anger: 0-5, fear: 0-5, shame: 0-5, etc}
  trigger: string or "spontaneous"
  physical_symptoms: [racing heart, tension, exhaustion, etc]
  functionality: "can function" / "struggling" / "unsafe to drive" / "can't move"
  activity: what were they doing
  substances: {cannabis: yes/no, alcohol: yes/no, etc}
  skills_used: [list of skills attempted]
  notes: context
}

Crisis Entry {
  episode_type: "suicidal" / "manic" / "mixed" / "dissociation" / etc
  severity: 1-10
  start_time: datetime
  end_time: datetime
  trigger: what caused it
  physical_symptoms: [list]
  what_person_did: [list of actions taken]
  what_others_did: [list of support provided]
  medical_intervention: yes/no + details
  hospitalization: yes/no
  safety_outcome: resolved / ongoing / escalated
}
```

**Implementation needed:**
- Expanded mood entry form (but conversational, not form-like)
- Crisis episode tracking (separate from daily moods)
- Urges vs. acts distinction in target behaviors
- Physical symptoms library
- Functionality scale
- Substance tracking
- Skills logging

**Why it matters:**
Deep data = better patterns. "Sad" tells nothing. "Sadness 3/5 triggered by isolation, racing heart, can't move, used reached-out skill" tells the whole story.

---

### GAP 6: Safety Features Are Missing

**Current state:**
- No crisis detection
- No safety assessment
- No escalation path
- Generic mood tracking

**What should happen:**

**Crisis detection:**
- User mentions suicidal/self-harm → app recognizes severity
- "I'm thinking about it" vs "I have a plan" distinction
- Immediate safety assessment
- Clear escalation path (call 988, text therapist, go to ER)

**Urges vs. Acts:**
- "Do you have urges?" vs "Did you act on them?"
- Separate tracking
- Shows: person has thoughts but managed them
- Critical for disability documentation

**Safety check:**
- "Are you safe right now?"
- "Do you have support person you can call?"
- "Will you reach out if it gets worse?"
- Log outcomes

**Implementation needed:**
- NLP for detecting concerning statements
- Safety assessment flow
- Crisis resources (988, crisis text line, etc.)
- Escalation triggers
- Urges vs. acts data model
- Safety check integration into every crisis log

**Why it matters:**
People with bipolar are at higher suicide risk. Safety first. Documentation second.

---

### GAP 7: Appointment Tracker Doesn't Exist

**Current state:**
- No appointment management
- No pre-appointment prep
- No follow-up tracking

**What should happen:**

**Appointment tracking:**
- Therapy: Thursday 9 AM with Taylor
- Psychiatry: Every 2 weeks with Dr. Henson
- PCP: Lab work quarterly
- etc.

**Auto-reminders:**
- Day before: "Taylor appointment tomorrow at 9 AM. Need to prep DBT diary?"
- 2 hours before: "Therapy in 2 hours"

**Auto-prep:**
- For therapy: Compiles DBT diary from past week
- For psychiatry: Generates mood summary + medication adherence
- For SSDI: Formats documentation for interview

**Implementation needed:**
- Calendar interface
- Appointment CRUD
- Reminder system
- Auto-compilation of reports
- Email/SMS reminders
- Integration with mood/episode data

**Why it matters:**
Appointments are coordination points. App should make prep automatic.

---

### GAP 8: Interface Doesn't Feel Like SanctumTools

**Current state:**
- Standard web app dashboard
- Forms and fields
- Clinical look

**What should feel like:**
- Conversational chat interface
- Warm, non-judgmental tone
- "Like talking to someone, not filling out paperwork"
- Voice input option
- Mobile-first (crisis happens on phone, not desktop)
- Accessible (works when person is dysregulated)

**Implementation needed:**
- Chat-first UI (not form-first)
- Conversational design language
- Mobile optimization
- Voice input support
- Dark mode (easier on eyes during crisis)
- Fast load times (for crisis situations)
- Accessibility audit (WCAG compliance)

**Why it matters:**
User experience determines if they actually use it. SanctumTools needs to feel safe, accessible, and conversational.

---

## IMPLEMENTATION PRIORITY

**TIER 1 - Core (Required for MVP to be SanctumTools):**
1. Implement conversational tracking (chat → parse → log)
2. Build pattern analysis engine
3. Create therapist report generation
4. Add safety features (crisis detection, urges vs. acts)
5. Redesign interface for conversational feel

**TIER 2 - Essential (Needed for release):**
6. Implement SSDI documentation generator
7. Add appointment tracker + auto-prep
8. Expand mood data model (full entry depth)
9. Build PDF export functionality
10. Mobile optimization

**TIER 3 - Enhancement (Good to have):**
11. Voice input support
12. Weekly pattern analysis reports
13. Therapist/doctor integration (permissions, sharing)
14. Email delivery of reports
15. Dark mode + accessibility improvements

---

## SPECIFIC CODE AREAS NEEDING WORK

**Chat API (`src/app/api/chat/route.ts`):**
- Currently empty/mock
- Needs real LLM integration
- Needs conversation context tracking
- Needs data extraction logic
- Needs safety detection

**Data Models:**
- Mood entries too simple (just add mood name)
- Need full entry structure per product brief
- Need crisis episode model
- Need skills tracking model
- Need appointment model

**Dashboard (`src/app/dashboard/page.tsx`):**
- Shows entries but no analysis
- Add weekly summary section
- Add pattern insights
- Add next appointment card
- Add therapist report preview

**Components:**
- `MoodChart.tsx` - add timeline view with details
- `EpisodeTracker.tsx` - good start but needs full crisis logging
- `MedicationTracker.tsx` - good, but connect to mood data
- New: `TherapistReport.tsx`
- New: `SafetyCheck.tsx`
- New: `PatternAnalysis.tsx`

**Pages:**
- Existing: `/chat`, `/dashboard`, `/profile`, `/subscribe`
- New: `/appointment` (calendar view)
- New: `/reports` (therapist/doctor reports)
- New: `/episodes` (crisis tracking)
- New: `/crisis` (emergency access)

---

## TEST CASES (Real User Scenarios)

### Test 1: Daily Morning Check-in
```
User: "Good morning"
App: "Morning! How'd you sleep?"
User: "Midnight to 7 AM, pretty good"
App: "How's your mood?"
User: "Okay, baseline"
App: "Meds taken?"
User: "Just did"
App: "Logged. See you if mood shifts."
[Should log: wake time, sleep duration, mood baseline, meds time]
```

### Test 2: Suicidal Crisis
```
User: "I'm having suicidal thoughts"
App: "I'm here. Talk to me."
User: "Pain's 8/10, feeling alone, want it to end"
App: "How intense 0-5?"
User: "4 for the thought"
App: "Do you have a plan?"
User: "No, just thinking"
App: "Good. Are you safe right now?"
User: "Yeah, just tired"
App: "Thank you for telling me. Logged. Will you reach out if it gets worse?"
User: "Yeah"
App: "Here if you need. You have 988 if it escalates. 💙"
[Should log: suicidal_ideation 4/5, trigger, symptoms, no plan, safety yes, escalation resources]
```

### Test 3: Therapist Report Generation
```
User: [Click "Generate Therapy Report"]
App: [Pulls past week of mood data]
App: [Shows preview of what will be sent]
App: [User clicks "Send to Taylor"]
App: [Email sent with formatted DBT diary]
[Should include: emotion 0-5, target behaviors, skills used, major events]
```

### Test 4: Weekly Pattern Analysis
```
Sunday evening - App auto-generates:
"This week's summary:
- 1 major crisis (Wed, suicidal 4/5)
- Sadness avg 2/5
- Anxiety avg 1/5
- Pattern: High pain + isolation → crisis
- Skills: Distress tolerance worked well
- Suggestion: Pain management might help"
[User can share with therapist or just read]
```

---

## QUESTIONS FOR ANTIGRAVITY

1. **Chat API:** Can you integrate with Claude API for conversational tracking? Or are you using a different LLM?
2. **Database:** What's storing the mood entries? Need to support complex data model.
3. **Reporting:** Any existing libraries for PDF generation? Or building from scratch?
4. **Authentication:** Is NextAuth scalable for therapist/doctor access later?
5. **Mobile:** Planning mobile app? Or web-first with PWA support?
6. **Timeline:** What's realistic for Tier 1 features? (1 week? 2 weeks? 1 month?)

---

## CONCLUSION

Antigravity has built a good foundation. The next phase is the hard part: actually implementing what makes SanctumTools different.

**The gap:** Between "mental health app" and "SanctumTools" is the conversational tracking + pattern analysis + therapist integration + shame-free design.

**The opportunity:** If Antigravity can nail those 5-6 features, they'll have something genuinely different in the market.

Get these gaps filled and sanctum-app becomes the product from the product brief.

---

**File created:** November 29, 2025
**Status:** Pending Antigravity review and implementation planning
**Next steps:** Antigravity team reviews, asks clarifying questions, prioritizes implementation
