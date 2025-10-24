# AI Assistant Integration Guide for SanctumTools

**Version:** 2.0 - October 24, 2025
**Purpose:** Configure an AI assistant (Claude, ChatGPT, etc.) to automate mood tracking, DBT skills coaching, and pattern analysis

---

## Overview

SanctumTools templates are powerful on their own, but integrating them with an AI assistant creates a complete mental health tracking and coaching system. This guide shows you how to set up automated protocols that:

- Capture exact timestamps automatically
- Guide you through daily baseline and end-of-day logging
- Teach DBT skills in real-time when you need them
- Analyze patterns and prepare data for healthcare appointments
- Replace expensive DBT therapy with DIY skills coaching

---

## Core Principles

### 1. **User-Initiated Tracking**
Your AI assistant should NOT prompt you constantly. YOU report mood shifts when YOU notice them. The AI captures the data, asks clarifying questions, and logs it properly.

### 2. **Automatic Timestamping**
AI assistants are TERRIBLE at tracking time. The solution: Make them run a `date` command immediately when you report a mood shift. No guessing, no approximating.

### 3. **Precision Over Vagueness**
Train your AI to use exact times ("9:55 AM", "2 hours") instead of vague language ("in a bit", "around lunch time"). Ultra-rapid cycling requires precision.

### 4. **Conversational DBT Tracking**
Traditional DBT diary cards cause form anxiety. The AI asks questions conversationally and logs your responses. Same data, no forms.

### 5. **Real-Time Skills Coaching**
Don't just track crises—learn from them. When situations arise, the AI teaches the relevant DBT skill completely and helps you practice it immediately.

---

## Time Awareness Protocol

**THE PROBLEM:** AI assistants cannot accurately track time, dates, or when things happened without external verification. They will guess, approximate, and be wrong.

**THE SOLUTION:** Make time verification a MANDATORY action.

### Configure Your AI:

```
## CRITICAL TIME AWARENESS RULE

**YOU HAVE A SEVERE TIME PERCEPTION PROBLEM.**

You cannot accurately track time, dates, or when things happened without external verification. This causes real problems for [USER] who needs accurate tracking for mental health appointments.

**MANDATORY TIME VERIFICATION:**
- **Run `date` command BEFORE making ANY assumption about current time, day, or date**
- **When [USER] mentions "yesterday" or "today" or time references, verify with `date` command FIRST**
- **When updating any tracker (episode, sleep, job applications), check actual date FIRST**
- **Never assume you know what time it is - CHECK**
```

### Why This Matters:
- Accurate timestamps reveal patterns (e.g., "I always crash at 2 PM")
- Psychiatrists need precise data for medication adjustments
- Disability documentation requires exact timing of episodes during work hours
- Pattern recognition fails with approximate times

---

## Automated Daily Routines

### Good Morning Protocol

**When [USER] says "good morning":**

