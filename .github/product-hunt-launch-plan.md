# Product Hunt launch workback

- **Launch date:** Thursday, November 12, 2026
- **Launch time:** 12:01 AM Pacific
- **Reminder time:** 9:00 AM America/Los_Angeles on milestone dates

The Product Hunt page is published by a person. The agent prepares and checks
the work, then sends one concise Telegram reminder on each milestone date. It
does not publish, solicit votes, or post on social media.

## Workback schedule

| Date | Milestone | Work to complete |
|---|---|---|
| October 15 | Start now | Decide the primary audience, the problem statement, and what success means. Check the Product Hunt maker profile and begin participating authentically. |
| October 22 | T-21 days | Finalize the positioning and one-sentence value proposition. Identify relevant communities and people who can give honest product feedback; do not ask for votes. |
| October 29 | T-14 days | Draft the Product Hunt tagline (60 characters max), description (260 characters max), maker comment, and launch-page links. Record a short terminal demo and prepare gallery assets. |
| November 5 | T-7 days | Check release readiness: test the advertised install paths, verify release assets and documentation, and validate the benchmark conditions. Make a human go/no-go decision; delay if a critical install or product issue remains. |
| November 11 | T-1 day | Review the scheduled listing, demo, screenshots, links, maker comment, and support plan. Confirm the product is available before launch. |
| November 12 | Launch day | The maker publishes/monitors the launch and replies to comments. Share organically with existing developer communities; never request or incentivize upvotes. |
| November 13 | T+1 day | Review questions and feedback, thank participants, and capture follow-up issues or documentation improvements. |
| November 19 | T+7 days | Review release downloads, repository and site traffic, useful feedback, and next steps. Disable the scheduled agent after this final report. |

## Readiness notes

- `got` is a developer CLI and GitHub Action; the launch should demonstrate a
  real large-repository checkout and normal Git usage.
- Use the LLVM benchmark only with its conditions and reproduction steps
  available. Do not imply every repository or server gets the same savings.
- Check current release and package status at each readiness review. The
  Homebrew install is available; Windows WinGet availability and other package
  statuses must be verified rather than assumed.
- Treat Product Hunt as a feedback and discovery channel. Track practical
  signals such as release downloads, repository/site traffic, and useful
  feedback rather than a target vote count.
- The GitHub schedule recurs annually. The sender suppresses Telegram messages
  outside 2026, but disable the workflow after November 19 to prevent future
  agent runs.
- The milestone schedule is encoded in
  `.github/workflows/product-hunt-launch-agent.md`. Update both locations if
  the launch date or reminder dates change.
