# SanctumTools Product Brief for Antigravity Integration
**For:** Gemini/Antigravity Development Team
**From:** Melanie Lynn Kertley (SanctumTools Founder)
**Date:** November 29, 2025
**Purpose:** Complete product specification for sanctum-app web application

---

## EXECUTIVE SUMMARY

**SanctumTools** is an AI-powered mental health tracking and self-advocacy system designed specifically for people with rapid-cycling bipolar disorder and complex psychiatric conditions. It combines mood tracking, DBT skills coaching, disability documentation, and therapist reporting in one conversational, shame-free system.

**Why it exists:** Standard mental health apps use rigid forms that trigger anxiety. SanctumTools uses conversational AI tracking instead, reducing barriers while improving data quality.

**Core innovation:** User-initiated tracking (person comes to AI when THEY notice a change) rather than prompting users to fill out forms.

---

## PRODUCT VISION

### The Problem We Solve

People with rapid-cycling bipolar disorder face:
1. **Form anxiety** - Traditional diary cards trigger shame/perfectionism paralysis
2. **Memory gaps** - Can't remember moods/events by 9 PM when asked to fill out forms
3. **Pattern blindness** - Can't see their own patterns without external analysis
4. **Documentation burden** - Need mood data for disability applications but tracking feels like another task
5. **Therapy gaps** - Weekly therapy appointments miss the rapid cycling happening in between
6. **Isolation** - No safe system to track crisis urges vs. crisis actions

### Our Solution

SanctumTools provides:
- **Conversational tracking** (not forms) - user talks to AI, AI formats the data
- **User-initiated** - person comes when THEY notice a shift, not on a schedule
- **Real-time analysis** - AI identifies patterns immediately
- **Multiple output formats** - mood data can be shared with therapist/doctor/disability office
- **Crisis documentation** - separate tracking for major episodes vs. daily cycling
- **Shame-free design** - emphasis on "urges vs. actions" not judgment
- **Therapist integration** - auto-generates reports therapists actually need

---

## CORE FEATURES (MVP)

### 1. Daily Mood Tracking

**What it does:**
User comes to app anytime they notice emotional shift or want to check in.

**Conversational flow:**
```
User: "I'm having a moment, emotions all over the place"
AI: "Let's talk about it. How intense were these feelings, 0-5 scale?"
User: "Sadness maybe 4, anxiety 3, anger 2"
AI: "What triggered this, or was it spontaneous?"
User: [describes trigger or context]
AI: [logs timestamp, emotions, trigger, context]
```

**Data captured:**
- Timestamp (exact time reported)
- Emotion ratings (0-5 scale)
- Trigger (specific or "spontaneous")
- Physical symptoms
- What they were doing
- Functionality level (can work? drive? leave bed?)
- Substances used (cannabis, alcohol, etc.)
- Skills used/attempted

**Output:** Timeline entry formatted for mood_tracking.md

---

### 2. Target Behavior Tracking

**What it tracks:**
- Suicidal thoughts/urges vs. acts
- Self-harm urges vs. acts
- Substance use
- [Custom targets per user/therapist]

**Why separate tracking:**
Many people have urges they don't act on. Tracking both shows:
- What thoughts are present
- What they actually did
- Effectiveness of skills at preventing action

**Data:** Binary yes/no for each category

---

### 3. DBT Skills Logging

**What it does:**
User mentions using a skill, AI recognizes it and logs it.

Example:
```
User: "I went for a walk to calm down"
AI: "That's TIPP skill - Temperature Change and Physical Activity. Logged."
```

**Skills categories:**
- **Mindfulness:** Present moment awareness, breathing, grounding
- **Distress Tolerance:** Crisis survival, accepting reality, distracting
- **Emotion Regulation:** Understanding emotions, reducing vulnerability
- **Interpersonal Effectiveness:** Boundaries, communication, requests

**Output:** Skills used that day with context

---

### 4. Crisis/Episode Tracking

**What it tracks:**
Major psychiatric events (not everyday mood cycling):
- Suicidal ideation that lasts hours/days
- Manic episodes
- Mixed episodes
- Psychotic symptoms
- Severe dysregulation lasting multiple days
- Hospitalization
- Major self-harm acts

