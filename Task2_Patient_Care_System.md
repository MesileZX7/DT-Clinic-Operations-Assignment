Objective
Reduce doctor’s non-clinical workload while ensuring patients receive timely, accurate communication using HMS + Google Sheets only.

STEP 1 — MESSAGE TYPE CLASSIFICATION (ONE-TIME)
Message Type
Example
Doctor Input Needed
Follow-up Reminder
“Please visit on Aug 5”
No
Post-Procedure Care
“Mild swelling is normal”
No
Side-Effect Advisory
“Nausea may occur”
No
Custom Instruction
“Avoid sun exposure for 7 days”
Yes
Patient Question
“Is itching normal?”
Yes


STEP 2 — CARE CONTROL SHEET (DAILY WORKING SHEET)
Google Sheet: Care_Control
Patient Name
Phone
Visit Type
Message Type
Message Text
Doctor Approval
Status
Ramesh K
9XXXX
OPD
Follow-up
Auto
Not Required
Pending
Sita P
9XXXX
Procedure
Post-Procedure
Auto
Not Required
Pending
Arjun M
9XXXX
OPD
Custom
Blank
Required
Waiting

Rule:
If it is not in this sheet, it does not exist.

STEP 3 — DOCTOR REVIEW WINDOW (EVERY 3–4 HOURS)
Process:
Filter: Doctor Approval = Required AND Status = Waiting
Sit with doctor for 10 minutes
Doctor dictates / approves
Staff types once
Doctor never:
Types messages
Opens WhatsApp
Replies individually

STEP 4 — PATIENT QUESTION HANDLING (GOOGLE FORM)
Google Form Fields:
Name
Phone
Question
Urgency (Routine / Urgent)
Responses populate: Patient_Questions sheet
Patient
Phone
Question
Answer
Status
Lakshmi
9XXXX
Is itching normal?
—
Pending

Execution:
Questions batched every 3 hours
Doctor answers once
Responses sent in batch

STEP 5 — MESSAGE DISPATCH RULES
Messages are sent only when:
Message Text is filled
Status = Pending
Doctor Approval = Not Required OR Approved
Status Flow:
Pending → Sent → Closed

STEP 6 — DAILY CLOSING CHECK (5 minutes)
Before clinic closes:
Filter Status = Pending
Ensure nothing critical is missed
Reschedule if required
Creates daily closure discipline.

OPTIONAL STEP 7 — AUTOMATION (DIFFERENTIATOR)
Logic only (no code required):
Apps Script reads rows with Status = Pending
Sends WhatsApp message via API
Updates Status = Sent
Automation executes decisions already made by humans.

