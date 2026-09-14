# CSCI 1030U - Group Project Plan

## Purpose

The group project is the primary vehicle for two learning outcomes that a written exam cannot assess:

- **Communicate** technical designs clearly (oral checkpoints + written documentation).
- **Collaborate** in a team to plan, build, and deliver software on schedule using
  GitHub.

It is deliberately designed so that, by the end of the term, a team's repository
**exercises as much of the course as possible** - every unit, from problem-solving
through intermediate programming, has to show up in the finished product.

Two design rules drive everything below:

1. **Each milestone demonstrates the topics from the lectures that came before it.** A
   team is never asked to use something they haven't been taught.
2. **Every student must personally contribute each topic.** For each milestone, every
   team member must have at least one *non-trivial commit* (see
   [What counts as a non-trivial commit](#what-counts-as-a-non-trivial-commit)) for each
   listed topic. Participation is individual and traceable in git history.

---

## The project

**Theme: a networked, multi-user Python application** - by default, a **turn-based
multiplayer game with an AI opponent and persistent data** (leaderboard, save/resume).

The networked, multi-user theme is not arbitrary: it is the smallest theme that forces
the whole course to appear. A finished project has to talk over sockets (Unit 05), serve
several users at once (async / threads, Unit 05), organize itself with classes (OOP,
Unit 03), read and write files (Unit 03), present an interface (Unit 03), and make good
use of a data structure and an algorithm (Unit 04) - all built on Unit 02 fundamentals
and planned with Unit 01 techniques.

Teams choose their specific application, subject to instructor approval of the proposal.
See [Suggested projects](#suggested-projects) for ideas that are known to fit.

### Scope and tech constraints

- **Python standard library only**, so the project stays aligned with what is taught:
  `socket`, `asyncio` / `threading` / `multiprocessing`, `tkinter`, `argparse`, `json`,
  `csv`. Any additional dependency needs instructor approval in the proposal.
- **Team size: 4-5 students.** The plan scales across that range; the per-student topic
  rule is the same regardless of size.
- Keep the scope honest: a small application that cleanly hits every topic beats an
  ambitious one that fakes half of them.

---

## Teams and participation

### The "everyone contributes" model

The project is decomposed into **vertical slices** - one comparable feature per team
member, each built end to end. When a milestone adds a topic, *each* member adds that
topic *to their own slice*. For example, at the networking milestone, no team writes one
server that one person owns; instead each member adds the message type and handler for
their feature to the shared server. That way a single shared codebase still yields an
individual, non-trivial commit per topic per person.

### The contribution matrix (required each milestone)

The repository must contain a `CONTRIBUTIONS.md` with a table, updated before every
checkpoint, mapping **each student** to the **commit(s) or pull request(s)** that
demonstrate **each required topic** for that milestone:

| Student | Topic A | Topic B | Topic C | ... |
|---------|---------|---------|---------|-----|
| Alice   | #12     | #15     | abc1234 | ... |
| Bob     | #13     | #16     | def5678 | ... |

Cells link to a merged PR or a commit hash. At the checkpoint, each student speaks to
their own row. A blank cell means that student did not demonstrate that topic, and loses
those individual marks - the rest of the team is unaffected.

### What counts as a non-trivial commit

A commit (or small set of commits) **authored by that student** that adds real, working
functionality for the topic. As a guideline:

- implements a genuine piece of logic - roughly a complete function, class, handler, or
  screen (on the order of 15+ meaningful lines), not a one-liner;
- lands on the project's `main` branch (*how* it gets there is the
  [git workflow](#git-workflow), whose emphasis grows over the term);
- is **not** formatting, renaming, comments, config, or generated/boilerplate code.

The TA verifies against git author information and the contribution matrix. "I pair
-programmed it" is fine, but the commit must be authored (or co-authored via
`Co-authored-by:`) by the student claiming it.

---

## Milestones

Milestones are pinned to the project presentation weeks already in the course schedule.
Each one demonstrates everything taught up to that point.

### Milestone 0 - Team, Topic, and Repository (between Lab 01 and Lab 02)

Not graded for code; sets the project up. It is walked through in **Lab 01** and
completed in the week between the first and second labs.

- **Form the team** (4-5 students).
- **Brainstorm and choose a topic** - the application the team will build, within the
  networked-app theme (see [Suggested projects](#suggested-projects)).
- **Accept the invitation to the CSCI1030U organization** on GitHub (sent out after the
  Lab 01 quiz closes, using the usernames submitted there).
- **Create the shared repository from the project template**: one member clicks
  **Use this template**, sets the owner to `CSCI1030U`, names it `project-yourteamname`,
  and makes it **private**. That member then adds every other member as a collaborator
  with **Write** access, plus the instructor/TA.
- Capture the decision in a short **`PROPOSAL.md`** in the repo: the chosen application, a
  first breakdown into one vertical slice per member, and the tech plan
  (standard-library-only, or an exception request).
- Agree on the git workflow taught in Lab 01 (see [Git workflow](#git-workflow)): commit
  in your own name and push; grow into branches and pull requests as the project goes on.

**Ties to:** Lab 01, which teaches the basic git/GitHub commands and describes these
setup steps, plus Unit 01 (decomposition, planning).

### Milestone 1 - Core Prototype (Week 4) - Units 01-02

A **single-machine, text-only prototype**: the core logic of the application working
locally in the terminal, no networking or fancy interface yet. This is where the team
proves the idea runs.

Per student, a non-trivial commit for **each** of:

- [ ] **Planning / problem-solving** - the written spec and decomposition for their slice
      (Unit 01).
- [ ] **Control flow** - conditionals and loops driving their feature (Unit 02).
- [ ] **Collections** - lists and dictionaries holding their feature's state (Unit 02).
- [ ] **Functions** - at least one non-trivial function they authored (Unit 02).

**Definition of done:** `python main.py` runs a playable/usable local version of the core
loop; a short `README` explains how to run it; `CONTRIBUTIONS.md` is filled in.

### Milestone 2 - Practical Application (Week 8) - Unit 03

The prototype becomes a **real, single-machine application**: organized into classes,
with a proper interface, persistence, and configuration.

Per student, a non-trivial commit for **each** of:

- [ ] **OOP** - at least one class they authored, with methods and state (Unit 03).
- [ ] **File I/O** - a save/load, high-score, or config feature reading/writing a file
      (`json` or `csv`) (Unit 03).
- [ ] **Recursion** - a recursive function used somewhere real in their slice (Unit 03).
- [ ] **Command-line arguments** - an `argparse` option they added (e.g., difficulty,
      data file, config) (Unit 03).
- [ ] **Interface** - a TUI menu/screen or a `tkinter` GUI element they built (Unit 03).

**Definition of done:** the app is class-based, launches with useful `argparse` options,
saves and loads state to disk, and is usable through a TUI or GUI. Comes right after the
Week 7 midterm, so it consolidates the whole practical unit.

### Milestone 3 - Final Product (Week 12) - Units 04-05

The application becomes **networked and multi-user**, backed by a real data structure and
a real algorithm. This is the finished product and the final presentation.

Per student, a non-trivial commit for **each** of:

- [ ] **Data structure** - a meaningful use of a stack, queue, or BST (e.g., turn queue,
      move history/undo stack, sorted leaderboard) (Unit 04).
- [ ] **Algorithm strategy** - a feature using backtracking, divide-and-conquer, greedy,
      or dynamic programming (e.g., an AI opponent, pathfinding, scoring/optimization),
      with a **short Big-O note** in the docs (Unit 04).
- [ ] **Sockets** - a client-server message + handler for their feature (Unit 05).
- [ ] **Concurrency** - an async task, thread, or process that lets their feature's I/O
      run alongside others (e.g., their handler on the concurrent server) (Unit 05).

**Definition of done:** two or more clients interact through the server at the same time;
the product is packaged with a `README`, run instructions, the contribution matrix, and a
one-page **design document** covering the architecture and the Big-O analysis.

---

## Presentations

Each checkpoint lab (Weeks 4, 8, 12) runs the same way. Teams push their work **before** the
session; at the start the TA goes around the (roughly five) teams to confirm each
submission matches the milestone's requirements; then each team gives an **8-10 minute**
presentation covering:

- an **introduction to the team** (who's in the group, which slice each member owns),
- **background on the topic** (what the application is, for a first-time viewer),
- the **technical concepts implemented**, with **each member speaking to their own
  contributions** (walking their row of the matrix), and
- a **demonstration** of the project in action.

**The balance shifts across milestones.** Because the team and topic are introduced at
Milestone 1, later checkpoints **compress** the introduction and background and **expand**
the technical explanation and demo, which grow substantially each milestone.

Presentations carry most of the project's oral-communication assessment. Every member must
speak.

---

## Git workflow

Good git habits are part of learning outcome 8, but they are introduced gently so
first-semester students aren't blocked by tooling. The **emphasis grows over the term**,
and it is a *recommended* progression, not a pass/fail gate - participation is always
graded on each student's own identifiable commits, whichever workflow the team uses.

- **Lab 01 through Milestone 1 (getting started):** everyone can clone, commit with a
  meaningful message **in their own name**, and push. Pull requests are **taught in Lab 01**
  and encouraged, but at Milestone 1 all that's needed is that each student has their own
  commits on `main`.
- **Milestones 2 and 3 (the recommended way to work):** teams are encouraged to move to a
  **branch per feature**, merged to `main` through a **pull request a teammate reviews**.
  This is the recommended workflow and makes the strongest case for the teamwork outcome -
  but a team that keeps committing straight to `main` is not penalized for that alone, as
  long as each member's contributions are clear in the history.

Throughout:

- Commit messages are meaningful and in the author's name (use `Co-authored-by:` for
  genuine pairing).
- `main` always runs. Protect it if the team is comfortable doing so.

These habits support learning outcome 8, and the per-student commit history is what makes
the topic rule verifiable regardless of which workflow a team chooses.

---

## Assessment (per milestone)

Each milestone is graded on four fronts; the exact weights are set with the overall
course weighting, still being finalized.

1. **Functionality** - does the deliverable meet its definition of done?
2. **Topic coverage** - are all listed topics present and used meaningfully (not
   token/decorative)?
3. **Individual participation** - does every member have their required non-trivial
   commits, verified via git history and the contribution matrix? (Scored per student.)
4. **Presentation and documentation** - clear demo, clear speaking, up-to-date README /
   design doc.

Fronts 1, 2, and 4 are largely team scores; front 3 is individual, so a team can be
strong while an individual who did not contribute is marked down without dragging the
others down.

---

## Topic coverage map

How the project is intended to touch the whole course:

| Unit | Topic | Where it appears | Milestone |
|------|-------|------------------|-----------|
| 01 | Problem-solving, decomposition | Proposal + per-slice specs | 0, 1 |
| 02 | Variables, types, conditionals, loops | Core game/app loop | 1 |
| 02 | Strings, lists, dictionaries | Game/app state | 1 |
| 02 | Functions | Everywhere | 1 |
| 03 | OOP | Classes for entities/players/board | 2 |
| 03 | File I/O | Save/load, high scores, config | 2 |
| 03 | Recursion | AI search, board fill, tree walk | 2 |
| 03 | Command-line arguments | Launch/config options | 2 |
| 03 | TUI / GUI | The client interface | 2 |
| 04 | Data structures (stack/queue/BST) | Turns, history, leaderboard | 3 |
| 04 | Algorithm strategies + Big-O | AI / pathfinding / scoring + design doc | 3 |
| 05 | Sockets | Client-server messages | 3 |
| 05 | Async / threads / processes | Concurrent server for many users | 3 |

---

## Suggested projects

Any of these can hit every required topic; the notes show the natural fit for the harder
Unit 04-05 items.

1. **Networked board game** (Battleship, Connect Four, Checkers) - AI opponent
   (backtracking / minimax = divide-and-conquer), move-history stack, sorted leaderboard,
   concurrent server for multiple matches.
2. **Multiplayer trivia / quiz** - question bank from file, real-time scoreboard (BST or
   sorting), greedy/DP scoring, async server fanning questions to many clients.
3. **Multiplayer word game** (Wordle-battle, Boggle, Scrabble-lite) - dictionary loaded
   into a fast lookup structure, a solver/AI (backtracking), networked rounds.
4. **Card game** (Blackjack, Crazy Eights, a Uno-like) - deck/hand classes, turn queue,
   simple AI (greedy), save/resume, concurrent tables.
5. **Collaborative tool** (shared to-do, whiteboard, or chat-with-games) - command
   parsing, persistence, concurrent clients, a data structure for the shared state.

