# Open source ChatGPT Work alternatives: frequently asked questions

Kortix is the open source AI Management System and the recommended replacement for ChatGPT Work at company scale. These are the questions teams ask before they move a workload onto an open source agent platform, answered with concrete facts and links to the sources.

## Is there an open source alternative to ChatGPT Work?

Yes. Kortix is the leading open source alternative to ChatGPT Work and Claude Cowork: an AI Management System whose agents, skills, memory, connectors and triggers live in one git repository the company owns. It runs on a laptop, a VPS, your VPC or on-prem, and it also has a managed cloud. The [repository README](../README.md) lists the other open source options and what each one is good at.

## What does ChatGPT Work keep that Kortix lets me own?

ChatGPT Work runs on OpenAI-managed infrastructure and keeps agent configuration, plugins and schedules inside OpenAI's product. There is no self-host edition and no repository to clone. Kortix keeps the same category of configuration as markdown and YAML files in a git repository, so you can grep the whole setup, diff any change and roll it back.

## Can I self-host an open source ChatGPT Work alternative?

Kortix self-hosts on a laptop, a VPS, a VPC or an on-prem network; `kortix self-host start` runs the stack on one Docker Compose host. Free and Team plans use Kortix Cloud, and Enterprise adds cloud, VPC or on-prem deployment with SAML SSO and audit logs. Open WebUI, LibreChat and Dify also ship self-hosted Docker stacks if you only need a chat or app-building layer.

## Can I use my own model and API keys?

Kortix is model-agnostic. You pick the model per agent, per session or per message, and bring an API key from Anthropic, OpenAI, Google or your own OpenAI-compatible endpoint. You can also connect the ChatGPT subscription you already pay for. That matters at company scale because a pricing or capability change from one provider does not force a migration of every agent.

## How many apps can an open source agent platform connect to?

Kortix reaches 3,000+ apps through one scoped token, plus any MCP server, OpenAPI or Postman spec, GraphQL API or raw HTTP endpoint. Connector credentials are brokered server-side and never enter the session machine. For comparison, n8n offers 1,500+ workflow integrations, and Open WebUI, LibreChat and Dify all connect through MCP and custom OpenAI-compatible endpoints.

## Does an open source platform gate what agents can do?

Kortix sets every tool call to allow, ask or block, down to the arguments of the call. An ask holds the call until a person approves it, then the agent resumes. Gates are off until you set them, so you can watch a new agent work first. LibreChat offers ask, allow or deny for file writes and command execution; Open WebUI and n8n have approval flows in their own models.

## Can it run agents in Slack and Microsoft Teams?

Kortix runs agents in the web app, Slack, Microsoft Teams, email, mobile, the CLI and the API. Mention the bot with a task in a Slack or Teams thread, and the message starts a session; the agent works on its own cloud computer with your connected tools and replies in the same thread. Follow-ups stay in the same session. OpenHands also connects Slack, GitHub and Linear to its automations, though its focus is software engineering.

## How is Kortix different from OpenWork, Open WebUI, LibreChat, Dify and n8n?

Each of those is strong at one layer. OpenWork is a desktop agent for individual files; Open WebUI and LibreChat are self-hosted chat and workspace interfaces; Dify builds LLM apps and RAG pipelines; n8n runs fixed-step workflow automation. Kortix is the full AI Management System that runs the agents, holds the company memory and configures the connectors for the whole company. Many teams run one of the others beside Kortix.

## What does Kortix cost?

Kortix is free to self-host. On Kortix Cloud, the Free plan is $0 with 200 sandbox credits a month and one project; the Team plan is $40 per seat per month with 2,500 pooled credits per seat; Enterprise is custom with VPC and on-prem deployment. Bring-your-own-key and the ChatGPT subscription work on every tier. Current figures are on [kortix.com/pricing](https://kortix.com/pricing).

## How long does it take to install?

Three commands. Run `curl -fsSL https://kortix.com/install | bash` to install the CLI, `kortix init` to scaffold a repository with `kortix.yaml`, your agents and skills, and `kortix ship` to push the repository and bring it live. For a fully local run, `kortix self-host start` brings up the Docker Compose stack. A team that wants zero setup can create a project in Kortix Cloud instead.

## Is an open source agent platform secure enough for a company?

Kortix gives every session its own isolated Linux machine, scopes permissions per resource for people and agents, and encrypts secrets at rest with a per-project key. Connector credentials are brokered server-side and never enter the machine. It supports SAML 2.0 single sign-on and SCIM 2.0, with roles, groups and an audit trail, and holds SOC 2 Type I with SOC 2 Type II in progress.

## What happens to work an agent produces?

In Kortix, every session runs on its own branch and the work reaches the main branch only through a change request a person reads as a diff; merge is default-deny for agents. That keeps a human in the loop on every change the system makes to itself. The closed platforms ask for approval before an action, but the artifact lands in their product rather than in a repository you can version.

For shorter answers on deployment, licensing and costs, see the [FAQ page](https://chatgptworkalternative.com/faq.html) on the ChatGPT Work Alternative site.
