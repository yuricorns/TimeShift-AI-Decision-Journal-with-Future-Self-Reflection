# TimeShift-AI-Decision-Journal-with-Future-Self-Reflection
An AI-powered decision journaling system that captures important decisions, analyzes reasoning quality, and revisits those decisions over time using scheduled AI reflections.  Built using n8n, LLMs, and Google Sheets to demonstrate time-aware, stateful AI workflows without overengineering.
What This Project Does

Captures important decisions with context and emotions

Uses AI to analyze:
Assumptions
Biases
Risks
Missing information
Stores decisions in persistent memory (Google Sheets)
Automatically revisits decisions after 7 days
Generates reflections from the user’s future self
Prevents duplicate reflections using review status tracking
This project separates real-time decision ingestion from scheduled AI reflection, similar to production AI systems.

# Workflow Architecture
# Workflow 1 — Decision Capture
Manual/Webhook Trigger
→ Input Normalization (Set)
→ AI Agent (Reasoning Analysis)
→ Parse AI Output
→ Merge State
→ Google Sheets (Append Row)

# Workflow 2 — Future-Self Scheduler (7-Day Reflection)
Schedule Trigger (Daily)
→ Read Rows from Google Sheets
→ IF (Pending + Older than 7 days)
→ AI Agent (Future-Self Reflection)
→ Update Same Row in Sheet


Both workflows share the same persistent memory layer.

 # Data Model (Google Sheets)
Column	Description
Timestamp	Decision creation time
Decision	The decision being made
Context	Situation details
Emotion	Emotional state
Urgency	Perceived urgency
Options	Available options
AI_Assumptions	Assumptions identified by AI
AI_Biases	Cognitive biases detected
AI_Risks	Potential risks
AI_MissingInfo	Missing information
Decision_Quality	AI-evaluated reasoning quality
Future_Review_Status	Pending / Reviewed
Future_Reflection_7D	AI reflection after 7 days
 Key Concepts Demonstrated

Stateless AI with explicit state recovery
Schema normalization and clean data flow
Deterministic parsing of LLM output
Time-based automation using schedulers
Idempotent workflows (no duplicate execution)
Separation of responsibilities across workflows
Persistent memory without a database

 # Tech Stack

n8n — Workflow orchestration
LLMs (AI Agent node) — Reasoning and reflection
Google Sheets — Persistent memory
JavaScript expressions — Date logic and conditions

No UI
No RAG
No unnecessary complexity

# Example Use Case

User logs a decision:

“Should I apply for this AI internship?”
AI analyzes reasoning quality and stores it
Decision is saved with status Pending
After 7 days:
Scheduler triggers
AI reflects as the user’s future self
Reflection is written back
Status updated to Reviewed

# Future Enhancements

30-day deep reflection workflow
Decision pattern detection over time
Risk vs outcome analysis
Multi-user support
Notion or database integration

👤 Author

Mayuri Mallya
Computer Science Engineering student
Interested in Applied AI, Automation, and Agentic Systems


# 🎥 Workflow Demo

![Workflow Demo](./workflow-video.gif)


