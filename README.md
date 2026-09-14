# Lab 01 - Git, GitHub, and Getting Your Project Started

Welcome to your first lab! There's no Python this week. Instead you'll learn the tools
you'll use in **every** lab and in the group project: **git** (which tracks changes to
your code) and **GitHub** (which stores it online and lets your team share it). Then
you'll get your group project off the ground.

There are two parts:

1. **Get set up on GitHub and learn the git workflow** by making changes to your own
   lab-01 repository.
2. **Start your group project** - form a team, choose a topic, and create your shared
   repository.

**Everything you hand in goes into the Lab 01 quiz on Canvas.** Open that quiz now and
keep it open in another tab - you'll type answers into it as you work, and it's where you
submit your repository at the end. Nothing is submitted by email or by messaging your
instructor.

**Time:** do **Part 1** during the 80-minute session. **Part 2** is a team task to finish
**before Lab 02**. Ask the lab instructor whenever you get stuck - that's what they're
here for.

## Before you start - install your tools

You need **Git** on your computer, and (recommended) the **GitHub CLI**, `gh`, which makes
signing in painless. If they aren't installed yet, follow **`install-tools.md`** in this
repo - it has step-by-step instructions and download links for **Windows, macOS, and
Linux**. Quick links:

- Git: <https://git-scm.com/downloads>
- GitHub CLI (`gh`): <https://cli.github.com/>

Check they're installed with `git --version` and `gh --version`. Your lab instructor can
help if the install gives you trouble.

## A note on cheat sheets

`git-cheatsheet.md` (in this repo) lists every command used below. Keep it open. If a
`git` command ever asks you for a password, read the last section of the cheat sheet -
that snag catches almost everyone the first time.

---

## Part 1 - Get on GitHub and learn the git workflow

### Step 1 - Create your GitHub account

Go to <https://github.com/signup> and create a free account. If you already have one you
can reuse it - skip to Step 2.

A few things worth getting right, because **you'll use this account for the whole term**
and for the group project:

- **Pick a username you're happy to be seen by classmates and future employers.** Your
  teammates will see it on every commit. Something based on your real name is a good
  default, but it does not have to be your real name.
- **Use an email address you'll keep after this term** if you can. Your `@ontariotechu.net`
  address works fine; a personal address will outlast your student one.
- **Verify your email.** GitHub won't let you create repositories until you click the link
  in the confirmation message.

> **Privacy note:** your Lab 01 repository will be public (see Step 3), so don't put
> anything in it you wouldn't want visible - no student number, no address, no phone
> number. Later labs will be private.

### Step 2 - Record your username in the Canvas quiz

Open the **Lab 01 quiz on Canvas** and answer the question that asks for your **GitHub
username**. Type just the username, not the full URL:

```
Correct:   jsmith2026
Not this:  https://github.com/jsmith2026
```

Do this now, before you go any further. Your instructor uses these answers to add you to
the **CSCI1030U** organization on GitHub, which is where your labs will live from Lab 02
onward. If your username is missing or misspelled, that invitation can't reach you.

You can keep working on the rest of the quiz as you go - just don't submit it until the
very end, when you have your repository URL and commit hash from Step 8.

### Step 3 - Create your lab repository from the template

Lab repositories are **templates**. Instead of accepting an invitation, you make your own
copy of the template with one click.

1. Open the **Lab 01 template** link in the Canvas assignment. It will take you to a repo
   named something like `CSCI1030U/lab01-template`.
2. Click the green **Use this template** button, then **Create a new repository**.
3. Fill in the form:
   - **Owner:** your own account (your username).
   - **Repository name:** `lab01-your-username` - for example `lab01-jsmith2026`. Use your
     real username in place of `your-username`.
   - **Visibility:** **Public**.
4. Click **Create repository**.

You now have your own independent copy, with the starter files and a fresh history.

> **Why public, just this once?** There's nothing in Lab 01 to copy - no solution, no code
> - and a public repo means your instructor can read it straight from the URL you submit,
> before you're a member of the course organization. From **Lab 02 onward your repos will
> be private**, inside the CSCI1030U organization, so classmates can't see your work.

> **Careful:** **Use this template** is the button you want. Do *not* use **Fork**. A fork
> can never be made private, and it wires your copy back to the template so that a stray
> click can open a pull request that shows your work to the whole class.

### Step 4 - Clone your repository

Now copy the repository to your computer. On *your* repo page (the one under your own
account, not the template), click the green **Code** button and copy the URL. Then, in a
terminal, in the folder where you want to keep your labs:

```
git clone https://github.com/your-username/lab01-your-username
cd lab01-your-username
```

### Step 5 - Make a change

Open **`about_me.md`** and fill in your answers (replace each `...`), including the GitHub
username you registered in Step 2. Save the file. Then see what git noticed:

```
git status
```

It should show that `about_me.md` was modified.

> The quiz also asks a few short questions about yourself and about how this lab went.
> Those are answered **in Canvas**, not in the repo. `about_me.md` just needs your name,
> program, and username.

### Step 6 - Stage, commit, and push

Save a snapshot of your change and upload it to GitHub:

```
git add about_me.md
git commit -m "Fill in about_me"
git push
```

Refresh your repo page on GitHub - your edited `about_me.md` is now there. **That's the
core loop you'll repeat all term: edit -> add -> commit -> push.**

### Step 7 - Work on a branch and open a pull request

