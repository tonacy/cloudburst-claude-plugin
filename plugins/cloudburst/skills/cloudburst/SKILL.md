---
name: cloudburst
description: Run many model calls in parallel with Cloudburst — dozens to hundreds of distinct variations (ad concepts, names, landing-page headlines, persona reactions, visual directions, hooks, research sweeps), then rank, compare and keep the best. Use when a task benefits from many independent attempts rather than one answer, or when the person asks for Cloudburst.
---

# Cloudburst

Cloudburst runs the wide part of a task: you design the work, it fires many model calls at once on Cloudflare, keeps every result, and shows the person a live view at app.cloudburst.sh.

## When to reach for it

- The person wants **many genuinely different options**: 50 ad concepts, 200 names, 30 landing-page headlines, a panel of 25 personas reacting to an idea, 20 visual directions, a bank of hooks.
- A result is only as good as the best of many attempts, and judging them side by side helps.
- Not for a single answer you can write yourself.

## If the tools are missing

The plugin connects Cloudburst's MCP server. If `list_capabilities` is unavailable, ask the person to run `/mcp`, choose **cloudburst** and approve it in the browser (they sign in with a passkey or an emailed code). Never call the MCP URL with raw HTTP.

## How to run work

1. **Goal first.** `create_goal` with the person's intent (or `read_goal` to continue one).
2. **Plan.** `create_pipeline` with just a `brief` gets a workflow; shape it with `add_step` / `update_step`. Use `assignmentMatrix` or a `modelMix` to keep variations genuinely different.
3. **Price it.** `preview_run` returns planned calls, a projected cost range with a confidence level, and a suggested budget. For a large run, start with a small **pilot** (fewer variations or `stopNodeId` at an early step); later previews of the same plan price themselves from the pilot's real costs.
4. **Ask before spending.** Connecting Cloudburst does not authorize spend. Tell the person the projected range and get an explicit budget before `start_run`. Use a stable `requestId`; recover uncertain starts with `read_run_request`.
5. **Watch and read.** `wait_run` until it settles; `read_run_outputs` (titles view for big batches), `contact_sheet` for images, `rank_outputs` when a judge step scored them.
6. **Keep the best.** `select_top` carries winners into a next round; `continue_run` retries only what failed. Link each run to the goal (`link_goal_run`) and report findings with evidence (`record_goal_note`).
7. **Share the view.** Give the person the `viewUrl` so they can watch results land.

## Rules

- Budgets cap spending; a projection is an estimate, not a quote.
- Human review approvals happen in the Cloudburst app, never by the agent.
- Report the range and how variable each model's spend was, not just the expected cost.
