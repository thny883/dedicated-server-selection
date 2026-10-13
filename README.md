# dedicated server hosting: when a KVM VPS stops being enough, what to actually pay for, and how to avoid renting hardware you don't need

Most people searching "dedicated server hosting" don't need a dedicated server. They need a box that doesn't slow to a crawl at 9pm, doesn't get its CPU stolen by a noisy neighbour, and doesn't choke the moment a post hits the front page of somewhere busy.

That distinction matters, because a dedicated server in the strict sense — an entire physical machine, your name on the chassis — is a four-figure-a-year commitment once you factor in bandwidth, IPs and management. Meanwhile a KVM VPS with properly allocated vCPU and RAM on premium routes will handle a surprising amount of real traffic for the price of a couple of coffees a month.

So this is a guide to telling those two situations apart, plus a look at what DMIT — the provider this site links to — actually sells across its Dedicated Cloud, BareMetal and cloud instance lines, with current plan pricing.

## What "dedicated" actually means, and where the word gets abused

The hosting industry stretches this term past breaking point. At least three different things get marketed as dedicated:

**Bare metal / dedicated server.** You rent a physical machine. Only your workloads run on it. You usually get IPMI or a KVM-over-IP console, so you can reinstall the OS, change BIOS settings and debug a machine that won't boot. This is the real thing.

**Dedicated instance or Dedicated Cloud.** A virtual machine on a host where the resources are contractually yours — no overselling, no sharing with other tenants on the same allocation. It behaves like a dedicated box for most purposes, without the remote hands problem, but you still don't control the hypervisor.

**Dedicated vCPU on a VPS.** The weakest use of the phrase. It means your cores aren't shared, which is genuinely useful, but RAM, disk I/O and network still come off a shared bus.

DMIT sits across all three categories. Its public product line is split into cloud instances, Dedicated Cloud (unmetered traffic, dedicated hardware resources) and BareMetal instances, which its product descriptions say use Intel or AMD platforms with Intel data-centre SSDs, 10Gbps uplinks and IPMI access. The company itself is a New York-registered entity — DMIT INC., incorporated in December 2017 — that started selling VPS hosting in 2018 and now runs out of Los Angeles, San Jose, Hong Kong and Tokyo.

What it's actually known for isn't the word "dedicated" at all. It's the routes.

## The part that decides your bill: network profiles

Buy a dedicated server from anyone and the hardware spec is the easy half of the decision. The hard half is what path your traffic takes, and that's where DMIT structures its entire catalogue.

Every plan carries one of three network profiles:

- **Premium (`.Pro`)** — Tier 1 transit plus premium providers, and the one that matters to a lot of buyers: China Telecom CN2 GIA (AS4809). DMIT's own cart describes it as "Tier 1 + all Premium Transit providers, such as DMIT's backbone, and China Telecom CN2 GIA."
- **Eyeball (`.EB`)** — built around CMIN2 and CMI, China Mobile's international premium network, with AS9929 for China Unicom. Cheaper than Premium for closely comparable specs, and it generally comes with more monthly transfer at the same price point.
- **Tier 1 (`.T1`)** — straight international BGP. No China optimisation at all. This is the budget tier, and it's where the $36.90/year entry plan lives.

If your users are in North America or Europe, Tier 1 is fine and Premium is money burned. If your audience is in mainland China, the reverse is true, and buying Tier 1 to serve them is the single most common expensive mistake in this market. Third-party reviewers consistently report Los Angeles Premium latency from mainland China holding under roughly 150ms even at peak, and Hong Kong Premium landing somewhere in the 20–50ms range depending on carrier and city.

Hardware runs on AMD EPYC across the fleet, with KVM virtualisation, and the platform generation in the SKU name tells you which silicon you're getting — AS3 is EPYC 7003, AN4 is the 9004 series, AN5 is 9005. Newer generation, higher price. DMIT's cart lets you filter by region, generation and network, which is why the same "TINY" name shows up at three different prices.

## When a dedicated server is genuinely the answer

Four situations justify it.

**You need the whole machine's I/O.** Databases with heavy write loads, video transcoding, game servers, anything where a shared NVMe bus becomes the bottleneck. A VPS with generous vCPU allocation can't fix slow storage on a host full of busy neighbours.

**Compliance or licensing requires physical isolation.** Some workloads must be provably single-tenant, and "our hypervisor is configured nicely" doesn't satisfy an auditor.

**You're running your own virtualisation.** If you want to sell VPS yourself, you need bare metal with nested virtualisation and enough bandwidth to back it.

