# Hi there, I'm Alex Gnaensky 👋

### Technical Project Manager (TPM) | Software Architect | Product Owner
*Bridging complex business requirements with elegant, autonomous technical execution.*

---

## 👨‍💻 About Me
I am a seasoned technology leader and software architect with over 20 years of experience building scalable solutions across **AI-driven logistics, FinTech, Healthcare (FHIR), and IoT**. I specialize in leading cross-functional Agile teams, orchestrating AI-driven workflows, and architecting robust .NET/C# microservices. My passion lies in transforming manual, legacy processes into zero-configuration, autonomous digital pipelines that deliver measurable business value.

---

## 🚀 What I'm Working On

### [**GoodsLoading**](http://www.goodsloading.com/)
*Software Engineer & Product Manager*  
Architected and integrated **AgentKit**, a code-first AI orchestration engine on the Microsoft Agent Framework, to replace legacy manual cargo planning with an autonomous, document-driven pipeline. 
- **Zero-Configuration UX**: Operators upload shipping documents (Bill of Lading, Packing Lists, etc.) and click "Start". The system autonomously parses, validates, optimizes, and reports.
- **AI Orchestration**: Designed a JSON-driven model to dynamically coordinate domain-specific AI agents for document parsing, 3D load optimization, weight/volume compliance validation, and automated report generation.

---
### **AgentKit**
A modular, multi-agent orchestration framework built on the Microsoft Agent Framework for .NET. Enables configuration-driven AI workflows, human-in-the-loop (HITL) interactions, and robust multi-agent collaboration
**AgentKit** supports declarative JSON workflow definitions, multi-agent GroupChat orchestration, Human-in-the-Loop (HITL) approval gates, and resilient state checkpointing.


### How Goodsloading Utilizes AgentKit
The Goodsloading application is a domain-specific logistics platform designed to optimize cargo placement. Rather than hardcoding AI logic, Goodsloading delegates its complex reasoning, data extraction, and compliance validation to AgentKit, a standalone, multi-agent AI orchestration engine built on the Microsoft Agent Framework.
Goodsloading interacts with **AgentKit** by passing declarative JSON workflow definitions (see goodsloading_workflow.json). AgentKit's WorkflowBuilderService parses this JSON, compiles it into an executable directed graph, and orchestrates the execution flow.

goodsloading_workflow.json

```json
{
  "workflowId": "CargoOptimization",
  "Id": "CO1",
  "name": "Cargo Optimization Pipeline",
  "description": "Extract cargo specifications, verify compliance, and generate optimized 3D loading plans",
  "version": "1.0.0",
  "orchestrationType": "sequential",
  "steps": [
    {
      "id": "step_0",
      "executor": {
        "executorId": "ContextInitializerExecutor",
        "description": "Load JSON workflow into context"
      }
    },
    {
      "id": "step_1",
      "executor": {
        "executorId": "DocumentUploadExecutor",
        "description": "Upload cargo manifest or shipping documents (BOL or packing list)",
        "input": {
          "FilePath": ""
        }
      }
    },
    {
      "id": "step_2",
      "skipStep": false,
      "executionMode": "groupchat",
      "agents": [
        {
          "agentId": "CargoExtractionAgent",
          "description": "Extract and analyze cargo specifications - AI parsing dimensions, weight, and cargo types",
          "enableHitL": false,
          "instructions": {
            "System": "You are a cargo data extraction specialist. Extract dimensions, weight, cargo types, and specifications from shipping documents.",
            "User": "Analyze the uploaded cargo manifest or packing list. Extract all cargo items with their dimensions (length, width, height), weight, cargo type, fragility, stacking restrictions, and any special handling requirements. Return structured data for each item."
          },
          "model": {
            "provider": "ollama",
            "modelId": "llama3.1:8b-instruct-q4_K_M"
          }
        },
        {
          "agentId": "CargoValidationAgent",
          "description": "Verify compliance with loading constraints - checking axle limits, volume capacity, and safety rules",
          "instructions": {
            "System": "You are a cargo compliance validator. Verify that cargo meets all loading constraints including axle weight limits, volume capacity, safety regulations, and distribution requirements.",
            "User": "Review the extracted cargo specifications. Verify compliance with: 1) Axle weight limits, 2) Total volume capacity, 3) Weight distribution balance, 4) Safety regulations, 5) Hazardous material restrictions. Flag any violations and suggest corrections."
          },
          "model": {
            "provider": "ollama",
            "modelId": "llama3.1:8b-instruct-q4_K_M"
          }
        }
      ]
    },
    {
      "id": "step_3",
      "executor": {
        "executorId": "LoadingPlanGeneratorExecutor",
        "description": "Generate optimized 3D loading plan visualization",
        "input": {
          "OutputFormat": "3D_VISUALIZATION"
        }
      }
    }
  ]
}
```


