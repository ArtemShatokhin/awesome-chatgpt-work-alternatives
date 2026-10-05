# Self-hosting basics for an open source agent platform

Self-hosting an open source agent platform means you run the control plane, the model keys and the connector credentials on infrastructure you control, and the agent's work reaches your systems only through a gate you set. It is closer to deploying a small service than to installing a desktop app, and four things decide whether it goes well: containers, keys, connectors and review.

For a concrete install of Kortix, the commands are at the end. For the field-wide deployment picture, see [the self-hosting guide](https://chatgptworkalternative.com/self-hosting.html).

## What you are actually running

A self-hosted agent platform runs as a small stack of services. The usual pieces are a database, the web application and API, an agent runtime that plans and calls tools, and a sandbox layer that gives each session a place to execute code and touch files. Some projects add a queue, a scheduler and an object store for artifacts.

Kortix ships the whole thing as one Docker Compose stack: `kortix self-host start` brings up the platform on your own box. Open WebUI, LibreChat and Dify each ship their own Docker Compose deployment, and OpenHands runs an agent server that you can point at Docker, a VM or your own infrastructure. The first decision is where that stack runs: a laptop for evaluation, a VPS for a team, a VPC or an on-prem network for a company with data-residency rules.

## Containers and isolation

The container layer does two jobs. It packages the platform so a deploy is reproducible, and it isolates the agent from everything you did not give it. The second job is the one to get right, because an agent runs code.

An agent platform should boot each session in its own environment rather than letting sessions share one machine. Kortix gives every session an isolated Linux machine with the repository and tools already on it, and runs thousands in parallel with no crossover between them. OpenHands runs each conversation in its own Docker container when you set the runtime to Docker. The rule to hold to: an agent can install, run and break anything inside its own environment, and only what it commits survives.

## Model keys

Model access is the line item people underestimate. A self-hosted platform needs API keys for whichever models it calls, and those keys should be scoped and rotatable rather than pasted into a config file once.

Kortix is model-agnostic: bring a key from Anthropic, OpenAI, Google or your own OpenAI-compatible endpoint, or connect the ChatGPT subscription you already pay for. You choose the model per agent, per session or per message. Open WebUI and LibreChat connect Ollama and any OpenAI-compatible API; Dify supports hundreds of providers; n8n can call OpenAI, Anthropic, Google or open source models. Keep the keys in a secret store, not in the repository, and give each environment its own credentials.

## Connectors and secrets

Connectors are how the agent reaches the rest of the company, and they are where a self-hosted deployment earns its keep or leaks. The design to look for brokers the connector credentials on the server side, so they never enter the agent's machine.

Kortix connects 3,000+ apps plus any MCP, OpenAPI, Postman, GraphQL or raw HTTP API through one scoped token, with credentials brokered server-side and never placed inside the session. It also lets you set each tool call to allow, ask or block, down to the arguments. If you self-host a chat tool such as Open WebUI or LibreChat, the equivalent decision is how its MCP and tool servers are authenticated and who may reach them.

## The review gate

The last piece is what happens to the work. A self-hosted platform that writes straight into production has moved the risk onto your network without giving you a review. The safer pattern is the one developers already use for code: each session works on its own branch, and the result reaches the main branch only through a change request a person reads as a diff.

Kortix works this way, and merge is default-deny for agents. You can start a session from the web, Slack, Teams, email, mobile, the CLI or the API, or from a cron schedule or signed webhook with nobody present, and still review every change before it lands. OpenHands gives coding agents a similar pull-request surface. Set the gate before you give an agent write access to anything that matters.

## Install Kortix

Install the CLI, scaffold a project, then run the stack locally or ship it:

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix ship

# or run everything on your own box: one Docker Compose stack
kortix self-host start
```

`kortix init` creates `kortix.yaml` with your agents, skills and runtime config. `kortix ship` pushes the repository and brings the system live. `kortix self-host start` runs it on your own hardware. The same repository runs on a laptop, a VPS, your VPC or on-prem.

## Operating it

Three habits keep a self-hosted deployment healthy. Back up the database and the git repository that holds the configuration; the repository is the company's real state. Track upstream releases and read the changelog before you upgrade, since agent platforms move quickly. Watch spend per model and per agent, because a long-running agent loop is where an unexpected bill comes from.

If operating that stack is not where your team wants to spend time, Kortix Cloud runs the same platform on managed infrastructure, and the repository moves with you. Kortix is open source (Elastic License 2.0): self-host, read and modify the code.
