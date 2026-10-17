# Product Hunt launch workback

**Launch:** Thursday, November 12, 2026, at 12:01 AM Pacific
**Telegram reminders:** 9:00 AM America/Los_Angeles on the milestone dates

The copy, media briefs, FAQs, and ready-to-send Telegram instructions are in
`.github/product-hunt-launch-content.md`. Treat that file as the approved
campaign package. The scheduled agent checks current repository facts, selects
the matching instruction block, and sends it in one Telegram message. It does
not edit files, create posts, publish, schedule, or contact communities.

## Workback schedule

| Date | Milestone | Complete when |
|---|---|---|
| October 15-21 | Start now | Use the prepared audience, positioning, and success measures. Confirm the personal Product Hunt account can post. Begin genuine participation in relevant developer communities without soliciting votes. |
| October 22 | T-21 days | Use the prepared positioning and one-line value proposition. Identify a small set of relevant communities and check their posting rules. |
| October 29 | T-14 days | Create the Product Hunt listing draft from the exact fields in the content package. Add the thumbnail and at least two gallery images, upload the demo to YouTube, and schedule the listing for November 12 at 12:01 AM PST. Save its canonical Product Hunt URL in the content package. |
| November 5 | T-7 days | Test current installation paths and the Action example. Confirm release and website details. Review every factual claim and image. Make a human go/no-go decision; delay if a critical install or product issue remains. |
| November 11 | T-1 day | Preview the scheduled listing, confirm the launch time, links, gallery order, YouTube visibility, maker comment, and prepared replies. |
| November 12 | Launch day | Check the live listing, answer comments as the maker, and share the prepared channel-specific copy where it is relevant. Do not ask for votes. |
| November 13 | T+1 day | Thank participants, answer remaining questions, and record useful feedback and follow-up issues. |
| November 19 | T+7 days | Compare release downloads, available site/repository traffic, and useful feedback with the prelaunch baseline. Choose follow-up work and disable the scheduled workflow. |

## Content and media

- Use the exact Product Hunt fields, first comment, channel-specific social
  drafts, blog draft, FAQ answers, image specifications, and Telegram message
  blocks in `.github/product-hunt-launch-content.md`.
- Product Hunt's current help article recommends a 240x240 square thumbnail and
  1270x760 gallery images, requires at least two gallery images for the gallery
  to be viewable, and accepts YouTube videos by full URL only. The video must
  not be private. Check the live submission form before export in case its
  requirements change:
  https://help.producthunt.com/en/articles/479557-how-to-post-a-product
- The blog draft is prepared in the Cloudless AI Hugo front-matter format as a
  draft only. Do not publish it or create Typefully drafts without the maker's
  request.
- Match the existing terminal-inspired site look. Use real product screenshots
  and verified terminal output; do not fabricate timings, download sizes, or UI.

## Verified facts and guardrails

- As checked on October 16, 2026, `v0.3.0` is the latest published GitHub
  release. Current assets include a macOS ARM64 Homebrew package, Linux
  x86_64/ARM64 installers, and Windows x64/ARM64 ZIPs. WinGet manifests are
  attached to the release, but package documentation still says WinGet is
  coming soon. Recheck before launch; do not claim WinGet installation is live
  until accepted in its community source.
- `got` is a CLI and GitHub Action built on native Git. Its commits and
  repositories remain standard Git. Sparse checkout narrows the working tree;
  reduced blob transfer depends on the remote's partial-clone filter support.
- The site currently displays LLVM checkout and disk-use measurements without
  complete reproduction conditions alongside them. Leave numerical benchmark
  claims out of public launch copy unless the conditions and reproduction steps
  are verified and linked.
- Product Hunt permits makers to post their own products from a personal
  account. Use the prepared feedback-oriented copy; do not solicit, reward, or
  coordinate votes.
- Success means useful feedback, working installs, and evidence about discovery
  and adoption. Do not set a vote-count target.
- The schedule recurs annually. The sender suppresses Telegram messages
  outside 2026, but the workflow itself must be disabled after November 19 to
  stop future agent runs.

Product Hunt guidance:

- https://www.producthunt.com/launch
- https://help.producthunt.com/en/articles/479557-how-to-post-a-product
- https://help.producthunt.com/en/articles/479581-can-i-post-my-own-product-on-product-hunt
- https://help.producthunt.com/en/articles/484935-can-i-ask-my-community-friends-family-to-upvote-a-product

Keep this file, `.github/product-hunt-launch-content.md`, and the schedule in
`.github/workflows/product-hunt-launch-agent.md` synchronized if dates or
decisions change.
