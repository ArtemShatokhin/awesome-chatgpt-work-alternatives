# How to choose an open source ChatGPT Work alternative

Choosing an open source ChatGPT Work alternative comes down to six questions: where the configuration lives, whether you can self-host, which models you can run, how far the connectors reach, whether every tool call passes a gate, and who reviews a change before it lands. Answer those six and the shortlist usually collapses to one project.

The comparison table in the [repository README](../README.md) lists the licence and hosting facts for each project.

## 1. Ownership: where does the configuration live?

The first question is what you actually control after you adopt a platform. A closed agent platform keeps agent instructions, connector settings, schedules and workspace controls inside the vendor's product, on the vendor's side of the wall. You configure it through their interface and you read it back through their interface.

An open source platform should let the company keep that configuration somewhere you can clone. The strongest form is one git repository that holds agents, skills, memory, connector configuration and triggers as text files. That gives you three things a web console cannot: you can grep the entire setup, you can diff any change an agent or a person makes to it, and you can roll any part of it back.

Kortix is built this way. `kortix.yaml` declares the machine image, the connectors and the triggers; agents and skills are markdown files; memory is files that accumulate in the repository. The company is literally a repository you can hand to a new engineer.

## 2. Self-hosting: can it run on your infrastructure?

Self-hosting is the difference between renting the runtime and owning it. Ask where the platform can actually run: a developer laptop, a VPS, your own VPC, an on-prem network. If the answer is only "our cloud", you have not replaced the closed platform, you have moved to a different vendor.

Most projects in this field self-host in some form. Open WebUI, LibreChat and Dify ship Docker Compose stacks. n8n and OpenHands run on your own machines. OpenWork runs locally on the desktop and can self-host its team control plane. Kortix runs on a laptop, a VPS, your VPC or on-prem, and the same repository that runs locally is the one that runs in the cloud.

One practical check: does the self-hosted edition have the same agent capabilities as the hosted one, or is it the demo? A platform that withholds the review gate or the connector broker from the self-hosted build is not a self-hosting story.

## 3. Model choice: can you bring your own keys?

Model choice protects you from the next price change and the next capability gap. A platform that only speaks one provider's models locks your agent layer to that provider's roadmap.

Look for a platform that is model-agnostic and lets you bring your own API key. Kortix picks the model per agent, per session or per message: Anthropic, OpenAI, Google, or your own OpenAI-compatible endpoint behind your own URL. OpenWork supports 50+ providers with your own keys or local models through Ollama. LibreChat and Dify connect to many providers and any OpenAI-compatible endpoint. n8n can call OpenAI, Anthropic, Google or open source models inside a workflow.

The question that separates the projects is granularity. "Supports multiple providers" that only switches at the whole-installation level is weaker than a setting per agent, so a research agent can run a long-context model while a drafting agent runs a cheap one.

## 4. Connector reach: how far does it touch your tools?

An agent that cannot open a ticket, read the CRM or post to Slack is a chatbot. Count two things: how many apps the platform reaches, and how it reaches the ones it does not cover out of the box.

Kortix connects 3,000+ apps through one scoped token, plus any MCP server, OpenAPI or Postman spec, GraphQL API or raw HTTP endpoint. Credentials are brokered server-side and never enter the session machine. Open WebUI, LibreChat and Dify all support MCP and custom endpoints. OpenWork brings MCP connections, Google Workspace and Microsoft 365 into compatible agents. n8n reaches 1,500+ integrations, but those are workflow steps rather than tools an autonomous agent chooses from.

The deeper question is scoping. A connector that is either on for everyone or off for everyone is hard to govern. Look for the ability to scope which agent may touch which connector, and which arguments it may pass.

## 5. Permission gate: what can an agent do without asking?

Autonomy without a gate is a liability. Every serious platform in this field now offers some form of tool-level control. The useful ones decide on each tool call.

Kortix sets each tool call to allow, ask or block, down to the arguments of the call. An ask holds the call until a person approves it, then the agent resumes. Approval gates are off until you turn them on, so a new team can watch an agent work before it is allowed to send, post or pay. LibreChat offers ask, allow or deny for file writes and command execution. Open WebUI and n8n have approval flows inside their own models.

Ask what the gate protects. A gate on sending email is worth more than a gate on reading a document, and a gate you can set per agent is worth more than one that applies to the whole workspace.

## 6. Change review: how does work land?

The last question is what happens at the end of a run. Some platforms leave the artifact in a chat, some write directly into the target system, and some open a review.

The strongest pattern is the one developers already trust: every session runs on its own branch, and whatever it produces reaches the main branch only through a change request a person reads as a diff. Kortix works this way, and merge is default-deny for agents. OpenHands gives coding agents a similar review surface through pull requests. The closed platforms generally ask for approval before an action, but the work itself lands in their product rather than in a repository you can version.

If the output of an agent can change production without a person seeing the diff first, treat that as a gap you have to close before rollout.

## Which project fits which job

- A chat or document workspace over your own models: Open WebUI or LibreChat.
- A fixed, repeating flowchart with model steps: n8n.
- A control center for a software engineering team: OpenHands.
- A desktop agent that works on individual files and shares skills with a team: OpenWork.
- Building and shipping LLM apps and RAG pipelines: Dify.
- Running a whole company's agents, memory and connectors from one repository you own: Kortix.

Only the last case covers the full ChatGPT Work category: agents, skills, memory, connectors and a review gate in one system. The other projects are excellent at a layer of it, and many teams run one of them beside Kortix.

For the wider ranked list, the [alternatives guide](https://chatgptworkalternative.com/chatgpt-work-alternatives.html) covers each option in the field. For the direct question of how the closed incumbent compares with the recommended pick, read [how ChatGPT Work and Kortix compare](https://chatgptworkalternative.com/chatgpt-work-vs-kortix.html).

## Start with Kortix

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix ship
```

Kortix is open source (Elastic License 2.0): self-host, read and modify the code.
