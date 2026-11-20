# All About Agents

Architecture notes, field guides, and reference blueprints on building and operating production AI systems.

## Read Online

- **Series home:** <https://evekhm.github.io/all-about-agents/>
- **Episode 01 — Securing the Agent-to-Database Connection:** [web page](https://evekhm.github.io/all-about-agents/ep01_securing_agent_to_database.html) · [PDF](https://evekhm.github.io/all-about-agents/ep01_securing_agent_to_database.pdf)
- **Episode 02 — A Mental Model for Designing Agentic Systems:** [web page](https://evekhm.github.io/all-about-agents/ep02_designing_agentic_systems.html) · [PDF](https://evekhm.github.io/all-about-agents/ep02_designing_agentic_systems.pdf) · [Medium](https://medium.com/google-cloud/a-mental-model-for-designing-agentic-systems-aaf90dcc9f3d)
- **Episode 03 — Five Foundational Questions in AI System Design:** [Question 01 · Trust](https://evekhm.github.io/all-about-agents/ep03_q1_enterprise_llm_trust.html) · [Question 02 · Model Spectrum](https://evekhm.github.io/all-about-agents/ep03_q2_model_spectrum_economics.html) · [Question 03 · Forecasting](https://evekhm.github.io/all-about-agents/ep03_q3_retail_demand_forecasting.html) · [Question 04 · Modern RAG](https://evekhm.github.io/all-about-agents/ep03_q4_modern_rag_pairings.html) · [Question 05 · Domain Agent](https://evekhm.github.io/all-about-agents/ep03_q5_domain_specific_agent.html) · [Cheat Sheet](https://evekhm.github.io/all-about-agents/ref/ai-interview-cheat-sheet.html)
## Topic: Agentic Governance

### [Episode 01 — Securing the Agent-to-Database Connection](https://evekhm.github.io/all-about-agents/ep01_securing_agent_to_database.html) ([PDF](ep01_securing_agent_to_database.pdf))

Follows a customer request from the top-level picture (user, agent, and database) down to the low-level details of each hop: which token travels on each call, which SQL runs, and whose identity the database sees. Maps where threats strike on the wire and layers defense-in-depth guardrails aligned to the OWASP Agentic Top 10 (2026) and OWASP LLM Top 10 (2025). The resulting architecture brings together workload identity, gateways, engine-level access rules, private networking, human approval, and audit on Google Cloud.

- **Hands-on lab:** [ep01_securing_agent_to_database-lab/](ep01_securing_agent_to_database-lab/README.md) · [Start Here Guide](ep01_securing_agent_to_database-lab/docs/START_HERE.md) · [Progress](ep01_securing_agent_to_database-lab/PROGRESS.md)

## Topic: System Design

### [Episode 02 — A Mental Model for Designing Agentic Systems](https://evekhm.github.io/all-about-agents/ep02_designing_agentic_systems.html) ([PDF](ep02_designing_agentic_systems.pdf) · [Medium](https://medium.com/google-cloud/a-mental-model-for-designing-agentic-systems-aaf90dcc9f3d))

Starts from an abstract sequence of agents and follows it down to what that sketch actually means as an architecture: where language models belong versus deterministic code, how the surrounding harness coordinates control flow and state, and how structured context moves from one step to the next. Uses a self-healing code repository system as a reference example to lay out a systematic, reusable approach to agentic system design. Ends with that architecture mapped onto Google Cloud, a printable cheat sheet, and a bridge into the controls of Episode 01.

## Topic: AI System Design Interviews

### Episode 03 — Five Foundational Questions in AI System Design

Five standalone deep dives covering core questions companies test in AI system-design interviews ([5-Question Master Cheat Sheet](ref/ai-interview-cheat-sheet.html)):

- **[Question 01 — Making an LLM Trustworthy for an Enterprise Customer](https://evekhm.github.io/all-about-agents/ep03_q1_enterprise_llm_trust.html)** ([PDF](ep03_q1_enterprise_llm_trust.pdf)): Reasoning-trace granularity, weight/activation opacity, nine stakeholder concerns, seven transparent system layers, and six architectural alternatives.
- **[Question 02 — Open-Weight vs. Proprietary Models Across the Full Model Spectrum](https://evekhm.github.io/all-about-agents/ep03_q2_model_spectrum_economics.html)** ([PDF](ep03_q2_model_spectrum_economics.pdf)): Governance constraints, Zero Data Retention boundaries, GPU VRAM and utilization math, and a five-tier hybrid router.
- **[Question 03 — Production Retail Demand Forecasting and Honest LLM Scoping](https://evekhm.github.io/all-about-agents/ep03_q3_retail_demand_forecasting.html)** ([PDF](ep03_q3_retail_demand_forecasting.pdf)): Stockout uncensoring, quantile safety stock, LightGBM + TimesFM + count ensembles, and three backtest-gated LLM sidecars.
- **[Question 04 — Modern RAG and Multi-Store Context Engineering](https://evekhm.github.io/all-about-agents/ep03_q4_modern_rag_pairings.html)** ([PDF](ep03_q4_modern_rag_pairings.pdf)): Six retrieval engineering shifts and five production pairings with SQL, graphs, prefix-cached long context, LoRA, and two-hop memory.
- **[Question 05 — Building a Lean, Domain-Specific Agent](https://evekhm.github.io/all-about-agents/ep03_q5_domain_specific_agent.html)** ([PDF](ep03_q5_domain_specific_agent.pdf)): Compiled policy RAG, auto-injected defined terms, parameterized DB access, deterministic precedence, and an ADK 2.x prior-authorization workflow.
