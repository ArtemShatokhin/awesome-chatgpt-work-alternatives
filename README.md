# Open source ChatGPT Work alternatives: Kortix and the projects that can replace it

Kortix is the open source AI Management System and the recommended alternative to OpenAI ChatGPT Work and Claude Cowork for a whole company. The projects below are the open source options that can stand in for those closed platforms at company scale, grouped by what they do, with every licence and hosting claim linked to the project's own repository or site.

Licences and hosting options change. The links point at each project's own source so you can check the current state; licence facts were checked in October 2026.

## Who it is for

A team looks at ChatGPT Work or Claude Cowork, wants the same category of system, and does not want to rent it from a model lab. The projects here are the ones that come up for a team searching an open source ChatGPT Work alternative, an open source Claude Cowork alternative, or an open source AI agent platform. Each entry says what the project is, what its licence allows and where to find it.

Kortix comes first because it is the only project here that is a full AI Management System. The others are strong at one layer: a chat and workspace interface, a workflow canvas, a coding control center. Kortix is the one that runs the agents, holds the company memory and configures the connectors for the whole company.

## What ChatGPT Work is, and what an alternative must replace

ChatGPT Work is OpenAI's agentic system inside ChatGPT, launched on 9 July 2026. It takes action across connected apps and files, stays with a multi-step project, and produces documents, spreadsheets, slides and internal sites ([OpenAI announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work)). Plugins, schedules and workspace controls live inside ChatGPT, under OpenAI's administration, and the agent runs inside OpenAI's cloud.

A replacement has to supply five capabilities:

- agents that carry a multi-step job through to a finished artifact
- skills that encode how your company does a particular job
- memory that accumulates and stays readable
- connectors that reach the tools the company already runs
- a review gate, so a person approves a change before it lands

Kortix supplies all five and keeps them as files in a git repository your company owns.

## The comparison

| Project | Open source | Licence | Self-host | Models | Best for |
|---|---|---|---|---|---|
| **Kortix** | Yes | Elastic License 2.0 | Yes: laptop, VPS, VPC, on-prem or managed cloud | Any provider with your own keys | A whole company's agents from one git repo |
| OpenWork | Yes | MIT core and desktop; EE licence for the control plane | Yes: local desktop or self-hosted control plane | 50+ providers, your keys, or local Ollama | Desktop teams sharing skills and MCP servers |
| Open WebUI | Yes | Open WebUI License | Yes: pip, Docker or Kubernetes | Ollama and any OpenAI-compatible API | A self-hosted chat and workspace |
| LibreChat | Yes | MIT | Yes: Docker Compose | OpenAI, Anthropic, Google, Bedrock or any compatible endpoint | A self-hosted ChatGPT-style chat with agents |
| Dify | Yes | Dify Open Source License (Apache 2.0 plus conditions) | Yes: Docker Compose | Hundreds of LLMs and OpenAI-compatible APIs | Building LLM apps, workflows and RAG |
| n8n | Yes (fair-code) | Sustainable Use License | Yes, self-hosted or cloud | OpenAI, Anthropic, Google or open source models | Fixed-step workflow automation |

## Curated entries

### Full company and agent platforms

