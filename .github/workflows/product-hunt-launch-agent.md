---
on:
  schedule:
    - cron: "0 9 22 10 *"
      timezone: "America/Los_Angeles"
    - cron: "0 9 29 10 *"
      timezone: "America/Los_Angeles"
    - cron: "0 9 5 11 *"
      timezone: "America/Los_Angeles"
    - cron: "0 9 11 11 *"
      timezone: "America/Los_Angeles"
    - cron: "0 9 12 11 *"
      timezone: "America/Los_Angeles"
    - cron: "0 9 13 11 *"
      timezone: "America/Los_Angeles"
    - cron: "0 9 19 11 *"
      timezone: "America/Los_Angeles"

permissions:
  contents: read
  issues: read
  pull-requests: read
  actions: read

engine:
  id: copilot
  model: gpt-6-luna

tools:
  github:
    toolsets: [repos, issues, pull_requests, actions]
safe-outputs:
  jobs:
    telegram-notify:
      description: "Send one approved milestone reminder to the launch owner's Telegram chat"
      runs-on: ubuntu-24.04
      output: "The Product Hunt milestone reminder was sent to Telegram."
      inputs:
        message:
          description: "A concise reminder with the milestone and next actions"
          required: true
          type: string
      steps:
        - name: Send one Telegram notification
          env:
            TELEGRAM_BOT_TOKEN: "${{ secrets.TELEGRAM_BOT_TOKEN }}"
            TELEGRAM_CHAT_ID: "${{ secrets.TELEGRAM_CHAT_ID }}"
          run: |
            node <<'NODE'
            const fs = require("node:fs");

            const token = process.env.TELEGRAM_BOT_TOKEN;
            const chatId = process.env.TELEGRAM_CHAT_ID;
            const outputPath = process.env.GH_AW_AGENT_OUTPUT;

            if (new Date().getUTCFullYear() !== 2026) {
              console.log("Outside the 2026 launch window; no Telegram message sent.");
              process.exit(0);
            }

            if (!token || !chatId || !outputPath) {
              throw new Error(
                "Telegram secrets or agent output are missing; configure TELEGRAM_BOT_TOKEN and TELEGRAM_CHAT_ID.",
              );
            }

            const output = JSON.parse(fs.readFileSync(outputPath, "utf8"));
            const messages = output.items.filter(
              (item) => item.type === "telegram_notify",
            );
            if (
              messages.length !== 1 ||
              typeof messages[0].message !== "string" ||
              !messages[0].message.trim() ||
              messages[0].message.length > 3500
            ) {
              throw new Error(
                "Expected exactly one non-empty Telegram message of at most 3500 characters.",
              );
            }

            async function sendMessage() {
              let response;
              try {
                response = await fetch(
                  `https://api.telegram.org/bot${token}/sendMessage`,
                  {
                    method: "POST",
                    headers: { "content-type": "application/json" },
                    body: JSON.stringify({
                      chat_id: chatId,
                      text: messages[0].message,
                    }),
                  },
                );
              } catch {
                throw new Error("Could not connect to the Telegram Bot API.");
              }

              let result;
              try {
                result = await response.json();
              } catch {
                throw new Error("Telegram returned an unreadable response.");
              }

              if (!response.ok || result.ok !== true) {
                throw new Error(
                  `Telegram rejected the message (HTTP ${response.status}${result.description ? `: ${result.description}` : ""}).`,
                );
              }
            }

            sendMessage()
              .then(() => console.log("Telegram milestone reminder sent."))
              .catch((error) => {
                console.error(error.message);
                process.exitCode = 1;
              });
            NODE
---

# Product Hunt launch workback agent

Use `.github/product-hunt-launch-plan.md` as the source of truth for the
November 12, 2026 Product Hunt launch and its milestone schedule. Use
`.github/product-hunt-launch-content.md` for the approved copy, image briefs,
FAQ answers, and complete Telegram message blocks.

On a scheduled run:

1. Use the scheduled date in `America/Los_Angeles`. Confirm it is one of the
   seven 2026 milestone dates in the plan. If it is not, call `noop` and do not
   send a message.
2. Find the matching dated Telegram block in
   `.github/product-hunt-launch-content.md`. Treat that block as the approved
   message, not a prompt to invent a new campaign. Preserve its copy and
   sequence. The only permitted edits are to remove Markdown code fences and
   replace a stale fact with a currently verified fact.
3. Verify time-sensitive claims relevant to that block against repository
   files and GitHub release data. Check the latest release/assets and current
   install or Action details when the block asks for them. If a fact changed,
   state the verified correction briefly in the Telegram message and update
   only the affected sentence. Do not infer completed maker actions: ask the
   maker to confirm them when repository evidence cannot establish completion.
4. On October 29, remind the maker to replace
   `PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE` in the content file after scheduling
   the listing. On November 12, do not include or endorse launch-day social
   drafts while that placeholder remains; tell the maker to insert the
   canonical Product Hunt URL first.
5. On November 19, retain the instruction to disable this workflow after the
   review. Do not change or disable it yourself.
6. Call `telegram-notify` exactly once with the matching block and any
   necessary verified correction. Keep the complete message below 3,500
   characters. Never call Telegram directly or attempt to access its
   credentials.

Safety and scope:

- This is a read-only launch assistant. Do not edit repository files, create
  issues or pull requests, or change release settings.
- Do not submit or publish the Product Hunt page, post on social media, or
  message communities. Those actions require the maker.
- Never ask for, offer incentives for, or coordinate Product Hunt votes.
- Do not claim benchmark results without linking them to their conditions and
  reproduction details.
- Only use the Telegram safe output for the milestone reminder. Do not send
  additional messages.
- Never send launch-day social copy containing
  `PASTE_CANONICAL_PRODUCT_HUNT_URL_HERE`.
- After the November 19 report, remind the maker to disable this scheduled
  workflow. The schedule recurs annually; the Telegram sender suppresses
  messages outside 2026, but disabling the workflow prevents unnecessary
  agent runs.

{{#runtime-import .github/product-hunt-launch-content.md}}
