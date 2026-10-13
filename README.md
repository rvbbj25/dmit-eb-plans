# DMIT EB: What Eyeball Actually Means, Which Plan Matches Your Carrier, and How to Order Without Overpaying for CN2 GIA

Search "DMIT EB" and you land in a pile of half-answers. Price lists with no platform attached. Forum posts yelling about restocks. Someone insisting Eyeball is a downgrade, someone else saying it's the best value in the lineup.

Both can be true. It depends on which carrier you're on, which hardware generation you bought, and whether you understood that you weren't buying CN2 GIA.

So here's the practical version: what Eyeball is, what it costs today, how it routes, and how to pick a tier without paying for optimization you'll never use.

## EB stands for Eyeball, and DMIT describes it plainly

Inside DMIT's cart, the Eyeball network profile carries this description:

> "This profile includes Tier 1 + Reasonable Effort For China Routing via CMIN2 or similar Chinese ISPs."

That phrase — reasonable effort — is the entire product. Premium (Pro) is CN2 GIA in both directions, and you pay for it. Tier 1 is plain international BGP with no China optimization at all. Eyeball sits in the middle: it prioritizes CN2-family and Chinese ISP peering for the return path, uses CMIN2 (China Mobile's second-generation international network) and AS9929 (China Unicom's premium CUG line), and leaves the rest to Tier 1 providers.

In practice, that combination gets most users 150–180ms from mainland China, which is respectable for the US West Coast. Independent tests on the LAX Eyeball series have measured around 163ms average across China with BBR enabled, with Beijing, Shanghai and Guangzhou all landing in the 150–175ms band.

## Where EB sits next to Pro and Tier 1

| Network profile | Routing you're buying | Price position | Who it's for |
| --- | --- | --- | --- |
| Premium (Pro) | CN2 GIA both directions, three-network direct | Highest | Telecom-heavy traffic, latency-sensitive production |
| Eyeball (EB) | CMIN2 + AS9929 return, "reasonable effort" China routing | Middle | Mobile and Unicom users, streaming and general workloads |
| Tier 1 (T1) | International BGP, no China optimization | Lowest | Overseas-facing projects, relays, budget boxes |

The pricing gap is where EB earns its place. Third-party trackers note that at a comparable tier, an Eyeball plan carries noticeably more monthly traffic than the Pro equivalent — one 2025 stock write-up put the difference around 50% more transfer for a similar price. If your traffic mostly comes in over China Mobile or Unicom, that's free capacity, because you were never going to benefit much from the GIA premium anyway.

If your users are almost all on China Telecom and you need the return path to be GIA rather than 9929/CMIN2 load-balanced, EB is the wrong line. That's the honest split.

## How Eyeball routes, carrier by carrier

**China Mobile.** CMIN2 in both directions. This is the best-case scenario for EB, and it's the reason mobile users tend to be the loudest fans of the series.

**China Unicom.** AS9929 both ways — Unicom's premium international line (CUG VIP), a clear step above the ordinary 4837 backbone in evening peak conditions.

**China Telecom.** Outbound is the higher-quality path; the return leg is where EB differs from Pro. Multiple traceroutes on the LAX EB plans show telecom return traffic going over AS9929 or CMIN2 on a load-balanced basis, not pure CN2 GIA. Early on, DMIT shifted some telecom return traffic onto 9929 specifically to relieve CMIN2 congestion at peak.

The published test IP for the Los Angeles Eyeball line is 154.17.226.2. Ping it before you buy anything — it takes thirty seconds and it's more reliable than any review, mine included, because routes get rebalanced.

## Los Angeles Eyeball plans and prices

DMIT sells the same LAX EB tier lineup on three hardware platforms: AS3 (AMD EPYC 7003), AN4 (EPYC 9004) and AN5 (EPYC 9005, with DDR5 ECC memory). The specs per tier are the same; the price is not. Newer generations cost more, which is exactly why you'll see conflicting prices online — one page is quoting AS3, another is quoting AN5. DMIT has also been moving the lineup forward, with the EB series migrating to AN5 through late 2025.

Here's the AS3 Eyeball lineup, which is the generation most listings quote. All prices are monthly, USD, with traffic counted bidirectionally:

