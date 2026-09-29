# Voice guide: how I talk upstream

## Who I am in threads

I am a student learning to contribute to Path Review. I have used Python for basic scripting, and I am interested in privacy and cybersecurity.
When I comment, I will say what I plan to check, then come back with the steps and results I actually observed. I want another person to be able to repeat my work.

## Rules I write by

### Rule: Promise the investigation, not the result

In a claim, say what I will investigate. Do not say I reproduced the bug before I have run it, and do not promise a fix or a completion date.

- Wrong: "I confirmed this bug and will fix it tomorrow."
- Right: "I plan to investigate the parenthesized phone-number case in #53 and post what I observe."

### Rule: Name the actual behavior

Refer to the input or behavior from this issue instead of writing a generic claim that could fit any issue.

- Wrong: "I will work on this issue."
- Right: "I will check whether the PII scrubber leaves a number like (555) 123-4567 visible."

### Rule: Say what I observed

In a reproduction comment, separate the command or input I used from the result I saw. If I cannot reproduce it, say so and show the attempt.

- Wrong: "The scrubber is broken."
- Right: "With the input I tested, the scrubber returned the parenthesized phone number unchanged. I included the command and output below."

### Rule: Own my evidence

Report my own environment, steps, and output. Another student's report can help me understand the issue, but I will not claim their result as mine.

- Wrong: "Same as the report above. Confirmed."
- Right: "I ran these steps on my Windows computer. Here is my input, the output I saw, and my Python version."

### Rule: Follow the repository's AI policy

Before posting, check the repository's contribution rules. If they require AI-assistance disclosure, state how I used it rather than leaving out a required disclosure.

- Wrong: "I did all the investigation myself." 
- Right: "I used Claude to review the wording of this report; I ran the commands and checked the output myself."

## Things I never post

- A promise that I will fix the issue by a particular date.
- "Confirmed" before I have run the steps and seen the relevant output.
- "Same as above" in place of my own reproduction evidence.
- A test result, environment detail, or AI disclosure that is not true.
- A claim that another student's work prevents me from working on a shared Path Review issue.