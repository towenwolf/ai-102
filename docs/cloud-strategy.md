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

## Resource groups
