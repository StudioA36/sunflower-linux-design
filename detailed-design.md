# Sunflower Linux Course: Detailed Design

A 12-hour, instructor-led Linux course that takes 25 Sunflower employees from never opening a terminal to handling everyday server tasks with a reference guide close by.

## Program overview

| Item | Detail |
| --- | --- |
| Client | Sunflower Inc. |
| Learners | 25 employees, low-to-no technical experience |
| Format | Instructor-led, onsite or remote |
| Length | 12 training hours over 2 days (6 hours a day with a 10-minute break each hour, plus a 1-hour lunch) |
| Environment | Browser-based Linux sandbox per learner, prepared by the delivery team (no installs needed) |
| Business outcomes | Shell scripting and basic automation; package management; working with local and remote file systems; creating, starting and stopping services |

**Working persona:** Maria, four years in customer support, comfortable with email, spreadsheets and ticketing, has never used a terminal. After the course she supports Linux servers in an entry-level IT support role, connecting remotely from her laptop.

**Design approach:** The business outcomes stay as written. Success is set at a beginner level: learners complete each task on their own using a reference sheet, not from memory. Advanced tasks, like mounting a remote file system, run as guided labs in a prepared environment.

**Sequence change:** Package management is taught on Day 1, after file systems, so learners install the software they later manage as services and automate with scripts. All five HLD units are kept.

## Time plan

| Day | Block | Hours |
| --- | --- | --- |
| Day 1 | Unit 1: Linux philosophy and architecture | 1.75 |
| Day 1 | Unit 2: File systems | 2.25 |
| Day 1 | Unit 4: Package management | 1 |
| Day 1 | Day 1 recap and questions | 0.5 |
| Day 2 | Unit 3: Utilities, commands and services | 2.5 |
| Day 2 | Unit 5: Shells, scripting and automation | 2.25 |
| Day 2 | Capstone | 0.75 |
| Both days | Breaks (10 minutes each hour) | 1 |
| **Total training** | | **12** |
| Both days | Lunch (1 hour each day, not counted in training time) | 2 |

Sample day: 9:00 to 4:00, lunch 12:00 to 1:00.

## Unit 1: Linux philosophy and architecture (1.75 hrs)

**Learning objectives.** Learners will be able to:

1. Explain what Linux is and where Sunflower uses it, in plain language.
2. Identify the main parts of a Linux system: kernel, shell, file system and users.
3. Run basic commands in the terminal and read their output.

**Concepts in order:** What an operating system is · Linux origins and open source · Where Linux runs (servers, cloud, devices) · Kernel, shell and users · The terminal and command structure (command, options, arguments) · Getting help with `man` and `--help`

**Tools:** Browser-based sandbox and terminal from the first 15 minutes; `whoami`, `date`, `echo`, `man`

**How we know:** Quick poll on where Linux runs · Learners label a simple system diagram · Hands-on check: run three commands and explain what each returned

## Unit 2: File systems (2.25 hrs)

**Learning objectives.** Learners will be able to:

1. Navigate the Linux directory tree using `pwd`, `ls` and `cd`.
2. Create, copy, move and delete files and directories.
3. Mount and check a remote NFS share using a step-by-step guide.

**Concepts in order:** The directory tree and root (`/`) · Absolute and relative paths · Home directories · Creating and managing files (`mkdir`, `touch`, `cp`, `mv`, `rm`) · Viewing files (`cat`, `less`) · File permissions basics · File system types (ext4, xfs, NFS) · Local vs remote storage · Mounting with `mount` and checking with `df -h` · Common mount errors (wrong path, wrong address, missing folder)

**Tools:** Sandbox terminal · A file system diagram handout · A prepared NFS server set up by the delivery team (guided lab only) · Troubleshooting checklist

**How we know:** Scavenger hunt: find and report the contents of hidden files · Lab: build a project folder structure from a spec · Guided lab: mount a remote share and confirm it with `df -h`

## Unit 3: Utilities, commands and services (2.5 hrs)

**Learning objectives.** Learners will be able to:

1. Use core utilities to search, filter and view text and logs.
2. Check, start, stop and restart a service with `systemctl`.
3. Use `sudo` safely to run tasks that need admin rights.

**Concepts in order:** Searching with `grep` and `find` · Pipes and redirection (`|`, `>`) · Reading logs (`tail`, `journalctl`) · Users, root and `sudo` · Processes (`ps`, `top`) · What a service is · Managing services with `systemctl` (status, start, stop, restart, enable)

**Tools:** Sandbox terminal · Sample log files · A practice web service in the sandbox · Command reference sheet

**How we know:** Log hunt: find the error in a sample log · Lab: a service is down, so check its status, restart it and confirm it is running · Exit ticket: when to use `sudo` and when not to

## Unit 4: Package management (1 hr)

**Learning objectives.** Learners will be able to:

1. Describe what a Linux distribution and a package manager are.
2. Search for, install, update and remove software with a package manager.

**Concepts in order:** Distributions (Ubuntu, Red Hat) · What a package is · Package managers (`apt` and `dnf`) · Updating package lists · Installing, updating and removing software

**Tools:** Sandbox terminal (Ubuntu with `apt`) · Comparison handout for `apt` and `dnf`

**How we know:** Lab: install a small tool, use it, then remove it · Quick check: match each distribution to its package manager

## Unit 5: Shells, scripting and automation (2.25 hrs)

**Learning objectives.** Learners will be able to:

1. Identify common shells and edit text files with `nano`.
2. Write and run a simple shell script from a template.
3. Schedule a script to run automatically with `cron`.

**Concepts in order:** Shells (bash, zsh) · Editing with `nano` · What a script is (a recipe the computer follows) · Script structure (shebang, comments, commands) · Making a script executable (`chmod +x`) · Variables · Scheduling with `cron` and reading a cron line

**Tools:** Sandbox terminal · `nano` · Script template · Cron cheat sheet

**How we know:** Lab: edit a template script that cleans up old files and run it · Lab: schedule it with `cron` and confirm the schedule with `crontab -l`

## Capstone (45 min)

Learners work a short ticket queue as Sunflower IT support. One ticket each covers navigation, a remote share, a stopped service, a software install and a cleanup script. Instructors check each ticket against a simple pass/fail rubric. The capstone shows each learner can do every business outcome with the reference sheet in hand.

## Knowledge checks

| Type | When | Purpose |
| --- | --- | --- |
| Quick hands-on checks | After each concept | Catch confusion early |
| Unit labs | End of each unit | Confirm the unit's objectives |
| Capstone | End of course | Confirm the business outcomes |

## Delivery team needs

- A browser-based Linux sandbox for every learner, tested before day one
- A prepared NFS server and a practice web service in the sandbox
- A command reference sheet and troubleshooting checklist for learners
- A facilitator guide with timings, demo scripts and common errors

## Validation plan

- **Design sign-off:** Sunflower stakeholders review this Detailed Design before build starts
- **Pilot review:** walk one built lesson through with Sunflower stakeholders and an instructor before full rollout
- **After delivery:** capstone pass rates and a 30-day check-in on whether learners are using the skills on the job

## To confirm in discovery

- Learners' current roles and what they'll do with Linux after the course
- Which distribution and systems Sunflower actually uses
- Laptops (Mac or Windows) and any IT restrictions on access
- Schedule, onsite or remote, and how success will be measured after the course
