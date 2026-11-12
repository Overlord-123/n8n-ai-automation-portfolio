# n8n AI Automation Portfolio

Production n8n workflows I designed and built in IT operations: AI agents with tool calling, API integrations, human-in-the-loop approvals, and DNS automation.

> All credentials, internal hostnames, IDs, and company data have been removed or replaced with placeholders (`example.com`, `DEMO_ID`, `<YOUR_TOKEN>`). The workflows are shared to show architecture and logic, not to be run as-is.

## Projects

| # | Project | What it does | Key techniques |
|---|---------|--------------|----------------|
| 1 | [Domain Onboarding](workflows/01-domain-onboarding) | Takes a domain request from Jira and sets it up in Cloudflare | AI agent with MySQL tools, structured output, Slack approval, retry limit, status tracking |
| 2 | [AI Helpdesk Bot](workflows/02-ai-helpdesk-bot) | L1 support agent in Slack; reduced L1 workload by ~40% | User context from Snipe-IT and LDAP, image analysis, escalation with summary, sub-agent |
| 3 | [Mailbox Provisioning](workflows/03-mailbox-provisioning) | Creates a mailbox and stores its password from a Jira request | iRedMail admin API, Team Password Manager API, AI parsing |
| 4 | [Cloudflare DNS Agent](workflows/04-cloudflare-dns-agent) | Planner + executor agents that create DNS records using Confluence as a knowledge base | Two-agent design, Confluence CQL search, Cloudflare API |
| 5 | [Mail Domain Inventory](workflows/05-mail-domain-inventory) | Collects domains from 8 mail servers into one table | Session-based API login, JavaScript parsing, upserts |
| 6 | [Jira AI Digest](workflows/06-jira-ai-digest) | Scheduled summary of my Jira tasks sent to Slack | JQL, filtering in code, AI formatting |

## Stack

n8n · OpenAI (GPT-4o) · Google Gemini · Slack API · Jira and Confluence API · Cloudflare API · MySQL · n8n Data Tables · LDAP · Snipe-IT · iRedMail · Team Password Manager · JavaScript

## Design principles

- **AI decides, code acts.** Agents make decisions and return structured JSON; critical changes (DNS records, zones) are made by deterministic code and direct API calls.
- **Human in the loop** for risky changes: approval forms in Slack before anything is created.
- **Tools instead of longer prompts.** Agents look up data (MySQL, Confluence, Jira) instead of keeping everything in the system prompt.
- **Fail loudly.** Retry limits, explicit stop-and-error nodes, and status tracking for every request.

## How to import

1. In n8n, open **Workflows → Import from File** and select a JSON file.
2. Workflows are imported inactive; nothing runs automatically.
3. Nodes will show missing credentials. Create your own credentials to run them.
4. For multi-workflow projects, re-select the sub-workflows in the **Execute Workflow** nodes.

## What I would improve today

- Keep every secret in n8n credentials (some early versions used tokens directly in HTTP nodes).
- Give nodes descriptive names instead of defaults like `Edit Fields1`.
- Add a final DNS lookup check and Slack alert after records are created.
- Collect baseline metrics before launch, not only after.

## Author

Mykhailo Osypenko · [LinkedIn](https://linkedin.com/in/mykhailo-osypenko) · [GitHub](https://github.com/Overlord-123)