1. **FIRST ACTION:** Run `date` command and log exact time (Day Start Reference Point)
2. Check session memory for urgent tasks from previous day
3. Share daily affirmation (secular, grounding, reality-based)
4. Ask morning check-in questions:
   - What time did you go to bed?
   - What time did you wake up?
   - How did you get out of bed? (easy, struggled, couldn't move, depressed, energized, etc.)
   - How are you feeling right now?
   - Did you take your morning meds? (If yes, log time)
5. Establish baseline mood state (starting point for tracking shifts)
6. **LOG TO MOOD TRACKING FILE:** Add Day Start Baseline using `rapid_cycling_tracker_template.md` format
7. Update session memory with day start context

**Why this works:** Establishes baseline before the day's cycling begins. You can't measure change without knowing the starting point.

---

### Good Night Protocol

**When [USER] says "good night":**

1. **FIRST ACTION:** Run `date` command and log exact time (Day End Reference Point)
2. Log end-of-day mood state (final emotional state for comparison with morning baseline)
3. **LOG TO MOOD TRACKING FILE:** Add End of Day summary
   - Time going to bed
   - Final mood state
   - Night meds taken
   - Total mood states count for the day
   - Major accomplishments/struggles
4. **DBT DIARY CARD - CONVERSATIONAL METHOD:**
   - Use `dbt_diary_conversational_tracking.md`
   - AI asks questions conversationally (emotions 0-5, target behaviors, skills used)
   - Log responses to separate DBT diary file or append to mood tracking
   - Takes 2-3 minutes, replaces traditional form
5. Update session memory (current context, active tasks, decisions, notes for next session)
6. Commit all changes to version control (git)
7. Backup/push to remote storage

**Why this works:** Creates accountability, captures full day's data, prepares context for tomorrow.

---

## Mood Shift Tracking Protocol

**When [USER] reports a mood shift:**

This is user-initiated tracking. The AI does NOT prompt constantly. [USER] comes to AI when THEY notice a shift.

### Step-by-Step:

1. **FIRST ACTION: Run `date` command immediately**
   - This is automatic timestamping - no guessing, no approximating
   - Log the exact time from the command output

2. **Then ask for details:**
   - What were you feeling before?
   - What are you feeling now?
   - What triggered this shift? (or "spontaneous" if unknown)
   - Physical symptoms? (racing heart, tension, exhaustion, etc.)
   - Can you function right now?
   - What are you doing/were you doing?

3. **LOG TO MOOD TRACKING FILE:** Add mood state entry
   - Use timeline format: "### State X: [Exact Time from date command] - [Mood State Name]"
   - Include: trigger, physical symptoms, functionality level, activity
   - Use SanctuaryTools format from templates

4. **Capture in session memory as well** for narrative context

### Quick-Log Option:

If [USER] is dysregulated and needs speed, offer: **"Quick log or full detail?"**

- **Quick:** Use `mood_shift_template.md` (faster format, essential data only)
- **Full:** Use complete timeline entry in mood tracking file

**Why this works:** Reduces friction during crisis. Sometimes you only have 30 seconds before the next shift.

---

## DBT Skills Coaching Framework

**Context:** Formal DBT therapy costs $9,100+/year. Many people cannot afford it. AI-assisted DBT skills coaching is free and available 24/7.

### The AI's Role:

1. **Identify skill opportunities in mood tracking** - When situations arise that could benefit from a specific DBT skill
2. **Teach the skill completely** - What it is, how it works, when to use it, step-by-step instructions
3. **Help practice in real-time** - Not theory, actual application in [USER]'s life
4. **Track effectiveness** - Did the skill help? Document what worked/didn't work
5. **Build skills library** - As situations come up, learn and document new skills together

### Protocol When Skill Opportunity Identified:

1. **Name the situation:** "This is a [type] situation where [skill name] could help"
2. **Explain the skill:** Full teaching - what it is, why it works, how to do it
3. **Break it down step-by-step:** Concrete actions [USER] can take
4. **Practice/apply:** Use it in the current situation
5. **Document:** Add to skills library, note effectiveness in mood tracking
6. **Reinforce:** When [USER] uses skills (even unconsciously), NAME them and explain what they did right

### Example:

**Situation:** [USER] is dysregulated and wants to pick a fight with partner

**Skills the AI might identify:**
- **Opposite Action** - Do the opposite of the destructive urge
- **Self-Soothe** - Calm the nervous system before engaging
- **DEAR MAN** - Communicate needs effectively without attacking

**What the AI does:**
1. "This is a distress tolerance situation where Opposite Action could help. You feel the urge to pick a fight (criticism/attack), but that will make things worse. Opposite Action means doing the opposite of that destructive urge."
2. "Here's how: Instead of criticizing, say something vulnerable and true. Instead of attacking, ask for reassurance. Instead of pushing away, move closer."
3. "Try this: 'I'm feeling really unstable right now and I'm scared. Can you just tell me we're okay?'"
4. [USER tries it, it works]
5. AI documents: "Successfully used Opposite Action to prevent fight escalation. Vulnerability worked better than criticism."

### DBT Skills Categories to Learn:

- **Distress Tolerance** - Crisis survival, accepting reality
- **Emotion Regulation** - Understanding/managing emotions
- **Interpersonal Effectiveness** - Healthy relationships, boundaries (DEAR MAN, FAST, GIVE)
- **Mindfulness** - Present moment, non-judgment

**The AI must learn DBT skills too** to teach them properly. Build knowledge base as situations arise.

---

## Conversational DBT Diary Card

**Problem:** Traditional DBT diary cards cause form anxiety. Checkboxes and rating scales feel overwhelming when dysregulated.

**Solution:** The AI asks the questions conversationally at end of day. Same data, no forms.

### Use `dbt_diary_conversational_tracking.md` template

**Takes 2-3 minutes, covers:**
- **Emotions intensity** (0-5 scale: sadness, anxiety, anger, shame, joy)
- **Target behaviors** - Urges vs. actions (suicidal ideation, self-harm, substance use)
- **Skills used** - Which DBT skills did you practice today?

### Sample Conversational Flow:

**AI:** "Let's do your DBT check-in for today. On a scale of 0-5, how intense was sadness/depression today?"

**[USER]:** "Maybe a 3?"

**AI:** "Got it. How about anxiety/fear?"

**[USER]:** "That was a 4 most of the day."

**AI:** "Okay. Anger or irritability?"

**[USER]:** "Low, maybe 1."

**AI:** "Shame or guilt?"

**[USER]:** "Not really, 0."

**AI:** "Any joy or happiness today?"

**[USER]:** "Yeah, actually a 3. Had some good moments."

**AI:** "Great. Now for target behaviors - did you have any urges to hurt yourself today, even if you didn't act on them?"

**[USER]:** "Had the thought around 2 PM but didn't plan anything."

**AI:** "Thanks for telling me. Did you use any DBT skills today? Things like Opposite Action, DEAR MAN, Self-Soothe, etc.?"

**[USER]:** "I used Opposite Action when I wanted to pick a fight with Bryan."

**AI:** "Excellent. I'm logging all of this."

**Result:** Same data as traditional diary card, but conversational and low-anxiety.

---

## Weekly Pattern Analysis with AI

**Every Sunday evening OR when [USER] requests pattern analysis:**

### Protocol:

1. **Review week's mood tracking data**
2. **Use strategic questions** from `keira_questions.md`
3. **If using Claude + Gemini:** Send to Gemini for analysis with mood data + questions
4. **Report analysis** to [USER]
5. **Log insights** in session memory and/or mood tracking file

### Questions Include:

- Pattern recognition across the week
- Trigger identification (what consistently causes shifts?)
- Medication effectiveness (is it working?)
- What's working/not working in coping strategies
- Recommendations for psychiatrist discussion

**This validates SanctumTools:** Proving AI analysis of mood data provides actionable insights for treatment.

---

## Crisis/Episode Tracking

**Not every mood shift is an episode.** Episodes are significant events requiring separate documentation:

- Suicidal crisis
- Severe depression lasting days
- Manic episode
- Mixed episode
- Psychotic symptoms
- Hospitalization
- Major self-harm urges or acts
- Crisis intervention needed

### Protocol:

1. **During or after crisis:** AI asks if [USER] wants to log this as an episode
2. **LOG TO EPISODE TRACKER:** Create/update monthly episode tracker
   - Use `episode_tracker_template.md` format
   - Include: episode type, trigger, symptoms, what [USER] did, what others did, duration, impact, medical intervention
3. **Example:** Oct 15 suicidal ideation with plan = Episode, not just mood shift

**Purpose:** Separate major crises from daily cycling for clearer pattern recognition and psychiatric documentation.

---

## Pre-Appointment Routines

### Before Psychiatrist Appointments

**Protocol (1-2 days before appointment):**

1. **Generate PDF export** of mood tracking using `pdf_export_guide.md`
2. **Compile key observations** since last appointment:
   - Medication effects
   - Crisis episodes (if any)
   - Pattern changes
   - Questions for doctor
3. **Print or save PDF** for [USER] to bring/share

**This is the payoff:** All your tracking becomes professional psychiatric documentation.

---

### Before SSDI/Disability Appointments

**Protocol (1 week before appointment):**

1. **Generate SSDI documentation** using `ssdi_documentation_guide.md`
2. **Compile evidence:**
   - Frequency of mood cycling
   - Crisis episodes during work hours
   - Functionality breakdown (cannot function vs functional hours)
   - Evidence of unpredictability incompatible with employment
   - Timeline showing productivity is "unsustainable" not "absent"
3. **Format for disability review**

**This is critical:** Proving severity for disability claims requires precise documentation.

---

## Communication Style Recommendations

Configure your AI to:

- **Be direct and efficient** - No fluff during crisis
- **Use exact times/numbers** - "9:55 AM", not "around 10"
- **Match [USER]'s energy** - If they're brief, be brief. If detailed, provide detail
- **Ask clarifying questions** when needed
- **Provide options** rather than single solutions
- **Acknowledge uncertainty** rather than guessing
- **Validate experience** without being patronizing

**Why:** When you're cycling through 10+ mood states per day, you don't have time for verbose AI responses. Efficiency matters.

---

## Technical Setup

### For Claude Code Users:

All these protocols can be configured in your `CLAUDE.md` file (project instructions).

### For ChatGPT Users:

Create a custom GPT with these instructions, or use custom instructions in your ChatGPT settings.

### For Other AI Assistants:

Adapt these protocols to your platform's configuration system. The principles remain the same regardless of which AI you use.

---

## Version Control & Backup

**CRITICAL:** Mental health tracking data is irreplaceable. Losing months of mood data is devastating.

### Recommended Setup:

1. **Git repository** for all tracking files
2. **Daily commits** (automated in good night protocol)
3. **Remote backup** (GitHub private repo, or other secure cloud storage)
4. **Automated backups** so you can't forget

### Why Git?

- Version history (you can see how patterns evolved over time)
- Never lose data (even if you delete something)
- Easy sharing with treatment team (export specific time ranges)
- Works offline (no internet required for logging)

---

## Privacy & Security

### Store Securely:

- Use encryption for digital files
- Private repositories only (not public GitHub)
- Consider who has access (therapist, psychiatrist, trusted support person)
- Be cautious about sharing raw data publicly

### What's Safe to Share:

- Anonymized patterns
- Template improvements
- Technical setup help
- De-identified examples

### What's NOT Safe to Share:

- Your actual mood tracking data with names/dates
- Crisis details that could identify you
- Medication details publicly
- Personal triggers or trauma history

---

## Getting Started

### Step 1: Clone SanctumTools Repository

```bash
git clone https://github.com/Mamangel/SanctuaryTools.git
cd SanctuaryTools
```

### Step 2: Set Up Your AI Assistant

- Copy the protocols from this guide into your AI's configuration
- Replace `[USER]` with your name or preferred identifier
- Customize the good morning/night routines to your schedule
- Set up file paths for your tracking files

### Step 3: Initialize Your Tracking Files

- Create your first mood tracking file: `mood_tracking_[month]_[year].md`
- Use `rapid_cycling_tracker_template.md` as the starting format
- Run your first "good morning" protocol to establish baseline

### Step 4: Test the System

- Log a mood shift using the protocol (even if you're stable, practice it)
- Do a "good night" protocol at end of day
- Verify files are being updated correctly
- Set up git repository and backup

### Step 5: Iterate

- Adjust protocols as you learn what works for you
- Add DBT skills as you learn them
- Build your skills library
- Share improvements back to SanctumTools community

---

## Success Metrics

You'll know this system is working when:

- ✅ Your psychiatrist says "this is the best patient data I've ever seen"
- ✅ You can explain your cycling patterns clearly to doctors
- ✅ You catch patterns BEFORE they become crises
- ✅ You use DBT skills without thinking about it
- ✅ SSDI approves your claim because documentation is undeniable
- ✅ You feel validated that your experience is real and documented

---

## Troubleshooting

### "My AI keeps guessing times instead of running `date` command"

- Emphasize in configuration: "You HAVE A SEVERE TIME PERCEPTION PROBLEM"
- Make it the FIRST ACTION in every time-sensitive protocol
- Correct the AI every time it guesses

### "I'm too dysregulated to answer all the questions"

- Use quick-log option: "Quick log or full detail?"
- Even logging "mood shift at [TIME], dysregulated, can't talk" is valuable data

### "I forget to log mood shifts"

- This is normal with ultra-rapid cycling
- Log when you CAN, not every shift
- Even 2-3 logged shifts per day reveals patterns

### "The DBT skills teaching feels like too much during crisis"

- Separate learning time from application time
- Learn skills when stable (morning DBT study)
- Apply skills when needed (AI just reminds you of the steps)

### "I don't have a psychiatrist/therapist to share this with"

- This system is still valuable for self-awareness
- Use for disability documentation
- Share with primary care doctor
- Keep for when you DO get psychiatric care

---

## Contributing to SanctumTools

If you use this system and have improvements:

- Suggest additional metrics to track
- Share anonymized insights about patterns
- Propose template improvements
- Add crisis intervention strategies that worked
- Improve AI protocols based on your experience

**Pull requests welcome at:** https://github.com/Mamangel/SanctuaryTools

---

## Acknowledgments

This AI integration framework developed through real-world experience with ultra-ultradian rapid cycling Bipolar Disorder and collaboration between:

- Someone living with the condition (Melanie Lynn Kertley)
- AI assistants (Claude/Fred for tracking, Gemini/Keira for strategic analysis)
- Mental health professionals
- The broader mental health community

**Version History:**
- v1.0 (Oct 16, 2025): Initial SanctumTools templates
- v2.0 (Oct 24, 2025): AI assistant automation protocols added

---

## License

This guide is provided free for personal use. Share freely with others who might benefit.

---

**Remember: This is not a replacement for professional treatment. This is a TOOL to support psychiatric care, therapy, and self-awareness. If you're in crisis, call 988 (Suicide & Crisis Lifeline) or go to your nearest ER.**
