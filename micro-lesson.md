# Micro Lesson: Finding Your Way Around Linux

**Unit 2 · File systems · Day 1 · 30 minutes**

**Objective:** Learners will navigate the Linux directory tree using `pwd`, `ls`, and `cd`.

## Run of show

| Time | Segment | Mode |
| --- | --- | --- |
| 0:00–0:03 | Hook: where am I, and what's here? | Instructor talk |
| 0:03–0:08 | The folder tree and paths | Instructor talk, check for understanding |
| 0:08–0:16 | Three commands | Live demo, then learners repeat |
| 0:16–0:26 | Practice: work the ticket | Pairs or solo |
| 0:26–0:30 | Check and exit ticket | Whole group |

## Before class

- [ ] Run the sandbox setup (end of this file) in every learner sandbox
- [ ] Open your own sandbox terminal, zoomed so the back row or a shared screen can read it
- [ ] Print or share the command reference sheet (hand out at the end)

---

## Slide 1: Where Am I?

> You've just logged into a server for the first time.
> Two questions: **Where am I?** and **What's here?**

### Instructor notes (3 min)

**Say:**
- "Imagine walking into an office building blindfolded. Your first two questions are: where am I, and what's in this room? Linux has a command for each, plus one to move between rooms. That's all this lesson is."
- Tie it to the job: "When a ticket says 'the report file is missing,' this is how you go look for it."

**Watch for:** nervous learners. Say early that typos are normal and nothing they do in the sandbox can break anything real.

---

## Slide 2: Linux Is a Tree of Folders

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

### Instructor notes (5 min)

**Say:**
- "Linux has one tree, and everything hangs off the root, written as a single slash."
- "A path is like a street address. Read /home/maria/tickets left to right: start at root, go into home, then maria, then tickets."
- Mac users: Finder folders work the same way. Windows users: it's like C:\ but with forward slashes and no drive letter.

**Check for understanding:** "What's the path to the log folder?" (Answer: `/var/log`)

**Common confusion:** learners think "home" means the root. Point out that home is one folder down from root, and each person has their own folder inside it.

---

## Slide 3: Three Commands

| Question | Command | Stands for | Example output |
|---|---|---|---|
| Where am I? | `pwd` | print working directory | `/home/maria` |
| What's here? | `ls` | list | `reports  tickets` |
| Take me there | `cd tickets` | change directory | *(no output: you moved)* |

**Handy shortcuts**

- `cd ..` go up one folder
- `cd ~` go back home from anywhere
- `ls -l` show details, like size and date

### Instructor notes (8 min): live demo, learners watch first

Say what each command stands for as you demo it. Type slowly and say each command out loud before pressing Return:

1. `pwd` → "print working directory. I'm in /home/maria."
2. `ls` → "list. Two folders here."
3. `cd tickets`, then `pwd` → "change directory. No output, and that's normal: silence means success. pwd proves I moved."
4. `ls` → show the ticket files.
5. `cd ..`, then `pwd` → "two dots means one folder up."
6. `cd ~` → "the tilde always brings you home. Use it when you're lost."

Then learners repeat steps 1–6 in their own sandbox. Walk the room or watch the chat.

**Common errors and fixes:**

| Error | Likely cause | Fix |
| --- | --- | --- |
| `No such file or directory` | Spelling or capitalization | Linux is case-sensitive: `Tickets` ≠ `tickets` |
| `command not found` | Typo, like `PWD` or `Cd` | Retype in lowercase |
| `command not found: cd..` | No space after `cd` | Commands need a space before what follows: `cd ..` |
| Lost in the tree | Too many `cd` moves | `cd ~` and start again |

**Tip:** press Tab to auto-complete folder names. It prevents most typos.

---

## Slide 4: Practice: Work the Ticket

> **Ticket #1042:** "The Q3 report is somewhere in Maria's folders. Find it and tell us its full path."

1. Start at home: `cd ~`
2. Use `ls` and `cd` to explore `reports` and its subfolders
3. When you find `q3-report.txt`, run `pwd`
4. Post the full path in the chat (or write it down)

**Done early?** Find the newest file in `/var/log` using `ls -l`.

### Instructor notes (10 min)

- Pairs work well in person; solo works fine remote.
- **Answer:** `/home/maria/reports/2026/q3/q3-report.txt`
- Give a hint at 5 minutes if needed: "Look for a folder named after the year."
- Watch for learners typing full paths without exploring. That's fine if it works, but ask how they found it.

**Debrief (2 min):** "What did you do when you hit a dead end?" (`cd ..` or `cd ~`). That habit is the real skill.

---

## Slide 5: Check: Where Would You Land?

You're in `/home/maria/reports`. Where are you after each command?

1. `cd ..`
2. `cd ~`
3. `cd /var/log`

**Exit ticket:** In one sentence, what does `pwd` tell you and when would you use it?

**Next:** Creating, copying, and moving files.

### Instructor notes (4 min)

**Answers:** 1. `/home/maria` · 2. `/home/maria` · 3. `/var/log`

- Poll or call out answers. If more than a few miss #1, re-demo `cd ..` before moving on.
- Collect exit tickets in chat or on sticky notes. Look for "it tells me where I am" plus a use like "when I'm lost" or "before I delete something."
- Hand out the command reference sheet now. Learners keep it for the rest of the course and the capstone.

---

## Sandbox setup (delivery team, before class)

Run once per learner sandbox, logged in as user `maria`:

```bash
mkdir -p ~/tickets ~/reports/2025/q4 ~/reports/2026/q3
touch ~/tickets/ticket-1040.txt ~/tickets/ticket-1041.txt ~/tickets/ticket-1042.txt
echo "Q3 revenue summary" > ~/reports/2026/q3/q3-report.txt
touch ~/reports/2025/q4/q4-report.txt
```

**Check:** `ls -R ~` should show both report folders and three ticket files.

**Tested:** Run end to end on macOS Terminal (same commands; home is `/Users/<name>` instead of `/home/<name>`).
