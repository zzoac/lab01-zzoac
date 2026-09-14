# Git cheat sheet

The handful of commands you'll use over and over this term. Run them in a terminal, from
inside your cloned repository folder.

## Everyday workflow

| Command | What it does |
|---------|--------------|
| `git clone <url>` | Download a copy of a GitHub repository to your computer |
| `git status` | Show what has changed and what is staged |
| `git add <file>` | Stage a file's changes for the next commit (`git add -A` for all) |
| `git commit -m "message"` | Save a snapshot of the staged changes, with a message |
| `git push` | Upload your commits to GitHub |
| `git pull` | Download and merge the latest commits from GitHub |
| `git log --oneline` | See the history of commits |
| `git rev-parse HEAD` | Print the full hash of your latest commit (this is what you submit) |

## Branches and pull requests

| Command | What it does |
|---------|--------------|
| `git switch -c <branch>` | Create a new branch and switch to it |
| `git switch <branch>` | Switch to an existing branch (e.g. `git switch main`) |
| `git push -u origin <branch>` | Push a new branch to GitHub for the first time |

To open a **pull request (PR)**, push your branch and then use the **GitHub website**:
open the repo, click *Compare & pull request*, review the changes, and *Merge*.

## Handing in a lab

Every lab is submitted through its **Canvas quiz**, by giving two things:

| Command | What it does |
|---------|--------------|
| `git status` | Check it's all committed and pushed *before* you read the hash |
| `git rev-parse HEAD` | Print the commit hash to paste into the quiz |

Get onto `main` and up to date first (`git switch main`, then `git pull`), so the hash you
submit includes everything - including anything you merged through a pull request.

## Writing a good commit message

- Say what the commit *does*: `"Add score-keeping to the game loop"`, not `"stuff"`.
- One commit = one logical change. Small, frequent commits are easier to review.

## If `git push` asks for a password

GitHub no longer accepts your account password on the command line. Either:

- run `gh auth login` (the GitHub CLI) once, or
- create a **Personal Access Token** on GitHub and use it in place of the password, or
- use the **GitHub Desktop** app.

Ask your lab instructor if you get stuck here - it's the most common first-time snag.
