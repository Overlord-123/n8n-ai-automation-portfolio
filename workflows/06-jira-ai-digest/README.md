# Jira AI Digest

A scheduled summary of my open Jira tasks, sent to Slack.

```mermaid
flowchart LR
    A[Schedule] --> B[Jira JQL<br/>my open issues]
    B --> C[Filter + format<br/>in JavaScript]
    C --> D[AI agent formats digest<br/>Jira tool for details]
    D --> E[Slack message]
```

## How it works

On a schedule, the workflow gets my open issues with JQL, skips service tasks, and builds a text block with deadlines, estimates, and comments. An AI agent formats it into a readable digest and can call a Jira tool when it needs more details. The result is sent to Slack.

## Files

- `jira-ai-digest.json`
