# System Map

## What is Actually Built & Running

<!-- A living map of the current system architecture and deployment -->

## System Overview

```
┌─────────────┐         ┌─────────────┐         ┌─────────────┐
│   Client    │────────▶│   Backend   │────────▶│  Database   │
│             │         │             │         │             │
└─────────────┘         └─────────────┘         └─────────────┘
```

<!-- Replace with your actual architecture diagram -->

## Components

### Frontend/Client
- **Technology:** [Framework/language]
- **Hosting:** [Where it's deployed]
- **Entry Points:** [URLs/endpoints]
- **Key Files/Modules:**
  - `[path]`: [purpose]
  - `[path]`: [purpose]

### Backend/API
- **Technology:** [Framework/language]
- **Hosting:** [Where it's deployed]
- **Entry Points:** [URLs/endpoints]
- **Key Files/Modules:**
  - `[path]`: [purpose]
  - `[path]`: [purpose]

### Database
- **Technology:** [Database type/version]
- **Hosting:** [Where it's deployed]
- **Key Tables/Collections:**
  - `[name]`: [purpose and key fields]
  - `[name]`: [purpose and key fields]

### External Services
- **Service Name:** [Provider]
  - **Purpose:** [What it does]
  - **Integration:** [How we connect]
  - **Credentials:** [Where stored]

## Data Flow

### Critical User Flows
1. **[Flow Name]**
   - User action: [what user does]
   - System flow: [component 1] → [component 2] → [component 3]
   - Data touched: [what data is read/written]

2. **[Flow Name]**
   - User action: [what user does]
   - System flow: [component 1] → [component 2] → [component 3]
   - Data touched: [what data is read/written]

## Deployment

### Environments
| Environment | Purpose | URL | Status |
|-------------|---------|-----|--------|
| Production  | Live users | [url] | 🟢 Active |
| Staging     | Pre-release testing | [url] | 🟢 Active |
| Development | Local development | localhost | 🟢 Active |

### Build & Deploy Process
1. [Step 1]: [description]
2. [Step 2]: [description]
3. [Step 3]: [description]

## Configuration

### Environment Variables
| Variable | Purpose | Required | Set In |
|----------|---------|----------|--------|
| `[VAR_NAME]` | [what it does] | Yes/No | [where it's set] |

### Feature Flags
| Flag | Purpose | Status | Controls |
|------|---------|--------|----------|
| `[flag_name]` | [what it enables] | On/Off | [what code/feature] |

## Dependencies

### Runtime Dependencies
- [Package/Library]: [version] - [purpose]
- [Package/Library]: [version] - [purpose]

### Build Dependencies
- [Package/Library]: [version] - [purpose]
- [Package/Library]: [version] - [purpose]

## Monitoring & Observability

### Logs
- **Location:** [where logs are stored]
- **Key Events:** [what we log]

### Metrics
- **Tool:** [monitoring tool]
- **Key Metrics:** [what we track]

### Alerts
- **Tool:** [alerting tool]
- **Critical Alerts:** [what triggers pages]

## Known Issues & Debt

- [ ] [Technical debt item]: [why it exists, impact]
- [ ] [Known bug]: [workaround if any]
- [ ] [Performance issue]: [current state]

---

**Last Updated:** [YYYY-MM-DD]
**Updated By:** [Name/Team]
