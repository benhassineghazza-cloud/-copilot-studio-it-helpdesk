# IT Helpdesk AI Agent — Copilot Studio Portfolio

> A production-grade IT Helpdesk conversational AI agent built with Microsoft Copilot Studio, Agent Flows, SharePoint, and Microsoft Teams.

## Demo
![Creating a ticket](docs/demo-create-ticket.gif)

## What it does
- Conversational IT ticket creation in natural language (Teams chat)
- Auto-resolution of common IT questions via RAG over SharePoint knowledge base
- Ticket status tracking by ID
- Automated IT team notifications (Teams channel + email confirmation)
- Urgent issue escalation with forced High priority

## Architecture
![Architecture](docs/architecture.png)

## Tech Stack
| Layer | Technology |
|---|---|
| Conversational AI | Microsoft Copilot Studio (GPT-4.1) |
| Agent Flows | 3 agent flows |
| Data storage | SharePoint Online (IT_Tickets + IT_KnowledgeBase) |
| Deployment channel | Microsoft Teams |
| ALM | Power Platform Managed Solution |

## Topics (Copilot Studio)
| Topic | Trigger | Description |
|---|---|---|
| Greeting | Conversation start | Welcome message + 3 quick replies |
| New Request | 'nouveau ticket', 'problème'... | Full ticket creation flow |
| FAQ Lookup | 'comment', 'procédure'... | RAG over SharePoint KB |
| Check Ticket | 'statut', 'mon ticket'... | Ticket status lookup |
| Escalate | 'urgent', 'critique'... | High-priority ticket + alert |
| Fallback | No match | Clear fallback with quick replies |

## Agent Flows (Power Automate)
| Flow | Trigger | Description |
|---|---|---|
| CS_CreateTicket | When an agent calls the flow | Creates SharePoint item with auto ID |
| CS_NotifyITTeam | When SharePoint item is created | Teams notification + email |
| CS_CheckTicketStatus | When an agent calls the flow | Reads ticket status from SharePoint |

## How to deploy
1. Create SharePoint site + lists (see `sharepoint/IT_Tickets_columns.md`)
2. Add KB articles from `sharepoint/IT_KnowledgeBase_articles.md`
3. Import `solution/ITHelpdeskAgent_v1.zip` into your Power Platform DEV environment
4. Reconfigure flow connections (SharePoint, Teams, Outlook)
5. Publish agent to Microsoft Teams

## Built with
Built by [GBH] · Power Platform Consultant · Fev. 2026
Copilot Studio UI version used: 2025/2026 (Agent Flows architecture)

