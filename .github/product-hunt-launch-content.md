# Product Hunt launch content for `got`

This is the ready-to-use copy and media brief for the November 12, 2026 launch.
Copy is intentionally factual: no vote ask, fabricated benchmark result, or
promise of universal speedup. Recheck release status, Product Hunt field
limits, and the published page preview before scheduling.

## Current verified product facts

Verified October 16, 2026:

- Latest release: `v0.3.0`, published at
  https://github.com/cloudless-ai/got/releases/tag/v0.3.0
- Website: https://getgot.sh
- Source and releases: https://github.com/cloudless-ai/got
- License: MIT.
- macOS Apple Silicon: `brew install cloudless-ai/tap/got`
- Linux x86_64 and ARM64: checksum-verifying installer from the latest release.
- Windows x64 and ARM64: release ZIPs. WinGet is not yet available from the
  community source; do not claim it is installable.
- CLI: `got checkout <remote> [<path>]`, followed by the normal Git workflow.
- GitHub Action: supports a repository-relative `path`; `additional-paths` can
  include shared build files.
- Sparse checkout narrows the working tree. Blob-transfer savings depend on
  server support for Git partial-clone filtering.

Recheck these facts before the November 5 readiness review. Use the current
latest release in links and examples rather than assuming `v0.3.0` will still
be current. The Action example uses the floating major tag `v0`, which the
release process updates for the latest stable v0 release.

## Product Hunt listing

Use a personal Product Hunt account to submit the product. Product Hunt says
makers may post their own product; a separate hunter is not required.

| Field | Prepared value |
|---|---|
| Product name | `got` |
| Product URL | https://getgot.sh |
| Product Hunt listing URL | `PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE` after scheduling; replace this placeholder in launch-day drafts |
| Tagline | **Work on one repo folder. Keep using Git as usual.** |
| Description | **A small CLI and GitHub Action for shallow whole-repo or sparse folder checkouts. Keep normal Git commits and pushes, without learning the low-level setup.** |
| Pricing | Free |
| Availability | Available now |
| Topics | Developer Tools, Open Source, and Git/GitHub if those exact topics are available. Choose only the few closest matches in the live form. |
| Promo | None |
| Product social account | Leave blank unless a dedicated `got` account exists and is verified. |
| Launch time | November 12, 2026, 12:01 AM PST |

The prepared tagline is under the 60-character planning limit and the
description is under Product Hunt's published 260-character description limit.
Verify both against the actual form before scheduling. Product Hunt's help
article says the product name should contain only the product name, not a
description or decorative emoji.

### Maker's first comment

```text
Hi Product Hunt! I'm Jim, the maker of got.

When a task touches one path in a large repository, setting up shallow and sparse checkout by hand can add friction. `got checkout <remote> <path>` creates a shallow checkout focused on that path. Then `got status`, `got add`, `got commit`, and `got push` keep using normal Git behavior. There is also a GitHub Action for path-focused CI checkouts.

The checkout stays a normal Git repository. got is a small wrapper around native Git, not a new commit format. It also does not promise the same download savings everywhere: blob-transfer savings depend on the remote's filter support.

I'd value feedback from developers using large repositories: which files or shared build paths do your real tasks need alongside the directory you're changing?
```

## Demo video

**Title:** `got: focus a Git checkout on one folder`

**Target length:** 35-45 seconds
**Upload:** YouTube; use the full video URL in Product Hunt. Confirm it is not
private before adding it.

| Time | Screen and narration |
|---|---|
| 0-3s | Show the terminal. On-screen title: `One folder. A normal Git repo.` Narration: “When a task only needs one part of a large repository, start with a focused checkout.” |
| 3-13s | Type and run `got checkout https://github.com/llvm/llvm-project.git clang`. Show the actual command output. Do not add a speed claim or timer overlay. |
| 13-20s | Enter the selected path using the destination printed by `got`, then show `got status`. Narration: “The worktree stays in the repository's original paths.” |
| 20-29s | Show a clean terminal card with `got status`, `got add`, `got commit`, and `got push`. Narration: “Use the normal Git workflow after checkout.” Do not fake a successful push or commit output. |
| 29-36s | Show the real Action example from the gallery card. Narration: “The same path-focused checkout is available in GitHub Actions.” |
| 36-42s | End card: `Built on Git. Made for the part you need.` and `https://getgot.sh`. |

Record actual commands and output using a real `got` release. If LLVM is too
large for the recording setup, use a smaller real repository and do not imply
that it demonstrates the LLVM benchmark. Keep terminal text readable and avoid
showing tokens, private paths, or unrelated notifications.

## Image and media checklist