## 🛠️ Tech Stack & Tools

| Category | Technologies |
| :--- | :--- |
| **Languages** | ![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) ![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white) ![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white) |
| **Frameworks** | ![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white) ![ASP.NET](https://img.shields.io/badge/ASP.NET-5C2D91?style=for-the-badge&logo=dotnet&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB) ![ML.NET](https://img.shields.io/badge/ML.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white) |
| **Architecture** | ![Microservices](https://img.shields.io/badge/Microservices-000000?style=for-the-badge&logo=serverless&logoColor=white) ![REST/OpenAPI](https://img.shields.io/badge/OpenAPI-6BA539?style=for-the-badge&logo=openapi-initiative&logoColor=white) ![Entity Framework](https://img.shields.io/badge/Entity%20Framework-000000?style=for-the-badge&logo=dotnet&logoColor=white) |
| **Tools & DevOps** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Jira](https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white) ![Azure IoT](https://img.shields.io/badge/Azure%20IoT-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white) ![n8n](https://img.shields.io/badge/n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white) |
| **AI & Automation** | ![Claude/AI Tools](https://img.shields.io/badge/Claude%20%26%20AI%20Tools-000000?style=for-the-badge&logo=google-gemini&logoColor=white) ![PlantUML](https://img.shields.io/badge/PlantUML-000000?style=for-the-badge&logo=plantuml&logoColor=white) |

---

## 🏆 Key Projects & Achievements

- **🏦 IT Kontakt (FinTech/Mortgage)**: Led development of Broker & Borrower Portals serving 50K+ users and 500+ brokers. Automated workflows reduced end-to-end cycle time by **33%** (30 to 20 days) and support ticket volume by **35%**.
- **🏥 WaveAccess (Healthcare)**: Architected FHIR data extraction and translation services (CARIN, US Core, DaVinci IGs), mapping legacy healthcare data to AidBox FHIR platforms for seamless API access.
- **🛡️ H3 Technologies (Digital Safety)**: Designed and led development of cross-platform parental control applications (Web, Android, Chrome/Firefox extensions) with real-time content monitoring and WCF/REST backend services.
- **📡 Cincinnati Bell / Friendly Technology (IoT/Device Mgmt)**: Built TR-069 ACS Management Consoles and Device Management services to remotely provision, diagnose, and manage hundreds of thousands of residential gateways and IoT devices.


## 💡 Leadership & Management Philosophy
- **Agile Excellence**: Deep expertise in Scrum, backlog refinement, Jira/JQL automation, and removing roadblocks for 10–15 person cross-functional teams (Dev, QA, BA, DevOps).
- **Strategic Alignment**: Translating high-level business goals into detailed functional designs, UML use cases, and actionable roadmaps.
- **Stakeholder Empathy**: Proven track record of bridging gaps between technical teams and non-technical departments (e.g., leading a seamless QuickBooks-to-mortgage-platform data migration for Accounting).

---

## 🤝 Let's Connect

I'm always open to discussing AI orchestration, .NET architecture, Agile product management, or innovative logistics solutions.

<p align="center">
  <a href="https://www.linkedin.com/in/alexgnaensky/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="mailto:your.email@example.com" target="_blank">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
  <a href="http://www.goodsloading.com/" target="_blank">
    <img src="https://img.shields.io/badge/GoodsLoading-239120?style=for-the-badge&logo=truck&logoColor=white" alt="GoodsLoading" />
  </a>
</p>

---

<details>
  <summary>📌 <b>Fun Facts & Personal Touch</b></summary>
  <ul>
    <li>🧠 I am just as passionate about optimizing a 3D bin-packing heuristic algorithm as I am about optimizing a Jira workflow.</li>
    <li>🌍 My career has spanned across the USA, Russia, and Israel, giving me a highly adaptable, global perspective on tech and product management.</li>
    <li>☕ Fueled by continuous learning, currently exploring advanced AI agent orchestration and autonomous workflow design.</li>
  </ul>
</details>
