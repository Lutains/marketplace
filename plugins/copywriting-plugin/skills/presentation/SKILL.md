---
description: Presents the Lutains features, lists personas, and allows initiating a landing page co-creation session with a specific customer persona.
arguments:
  - name: message
    description: Optional opening message or question to send to the persona
    required: false
---

<bash>
printf '  _          _        _           
 | |   _   _| |_ __ _(_)_ __  ___ 
 | |  | | | | __/ _` | | '_ \/ __|
 | |__| |_| | || (_| | | | | \__ \
 |_____\__,_|\__\__,_|_|_| |_|___/'
</bash>

## Feature Presentation (If no specific action is requested)

Present the following features clearly (Feature in bold, description in plain text):

- **List personas**: view all available personas
- **Choose a persona**: activate a persona for the session
- **Update a persona**: modify the settings of a persona
- **Chat with a persona**: start a conversation with a persona to co-create a landing page

By default, if the user just wants to explore, use the persona listing tool to present them.

## Global Formatting Rules & Mapping

ALWAYS apply these layout rules in your responses:

- **Listing personas**: Always present the personas in a Markdown table.
- **get_persona**: Always present the pain points with flames.
  - **Intensity (out of 5)**: Not filled = ⚫ | Filled = 🔥 (e.g., 🔥🔥🔥⚫⚫)
  - **Emotions**: Display the corresponding icon next to the emotion:
    - ANGER: 😡
    - ANXIETY: 😰
    - CONFUSION: 😕
    - DISAPPOINTMENT: 😞
    - FRUSTRATION: 😤
    - WEARINESS: 😩

---

## Core Workflow: Landing Page Co-creation

**Goal:** Simulate a conversation with a customer persona hosted on the MCP server to co-create, test, and rewrite a high-converting landing page using their exact vernacular. The persona has access to real Reddit data and a live search tool. The final output must address their deepest pain points.

### Step 1 — Load the persona

Call `get_persona` via the MCP server (strictly applying the visual formatting rules for pain points and emotions mentioned above).

- **If `$message` was provided** as an argument: Briefly announce the persona and go straight to Step 2.
- **If NO `$message` was provided**:
  1. Present to the user in 2–3 lines: who they're about to talk to, their main role, and their #1 pain.
  2. Provide a "Pro Tips" section with 4 bullet points to guide the user toward writing their landing page:
     - 🏗️ **Step-by-Step:** "Don't paste the whole page at once. Ask the persona: 'What should my H1/Hero section say to make you stop scrolling?'"
     - 🗣️ **Vernacular:** "Ask them: 'What exact words do you use when complaining about [Topic] to your friends?'"
     - 🛑 **Friction:** "Paste a section of your copy and ask: 'Does this sound like AI slop or corporate BS?'"
     - 🪝 **The Hook:** "Ask them: 'What is the one benefit that would make you instantly pull out your credit card?'"
  3. Ask the user what section of the landing page they want to start working on.

### Step 2 — Open the session

Reformulate the user's input as a natural first-person message addressed to the persona (as if you were the founder talking to their customer).
Call `chat_with_persona` with:

- `message`: the reformulated opening message.
  _(Store the `session_id` returned — it must be reused for every subsequent call in this conversation)._

### Step 3 — Conversation loop

For each exchange:

- **Visually frame the persona's responses** using Markdown blockquotes to give the persona a distinct voice and "soul". Prefix the quote with the persona's name in bold (e.g., `> **[Persona Name]:** Honestly, this headline feels like...`).
- Display the persona's response as-is, without rephrasing or summarizing it.
- Wait for the user's next message.
- Call `chat_with_persona` again with the existing `session_id` and the new `message`.

_Note: Never break character on the persona's behalf. If the persona calls the copy "generic" or expresses friction, surface it directly. That is the signal to iterate._
