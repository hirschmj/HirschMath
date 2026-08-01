# Summer Lessons Requirements

## Feature requests

### Rotate repeatedly chosen activities

Students should not be able to complete every session by repeatedly choosing the easiest activity or skill. Each math or writing exercise may be selected only once per student session. After it is selected, disable that exercise and label it **Done this session** until the session resets.

The used-exercise list must persist across refreshes, be tracked separately for each student, and reset only when that student's session is successfully completed. The rotation should encourage variety without forcing work that is substantially above the student's current ability level.

### Make writing feedback specific and actionable

When a writing response does not pass validation, the feedback must clearly explain what is preventing it from passing and what the student should change. Avoid vague messages such as "write a little more" when a more precise instruction is available.

Feedback should:

- Identify each unmet requirement, such as the number of additional sentences or words needed, a missing capital letter, missing ending punctuation, or an unchecked revision step.
- Give a concrete next action, such as "Add two more complete sentences that explain why you chose this answer."
- Use age-appropriate language and short instructions that a student can act on without adult interpretation.
- Update after each revision so requirements that have already been satisfied are no longer presented as problems.
- Preserve encouragement while making it unmistakable what the student must do before the response can be saved and counted as complete.

## Session completion: time plus actual work

The next version must require both active practice time and completed work before a student can finish a session and email the summary to Dad.

### Completion requirements

A session is complete only after the student has achieved both of the following:

- At least 15 minutes of active practice time.
- At least 15 work points.

Reaching only one requirement must not enable the **I'm Done - Email Dad** button.

### Work-point values

- Each submitted math question: **1 point**.
- Each completed, validated, and saved writing assignment: **5 points**.

This allows any combination totaling 15 points, including:

- 15 math questions.
- 3 writing assignments.
- 10 math questions and 1 writing assignment.
- 5 math questions and 2 writing assignments.

A genuine math attempt earns its point whether the answer is correct or incorrect. Accuracy must still be recorded and shown in progress reports, but it must not prevent a student who attempted the work from completing the session.

### What counts as completed work

A math question counts when the student submits an answer through the normal answer-checking flow. Merely opening an activity, navigating between pages, or entering text without submitting it does not count.

A writing assignment counts only when it passes the existing writing validation and is successfully saved. Starting a prompt, typing an incomplete response, or repeatedly saving the same assignment does not award additional points.

Each individual math question and writing assignment may award points only once per session. The implementation must retain identifiers for credited work so that repeated clicks, rechecks, saves, or page refreshes cannot duplicate points.

### Floating session box

The existing floating session box must show both requirements and the student's progress toward each one:

```text
CURRENT SESSION

Active time       11:42 / 15:00
[ progress bar ]

Work completed       7 / 15 points
[ progress bar ]

Still needed: 3:18 active time and 8 points

[ I'm Done - Email Dad ]
```

The displayed status should clearly handle cases where only one requirement remains, for example:

- `Still needed: 4 points`
- `Still needed: 2:35 active time`
- `Session requirements complete!`

When both requirements are complete, the floating box should change to its ready/green state and enable the finish button.

### Active-time behavior

The 15-minute requirement must use tracked active time rather than total wall-clock time. Time should accrue only while the student is interacting within the application's existing active-time grace period. Leaving the application open while idle must not satisfy the time requirement.

### Persistence and session reset

Current-session progress must be saved locally, including:

- Session start time.
- Accumulated active seconds.
- Accumulated work points.
- Identifiers for math questions and writing assignments already credited.

Refreshing or reopening the page must restore the unfinished session without losing progress or awarding duplicate points.

After a session summary is successfully sent, the session timer, work points, and credited-work identifiers must reset together for the next session. Switching student profiles must keep each student's session progress separate.

### Session summary

The finish modal and email summary must include:

- Active practice time.
- Work points earned out of the required 15.
- Math questions attempted.
- Math accuracy.
- Writing assignments completed.

### Acceptance criteria

- The finish button stays disabled at 15 active minutes if the student has fewer than 15 work points.
- The finish button stays disabled at 15 work points if the student has fewer than 15 active minutes.
- The finish button becomes enabled as soon as both requirements are met.
- Fifteen submitted math questions satisfy the work requirement.
- Three validated and saved writing assignments satisfy the work requirement.
- Mixed math and writing work satisfies the requirement when its combined value reaches 15 points.
- Incorrect but genuinely submitted math attempts count once and remain visible in accuracy reporting.
- Idle wall-clock time does not count as active practice time.
- Refreshing the page does not erase progress or award duplicate points.
- The floating box always shows current progress, required progress, and what remains.
