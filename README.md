# Private Cloud Solution Providers: Single-Tenant or VPC, Why the Prices Don't Compare, and the VMware Renewal Questions to Ask First

Choose the isolation model before you choose a vendor. A VPC is a logically separated network inside a multi-tenant public cloud: your traffic stays private, the physical hosts do not. A full private cloud hands one customer the compute, storage and network hardware, either on their own floor or hosted by a provider. Price units, noisy-neighbour exposure and most of the compliance answers follow from that one line.

Two forces are making a wrong pick expensive right now. VMware Cloud Foundation renewals have turned into budget events, with Mirantis building a migration offer around a customer facing a 600% price increase. Data sovereignty rules increasingly dictate where the hardware itself may sit. Below are the benchmarks that let you sanity-check a quote, the questions that separate a real private cloud from a rebranded VPS, and a bare-metal route for teams who would rather build the platform than rent one.

## VPC or single-tenant hardware? Decide this before you read another vendor page

Vendor lists blur the difference because the same three words cover both products. A virtual private cloud is a logically isolated slice of shared hardware, which is what AWS, Azure and Google Cloud sell under that label. You get elasticity and a familiar API, plus the risk that a noisy neighbour on the same host affects your latency, and a bill that moves with usage. A full private cloud, sometimes called single-tenant, gives you the physical compute, storage and networking exclusively. Performance stays consistent, and cost becomes predictable once the workload is stable.

The buyer-side drivers are consistent across the market. Hitachi Vantara's private cloud solution profile names three: performance limits in legacy infrastructure, unexpected public cloud cost escalations, and data sovereignty requirements. The promised returns are agility, lower total cost of ownership and higher availability. Treat those as goals to test in a proof of concept rather than features on a datasheet.

The evaluation axes worth scoring every candidate on are cost structure, operational difficulty, scalability and security features. A provider that is cheap per month but requires your team to run the hypervisor, patching and backups is a different purchase from one that charges three times more and includes 24/7 operations.