| Plan | vCPU | RAM | SSD | Monthly traffic | Port | Over-quota speed | Price / month | Order |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AS3.EB.TINY | 1 | 2 GB | 20 GB | 1.5 TB | 2 Gbps | 4 Mbps unlimited | $10.90 | [Check current TINY stock and price](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.AS3.EB.Pocket | 2 | 2 GB | 40 GB | 3 TB | 4 Gbps | 4 Mbps unlimited | $16.90 | [Order the Pocket plan](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.AS3.EB.STARTER | 2 | 2 GB | 80 GB | 5 TB | 10 Gbps | 4 Mbps unlimited | $34.90 | [Order the STARTER plan](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.AS3.EB.MINI | 4 | 4 GB | 80 GB | 10 TB | 10 Gbps | 8 Mbps unlimited | $62.90 | [Order the MINI plan](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.AS3.EB.MICRO | 4 | 4 GB | 160 GB | 14 TB | 10 Gbps | 8 Mbps unlimited | $87.90 | [Order the MICRO plan](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.AS3.EB.MEDIUM | 6 | 8 GB | 160 GB | 30 TB | 10 Gbps | 10 Mbps unlimited | $199.90 | [Order the MEDIUM plan](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.EB.LARGE | 8 | 16 GB | 320 GB | 50 TB | 10 Gbps | 10 Mbps unlimited | from $459.90* | [Check LARGE pricing and availability](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |
| LAX.EB.GIANT | 12 | 24 GB | 640 GB | 100 TB | 10 Gbps | 10 Mbps unlimited | from $619.99* | [Check GIANT pricing and availability](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=eyeball&aff=12046) |

*Third-party trackers disagree on the exact LARGE and GIANT list prices and which platform (AS3 or AN5) each is sold on — figures in the $459.90 to $499.90 range for LARGE and $619.99 to $929.99 for GIANT both appear. Confirm the live number in the cart before ordering.

The same tier on AN5 costs more: the TINY spec is listed around $10.90 on AS3 but roughly $13–15 on the newer platforms depending on which tracker you read. You're paying for a faster single-core chip and DDR5, not for more traffic.

One thing worth knowing regardless of tier: DMIT doesn't cut you off when you exhaust your monthly transfer. The port drops to the over-quota speed listed above and the box keeps running. For a small site or a personal service, that's a much softer failure mode than a suspension.

## Which tier to actually pick

**TINY ($10.90/mo)** is a 1-core, 2GB box with 1.5TB of traffic. Fine for a proxy, a small site, a dev environment, or a monitoring node. If you're just testing whether Eyeball's routing works for your carrier, start here.

**Pocket ($16.90/mo)** is the tier most people should look at first. Two cores, 3TB, and a 4Gbps port for six dollars more. Third-party reviews of the 2-core Pocket plan measured disk I/O above 1GB/s and speed tests around 500Mbps in both directions — comfortably more than most individual connections will push.

**STARTER ($34.90/mo)** doubles the disk to 80GB and the traffic to 5TB, and gets you a 10Gbps port. Justified if you're running a site with real images, or pushing traffic through.

**MINI and MICRO ($62.90 / $87.90)** are the 4-core, 4GB steps, with 10TB and 14TB respectively. Reviews note that Windows requires 4GB of RAM or more, so these are also the cheapest tiers where a Windows install is realistic.

**MEDIUM and above** add a second IPv4 and raise the over-quota throttle to 10Mbps. That's enterprise-shaped capacity — 30TB to 100TB a month.

### The annual specials that keep selling out

Watching the "DMIT EB restock" threads, the plans people actually fight over aren't in the table above. They're the limited annual ones:

- **LAX.EB.WEE** — 1 vCPU, 1GB RAM, 20GB SSD, 1000GB transfer at 1Gbps, $39.90/year
- **LAX.EB.CORONA** — 1 vCPU, 1GB RAM, 20GB SSD, 2000GB at 2Gbps, $49.90/year, later upgraded from 1.5TB to 2TB
- **LAX.EB.FONTANA** — 2 vCPU, 2GB RAM, 40GB SSD, 4000GB at 4Gbps, around $100/year

Per-year pricing works out far below the monthly tiers, which is why they disappear within days of a restock and why DMIT periodically retires them. If your budget is under $100 a year, these are the plans to watch for rather than the monthly lineup. 👉 [Open DMIT's order page to see what's currently in stock](https://www.dmit.io/aff.php?aff=12046)

## Hong Kong and Tokyo Eyeball, briefly

Eyeball is not just a Los Angeles thing. DMIT runs HKG.EB (three-network CMI return) and TYO.EB, and Hong Kong EB is split across AS3 and AN5 platforms much like LAX.

Two things matter more than the numbers here. First, Hong Kong Eyeball pricing is several times the LAX band — entry plans are tracked in the $25–40/month range, and the top tiers run into the hundreds. You're paying for proximity to the mainland, not for more CPU. Second, DMIT marks the Hong Kong Eyeball network as Beta, with routing and product specs subject to change. If you need a Hong Kong node with a settled, guaranteed route, that caveat should factor into your decision more than a few dollars of price difference.

Trackers also report that the older HKG EBv2 line is being retired, with affected users offered recurring discounts in the 20–30% range to migrate onto the current version. If you're holding an EBv2 plan, that's a support-ticket conversation worth having before the cutoff.

## Discount codes circulating for Eyeball

These are worth thirty seconds of your time at checkout, and no more than that — DMIT's codes are tied to specific product lines and billing cycles, and older ones expire without ceremony.

**LAX EB, quarterly billing or longer:**
`LAX-EB-LAUNCH-NON-MONTHLY-RECURRING-20OFF` — a 20% recurring discount. It's been referenced in stock write-ups through 2025 and into 2026 listings, and the "recurring" part means it applies to renewals, not just the first invoice. Month-to-month orders are excluded.

**Seasonal LAX promotions (verify before relying on them):**
The Christmas campaign offered 15% recurring plus 10% account credit on annual Pro/EB orders at STARTER and above, and 10% recurring plus 5% credit on other LAX Pro/EB orders. Campaign codes like these usually stop validating once the promotion window closes.

**Hong Kong EB:**
`HKG-EB-V2-ANNUALLY-15OFF-RECUR` for annual orders at TINY and above, and `HKG-EB-UPGRADE-TO-V2-15OFF-RECUR` for users migrating from Lite to EB via a support ticket.

The mechanics are the same either way: pick your plan and billing cycle first, then paste the code and hit Validate. If it doesn't validate, it isn't active for that combination — there's no workaround worth chasing.

## What independent tests actually found

Hardware on the AS3 platform is AMD EPYC 7003 series, and the AN5 refresh moved the Eyeball line to EPYC 9005 with DDR5 ECC. Reported figures for the AS3 2-core Pocket: Geekbench 5 single-core in the 1398–1454 range, 64k mixed disk I/O at roughly 1GB/s, and mainland ping averages near 163ms with BBR on.

The 2-core STARTER-class tests reported similar results — EPYC 9654, single-core around 1398, dual-core around 2414, disk around 960MB/s. Nothing here looks like a budget box that got cut down to fit a price point.

IP reputation and streaming unlock is where the reviews genuinely disagree. Some testers report Netflix, YouTube and Amazon Prime Video working on the LAX EB IPs they drew; others report that Netflix licensed content and Disney+ don't unlock, with IPv6 performing worse than IPv4. The honest read is that unlock behavior is a per-IP lottery rather than a feature DMIT sells — check the IP you actually receive instead of trusting any table. ChatGPT and TikTok access is reported as working across most tests.

If you get an IP that's blocked, DMIT lets you replace it free once every 15 days, with a $5 charge for replacements beyond that frequency.

## Ordering checklist

Run through these before you pay, in this order:

1. **Ping 154.17.226.2** and confirm the LAX Eyeball route behaves on your carrier.
2. **Decide the platform.** AS3 is the cheaper option; AN5 costs more for newer silicon. Both run the same tiers.
3. **Choose a billing cycle.** Quarterly or annual unlocks the recurring codes; monthly generally doesn't.
4. **Check stock first.** The annual specials and several monthly tiers go out of stock regularly, and the restocks are unpredictable.
5. **Validate your code** at checkout before completing the order. Codes are product-line and cycle specific.
6. **Plan for the throttle**, not a shutdown, if you expect to exceed the transfer allowance.

### Common questions, answered quickly

**Is EB a downgrade from Pro?** Only on the China Telecom return path. Everywhere else you're trading a little routing purity for more traffic and a lower price.

**Can I use EB for a website?** Yes. The bottleneck for most sites is CPU and disk, and both are strong here — the network profile is the differentiator, not the hardware.

**Does it work for streaming?** Sometimes, depending on the IP. Don't buy it as a streaming-unlock solution.

**Windows support?** Reviews indicate 4GB of RAM or more, so MINI and up.

The Eyeball line exists because not everyone needs CN2 GIA in both directions, and paying for it anyway is the most common waste of money in this product category. If your traffic comes in over Mobile or Unicom, or you mostly care about getting a fast pipe on a US West Coast node without a Pro-sized invoice, LAX EB is the tier lineup that makes sense — and the TINY at $10.90 a month is a cheap way to find out whether it does. 👉 [Check live LAX Eyeball pricing and stock on DMIT](https://www.dmit.io/aff.php?aff=12046)
