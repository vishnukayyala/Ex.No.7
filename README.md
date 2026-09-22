# Ex.No.7 Develop a Prompt-Based Application Tailored to Personal Needs

### Date:6.09.26
### Register No.:212223240185

## Aim:
To develop a prompt-based application using ChatGPT to organize daily tasks, demonstrating the progression from simple to more advanced prompt designs and their corresponding outputs, fostering creativity and practical problem-solving using Large Language Models.

## AI Tools Required:
- ChatGPT (GPT-4/5)
- Claude (Anthropic)

---

## Explanation

**Prompt:**
> "Design a personal productivity assistant that can help manage daily tasks, schedule reminders, suggest wellness tips, and answer general queries. The assistant should interact using natural language and be adaptable to the user's changing preferences over time."

The goal is to build a **Personal Productivity Assistant** — a prompt-based application that helps a student/professional manage daily tasks, reminders, and wellness habits through natural language, using progressively more sophisticated prompt designs.

---

## Procedure

### Step 1: Define Core Requirements

| Requirement | Description |
|---|---|
| Task Management | Accept, store, and organize tasks by priority/deadline |
| Smart Scheduling | Understand time references and detect conflicts |
| Wellness Suggestions | Give contextual health/productivity tips |
| Adaptive Memory | Remember user preferences across sessions |
| Natural Language Interaction | No rigid command syntax required |

---

### Step 2: Prompt Progression — Simple to Advanced

#### Level 1 — Zero-Shot (Basic) Prompt
> "Add a task: Call mom at 6 PM."

**Sample Output:**
```
Task added: "Call mom" — Reminder set for 6:00 PM today.
```

*Limitation: Handles a single task literally, with no prioritization, categorization, or context.*

---

#### Level 2 — Instructional Prompt (Structured Output)
> "Add the task 'Call mom at 6 PM' to my task list. Categorize it by priority (High/Medium/Low) and show it along with my existing tasks in a table."

**Sample Output:**
```
| Task              | Time    | Priority |
|-------------------|---------|----------|
| Submit assignment | 2:00 PM | High     |
| Call mom          | 6:00 PM | Medium   |
| Buy groceries     | 8:00 PM | Low      |
```

---

#### Level 3 — Few-Shot Prompt (Learning from Examples)
> "Here is how I categorize tasks:
> - 'Submit assignment by 2 PM' → High priority, Academic
> - 'Buy groceries in the evening' → Low priority, Personal
>
> Now categorize this new task in the same style: 'Call mom at 6 PM.'"

**Sample Output:**
```
"Call mom at 6 PM" → Medium priority, Personal (Family)
```

---

#### Level 4 — Persona Pattern Prompt
> "You are a friendly, motivating personal productivity coach. A student tells you: 'I have an assignment due at 2 PM, groceries to buy, and I need to call mom at 6 PM.' Organize their day and give one encouraging tip."

**Sample Output:**
```
Here's your day sorted out:
1. 2:00 PM — Submit assignment (High priority — tackle this first!)
2. 6:00 PM — Call mom (a great way to recharge)
3. Evening — Groceries (fit this in whenever's convenient)

Tip: Finish the assignment early so the rest of your evening feels light and stress-free. You've got this!
```

---

#### Level 5 — Chain of Thought + Adaptive Memory Prompt
> "Given my past preference for reminders 15 minutes before tasks, and that I usually skip low-priority tasks when busy, plan today's schedule step by step: Assignment (2 PM, High), Call mom (6 PM, Medium), Groceries (8 PM, Low). Explain your reasoning, then output the final schedule."

**Sample Output:**
```
Reasoning:
- High priority task (assignment) is scheduled first, with a reminder at 1:45 PM.
- Medium priority (call mom) kept as-is, reminder at 5:45 PM.
- Low priority (groceries) is flagged as "optional today" based on your past tendency to skip it when busy.

Final Schedule:
1:45 PM — Reminder: Assignment due at 2 PM
5:45 PM — Reminder: Call mom at 6 PM
8:00 PM — Groceries (optional — reschedule if busy)
```

---

