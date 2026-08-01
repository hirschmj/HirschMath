# Bright Steps: Next Steps and Feedback

This file collects usability feedback before the next round of behavior changes.

## Writing

### Refactor "Stronger Word Choice"

**Status:** Implemented. Validation now checks whether the weak words from the original sentence were actually replaced; it no longer requires matches from a short approved-vocabulary list.

**Feedback:** Requiring three stronger words in a short rewritten sentence is difficult and frustrating for students. The task can feel like guessing which words the app considers "strong."

**Original problem:**

- The activity goal says, "Use at least 3 stronger words."
- Prompts usually ask the student to rewrite one short sentence.
- Validation recognizes only a small fixed list of vivid words.
- A reasonable synonym can be rejected simply because it is not in that list.
- The feedback asks for at least two replacements in some cases, which does not match the stated goal of three.

**Implemented refactor:**

- Change the goal from an arbitrary count to: **"Replace the plain words with more exact words."**
- Identify the specific plain words in each prompt, such as `big`, `went`, or `good`.
- Require one strong replacement for each highlighted plain word, usually one or two replacements per sentence.
- Tell the student exactly which word still needs attention.
- Accept a much broader range of reasonable replacements instead of relying on a short vocabulary whitelist.
- Show a simple checklist:
  - Complete sentence
  - Plain word replaced
  - Capital letter and ending punctuation
- Allow a good short sentence to pass without forcing the student to add unnecessary adjectives or adverbs.

**Example:**

> Original: The big dog went fast across the yard.
>
> Student: The enormous dog sprinted across the yard.

This should pass because the student replaced the two weak ideas—`big` and `went fast`—with precise language.

**Suggested student-facing feedback:**

- "Nice start! Replace **big** with a more exact word."
- "You improved **went**. Now choose a stronger word for **good**."
- "Great revision—your new words make the sentence clearer."

**Acceptance criteria:**

- The instructions and validation require the same number of changes.
- Correct synonyms are not rejected merely because they are absent from a short hard-coded list.
- Feedback names the remaining plain word rather than asking generally for "more vivid words."
- A concise, well-revised sentence can pass.
- Students are never required to force three vivid words into a sentence that only contains one or two weak ideas.

## Student Profiles

### Make profile controls accessible

The floating session/email panel should start collapsed and remain out of the way of the student selector and **+ Student** button.

### Support renaming a student

Add a parent-accessible way to rename an existing student profile without deleting or losing that student's saved history.

## Session Completion

### Clearly show the early-finish option

**Status:** Implemented as a 35-point early-finish path. Twenty math questions plus three writing assignments are the student-facing example, and equivalent point combinations also qualify.

**Feedback:** Students should know that completing **20 math questions and 3 writing assignments** allows them to finish early. If this option is hidden or only becomes apparent near the end, students cannot use it as a motivating goal.

**Implemented refactor:**

- Present two clear ways to complete a session:
  1. Meet the normal active-time and work requirements.
  2. Finish early by completing 20 math questions and 3 validated writing assignments.
- Show the early-finish option in the session panel from the beginning.
- Display live progress for both parts, such as `Math: 12 / 20` and `Writing: 2 / 3`.
- Use encouraging language when the student is close, such as, "8 more math questions and 1 more writing assignment to finish early."
- Enable the finish control immediately when either completion path is satisfied.
- Explain that writing only counts after it passes validation and is saved.

**Suggested student-facing text:**

> Want to finish early? Complete 20 math questions and 3 writing assignments.

**Acceptance criteria:**

- The early-finish option is visible before the student begins working.
- The student can always see their progress toward 20 math questions and 3 writing assignments.
- Completing both early-finish targets enables the finish button even if the normal active-time requirement has not been reached.
- Completing only 20 math questions or only 3 writing assignments does not enable early finish.
- Each math question and saved writing assignment counts only once.

## Parent Email Setup

### Keep personal addresses out of source control

The parent email should be entered after unlocking the Parent area and stored locally with the browser's student-history data. When no recipient is configured, the student-facing email control should clearly say that Dad needs to complete setup.

## Feedback Template

### Short title

**Feedback:** What the student or parent experienced.

**Why it matters:** How it affects learning, clarity, privacy, or usability.

**Proposed refactor:** The intended improvement without prematurely locking in implementation details.

**Acceptance criteria:**

- Observable result one.
- Observable result two.
