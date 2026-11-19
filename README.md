# All About Agents

Architecture notes, system-design mental models, and governance blueprints for production AI agents.

## Read Online

- **Series home:** <https://evekhm.github.io/all-about-agents/>
- **Episode 01 — Securing the Agent-to-Database Connection:** [web page](https://evekhm.github.io/all-about-agents/ep01_securing_agent_to_database.html) · [PDF](https://evekhm.github.io/all-about-agents/ep01_securing_agent_to_database.pdf)
- **Episode 02 — A Mental Model for Designing Agentic Systems:** [web page](https://evekhm.github.io/all-about-agents/ep02_designing_agentic_systems.html) · [PDF](https://evekhm.github.io/all-about-agents/ep02_designing_agentic_systems.pdf) · [Medium](https://medium.com/google-cloud/a-mental-model-for-designing-agentic-systems-aaf90dcc9f3d)
- **Episode 03 — Five Foundational Questions in AI System Design:** [web page](https://evekhm.github.io/all-about-agents/ep03_ai_architecture_field_questions.html) · [PDF](https://evekhm.github.io/all-about-agents/ep03_ai_architecture_field_questions.pdf)

## Topic: Agentic Governance

### [Episode 01 — Securing the Agent-to-Database Connection](https://evekhm.github.io/all-about-agents/ep01_securing_agent_to_database.html) ([PDF](ep01_securing_agent_to_database.pdf))

Follows a customer request from the top-level picture (user, agent, and database) down to the low-level details of each hop: which token travels on each call, which SQL runs, and whose identity the database sees. Maps where threats strike on the wire and layers defense-in-depth guardrails aligned to the OWASP Agentic Top 10 (2026) and OWASP LLM Top 10 (2025). The resulting architecture brings together workload identity, gateways, engine-level access rules, private networking, human approval, and audit on Google Cloud.

- **Hands-on lab:** [ep01_securing_agent_to_database-lab/](ep01_securing_agent_to_database-lab/README.md) · [Start Here Guide](ep01_securing_agent_to_database-lab/docs/START_HERE.md) · [Progress](ep01_securing_agent_to_database-lab/PROGRESS.md)

## Topic: System Design

### [Episode 02 — A Mental Model for Designing Agentic Systems](https://evekhm.github.io/all-about-agents/ep02_designing_agentic_systems.html) ([PDF](ep02_designing_agentic_systems.pdf) · [Medium](https://medium.com/google-cloud/a-mental-model-for-designing-agentic-systems-aaf90dcc9f3d))

Starts from an abstract sequence of agents and follows it down to what that sketch actually means as an architecture: where language models belong versus deterministic code, how the surrounding harness coordinates control flow and state, and how structured context moves from one step to the next. Uses a self-healing code repository system as a reference example to lay out a systematic, reusable approach to agentic system design. Ends with that architecture mapped onto Google Cloud, a printable cheat sheet, and a bridge into the controls of Episode 01.

### [Episode 03 — Five Foundational Questions in AI System Design](https://evekhm.github.io/all-about-agents/ep03_ai_architecture_field_questions.html) ([PDF](ep03_ai_architecture_field_questions.pdf))

Builds a ground-up foundation across five questions that companies ask in AI system-design interviews: making a language model trustworthy for an enterprise customer, choosing across the full model spectrum, retail demand forecasting, modern RAG and what it pairs with, and building a lean domain-specific agent. Ends with a single-agent policy workflow in ADK 2.x and a printable cheat sheet.

## Up Next

- **Governance:** *Dual LLM and CaMeL, in depth.*