On real projects you don't edit `main` directly - you make a **branch**, propose the
change with a **pull request (PR)**, and merge it. Practise that now.

Create a branch and switch to it:

```
git switch -c add-goal
```

Add one line to the bottom of `about_me.md`, for example:

```
- **My goal for this course:** ...
```

Commit it and push the new branch to GitHub:

```
git add about_me.md
git commit -m "Add my goal for the course"
git push -u origin add-goal
```

Now go to your repo on the **GitHub website**. It will offer a **Compare & pull request**
button - click it, look over your change, create the PR, and then **Merge** it into
`main`.

Finally, bring the merged change back to your computer:

```
git switch main
git pull
```

You've now done the whole workflow: branch -> commit -> push -> pull request -> merge ->
pull. That's exactly how your team will work on the project.

### Step 8 - Submit your repository URL and commit hash

This is how every lab gets handed in this term, so it's worth doing slowly once.

**First, make sure everything is pushed and you're up to date on `main`:**

```
git switch main
git pull
git status
```

`git status` should say `nothing to commit, working tree clean` and that your branch is up
to date with `origin/main`. If it lists changes, go back to Step 6 and commit and push
them.

**Then ask git for the hash of your latest commit:**

```
git rev-parse HEAD
```

That prints a 40-character line of letters and numbers, like:

```
3f9a1c2e8b7d4056a1f2e3d4c5b6a7f8091a2b3c
```

That's your **commit hash** - a permanent name for the exact snapshot you're handing in.

**Finally, in the Canvas quiz, enter:**

- your **repository URL**, in full: `https://github.com/your-username/lab01-your-username`
- your **commit hash**, pasted exactly as `git rev-parse HEAD` printed it

Then answer any remaining questions and **submit the quiz**. The Canvas timestamp on your
submission is what counts as your submission time, so submit before the deadline even if
you plan to keep tidying up the repo afterwards.

> **Anything you push after you submit the quiz is not marked.** The hash you submit points
> at one specific snapshot, and that snapshot is what gets read. If you fix something
> important later, get the new hash and resubmit if the quiz still allows it, or contact
> your instructor.

---

## Part 2 - Start your group project (Milestone 0)

This part is done with your team, and finished **before Lab 02**. It is the project's
Milestone 0 - see `project/overview.md` for the full project plan.

### Step 1 - Accept your organization invitation

After the Lab 01 quiz closes, your instructor will invite every student who submitted a
username to the **CSCI1030U** organization on GitHub. Watch for the invitation email (or
check <https://github.com/CSCI1030U>) and **accept it**. Your team's shared repository, and
every lab from Lab 02 onward, lives inside that organization.

If the invitation hasn't arrived a day or two after the quiz closes, tell your instructor -
usually it means the username in your quiz answer had a typo.

### Step 2 - Form your team

Get into a team of **4-5 students**. Everyone needs a GitHub account and needs to have
accepted the organization invitation.

### Step 3 - Brainstorm and choose a topic

Your project will be a **networked, multi-user application** (by default, a turn-based
multiplayer game). Skim the **Suggested projects** list in `project/overview.md`, then
agree on what you'll build. Aim for something small that you can grow all term - you'll
add networking, files, an interface, and an AI/algorithm to it as the course goes on.

### Step 4 - Create your shared repository

Once everyone has accepted the organization invitation:

- **One** team member opens the **group-project template** link on Canvas (this is a
  *different* link from the Lab 01 one), clicks **Use this template**, and sets:
  - **Owner:** `CSCI1030U` (the organization, *not* their own account)
  - **Repository name:** `project-yourteamname`
  - **Visibility:** **Private**
- That member then goes to the new repo's **Settings -> Collaborators and teams** and adds
  **every other team member** with **Write** access.
- Add your TA as a collaborator, if they ask you to.

Everyone then clones the shared repo, just like in Part 1.

### Step 5 - Add your proposal

Copy `PROPOSAL_TEMPLATE.md` into your **group** repo as **`PROPOSAL.md`**, fill it in
together (team, the application, one feature per member, tech plan), and commit and push
it. Practise the workflow: at least a couple of members should make a commit so everyone
is set up and authenticated.

### Step 6 - Agree on how you'll work

You just practised the full workflow - branch, pull request, review, merge - and you'll
grow into it over the term. As a team, agree on how you'll start:

- for now, everyone commits in their **own name**, with **meaningful commit messages**, and
  pushes;
- use **branches** and **pull requests** whenever your team is comfortable - they're the
  **recommended** way to work from Milestone 2 on;
- keep `main` working, and make sure each person's contributions are clear in the history.

---

## How this lab is checked

There's no autograder this week. Your submitted commit hash is read, and your lab
instructor will confirm:

- **Part 1:** your GitHub username is recorded in the quiz, your repository was created
  from the template and its URL and commit hash are submitted, `about_me.md` is filled in
  and pushed, and you opened and merged a pull request (visible under the repo's **Pull
  requests** tab).
- **Part 2:** your team's shared repository exists in the CSCI1030U organization, with a
  completed `PROPOSAL.md`, and you personally have at least one commit in it.

## Getting Help

There is a lab instructor present for the whole session. Ask them whenever you're stuck -
especially with account creation, cloning, pushing, or authentication, which are new to
almost everyone.

## Using AI

You're welcome to ask an AI assistant to **explain** a git idea or what a command does.
But the goal this week is to actually run the workflow yourself and understand it - don't
just paste in commands you can't explain, because you'll be using them all term.
