# Installing your tools (Git and the GitHub CLI)

Before Lab 01 you need two tools on your own computer:

- **Git** (**required**) - the program that tracks your changes. Every lab uses it.
- **GitHub CLI**, `gh` (**recommended**) - a helper that signs you in to GitHub from the
  terminal. It isn't strictly required, but it makes the "`git push` asks for a password"
  snag (see `git-cheatsheet.md`) go away, so install it if you can.

Pick your operating system below. When you're done, jump to
[Check it worked](#check-it-worked) and then [Sign in to GitHub](#sign-in-to-github).

Official download pages, if you'd rather start there:

- Git: <https://git-scm.com/downloads>
- GitHub CLI: <https://cli.github.com/>

---

## Windows 10/11

**Git.** Download **Git for Windows** and run the installer, accepting the defaults. This
also installs **Git Bash**, a terminal you can use for every lab.

- <https://git-scm.com/download/win>

Or, if you prefer the built-in `winget` package manager (Windows 10/11), run in a terminal:

```
winget install --id Git.Git -e
```

**GitHub CLI (`gh`).** Download the Windows installer, or use `winget`:

- <https://cli.github.com/>

```
winget install --id GitHub.cli -e
```

> Prefer clicking to typing? **GitHub Desktop** (<https://desktop.github.com/>) bundles Git
> and handles sign-in for you. You'll still want Git Bash for the command-line steps in the
> lab, but Desktop is a friendly backup.

After installing, **close and reopen** your terminal so it picks up the new tools.

---

## macOS

The easiest path is **Homebrew** (a package manager). Install it once from
<https://brew.sh>, then:

```
brew install git gh
```

Don't want Homebrew? You can get Git on its own by installing Apple's **Command Line
Tools**:

```
xcode-select --install
```

(That gives you Git but not `gh` - use Homebrew, or the installer at
<https://cli.github.com/>, for `gh`.)

---

## Linux (Debian / Ubuntu)

**Git** is one command:

```
sudo apt update
sudo apt install git
```

**GitHub CLI (`gh`)** comes from GitHub's own package repository. Run these lines once (they
add the repository, then install `gh`):

```
sudo mkdir -p -m 755 /etc/apt/keyrings
wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg \
  | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null
sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" \
  | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

If that looks like a lot, the always-current version of these instructions is here, and
your lab instructor can walk you through it:

- <https://github.com/cli/cli/blob/trunk/docs/install_linux.md>

---

## Check it worked

Open a terminal and run:

```
git --version
gh --version
```

Each should print a version number. If a command is "not found", the tool isn't installed
yet (or you need to close and reopen the terminal). Ask your lab instructor if you're
stuck - install problems are common and quick to fix in person.

## Sign in to GitHub

If you installed `gh`, sign in once so pushing to GitHub just works:

```
gh auth login
```

Choose **GitHub.com**, **HTTPS**, and follow the prompts (the browser option is easiest).
This is what prevents the password error described at the bottom of `git-cheatsheet.md`.