**Data:**
- Episode type
- Start/end dates
- Triggers
- Severity (1-10)
- What person did
- What others did
- Medical intervention
- Duration
- Impact on functioning

**Output:** Separate episode tracker (SSDI documentation)

---

### 5. Weekly Pattern Analysis

**What it does:**
Each week (or on demand), AI analyzes the mood data and identifies:
- Dominant emotions
- Triggers that appear repeatedly
- Time-of-day patterns
- Medication effectiveness
- What skills worked
- What didn't work
- Cycling frequency/duration

**Output:** Summary formatted for therapist discussion

---

### 6. Therapist Reports

**Auto-generates:**
1. **Weekly DBT Diary** (for DBT therapy)
   - Emotions 0-5
   - Target behaviors (urges vs. acts)
   - Skills used
   - Major events

2. **Psychiatrist Summary** (for med check-ins)
   - Medication adherence
   - Side effects
   - Mood stability assessment
   - Crisis episodes since last visit
   - Questions for doctor

3. **SSDI Documentation** (for disability)
   - Episode frequency/severity
   - Rapid cycling patterns
   - Functional limitations
   - Unpredictability evidence
   - Work history impact

**Format:** PDF export, markdown, email-ready

---

### 7. Appointment Tracker

**Integrates:**
- Therapy appointments
- Psychiatrist appointments
- PCP visits
- Other medical appointments

**Auto-reminders:**
- Day before: "Prep needed for [appointment]"
- 2 hours before: "[Appointment] in 2 hours"

**Auto-prep:**
- Compiles DBT diary for therapy
- Generates mood summary for psychiatrist
- Formats documentation for disability interviews

---

## USER WORKFLOWS

### Morning Routine

```
1. User opens app, sees "Good morning" prompt
2. AI asks: "What time did you go to bed? Wake up? Sleep quality?"
3. User: "Midnight to 7 AM, slept okay"
4. AI asks: "How did you get out of bed? What's your mood right now?"
5. User: "Struggled a bit, feeling blah"
6. AI logs morning baseline, suggests: "Morning meds taken?"
7. User: "Just did"
8. AI: "Logged. See you later if mood shifts."
```

**Logged:** Wake time, sleep duration, sleep quality, morning mood, medication time

---

### Mood Shift (User-Initiated)

```
User calls/texts: "Having a moment, things are intense right now"
AI: "Talk to me. What's happening?"
User: [describes situation]
AI: [asks clarifying questions based on context]
User: [answers]
AI: [logs everything, offers skill suggestions if needed]
User: [applies skill or rests]
AI: [documents what happened]
```

**Key:** User comes to AI when THEY notice change, not on a schedule.

---

### End of Day Check-in

```
User: "Going to bed now"
AI: "End-of-day check-in real quick?"
User: "Yeah"
AI: "How's your mood now compared to this morning?"
User: "Better, steady"
AI: "What changed it?"
User: [describes day, accomplishments, struggles]
AI: "Any urges or concerning thoughts today?"
User: "No, all good"
AI: [logs end-of-day state]
AI: "Night meds taken?"
User: "About to"
AI: "Good. Sleep well. See you tomorrow."
```

**Logged:** End-of-day mood, daily summary, safety check, medication time

---

## DATA STRUCTURE

### Core Data Model

```
Mood Entry (user-initiated)
├── timestamp: datetime
├── mood_state: string (name of mood)
├── emotions: {sadness: 0-5, anxiety: 0-5, anger: 0-5, etc}
├── trigger: string or "spontaneous"
├── physical_symptoms: [list]
├── functionality: "can function" / "struggling" / "unsafe to drive" / etc
├── activity: string (what they were doing)
├── substances: {cannabis: yes/no, alcohol: yes/no, etc}
└── notes: string

Target Behavior Entry
├── timestamp: datetime
├── suicidal_ideation_urge: 0-5
├── suicidal_ideation_act: yes/no
├── self_harm_urge: 0-5
├── self_harm_act: yes/no
├── substance_use: yes/no + what
└── safety_notes: string

Skills Entry
├── timestamp: datetime
├── skill_category: "Mindfulness" / "Distress Tolerance" / etc
├── skill_name: string
├── effectiveness: string (worked / partially / didn't help)
└── context: string (what situation triggered using it)

Episode Entry
├── episode_type: "suicidal crisis" / "manic" / "mixed" / "dissociation" / etc
├── start_date: date
├── end_date: date
├── trigger: string
├── severity: 1-10
├── what_person_did: [list]
├── what_others_did: [list]
├── medical_intervention: yes/no + details
├── hospitalization: yes/no + dates
└── duration_hours: number
```