Use the terminal-inspired palette and typography already used by the `got`
site. Use actual screenshots or clean diagrams. No fake UI, fake terminal
output, stock developer photos, or unverified performance numbers.

The first thumbnail draft is `.github/product-hunt-assets/ph-thumbnail.png`;
its editable source is `.github/product-hunt-assets/ph-thumbnail.svg`.

| Filename | Size / format | Exact brief and on-image text | Alt text |
|---|---|---|---|
| `ph-thumbnail.png` | 240x240 square PNG; static | Simple high-contrast `got` wordmark with a small terminal cursor. No tagline, tiny text, or extra badges. | `The got wordmark with a terminal cursor.` |
| `ph-01-hero.png` | 1270x760 PNG | First gallery image. Real terminal crop showing the `got checkout ... clang` command. Overlay: `One folder. A normal Git repo.` Keep command legible; no time or percentage claims. | `Terminal showing got starting a path-focused checkout of the clang directory.` |
| `ph-02-how-it-works.png` | 1270x760 PNG | Three-step diagram: `Choose a repo path` -> `got sets up shallow and sparse checkout` -> `Keep using Git`. Label the middle result `focused working tree`; do not say only selected blobs are transferred. | `Diagram of choosing a repository path, creating a focused working tree, and continuing with Git.` |
| `ph-03-git-workflow.png` | 1270x760 PNG | Actual terminal or clean code card with `got status`, `got add .`, `got commit -m "Update API"`, and `got push`. Do not show a fabricated result or imply automatic staging. | `The got status, add, commit, and push commands shown in a terminal.` |
| `ph-04-github-action.png` | 1270x760 PNG | Readable YAML card: `uses: cloudless-ai/got@v0` and `with: path: apps/api`. Caption: `Path-focused checkout in CI`. Do not hard-code a release version that may be stale. | `GitHub Actions YAML using cloudless-ai/got with the apps/api path.` |
| `got-blog-hero.png` | 16:9 PNG source, 1600x900 or larger | Reuse the terminal/check-out visual language, composed for a blog card. No Product Hunt badge and no speed claim. Keep the central terminal readable in a card crop. | `A terminal showing got checking out a repository path while retaining a normal Git workflow.` |

Product Hunt's current help article recommends a 240x240 square thumbnail and
1270x760 gallery images. It says the gallery needs at least two images before
it is viewable. The four prepared cards exceed that minimum. If the uploader's
current preview crops differently, adjust safe margins without changing the
claims.

## Social copy

These are drafts only. Adapt each for its channel; do not paste the same
announcement everywhere. Use the direct product site link. Do not schedule or
publish through Typefully unless explicitly requested.

### X

```text
Need one path in a large Git repo? `got checkout <remote> <path>` sets up a shallow, sparse checkout. The worktree stays a normal Git repo, so commits and pushes stay familiar. CLI + GitHub Action: https://getgot.sh #Git #OpenSource #DevTools
```

### LinkedIn

```text
Working in a monorepo can mean starting with more history and files than a task needs.

`got checkout <remote> <path>` wraps a shallow, sparse checkout in one command. The worktree stays a normal Git repository, so status, add, commit, and push keep their usual behavior. There is also a GitHub Action for path-focused CI checkouts.

It is a small wrapper around native Git, not a new repository format. Sparse checkout narrows the working tree; transfer savings depend on the remote's support for partial-clone filtering.

Install and examples: https://getgot.sh

#Git #OpenSource #DevTools
```

### Bluesky

```text
One part of a large Git repo, without a new repo format. `got checkout <remote> <path>` sets up a shallow, sparse checkout. Keep using normal Git commits and pushes. CLI + GitHub Action: https://getgot.sh
```

### Launch-day X variation

```text
I'm launching got on Product Hunt today. It wraps shallow, sparse Git checkouts in a small CLI and GitHub Action. The worktree and commits stay standard Git. Try it: PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE
```

### Thank-you post for November 13

```text
Thanks to everyone who tried got and shared how your team works in large Git repositories. The useful feedback is about real workflows, missing paths, installs, and docs. I'm collecting it to decide what to improve next: https://getgot.sh
```

## Blog article draft

**Draft destination:** Cloudless AI blog, pending the maker's publication
approval. This is not scheduled or published.

```toml
+++
title = "A focused checkout is still a real Git repository"
date = "2026-11-12"
description = "How got wraps shallow and sparse checkout for work focused on one part of a large repository."
slug = "focused-git-checkout"
image = "img/blog/got-blog-hero.png"
imageAlt = "A terminal showing got checking out a repository path while retaining a normal Git workflow."
tags = ["Git", "Developer Tools", "Open Source"]
+++
```