### Step 3: Simulate Natural User Interaction (Command-Line Prototype)

A simple Python CLI was built to simulate the assistant's task/reminder/wellness logic locally, before wiring it to an LLM API.

```python
import datetime

tasks = []
wellness_tips = [
    "Drink a glass of water — you've been at the screen a while.",
    "Stand up and stretch for 2 minutes.",
    "Take a 5-minute screen break every hour."
]

def add_task(description, time_str, priority="Medium"):
    tasks.append({"task": description, "time": time_str, "priority": priority})
    print(f"Task added: '{description}' at {time_str} [{priority}]")

def show_tasks():
    if not tasks:
        print("No tasks scheduled.")
        return
    print("\nYour tasks today:")
    for t in sorted(tasks, key=lambda x: x["time"]):
        print(f"- {t['time']} | {t['task']} ({t['priority']})")

def wellness_tip():
    import random
    print("Wellness tip:", random.choice(wellness_tips))

def main():
    add_task("Submit assignment", "2:00 PM", "High")
    add_task("Call mom", "6:00 PM", "Medium")
    add_task("Buy groceries", "8:00 PM", "Low")
    show_tasks()
    wellness_tip()

if __name__ == "__main__":
    main()
```

**Sample Console Output:**
```
Task added: 'Submit assignment' at 2:00 PM [High]
Task added: 'Call mom' at 6:00 PM [Medium]
Task added: 'Buy groceries' at 8:00 PM [Low]

Your tasks today:
- 2:00 PM | Submit assignment (High)
- 6:00 PM | Call mom (Medium)
- 8:00 PM | Buy groceries (Low)

Wellness tip: Stand up and stretch for 2 minutes.
```

---

### Step 4: Collect Feedback and Adapt Responses

**User feedback prompt:**
> "I don't like being reminded of low-priority tasks when my day is packed. From now on, only remind me about High and Medium priority tasks unless I ask for the full list."

**Adapted Assistant Behavior (Sample Output):**
```
Got it — from now on, I'll only surface High and Medium priority tasks by default.
Low-priority tasks (like groceries) will be silently logged and shown only if you ask for "full list."

Today's reminders:
- 2:00 PM — Submit assignment (High)
- 6:00 PM — Call mom (Medium)
```

---

### Step 5: Integrate Basic Memory (Preference Adaptation)

A simple preference dictionary simulates session memory:

```python
user_preferences = {
    "reminder_lead_time_minutes": 15,
    "hide_low_priority_by_default": True,
    "wellness_tip_frequency": "hourly"
}

def apply_preferences(task_list):
    if user_preferences["hide_low_priority_by_default"]:
        return [t for t in task_list if t["priority"] != "Low"]
    return task_list
```

This mirrors what the LLM does conversationally — retaining stated preferences ("remind me 15 minutes early," "hide low priority tasks") across the interaction and applying them to future responses without the user repeating themselves.

---

## Expected Output Summary

**Personal Productivity Assistant Features:**

1. **Daily Task Manager**
   - Accepts tasks via natural language (e.g., "Remind me to call mom at 6 PM")
   - Organizes tasks by priority and deadline
   - Provides daily summaries and pending items

2. **Smart Scheduler**
   - Schedules events and sets reminders using contextual understanding
   - Notifies the user of overlapping appointments or free time slots

3. **Wellness Tips Generator**
   - Suggests daily wellness advice (hydration, exercise, screen-time breaks)
   - Adapts suggestions based on past user preferences and responses

---

## Result:
The lab exercise resulted in the creation of a working prototype concept for a personal productivity assistant powered by Large Language Models, progressing from a basic zero-shot prompt to an adaptive, memory-aware Chain-of-Thought prompt. Through this exercise:
- The progression from simple to advanced prompt design was demonstrated with corresponding outputs at each level.
- Prompt engineering techniques (zero-shot, few-shot, persona, chain-of-thought, adaptive memory) were applied to a real, personal use case.
- A command-line prototype simulated natural user interaction and preference-based adaptation.
- The exercise confirmed the versatility of generative AI in solving everyday productivity problems through well-structured prompts.
