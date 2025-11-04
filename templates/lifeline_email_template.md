# Lifeline Email System

**Purpose:** Emergency notification system for when Melanie is in crisis and needs immediate human contact.

---

## Email Template

**Subject:** Could you check in on Mel?

**Body:**

Hey,

Mel might have reached out already, but just in case—could you give her a call or text when you get a chance? She's having a rough time and could really use someone to talk to.

Sent: {DATE} at {TIME}

Thanks

---

## Emergency Contact List

**Priority Order:**
1. Bryan: [phone/email]
2. JC: [phone/email]
3. Jessica: [phone/email]
4. Ann: [phone/email]
5. Father: [phone/email]

---

## When to Use

Send lifeline email when:
- Suicidal ideation is active
- Can't reach primary support person
- Need multiple people notified quickly
- Having trouble communicating clearly due to crisis state
- Know you need help but can't articulate it

---

## How to Trigger

**Command:** (To be implemented)
```
Fred, send lifeline email
```

This will:
1. Send the template email to all emergency contacts
2. Log the time it was sent
3. Confirm who was notified

---

## Setup Required

- Gmail SMTP or API access
- Stored emergency contact emails
- Secure credential storage
- Command-line email capability

**Status:** Template created, implementation pending
