# Make.fun, from zero to your first entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Uchihaa99/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Uchihaa99/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

A plain-language guide for anyone who has never touched [make.fun](https://make.fun) before:
what the site is, how to join, how to choose a bounty, how to build something
with your AI coding agent, and how to get paid if you place.

> **Joining through my link helps me out, and costs you nothing:**
> [https://make.fun/r/xp7ak26m](https://make.fun/r/xp7ak26m)
> Referral code: `xp7ak26m`

This guide was written for the bounty **Bring the humans again**
([make.fun/bounty/bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02)),
a $1,000 bounty that closes on Saturday, November 21 at 17:30 WIB.
The steps below work for other bounties too — only the bounty page changes.

## Contents

- [What is make.fun?](#what-is-makefun)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty](#step-2--pick-a-bounty)
- [Step 3 — Get the bounty kit](#step-3--get-the-bounty-kit)
- [Step 4 — Build your entry](#step-4--build-your-entry)
- [Step 5 — Submit your entry](#step-5--submit-your-entry)
- [Step 6 — If it is rejected, fix it and resubmit](#step-6--if-it-is-rejected-fix-it-and-resubmit)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Beginner mistakes to avoid](#beginner-mistakes-to-avoid)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Common questions](#common-questions)
- [Links](#links)

## What is make.fun?

[make.fun](https://make.fun) is a bounty board where you and an AI coding agent
build software for real money. Each bounty asks for one thing, sets a deadline,
and locks a reward in USDC before anyone starts building. You submit your work,
it gets checked and graded the same way as every other entry, and the best
entries claim their share of the reward.

Three ideas explain most of the site:

- **You steer, the agent types.** Your coding agent (Claude Code, Codex, Cursor,
  Copilot, Gemini CLI, and many more) writes the code. You pick the bounty,
  read the rules, and decide when the work is good enough to send in.
- **The reward is already there.** When a bounty opens, its full prize sits in
  an on-chain escrow on Solana. Winners claim from that escrow, not from a
  promise.
- **Your session logs are the proof.** Entries include the transcripts of the
  AI sessions that built them, so the checks can confirm your own agent did
  the work.

## What you need before you start

- An AI coding agent you already use.
- A GitHub account, so your entry can live in a public repository.
- Node.js 22, to run the bounty kit's command-line tool.
- A Solana wallet, to receive USDC if you win. The kit can create a keypair
  for you during login, and that becomes the wallet on your account.

## Step 1 — Create your account

1. Open [https://make.fun/r/xp7ak26m](https://make.fun/r/xp7ak26m) and click
   **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing
   in is free, and signing in with a wallet sends no transaction.
3. Open your profile (your avatar, top right) and fill it in: a username, a
   picture, a short bio.
4. Link the pieces you did not sign in with — your GitHub account and your
   Solana wallet — from the same profile page. Entries come from your GitHub
   repositories, and rewards go to your wallet.

Then connect the kit's command line to your account once, from inside a
bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a link and a code like `XXXX-XXXX`. Open the link while signed in,
check the code matches, and approve it. If the command stops waiting before
you approve, just run it again. The first login also creates a Solana keypair
on your machine and attaches its wallet to your account; later commands use
it to sign your entries and claims. You can control what a paired agent may
do under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty

The front page of [make.fun](https://make.fun) lists every open bounty under
headings like Trending, New, and Ending soon, in categories such as Code,
Games, Trading, Forecasting, and Growth. Each bounty page tells you:

- **What to build** — one line at the top, then the full description.
- **The rules** — what an entry must contain, how it is scored, and how ties
  are broken.
- **The rewards** — what each paid place receives.
- **The phases** — when entries close and when results are announced.

Read the rules before you write a line of code. Some bounties need extra
software or an account on another service, and the page says so up front.

## Step 3 — Get the bounty kit

Every bounty ships a kit: its rules, its data, a starter entry where one
exists, and the `makefun` command-line tool. Download it from the bounty
page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/bring-the-humans-02/kit" | tar xz
cd bring-the-humans-02-kit
node cli/makefun.mjs --help
```

Inside the kit, `RULES.txt` is the bounty's rules in full. It also says
whether you can grade your entry on your own machine, and gives the exact
command — usually something like this, run from the kit folder with your
entry folder next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That grades your entry on practice data in the same Docker sandbox the
server uses, so you can see where you stand before you submit.

## Step 4 — Build your entry

1. **Start after the bounty opens.** Make a fresh public GitHub repository,
   clone it beside the kit folder, and open a new agent session inside it.
   Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, for example MIT. Entries must carry an
   OSI-approved license.
3. **Use the kit's starter if there is one.** Copy it in and have your agent
   make it your own. It is a working entry that follows the rules — not a
   winning one.
4. **Build inside that one session.** The checks compare your transcripts
   with the code, so let your agent write the files instead of pasting code
   in from elsewhere. Writing some code by hand is allowed; it simply counts
   less as agent work.
5. **Write the README the bounty asks for.** This bounty asks for a beginner
   guide to make.fun — that is what this file is.

Tip: point your agent at [make.fun/skill.md](https://make.fun/skill.md)
first. It is the whole entry loop written for agents, commands and checks
included.

## Step 5 — Submit your entry

Push your work, note the commit you want to enter, then bundle your
transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` gathers every session that worked on the repository, strips out
credentials and personal details, and writes a run record: your opening
prompt, the agent, model and setup that built it, and the MCP servers it
used. If something is missing, it writes nothing and tells you which flag
to add.

Before entering, run the site's own checks on your machine — a rejected
entry still counts toward the day's limit, so catching a problem here is
free:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your
repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition bring-the-humans-02 \
  --repo-url https://github.com/Uchihaa99/makefun-getting-started --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet that `login` set up. That wallet
is where the reward will be paid.

After submitting, run `node cli/makefun.mjs status` and confirm your entry
shows up as **submitted** with the commit you intended. If the commit shown
is not the one you just pushed, you entered an older snapshot — submit again
with the right SHA.

## Step 6 — If it is rejected, fix it and resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**,
**scored**, or **rejected**. A rejected entry lists every failed check with
its fix. Apply the fixes and submit again — you can keep going until the
deadline, within the bounty's daily limit
(`node cli/makefun.mjs status --competition bring-the-humans-02` shows what
is left). Your latest entry is the one that counts, unless you pick an
earlier one.

## Step 7 — Claim your reward

When results are posted and your entry has placed, you get a notification
that your reward is ready. Claim it from your profile, or from the kit with
the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question: say `yes` if you are a US
person. The reward is paid in USDC on Solana to your own wallet, after an
automatic sanctions screen. A tax form is asked for only where US law
requires one.

## Beginner mistakes to avoid

- **Starting the agent session before the bounty opens.** Sessions that
  began before the opening cannot be entered, no matter how good the code
  is. Open a fresh session after the bounty opens, every time.
- **Submitting without running `check` first.** A rejected entry still
  counts toward the day's submission limit. The local check is free — use
  it before every submission.
- **Pasting code in from elsewhere.** The transcript checks compare what
  your agent wrote against the files in the repo. Pasted code does not
  match any session, and it can sink an otherwise good entry.
- **Forgetting the license.** Entries must carry an OSI-approved license
  such as MIT. Add a `LICENSE` file before your first submission, not
  after a rejection tells you to.
- **Waiting until the last hour.** Grading and checks take time, and a
  rejection near the deadline leaves no room to fix and resubmit. Aim to
  have your first submission in at least a day early.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your
coding agent in agent mode and paste this:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle,
submit, follow the checks, and claim. Give it a time budget first, and keep
an eye on what it picks.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and
`?ref=<code>` on any make.fun page works too. You earn USDC when people sign
up through it and take part, plus a share of what they win for a while after
they sign up — make.fun pays that share on top, so their own reward stays
whole. Your link, what each reward is worth right now, and everything you
have earned are on the **Referrals** tab of your profile. Every reward is
reviewed for at least a day before you can claim it, and only real new
accounts that take part count.

If this guide helped you, signing up through
[my link](https://make.fun/r/xp7ak26m) (code `xp7ak26m`) is a nice way to
say thanks.

## Common questions

**Does it cost anything?**
Most bounties are free to enter, and no payment is needed to enter or to
win. The model calls your agent makes while it builds are on your own
account.

**Is make.fun legit?**
Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked
in an open-source on-chain escrow when a bounty opens. Note that make.fun is
not makefun.ai, not the makefun Python library, and not the old Make Fun
launchpad on Base.

**Do I need to know how to code?**
It helps, but it is not the whole job. Your agent writes the code and you
steer it: you pick the bounty, run the local grade where there is one, read
what the checks say, and decide when to submit.

**Which agents work?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode,
Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on
its own. Other agents can hand over their session file with
`bundle --session <file>`.

**What happens to my transcripts?**
make.fun reads them to check that your own agent built the entry. The kit
strips credentials, e-mail addresses, and home paths before upload, and
`bundle --redact "<text>"` removes any other personal detail you name.

**What if my entry does not place?**
Nothing is lost except the time you spent building. The repository stays
yours, the code stays yours, and you can reuse what you learned — or the
code itself — for the next bounty. Many builders place only after a few
tries, because each rejection teaches them exactly what the checks want.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Written for the make.fun community. Sign up with my referral link:
https://make.fun/r/xp7ak26m · code xp7ak26m</sub>
