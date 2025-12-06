# Azure Cloud Strategy
The cloud is endlessly customizable, but without a clear strategy, can increase costs, complexity, and reduce operability for developers. A clear strategy is used to make cloud development simple, economic, and effective.

## Subscriptions
Subscriptions should be used to logically separate based on environment, function, and risk domain. According to the CAF, subscriptions are isolation boundaries for security, governance, cost, and environments. There are two categories of subscriptions platform and foundational, or workload landing zones.

Examples  
- Platform: identity, management, connectivity.
- Landing zones: app workloads, data platforms, business-unit environments like dev, test, prod for individual solutions.

What orgs try to avoid  
- Putting everything in one subscription (messy, governance failure)
- Putting too little in each subscription (administrative sprawl)
- Using subscriptions for microservices (too granular)

### Strategy
Create **platform subscriptions** for shared infrastructure used by everyone.
Create **landing zone subscriptions** for specific workloads or teams needing isolation, separate costs, or their own environments.

**1 person:** One shared subscription; no separation needed.  
**10 people:** Split prod into its own subscription; dev/test shared.  
**20 people:** Add platform subscription; each major workload gets its own prod subscription.  
**100 people:** Full CAF model—dedicated platform subscriptions plus separate dev, test, prod landing zones per workload or business unit.

## Environments
Two different strategies to consider. Non-prod & prod (np, prod), then also 3 env approach (dev, qa, prod). The lightweight approach is to start with np & prod, then scale to dev, qa, prod if development workloads expand.

Tags, depending on the approach:  key="env"  
- np, prod
- dev, qa, prod

## Resource groups
Governance for resource groups is nuanced, but a useful mental model is separating them into “platform” and “workload” scopes. These aren’t strict governance boundaries, but they help organize resources by ownership and lifecycle. Platform scopes represent long-lived, shared services—such as an AI platform or a logging foundation—which may span one or more resource groups depending on architecture. Workload scopes contain application-specific resources with independent lifecycles. This distinction keeps shared services centralized while allowing workloads to evolve or be retired without affecting the broader platform.

Platform examples:  
1. **Identity platform** – Central authentication and access control.
2. **Networking platform** – Shared hubs, firewalls, connectivity services.
3. **Logging/monitoring platform** – Centralized telemetry and observability.
4. **Data platform** – Shared storage, analytics, and integration services.
5. **DevOps platform** – Build, release, and automation tooling.

Examples:  
- Key Vault = `<orgOrBU>-<env>-<region>-<workloadOrFunction>-rg` would be `trwolf-dev-wus2-secrets-rg`
- Network = `<orgOrBU>-<env>-<region>-<workloadOrFunction>-rg` would be `trwolf-dev-wus2-network-rg`
- Microsoft Foundry = `<orgOrBU>-<env>-<region>-<workloadOrFunction>-rg` would be `trwolf-dev-wus2-ai-rg`
- Data factory = can be a "platform", if it is used as a centralized integration service. Otherwise, each workload has its own resource group and its own data factory as an etl service (not recommended). `<orgOrBU>-<env>-<region>-<workloadOrFunction>-rg` would be `trwolf-dev-wus2-etl-rg`
- Analytics = `<orgOrBU>-<env>-<region>-<workloadOrFunction>-rg` would be `trwolf-dev-wus2-analytics-rg`

Tags, depending on the approach:  key="type"
- platform, workload

