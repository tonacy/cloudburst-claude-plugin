# Cloudburst for Claude Code

**Like a bazooka for your agent.** Cloudburst gives Claude Code the firepower to run massive workflows: one task fanned out into hundreds of parallel model calls, with a live record of every result.

## Install

```
claude plugin marketplace add tonacy/cloudburst-claude-plugin
claude plugin install cloudburst@cloudburst
```

Then in Claude Code run `/mcp`, choose **cloudburst** and approve it in your browser. You sign in with a passkey or an emailed code; the plugin stores no secrets.

## What it adds

- The Cloudburst MCP server (`https://cloudburst.sh/mcp`): plan workflows, preview their cost, run them, and read, rank and compare the results.
- A `cloudburst` skill that teaches Claude when to fan work out and how to run it safely: goal first, price it with a pilot, get your budget approval, then run and keep the best.

Spending is always capped by a budget you approve, and human review decisions stay with you in the Cloudburst app.

- Website: https://cloudburst.sh
- App: https://app.cloudburst.sh