**Sustained traffic is cheaper on a dedicated box.** Once you're paying $200+ per month for a large cloud instance, the maths often flips in favour of hardware you control outright.

For a WooCommerce store doing a few hundred orders a month, a Nextcloud instance for a ten-person team, or a game server for two dozen friends? You're not in that group yet. The honest answer is a Premium-line cloud instance with real dedicated vCPU allocation and a good route, and you'll pay a fraction of the price.

DMIT's Hong Kong Premium line is the clearest illustration of the trade-off in the other direction. A HKG.AS3.Pro.TINY — one vCPU, 1GB RAM, 20GB SSD, 500GB of transfer on a 1Gbps port — costs $39.90/month. That's not a typo, and it's not a dedicated server. You are paying for a Hong Kong IP on a CN2 GIA route, in a market where the physical distance to mainland China is roughly 20 milliseconds' worth. People who need that will pay it. People who don't are looking at the wrong column entirely.

## The full plan line-up

The table below covers DMIT's publicly listed cloud instance plans across its three network profiles and its two largest regions. Prices are per the provider's current listings; DMIT flags stock constantly, and the hardware generation affects the price, so treat this as the shape of the line-up rather than a frozen quote.

| Location | Plan & route | vCPU / RAM / SSD | Transfer & port | Billing | Price (USD) | Order |
| --- | --- | --- | --- | --- | --- | --- |
| Los Angeles | LAX.AS3.Pro.TINY — CN2 GIA | 1 / 2GB / 20GB | 1TB @ 1Gbps | Monthly | 10.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.Pro.Pocket — CN2 GIA | 2 / 2GB / 40GB | 1.5TB @ 4Gbps | Monthly | 16.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.Pro.STARTER — CN2 GIA | 2 / 2GB / 80GB | 3TB @ 10Gbps | Monthly | 34.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.Pro.MINI — CN2 GIA | 4 / 4GB / 80GB | 5TB @ 10Gbps | Monthly | 62.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.Pro.MICRO — CN2 GIA | 4 / 4GB / 160GB | 7TB @ 10Gbps | Monthly | 87.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.Pro.MEDIUM — CN2 GIA | 6 / 8GB / 160GB | 14TB @ 10Gbps | Monthly | 199.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.EB.TINY — CMIN2 / AS9929 | 1 / 2GB / 20GB | 1.5TB @ 2Gbps | Monthly | 10.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.EB.Pocket — CMIN2 / AS9929 | 2 / 2GB / 40GB | 3TB @ 4Gbps | Monthly | 16.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.EB.STARTER — CMIN2 / AS9929 | 2 / 2GB / 80GB | 5TB @ 10Gbps | Monthly | 34.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.EB.MINI — CMIN2 / AS9929 | 4 / 4GB / 80GB | 10TB @ 10Gbps | Monthly | 62.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.EB.MICRO — CMIN2 / AS9929 | 4 / 4GB / 160GB | 14TB @ 10Gbps | Monthly | 87.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.EB.MEDIUM — CMIN2 / AS9929 | 6 / 8GB / 160GB | 30TB @ 10Gbps | Monthly | 199.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.WEE — international BGP | 1 / 1GB / 20GB | 1TB @ 4Gbps | Annual | 36.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.TINY — international BGP | 1 / 1GB / 20GB | 2TB @ 4Gbps | Monthly | 6.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.STARTER — international BGP | 1 / 2GB / 40GB | 4TB @ 10Gbps | Monthly | 12.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.MINI — international BGP | 2 / 2GB / 60GB | 8TB @ 10Gbps | Monthly | 21.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.MICRO — international BGP | 4 / 4GB / 80GB | 16TB @ 10Gbps | Monthly | 32.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.MEDIUM — international BGP | 4 / 8GB / 160GB | 32TB @ 10Gbps | Monthly | 49.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.LARGE — international BGP | 8 / 16GB / 320GB | 64TB @ 10Gbps | Monthly | 99.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Los Angeles | LAX.AS3.T1.GIANT — international BGP | 8 / 24GB / 640GB | 128TB @ 10Gbps | Monthly | 199.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.Pro.TINY — CN2 GIA | 1 / 1GB / 20GB | 500GB @ 1Gbps | Monthly | 39.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.Pro.STARTER — CN2 GIA | 1 / 2GB / 40GB | 1TB @ 1Gbps | Monthly | 79.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.Pro.MINI — CN2 GIA | 2 / 4GB / 60GB | 1.5TB @ 1Gbps | Monthly | 126.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.Pro.MICRO — CN2 GIA | 4 / 4GB / 80GB | 2TB @ 1Gbps | Monthly | 179.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.Pro.MEDIUM — CN2 GIA | 4 / 8GB / 160GB | 2.5TB @ 1Gbps | Monthly | 239.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.WEE — international BGP | 1 / 1GB / 20GB | 1TB @ 4Gbps | Annual | 36.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.TINY — international BGP | 1 / 1GB / 20GB | 2TB @ 4Gbps | Monthly | 6.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.STARTER — international BGP | 1 / 2GB / 40GB | 4TB @ 10Gbps | Monthly | 12.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.MINI — international BGP | 2 / 2GB / 60GB | 8TB @ 10Gbps | Monthly | 21.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.MICRO — international BGP | 4 / 4GB / 80GB | 16TB @ 10Gbps | Monthly | 32.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.MEDIUM — international BGP | 4 / 8GB / 160GB | 32TB @ 10Gbps | Monthly | 49.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.LARGE — international BGP | 8 / 16GB / 320GB | 64TB @ 10Gbps | Monthly | 99.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |
| Hong Kong | HKG.AS3.T1.GIANT — international BGP | 8 / 24GB / 640GB | 128TB @ 10Gbps | Monthly | 199.90 | [Check current price](https://www.dmit.io/aff.php?aff=12046) |

A note on what's deliberately missing: DMIT's Dedicated Cloud and BareMetal lines don't publish a comparable fixed price list the way the cloud instances do — the pricing you see depends on configured hardware and current stock. Rather than invent numbers for those, the honest move is to go look. 👉 [See what's currently listed and in stock](https://www.dmit.io/aff.php?aff=12046)

Japan is the third region, with Tokyo plans following the same Pro / EB / T1 structure and a Tier 1 entry plan starting at the same annual figure. It sits between Hong Kong and Los Angeles on both latency and price.

## Six things to check before you order anywhere

**Is transfer metered in one direction or both?** DMIT counts it in both directions, which is common for this segment but halves your effective allowance compared to providers who only count outbound.

**What happens when you exceed it?** This is where DMIT is genuinely better than average. Instead of suspending the machine, overage drops you to a throttled rate and keeps you online — 4Mbps on the Premium and Eyeball plans, and anywhere from 50Mbps to 1Gbps on Tier 1 depending on the plan. For a site that occasionally spikes, that's the difference between a slow evening and an outage.

**How many IPv4 addresses, and how fast can you get more?** Budget plans typically ship one IPv4 plus an IPv6 /64. Dedicated-class and larger plans get more. If you're running mail or multiple services that need separate reputations, count the IPs before you count the cores.

**Is IPMI included?** Without it, a machine that fails to boot means a support ticket and a wait. With it, you fix it yourself at 3am. Bare metal without out-of-band access is a trap.

**Payment and refund terms.** DMIT accepts PayPal, credit card and Alipay, which removes the foreign-card friction that stops a lot of buyers. Refund windows are narrow on this kind of product generally, so read the terms before a large prepay.

**Where support actually is.** Several third-party reviews of DMIT note that scheduled host maintenance doesn't always come with an advance email, and that written SLAs aren't the company's strong suit. If your business needs a contractual uptime guarantee with penalties attached, that's a real consideration — and it's the sort of thing a dedicated server with a managed SLA contract solves better than a cheap one does.

## How to actually decide

Work backwards from latency requirements and transfer volume, not from the word "dedicated."

If your users are outside mainland China, take a Los Angeles Tier 1 plan. LAX.AS3.T1.MINI at $21.90/month gets you 2 vCPU, 2GB RAM, 60GB SSD and 8TB on a 10Gbps port — more headroom than most dedicated boxes offered five years ago, at a price that doesn't require a business case.

If your users are in mainland China and you're weight-sensitive, Eyeball is the pragmatic pick. Same $34.90 as the Premium STARTER gets you 5TB instead of 3TB, on CMIN2 and AS9929 rather than CN2 GIA. You give up the best route in the catalogue and get 60% more transfer for it.

If mainland latency is the product — real-time apps, trading-adjacent work, anything where 40ms versus 150ms changes the outcome — you're in Premium territory, and Hong Kong Premium is the end of that road. 👉 [Compare the Hong Kong Premium plans](https://www.dmit.io/aff.php?aff=12046)

And if you've reached the point where a $199.90/month six-core instance still isn't cutting it? That's the actual signal to stop shopping for VPS plans and go find out what a BareMetal instance costs. Just don't start there.
