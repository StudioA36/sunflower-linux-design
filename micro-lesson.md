---
marp: true
title: "Micro Lesson: Finding Your Way Around Linux"
paginate: true
---

# Finding Your Way Around Linux
### Unit 2 · File systems · Day 1 · 30 minutes

**Objective:** Navigate the Linux directory tree using `pwd`, `ls`, and `cd`.

> You've just logged into a server for the first time.
> Two questions: **Where am I?** and **What's here?**

<!--
INSTRUCTOR NOTES (3 min)

Before class:
- Run the setup script (end of this file) in every learner sandbox. It builds the practice folders.
- Open your own sandbox terminal, zoomed so the back row (or a shared screen) can read it.

Say:
- "Imagine walking into an office building blindfolded. Your first two questions are: where am I, and what's in this room? Linux has a command for each, plus one to move between rooms. That's all this lesson is."
- Tie it to the job: "When a ticket says 'the report file is missing,' this is how you go look for it."

Watch for: nervous learners. Say early that typos are normal and nothing they do in the sandbox can break anything real.
-->

---

# Linux Is a Tree of Folders

```
/                     ← the root: where everything starts
├── home
│   └── maria         ← your home folder: you start here
│       ├── tickets
│       └── reports
├── var
│   └── log           ← where servers keep their logs
└── etc               ← settings files
```

- Every folder lives inside another one, all the way back to `/`
- A **path** is the address of a folder: `/home/maria/tickets`

<!--
INSTRUCTOR NOTES (5 min)

Say:
- "Linux has one tree, and everything hangs off the root, written as a single slash."
- "A path is like a street address. Read /home/maria/tickets left to right: start at root, go into home, then maria, then tickets."
- Mac users: Finder folders work the same way. Windows users: it's like C:\ but with forward slashes and no drive letter.

Check for understanding (ask the room or chat):
- "What's the path to the log folder?" (Answer: /var/log)

Common confusion: learners think "home" means the root. Point out that home is one folder down from root, and each person has their own folder inside it.
-->

---

# Three Commands

| Question | Command | Example output |
|---|---|---|
| Where am I? | `pwd` | `/home/maria` |
| What's here? | `ls` | `reports  tickets` |
| Take me there | `cd tickets` | *(no output: you moved)* |

**Handy shortcuts**

- `cd ..` go up one folder
- `cd ~` go back home from anywhere
- `ls -l` show details, like size and date

<!--
INSTRUCTOR NOTES (8 min) — live demo, learners watch first

Demo slowly, saying each command out loud before pressing Enter:
1. pwd → "print working directory. I'm in /home/maria."
2. ls → "two folders here."
3. cd tickets, then pwd → "cd gave no output. That's normal: silence means success. pwd proves I moved."
4. ls → show the ticket files.
5. cd .. then pwd → "two dots means one folder up."
6. cd ~ → "the squiggle (tilde) always brings you home. Use it when you're lost."

Then learners repeat steps 1–6 in their own sandbox. Walk the room or watch the chat.

Common errors and fixes:
- "No such file or directory" → check spelling. Linux is case-sensitive: Tickets ≠ tickets.
- "command not found" → usually a typo, like PWD or Cd.
- Lost in the tree → cd ~ and start again.
- Tip: press Tab to auto-complete folder names. It prevents most typos.
-->

---

# Practice: Work the Ticket

> **Ticket #1042:** "The Q3 report is somewhere in Maria's folders. Find it and tell us its full path."

1. Start at home: `cd ~`
2. Use `ls` and `cd` to explore `reports` and its subfolders
3. When you find `q3-report.txt`, run `pwd`
4. Post the full path in the chat (or write it down)

**Done early?** Find the newest file in `/var/log` using `ls -l`.

<!--
INSTRUCTOR NOTES (10 min)

- Pairs work well in person; solo works fine remote.
- Answer: /home/maria/reports/2026/q3/q3-report.txt
- Give a hint at 5 minutes if needed: "Look for a folder named after the year."
- Watch for learners typing full paths without exploring. That's fine if it works, but ask them how they found it.

Debrief (2 min):
- "What did you do when you hit a dead end?" (cd .. or cd ~). That habit is the real skill.
-->

---

# Check: Where Would You Land?

You're in `/home/maria/reports`. Where are you after each command?

1. `cd ..`
2. `cd ~`
3. `cd /var/log`

**Exit ticket:** In one sentence, what does `pwd` tell you and when would you use it?

**Next:** Creating, copying, and moving files.

<!--
INSTRUCTOR NOTES (4 min)

Answers:
1. /home/maria
2. /home/maria
3. /var/log

- Quick poll or call-out answers. If more than a few miss #1, re-demo cd .. before moving on.
- Collect exit tickets in chat or on sticky notes. Look for "it tells me where I am" plus a use like "when I'm lost" or "before I delete something."
- Hand out the command reference sheet now. Learners keep it for the rest of the course and the capstone.
-->

---

<!--
SANDBOX SETUP (delivery team, before class)
Run once per learner sandbox, logged in as user maria:

mkdir -p ~/tickets ~/reports/2025/q4 ~/reports/2026/q3
touch ~/tickets/ticket-1040.txt ~/tickets/ticket-1041.txt ~/tickets/ticket-1042.txt
echo "Q3 revenue summary" > ~/reports/2026/q3/q3-report.txt
touch ~/reports/2025/q4/q4-report.txt

Check: ls -R ~ should show both report folders and three tickets.
-->

# Setup Notes

The setup steps for the delivery team are in this slide's notes.