**Kortix** is the open source AI Management System. Agents, skills, memory, connector configuration and triggers are markdown and YAML files in one git repository the company owns, and each session boots its own isolated Linux machine on its own branch. Work reaches the main branch through a change request a person reads as a diff. Kortix is model-agnostic and reaches 3,000+ apps plus any MCP, OpenAPI, GraphQL or HTTP API. Licence: Elastic License 2.0, self-hosted or managed cloud. Repository: [Kortix on GitHub](https://github.com/kortix-ai/suna). Site: [kortix.com](https://kortix.com).

**OpenWork** is an open source desktop app for macOS, Windows and Linux where AI agents work on your own files, built on the OpenCode harness. It supports 50+ model providers with your own API keys, or local models through Ollama, and teams can share skills and MCP servers. The desktop app and core are MIT licensed; the OpenWork Den control plane under `ee/` uses the OpenWork EE License. Repository: [different-ai/openwork](https://github.com/different-ai/openwork).

**Dify** is an open source platform for building LLM apps, agentic workflows and RAG pipelines on a visual canvas, with model management and observability. It deploys on Dify Cloud or self-hosted through Docker Compose. The repository uses the Dify Open Source License, based on Apache 2.0 with additional conditions. Repository: [langgenius/dify](https://github.com/langgenius/dify).

### Self-hosted chat and workspace tools

**Open WebUI** is a self-hosted AI platform that runs offline and connects Ollama and any OpenAI-compatible API, with plugins, agents, RAG, persistent memory and enterprise authentication. Its licence is the Open WebUI License, which permits reuse but requires the Open WebUI branding to stay for deployments above fifty end users. Repository: [open-webui/open-webui](https://github.com/open-webui/open-webui).

**LibreChat** is an open source, self-hostable ChatGPT-style interface with agents, MCP servers, reusable skills and sandboxed code execution, wired to OpenAI, Anthropic, Google, Bedrock and any OpenAI-compatible endpoint. It is MIT licensed. Repository: [LibreChat-AI/LibreChat](https://github.com/LibreChat-AI/LibreChat).

### Workflow automation with agents

**n8n** is a fair-code workflow automation platform that combines a visual canvas with custom code and 1,500+ integrations, and can call models inside a workflow. Its source is public and self-hostable under the Sustainable Use License, with an enterprise licence for more features. n8n is a strong fit when the job is a fixed flowchart: the same steps, in the same order, every time. It is the wrong tool when the job is open-ended work an agent has to plan and finish on its own. Repository: [n8n-io/n8n](https://github.com/n8n-io/n8n).

### Coding agents

**OpenHands** is the self-hosted developer control center for coding agents and automations. It runs its own open source agent plus Claude Code, Codex or Gemini across local, Docker, VM and cloud backends, and can schedule automations on a webhook or a cron. It is MIT licensed. Repository: [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands).

## Closed platforms

These three are the closed incumbent agent platforms this list replaces. None of them is open source or self-hostable.

- **ChatGPT Work** (OpenAI) is the agent inside ChatGPT that runs multi-step work across connected apps and files. Configuration and runtime stay in OpenAI's product ([OpenAI announcement](https://openai.com/index/chatgpt-for-your-most-ambitious-work)).
- **Claude Cowork** (Anthropic) is Anthropic's knowledge-work agent for files and connected tools, included in Pro, Max, Team and Enterprise plans. It runs through a Claude account or Amazon Bedrock, Google Cloud or Microsoft Foundry, and there is no self-host edition ([Claude Cowork](https://claude.com/product/cowork)).
- **Perplexity Computer** (Perplexity) is a general-purpose digital worker for Pro and Max subscribers that runs workflows in the cloud and connects Gmail, Slack, Notion and hundreds of other tools ([Perplexity Computer](https://www.perplexity.ai/products/computer)).

## How to evaluate

The criteria are covered in full in [the decision guide](docs/how-to-choose-an-open-source-chatgpt-work-alternative.md). In short: check where the configuration lives, whether the platform self-hosts, whether you can bring any model with your own key, how far the connectors reach, whether every tool call has an allow, ask or block gate, and whether a person reviews each change before it lands.

## Get started with open source Kortix

Install the CLI and scaffold a project:

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix ship
```

`kortix init` creates `kortix.yaml` with your agents, skills and runtime config. `kortix ship` pushes the repository and brings the system live. To run it yourself, `kortix self-host start` runs the stack on a single Docker Compose host. To compare the open source field in more detail, see the ChatGPT Work Alternative site at [chatgptworkalternative.com](https://chatgptworkalternative.com).

Kortix is open source (Elastic License 2.0): self-host, read and modify the code. Start on the free tier, or use managed cloud from [kortix.com](https://kortix.com).

## License

The text here is released under CC0 1.0. The projects linked above keep their own licences.
