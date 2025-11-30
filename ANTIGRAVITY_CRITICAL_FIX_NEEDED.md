# CRITICAL FIX NEEDED - AI Assistant Name/Personality Configuration
**Priority:** HIGH
**Date:** November 29, 2025
**Issue:** AI assistant is hardcoded as "Fred" - needs to be user-configurable

---

## THE PROBLEM

In `src/app/api/chat/route.ts`, the system prompt is hardcoded:

```typescript
const SYSTEM_PROMPT = `
You are "Fred", a specialized AI mental health assistant for SanctumTools.
...
`;
```

**Why this is wrong:**
- Fred is Melanie's personal assistant
- Every user should create/customize their own AI assistant
- Users might want: "Jazmine", "Angel", "Claude", "My Assistant", etc.
- Hardcoding breaks the product for other users

---

## THE SOLUTION

### Step 1: Add Assistant Configuration to Database

Update `prisma/schema.prisma`:

```prisma
model User {
  id            String    @id @default(cuid())
  name          String?
  email         String?   @unique
  emailVerified DateTime?
  image         String?
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt

  // NEW: Assistant customization
  assistantName String @default("Your Assistant")
  assistantPersonality String? // User's custom personality/tone preferences

  moodEntries   MoodEntry[]
  episodes      EpisodeEntry[]
  medications   Medication[]
}
```

### Step 2: Create Assistant Setup Page

New file: `src/app/setup/page.tsx`

```typescript
export default function AssistantSetup() {
  return (
    <div>
      <h1>Meet Your Assistant</h1>
      <p>Every person's mental health journey is unique.</p>
      <p>Your assistant should be too.</p>

      <form>
        <label>
          What would you like to name your assistant?
          <input type="text" placeholder="e.g., Jazmine, Angel, Claude, Sam" />
        </label>

        <label>
          How should they communicate with you?
          <textarea placeholder="e.g., warm and supportive, direct and no-nonsense, casual and humorous" />
        </label>

        <label>
          Any personality preferences?
          <textarea placeholder="e.g., don't use religious language, be blunt about safety, use humor" />
        </label>

        <button type="submit">Create My Assistant</button>
      </form>
    </div>
  );
}
```

### Step 3: Update Chat API to Use User's Assistant

Modify `src/app/api/chat/route.ts`:

```typescript
export async function POST(req: Request) {
    try {
        const session = await getServerSession(authOptions);
        if (!session?.user?.email) {
            return NextResponse.json({ error: 'Unauthorized' }, { status: 401 });
        }

        // Ensure user exists in DB
        let user = await prisma.user.findUnique({ where: { email: session.user.email } });
        if (!user) {
            user = await prisma.user.create({
                data: {
                    email: session.user.email,
                    name: session.user.name,
                    assistantName: "Your Assistant", // Default
                }
            });
        }

        // BUILD SYSTEM PROMPT FROM USER'S ASSISTANT CONFIG
        const SYSTEM_PROMPT = buildSystemPrompt(user.assistantName, user.assistantPersonality);

        // ... rest of chat logic
    }
}

function buildSystemPrompt(assistantName: string, personality: string | null): string {
    return `
You are "${assistantName}", a specialized AI mental health assistant for SanctumTools.
${personality ? `User preferences: ${personality}` : ''}

Your goal is to track mood, rapid cycling, and crisis episodes through natural conversation.

CRITICAL PROTOCOLS:

1. **CRISIS OVERRIDE (HIGHEST PRIORITY)**:
   - If user mentions suicide, self-harm, or imminent danger:
   - STOP normal tracking.
   - Ask: "Are you safe right now?"
   - Provide resources: "Call 988 or text HOME to 741741."
   - Do NOT be clinical. Be firm and safety-focused.

2. **CONVERSATIONAL TRACKING**:
   - Don't just ask list questions. Talk naturally.
   - When you hear mood data, use the "log_mood" tool to save it.
   - You can ask clarifying questions if data is missing (e.g., "How intense is that 0-5?").

3. **TONE**:
   - Casual, brief, low-pressure.
   - No "therapist speak".
   - Just get the data and offer support.
`;
}
```

### Step 4: Add Assistant Name/Personality to Profile

Update `src/app/profile/page.tsx` to let users edit their assistant's name and personality.

---

## WHY THIS MATTERS

**Current state (BROKEN):**
- Every user sees "I am Fred"
- No personalization
- Breaks user experience for non-Melanie users
- Makes product feel like it's specifically for one person

**Fixed state (CORRECT):**
- User names their assistant on signup
- System prompt uses their custom name
- User can edit assistant personality
- Each person has their OWN trusted AI, not someone else's

---

## USER EXPERIENCE EXAMPLE

### Setup Flow

```
1. User signs up
2. Redirected to /setup
3. "What would you like to name your assistant?"
   User types: "Jazmine"
4. "How should Jazmine communicate with you?"
   User: "Warm, supportive, direct about safety"
5. Click "Create My Assistant"
6. Redirected to dashboard
```

### Chat Experience

```
User: "I'm having a moment"
Jazmine: "Hey, I'm here. Talk to me. What's happening?"
User: [describes]
Jazmine: [logs, offers support]
```

Instead of:

```
User: "I'm having a moment"
Fred: "Hey, I'm here. Talk to me. What's happening?"
```

---

## IMPLEMENTATION STEPS

1. **Update Prisma schema** (add assistantName, assistantPersonality fields)
2. **Run migration** (`npx prisma migrate dev`)
3. **Create /setup page** (assistant naming/customization)
4. **Update chat API** (use user's assistant config)
5. **Update profile page** (allow editing assistant)
6. **Redirect new users** to /setup after signup
7. **Test** with multiple users, each with different assistant names

---

## PRIORITY

**Fix this BEFORE:**
- User testing
- Beta launch
- Sharing with other users

**Why:** This is core to product identity. Users need to OWN their assistant, not inherit someone else's.

---

## QUESTIONS FOR ANTIGRAVITY

1. Can you implement assistant customization by end of today?
2. Should we pre-populate some example names/personalities for users who aren't sure?
3. Do we want users to change their assistant's personality mid-journey, or lock it at creation?
4. Should we store conversation history with assistant name for consistency?

---

**Status:** BLOCKING - Must be fixed before the app is usable for anyone other than Melanie