> **The short version for most readers:** if you want hardware-level isolation, a fixed monthly bill and you have someone who can run Proxmox, OpenStack or vSphere, rent single-tenant bare metal and build the cloud yourself. SpinServers sells 10Gbps dedicated servers in Dallas and San Jose, with third-party listings putting the entry configuration at $49/month for a 4-core Xeon E3-1280 v5 with 32GB RAM and a 1TB NVMe drive. 👉 [Check the current Dallas and San Jose configurations and live pricing](https://bit.ly/Spinservers)

## SpinServers plans at a glance

SpinServers prices per configuration, and inventory turns over, so treat the ranges below as a map of the tiers rather than a quote. Where two published listings disagree, the range shows both figures. Confirm the live number on the order page before you commit.

| Tier | Core configuration | Port and transfer | Price (verify live) | Best for | Order |
| --- | --- | --- | --- | --- | --- |
| Entry single-CPU | Xeon E3-1280 v5, 4 cores / 8 threads, 32GB DDR4, 1TB NVMe | 10Gbps port, 30TB/month | $49/mo | Lab, single hypervisor node, small private cloud pilot | [ View this configuration](https://bit.ly/Spinservers) |
| Dual Xeon, high memory | 2× E5-2630L v3, 16 cores / 32 threads, 64GB to 256GB DDR4, SSD or NVMe | 10Gbps, 30TB/month, or 1Gbps unmetered | $69–$109/mo | Memory-heavy VM consolidation on a budget | [ View this configuration](https://bit.ly/Spinservers) |
| Dual Xeon, high core count | 2× E5-2696 v3, 36 cores, 128GB DDR4, 480GB SSD | 10Gbps, 30TB/month | $139–$149/mo | Dense VM hosts where core count beats clock speed | [ View this configuration](https://bit.ly/Spinservers) |
| Flagship | 2× Xeon Platinum 6162 (48c/96t) or 4× Platinum 8268 (96c/192t), 1TB to 1.5TB DDR4, NVMe | 10Gbps, up to 100TB/month | $449–$599/mo | Private cloud core nodes, databases, heavy multi-tenant workloads | [ View this configuration](https://bit.ly/Spinservers) |
| San Jose, Asia-optimised | 2× E5-2630L v3, 64GB to 256GB DDR4, SSD or NVMe | 10Gbps, 30TB/month, or 100Mbps China Telecom route | $79–$109/mo | APAC-facing services, China-route latency | [ View this configuration](https://bit.ly/Spinservers) |
| VPS | 2 cores, 2GB RAM, 20GB to 40GB SSD | 1Gbps, 1TB to 4TB/month | $6–$14/mo | Jump host, control plane, monitoring. Not a private cloud | [ View this configuration](https://bit.ly/Spinservers) |

Two things worth knowing before you order. The older E5 v3 and v5 generations deliver strong multi-threaded throughput per dollar, but single-core performance trails current EPYC and Xeon Scalable parts, so a latency-sensitive database may not be the right fit. Listings also note that assigned IPs are not guaranteed to be native US addresses and streaming-service unlocking is not supported as a feature. Self-service OS installs, reinstalls and reboots are handled from the control panel, and payment options include PayPal, credit cards, Alipay and WeChat.

## Why the published prices cannot be lined up in one column

Four providers, four different billing units. Lining them up as if they were comparable is how shortlists go wrong.

**UpCloud** publishes the clearest number in this set: Dedicated Private Cloud starting at €3,190 per month, quote-based, deployable across 15 data centres on dedicated AMD EPYC hardware. Three node profiles are listed. High-Performance runs an EPYC 9575F with 64 cores / 128 threads, 1920GB RAM and up to 500 VMs. Premium uses the same CPU with 1280GB and up to 300 VMs. Standard runs an EPYC 9355, 32 cores / 64 threads, 640GB and up to 200 VMs. All three include API, CLI and Terraform. Storage is billed separately: €0.22/GB/month for MaxIOPS block storage, €0.085 for Standard, €0.056 for Archive. Five terabytes of Standard storage alone adds €425/month. The provider also advertises zero egress costs. That €3,190 is a floor for a redundant layout, since one host is not a cloud.

**Atlantic.net**, as described in a 2024 comparison published by OpenMetal, listed cloud plans from $17/month on Linux and $29/month on Windows, with hourly and monthly billing, 1-, 2- and 3-year commitment discounts, a one-year free tier, and a ceiling of 32 vCPU / 192GB RAM. The same source reported claims of up to 50% savings against AWS and Azure for equivalent configurations, HIPAA BAAs, PCI-compliant hosting, SOC 2/SOC 3 data centres and Singapore plus US regions. Those are 2024 figures from a competitor's blog, so use them as a shape, not a current quote.

**OpenMetal** sells hosted private cloud on OpenStack with full single-tenancy and pay-as-you-go billing that runs from hourly to five-year agreements, plus a 30-day proof of concept.

Now put the units side by side. €3,190 per month is €38,280 a year for a managed platform before storage. A $49/month dedicated server is $588 a year for hardware you operate yourself. Those numbers are not in the same category, and the gap is the price of someone else running the hypervisor, the control plane, the patching and the on-call rota. The useful comparison is your loaded ops cost against that gap, not the sticker prices.

One customer quote is worth noting as a vendor-reported data point: Thiseas Meggos, Director of Infrastructure at Hack The Box, said the proposed private cloud plan "decreased costs by around 30%" during the proof of concept, alongside faster service go-to-market times. That is UpCloud's published case study, not an independent audit.

## The VMware renewal line nobody puts in the comparison table

If your private cloud runs vSphere today, the renewal quote is the real decision deadline. Mirantis launched an enterprise virtualisation offer in October 2026 aimed squarely at teams migrating off VMware ahead of VCF renewal increases. It bundles Mirantis OpenStack for Kubernetes, implementation and migration services, and managed operations, with eligible customers getting free migration and implementation plus multi-year pricing. Existing servers, SAN and network fabric can be retained rather than replaced.

The numbers in that announcement are the useful part. A leading cloud infrastructure provider facing a 600% VMware price increase has a migration project underway spanning three data centre sites. The packaged migration module typically runs five weeks, scoped during discovery, and Mirantis offers a complimentary two-day architecture discovery workshop. OpsCare Plus provides 24/7 managed operations with an uptime SLA of up to 99.99%.

The other half of the VMware story is policy. Broadcom's partner programme changes mean hardware used for VMware services may in future only be owned by Pinnacle partners, according to Copaco's description of the programme. Hardware kept inside Broadcom's policy must be suitable for VMware Cloud Foundation 9, and Broadcom assesses that per individual component, compute and storage separately, against its compatibility guide. Copaco holds VCSP Pinnacle status and runs its platform on VCF 9, offering shared hardware or fully isolated Dedicated Resource Domains.

Five questions to put to any candidate that claims VMware compatibility:

1. Are you a Broadcom VCSP Pinnacle partner today, and which VCF version is your platform on?
2. Which of my existing servers and SAN arrays appear on the compatibility guide for VCF 9, judged component by component?
3. How many weeks is the migration, who scopes it, and is discovery billed?
4. What exactly does the SLA cover, and what is excluded from it?
5. If I keep my own hardware, who is allowed to own and operate it under the new partner rules?

## Sovereignty and compliance: ask for scope, not logos

Certification badges tell you a provider passed an audit. They do not tell you which data centres, which staff and which sub-processors the audit covered.

Copaco's numbers are a useful template for what a straight answer looks like: six data centres, four in the Netherlands and two in Belgium, technical teams located in both countries, ISO 27001 and ISAE 3400 / 3402 compliance, and a partner-only sales model that never contracts directly with end customers. Hitachi Vantara's documentation adds the operational framing, listing compliance with local, state and federal data residency, access and sharing rules as a requirement rather than a feature.

Ask these before signing:

- Which physical facilities will hold my data, and can I name them in the contract?
- Who has administrative access, what nationality and jurisdiction do those staff sit in, and is access logged?
- What is the exact scope of each certification (entity, sites, services)?
- Which sub-processors touch my data, and how much notice do I get before a new one is added?
- On exit, in what format do I get my data back, over what period, and at what cost?

Vendor performance claims deserve the same scrutiny. Hitachi's UCP RS documentation promises a 100% data availability guarantee, microsecond latency, and VSP arrays scaling to 69PB and 33M IOPS across a three-data-centre architecture. Those are the vendor's own figures. Ask for the reference architecture and the SLA credits behind them.

## Which option fits your situation

**You need physical isolation on a fixed monthly bill and have ops capability.** Rent single-tenant bare metal and build the cloud yourself with Proxmox, OpenStack or vSphere. A three-node cluster of SpinServers' dual-Xeon tiers lands in the low hundreds of dollars per month rather than thousands, and 10Gbps ports remove the network as a bottleneck. Budget for your own time, monitoring and spare capacity. 👉 [Compare the dedicated server tiers and current monthly pricing](https://bit.ly/Spinservers)

**You need the hypervisor managed for you and an SLA to point at.** Look at platforms like UpCloud's dedicated private cloud or OpenMetal's hosted OpenStack, and price storage and egress explicitly. Ask what happens at the VM ceiling of each node profile.

**You are exiting a VMware renewal.** Prioritise providers with current VCF 9 alignment and a documented migration module. Get the discovery workshop in writing before you commit to a timeline.

**You need EU-resident hardware with audit reports.** A Dutch or Belgian provider with in-country technical staff and scoped ISO 27001 and ISAE 3400/3402 coverage answers more questions in one call than a global provider with a regional footprint.

**You need a managed service and no operations burden at all.** Self-managed bare metal is the wrong purchase. Pay for the managed tier and treat the price gap as your staffing budget.

Before you order anything, confirm four items in writing: the contract term and what renewal pricing looks like, whether setup or migration work is billed separately, the notice period and data return process on exit, and whether the price you were quoted includes storage, transfer and support. On a bare-metal order, verify the exact CPU generation and drive model in the cart, since listings for the same tier can differ by a generation and by a hundred dollars a month. 👉 [Start from the live SpinServers configuration page](https://bit.ly/Spinservers) and price the tier that matches your workload before you compare it to a managed quote.