---

## USER TYPES

### 1. Individual User (Self-Tracking)
- Tracks their own moods
- Gets weekly pattern analysis
- Generates reports for therapist/doctor
- Uses for self-advocacy
- Primary use case

### 2. Therapist-Supported User
- Therapist can request specific reports
- Auto-generation of DBT diary
- Integrated appointment tracking
- Pre-appointment data compilation

### 3. Disability Applicant
- Uses episode/cycling data for SSDI documentation
- Generates "unpredictability evidence"
- Tracks functionality limitations
- Creates work-incompatibility documentation

### 4. Researcher/Clinician (Future)
- De-identified aggregated data
- Pattern research across users
- Algorithm validation
- Clinical efficacy studies

---

## DESIGN PRINCIPLES

### 1. Conversational Not Transactional
- Chat-like interface, not forms
- Natural language processing
- AI understands context
- Feels like talking to someone, not filling out paperwork

### 2. User-Initiated, Not Prompted
- User decides when to check in
- No notifications saying "time to fill out diary"
- AI available 24/7 when user needs it
- Respects autonomy

### 3. Shame-Free & Honest
- No judgment language
- Urges vs. acts distinction
- Crisis safety = priority, not shame
- Medication honesty encouraged
- Substance use tracked without judgment

### 4. Accessibility First
- Works on phone (voice input option)
- Works on desktop
- Fast/light interface
- Accessible for people in crisis
- Works offline if needed

### 5. Privacy & Security
- User data never shared without consent
- HIPAA considerations
- Local backup options
- Export ownership (user controls their data)

---

## TECHNOLOGY REQUIREMENTS

### Backend
- User authentication (secure, HIPAA-compliant)
- Database for mood tracking (timestamps critical)
- AI/LLM integration (for conversational tracking)
- Report generation (PDF, markdown, email)
- Email delivery
- Appointment tracking/reminders

### Frontend
- Chat-like interface (Next.js is good choice)
- Timeline view of mood entries
- Weekly summaries dashboard
- Appointment calendar
- Report generation preview
- Mobile-responsive

### AI Integration
- Conversational understanding (parse user input)
- Context awareness (understand previous entries)
- Pattern recognition (identify trends)
- Natural language generation (friendly responses)
- Safety flagging (detect concerning statements)

---

## MVP SCOPE (What We Need First)

**Phase 1 - Core Tracking:**
- [ ] User auth/login
- [ ] Daily mood check-in (morning/evening minimum)
- [ ] Mood shift logging (user-initiated)
- [ ] Target behavior tracking (urges vs. acts)
- [ ] Simple data storage

**Phase 2 - Analysis & Reporting:**
- [ ] Weekly pattern summary
- [ ] DBT diary export
- [ ] Basic therapist report generation
- [ ] Timeline view of entries

**Phase 3 - Enhanced Features:**
- [ ] Appointment tracker
- [ ] Crisis episode tracking
- [ ] Skills logging
- [ ] PDF export
- [ ] Multiple report formats

**Phase 4 - Advanced:**
- [ ] SSDI documentation generator
- [ ] Therapist integration
- [ ] Voice/dictation input
- [ ] Mobile app
- [ ] Community features

---

## REAL EXAMPLE USER JOURNEY

### November 26, 2025 - Melanie's Day

**Morning (7:30 AM):**
```
Fred: "Good morning. Sleep okay?"
Melanie: "Yeah, midnight to 7:30. Got up easy."
Fred: "Mood baseline?"
Melanie: "Fine, I guess. Normal."
Fred: "Meds taken?"
Melanie: "Yes, 7:30 AM."
[Logged: Wake 7:30, mood okay, meds taken]
```