### A focused checkout is still a real Git repository

A repository can be large while a task is small. A change in `apps/api`
doesn't always need the repository's full history or every file in its working
tree. Git already has shallow history, sparse checkout, and partial clone. Each
solves a different part of the problem, and the flags are easy to combine
incorrectly.

`got` puts the common setup behind a small command:

```sh
got checkout https://github.com/cloudless-ai/got.git action
cd got-action/action
got status
```

With a path, `got checkout` creates a shallow checkout and focuses the working
tree on that repository path. Without a path, it creates a shallow checkout of
the whole repository. The selected files keep their original repository
paths. The command creates a normal work branch based on the resolved commit.

That distinction matters. A sparse working tree is not a separate repository
format, and it does not mean every unselected object has been removed from the
Git tree. The checkout still represents the original repository. You can
inspect changes and use ordinary Git operations:

```sh
got status
got add .
got commit -m "Update API"
got push
```

Those commands preserve Git's normal staging and commit behavior. `got` does
not stage files automatically, rebase the work, or force-push over another
branch. A commit remains a standard Git commit with the selected base commit
as its parent.

Shallow history and sparse working-tree paths are also different from
transferred bytes. When a remote supports Git partial-clone filtering, the
filter can avoid downloading some blobs until they are needed. When it does
not, `got` can keep the checkout shallow and sparse, but unselected blobs may
still be transferred. That is why a result measured on one repository and
server is not a promise about every checkout.

The same path-focused setup is useful in CI. The GitHub Action accepts a
`path`, plus optional `additional-paths` for shared build files:

```yaml
steps:
  - uses: cloudless-ai/got@v0
    with:
      path: apps/api
```

Use a focused checkout when the task really can work from a subset of the
repository. If a build depends on root configuration, shared tooling,
submodules, or Git LFS, include those requirements or use a full checkout.
Partial clones can also fetch missing objects later when a command needs them.

`got` is a thin interface around existing Git behavior. Its value is making a
common checkout shape easier to request while keeping the repository and
contributor workflow familiar. The right question is not whether every clone
should be sparse. It is whether the task needs the entire repository before it
can start.

Try it with a repository and path you understand, then check the result with
`got status` and your normal build. Installation and Action details are at
https://getgot.sh.
```

Do not add the LLVM numbers from the documentation chart to this post unless
the benchmark environment, commands, repeated-run method, and filter support
are documented and linked. The current chart alone is not sufficient
reproduction detail.

## Prepared FAQ replies

**Is `got` a new Git format?**

No. It uses native Git and creates ordinary Git repositories, branches, and
commits. The CLI passes normal status, add, commit, and push operations through
to Git.

**Does it download only the selected folder?**

The selected path controls the sparse working tree. Whether Git can avoid
transferring unselected blobs depends on the remote's partial-clone filter
support. If filtering is unavailable, `got` keeps the checkout shallow and
sparse and warns that unselected blobs may still be transferred.

**Can I commit and push?**

Yes. `got status`, `got add`, `got commit`, and `got push` preserve the normal
Git workflow. `got` does not silently stage, rebase, or force-push.

**Which platforms are supported?**

Check the latest release before answering. As verified on October 16, 2026,
prebuilt assets are available for macOS Apple Silicon, Linux x86_64/ARM64, and
Windows x64/ARM64. Homebrew and the Linux installer are available. Windows ZIPs
are available; WinGet is still coming soon.

**Is it free?**

Yes. The source is MIT-licensed and the current release is free to install.

## Telegram instruction blocks

The scheduled agent must select the block matching the run date, verify any
time-sensitive facts, and send one message. Preserve the copy exactly unless a
fact has changed. Keep the message below 3,500 characters.

### 2026-10-22: positioning and community preparation

```text
TODAY, OCT 22 | T-21 days: position and prepare

Use this positioning:
Audience: developers and CI maintainers working in large Git repositories.
Problem: a task may need one repository path, while setting up shallow and sparse checkout by hand adds friction.
Promise: `got checkout <remote> <path>` sets up a shallow, path-focused working tree; the repository and commits remain normal Git.
Goal: useful feedback and working installs, not a vote target.

Ready-to-use one-liner:
“Work on one repo folder. Keep using Git as usual.”

Actions:
1. Confirm your personal Product Hunt account can post. Product Hunt allows makers to post their own products; a separate hunter is not required.
2. Identify a few developer communities where a discussion about monorepo checkout workflows is relevant. Read their rules and participate genuinely. Do not ask for votes.
3. Use the prepared listing, maker comment, demo, and image plan in `.github/product-hunt-launch-content.md`. No copy needs to be invented from scratch.
```

### 2026-10-29: listing and media

```text
TODAY, OCT 29 | T-14 days: create and schedule the listing

