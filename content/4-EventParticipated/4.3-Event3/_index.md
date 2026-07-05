---
title: "Event 3: FCAJ Community Day - 2026/06/06"
date: 2026-06-27
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---
### **1. Speaker 1 (Steve Tran): AgenticOps for your Cloud**
*   **Customer Challenges:** As systems evolve from **Microservices** to **Observability**, teams eventually hit a **"Complexity Wall"**, pushing the need toward **self-healing infrastructure**. This growth leads to more tools per ops team, more engineers needed for cloud operations, and higher **MTTR** (Mean Time to Resolution) per incident.
*   **The Solution — CloudThinker:** An **Enterprise AgenticOps Platform** built on the principle that AI agents process and react far faster than humans.
    *   **Key Benefits:** Optimizes cost, resolves security issues and incidents, and streamlines output review/debugging.
    *   **Specialist Agents:** Deploys custom agents tailored to each operational role.
    *   **Observability Loop:** The platform continuously observes the entire environment, then learns and acts based on those observations.
    *   **Cost Management:** While multi-agent systems typically increase costs, CloudThinker applies **context optimization** to keep this efficient.
    *   **Operating Model:** Follows a **Detect → Resolve → Validate** cycle across managed surfaces, incorporating human approval checkpoints and SLA-backed delivery.

### **2. Speaker 2 (Trung Vu, Nghi Danh, Kiet Tran): Building Voice Agent (VA) at Scale**
*   **Current Limitations:** True **speech-to-speech** technology is not yet production-ready.
*   **Practical Approach:** Teams instead rely on **TTS (Text-to-Speech)** combined with fine-tuned models designed to sound more natural and conversational.
*   **Performance Optimization:** Models must be **"warmed up"** in advance to ensure low latency and fast response times.
*   **Continuous Improvement:** Systems should be built with strong **metrics and observability**, including traces that allow human developers to monitor and improve the model over time.

### **3. Speaker 3 (Bao Phan, Nguyen Nguyen): AWS DevOps Agent**
*   **Challenges:** High costs of manual incident investigation, elevated **MTTD** (Mean Time to Detect) and **MTTR**, loss of context during handoffs, and a generally **reactive** approach to problem-solving.
*   **The Solution:** An autonomous AI agent designed to resolve and proactively prevent incidents, built around five pillars: **Context Learning, Control, Integration, Collaboration**, and **Cost-effectiveness**.
*   **Incident Lifecycle:** Follows a structured flow of **Triage → Investigation → Mitigation → Prevention**.
*   **Ideal Use Case:** Works best in environments with mature observability (clear logs, metrics, and alarms) and at large scale. Importantly, the agent only **suggests** next steps — humans remain responsible for final approval and execution.

### **4. Speaker 4 (Truong Tran, Anh Minh): AI-Powered Productivity Workforce Planning for Enterprise**
*   **HR in the AI Era:** Traditional HR processes are time-consuming, prone to missing key talent, and often rely on gut feeling rather than data.
*   **The AI-Enabled Shift:** AI reduces manual screening effort, elevates HR's role to strategic talent advisory, enables data-driven hiring decisions, sharpens focus on leadership development, and improves cost savings and scaling speed.
*   **Amazon Quick Solutions:** A suite of "agentic teammates" — including **Chat Agents, Research, QuickSight, Flows,** and **Automate** — that convert raw data into analytical reports, visualizations, and automated workflows for both simple and complex multi-step tasks.
*   **HR Application Scenario:** The workflow connects data → analysis → automated reporting/visualization → applicant evaluation → automated tracking. This includes generating targeted interview questions, evaluating candidates, advising HR on final decisions, and designing screening processes tailored to company requirements.

### **5. Speaker 5 (Toan Nguyen, Nghi Danh): Building Secure Private MCP for AWS Quick**
*   **Background:** An overview of Amazon Quick and its underlying **MCP (Model Context Protocol)** architecture.
*   **The Problem:** While Quick supports MCP connectors by default, this requires a **public endpoint**, meaning context and logs travel over the public internet — significantly increasing the attack surface.
*   **The Solution — VPC Connection for Quick:**
    *   **Private Entry:** Removes reliance on a public endpoint.
    *   **Private DNS:** Hostnames resolve only within the VPC.
    *   **Fully Private Internal Path:** Traffic flows securely through **ENI → ALB → MCP**, keeping the entire connection isolated from the public internet.