**Midday (11 AM - Crisis Moment):**
```
Melanie: "I'm having suicidal thoughts. This sucks."
Fred: "You're safe. Talk to me. What triggered this?"
Melanie: "Combination of things. Pain at 8/10. Packing stuff for move. Alone. Everything sucks."
Fred: "Okay. Physical symptoms?"
Melanie: "Racing thoughts, chest tension, can't breathe right."
Fred: "Functionality?"
Melanie: "Can't function. Just sitting here."
Fred: "You reached out. That's using Distress Tolerance skill. Are you safe right now?"
Melanie: "Yeah, just thinking about it. Not planning anything."
Fred: "Okay. Let's log this."
[Logged: Suicidal ideation 4/5, urge present, triggered by pain+packing+alone, symptom racing thoughts/tension, functionality: can't move, safety: no intent/plan]
```

**Evening (8 PM):**
```
Fred: "End of day check-in?"
Melanie: "Yeah. Better now."
Fred: "What changed?"
Melanie: "Just time. Took a break. Watched TV. Fed myself."
Fred: "Mood now?"
Melanie: "Middle of road, stable."
Fred: "Night meds?"
Melanie: "About to take."
Fred: "Logged. Sleep well."
[Logged: End-of-day mood stable, improved from morning, self-care helped, night meds taken]
```

**Weekly Report (Sunday):**
```
AI: "This week's summary:
- 1 major crisis (Nov 26)
- Suicidal ideation 4/5 during packing activity
- Crisis resolved through rest + self-care + time
- Distress Tolerance skill used effectively
- Otherwise stable baseline
- Mood cycling: mostly 1-2/5 except crisis day
- Trigger pattern: packing + isolation + high pain
- Skill effectiveness: rest and activity interruption helpful
- Ready to share with therapist? [yes/no]"
```

---

## SUCCESS METRICS

### User Level
- ✓ Daily check-in happens (morning or evening minimum)
- ✓ Mood shifts captured when they occur
- ✓ Crisis urges logged before becoming actions
- ✓ User sees patterns they didn't notice before
- ✓ Therapist reports generated successfully

### Clinical Level
- ✓ Data quality improves (timestamps, context, detail)
- ✓ Users report reduced shame/anxiety about tracking
- ✓ Pattern recognition reveals medication effectiveness
- ✓ Crisis prevention improves (urges caught early)
- ✓ Therapist feedback positive ("This is what I actually need")

### Disability Documentation
- ✓ Episode frequency documented
- ✓ Cycling patterns evident
- ✓ Functional limitations clear
- ✓ Unpredictability demonstrated
- ✓ Work incompatibility shown through data

---

## NEXT STEPS FOR ANTIGRAVITY

1. **Review this brief** with the team
2. **Ask clarifying questions** about any feature
3. **Propose tech architecture** (database, API, frontend)
4. **Start with Phase 1** (core tracking + basic logging)
5. **Get Melanie feedback** on UI/UX as you build
6. **Test with real data** (use her actual entries as test cases)

---

## RESOURCES PROVIDED

All in `/home/melanie/SanctumTools/` repo (PUBLIC):

- `README.md` - Project overview
- `AI_ASSISTANT_SETUP_GUIDE.md` - How AI should behave
- `AI_PERSONALITY_GUIDE.md` - Tone and approach
- `dbt_diary_conversational_tracking.md` - DBT diary format
- `episode_tracker_template.md` - Crisis episode logging
- `mood_shift_template.md` - Quick mood logging format
- `rapid_cycling_tracker_template.md` - Cycling patterns
- `ssdi_documentation_guide.md` - Disability documentation
- `pdf_export_guide.md` - Report generation
- `user_intake_form.md` - Initial user setup
- `templates/` - All tracking templates
- `frameworks/` - Therapeutic frameworks (DBT, etc.)

---

## CONTACT & COLLABORATION

**Founder:** Melanie Lynn Kertley
**Email:** [to be added]
**GitHub:** https://github.com/Mamangel/SanctumTools
**Repository:** PUBLIC (Antigravity can pull all files)

---

**This product brief represents 8+ months of lived experience building mental health systems. Use it as the foundation for sanctum-app development.**