Copy these Product Hunt fields:
Name: got
URL: https://getgot.sh
Tagline: Work on one repo folder. Keep using Git as usual.
Description: A small CLI and GitHub Action for shallow whole-repo or sparse folder checkouts. Keep normal Git commits and pushes, without learning the low-level setup.
Pricing: Free
Topics: Developer Tools, Open Source, and Git/GitHub if selectable.

Paste the prepared maker's first comment from `.github/product-hunt-launch-content.md`.

Media checklist:
• Thumbnail: 240x240 square.
• Gallery: upload four 1270x760 images; at least two are needed for the gallery to show.
• Demo: upload to YouTube, use the full URL, and confirm it is not private.

Schedule the launch for Nov 12 at 12:01 AM PST from your personal account. Preview every field and replace `PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE` in the content file with the scheduled listing's canonical URL. Do not request votes or add a promo offer.
```

### 2026-11-05: readiness and go/no-go

```text
TODAY, NOV 5 | T-7 days: verify the product and links

Install checks:
macOS Apple Silicon: `brew install cloudless-ai/tap/got`
Linux: `curl -fsSL https://github.com/cloudless-ai/got/releases/latest/download/install.sh | sh`
Windows: use the current x64 or ARM64 ZIP from GitHub Releases. WinGet is coming soon; do not advertise it as available.

Also verify the latest release, `https://getgot.sh`, the Action version in the listing, the YouTube demo, and all gallery assets. Test the Action example using `cloudless-ai/got@v0`.

Do not publish a speedup number unless you can link the repository, environment, commands, repeated-run method, and filter-support conditions. The current site chart does not provide all of those details.

Make a human go/no-go decision. Delay if a critical install, link, or product issue remains.
```

### 2026-11-11: final review

```text
TODAY, NOV 11 | T-1 day: final listing review

Confirm the scheduled page goes live at 12:01 AM PST tomorrow. Check the product URL, tagline, description, topics, pricing, thumbnail, gallery order, and full YouTube URL. Confirm the video is not private.

Keep the prepared first comment ready to paste if needed. Check that the latest release and install links are current. Plan to answer questions as the maker; do not ask for votes.
```

### 2026-11-12: launch day

```text
TODAY, NOV 12 | Launch day

The listing was scheduled for 12:01 AM PST. Open it, confirm it is live, and reply to real questions as the maker. Use the prepared FAQ answers if useful.

Before sharing, replace `PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE` in both launch-day drafts with the scheduled listing's canonical Product Hunt URL. If the placeholder is still present, do not publish that draft.

X draft:
“I'm launching got on Product Hunt today. It wraps shallow, sparse Git checkouts in a small CLI and GitHub Action. The worktree and commits stay standard Git. Try it: PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE”

LinkedIn draft:
“Working in a monorepo can mean starting with more history and files than a task needs.

`got checkout <remote> <path>` wraps a shallow, sparse checkout in one command. The worktree stays a normal Git repository, so status, add, commit, and push keep their usual behavior. There is also a GitHub Action for path-focused CI checkouts.

It is a small wrapper around native Git, not a new repository format. Sparse checkout narrows the working tree; transfer savings depend on the remote's support for partial-clone filtering.

Product Hunt: PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE
Install and examples: https://getgot.sh

#Git #OpenSource #DevTools”

Share only where the post is relevant. Never request or incentivize votes.
```

### 2026-11-13: feedback and follow-up

```text
TODAY, NOV 13 | T+1 day: follow up

Thank people who tried got, answer remaining questions, and capture recurring requests or documentation gaps. Use this thank-you draft:

“Thanks to everyone who tried got and shared how your team works in large Git repositories. The useful feedback is about real workflows, missing paths, installs, and docs. I'm collecting it to decide what to improve next: https://getgot.sh”

Record product feedback separately from votes. Do not promise fixes or dates before they are planned.
```

### 2026-11-19: review and stop

```text
TODAY, NOV 19 | T+7 days: review the launch

Compare the last week with the prelaunch baseline where data is available:
• GitHub release asset downloads.
• Website visits/referrals, if analytics are available.
• Repository traffic/stars, if GitHub exposes the data.
• Useful questions, install problems, and feature requests.

Do not use vote count as the success measure. Write down the strongest feedback themes and choose one practical follow-up.

After saving the review, disable the recurring Product Hunt launch workflow in GitHub Actions. Its Telegram sender suppresses messages outside 2026, but the workflow itself otherwise continues running each year.
```
