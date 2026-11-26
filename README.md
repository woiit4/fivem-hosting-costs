# FiveM Server Hosting: What It Really Costs, How Many Slots You Actually Get, and How Much RAM Your City Needs (With Priced-Out Los Angeles VPS Options)

A FiveM server bills you twice. One payment goes to whoever rents you the machine, and a second goes to Cfx.re once you pass 48 concurrent players, starting at $15/mo + VAT for Element Club Argentum. Game-server plans big enough to run QBCore or ESX with a real population currently sit between roughly $5 and $48 a month. A self-managed VPS in Los Angeles, which is what SixtyNet sells, starts at $200 a year for 2 cores and 2 GB.

Below I've priced both sides using published numbers: Cfx.re's official slot tiers, the RAM guidance hosts put in their own FAQs, and the SixtyNet configurations that are listed with prices. No estimates or "usually around" figures.

## Quick answer before the details

> Most new cities never pass 48 players, so a 4 GB game-server plan plus the free Cfx.re server key covers them completely. If you want root access, dedicated CPU and the freedom to run other services on the same box, SixtyNet's **LAX-MICRO** (4 cores, 4 GB RAM, 80 GB NVMe, 10 TB traffic, DDoS protection, Los Angeles) is **$400/year**, billed annually.
>
> 👉 [See SixtyNet's current VPS plans and prices](https://sixtynet.net/aff.php?aff=39)

## SixtyNet's listed plans, priced out

SixtyNet is a VPS provider, not a one-click FiveM game panel. That distinction matters for how you use it, and I'll come back to the setup work it implies. These are the four plans with published prices on the Los Angeles network, all with DDoS protection and annual billing:

| Plan | vCPU / RAM | NVMe storage | Traffic & port | Price (annual) | Order |
| --- | --- | --- | --- | --- | --- |
| LAX-STARTER | 2 cores / 2 GB | 40 GB (12,500 IOPS) | 5 TB, 2 Gbps | $200/yr (list $240) | [Order LAX-STARTER](https://sixtynet.net/aff.php?aff=39) |
| LAX-MICRO | 4 cores / 4 GB | 80 GB (12,500 IOPS) | 10 TB, 4 Gbps | $400/yr (list $480) | [Order LAX-MICRO](https://sixtynet.net/aff.php?aff=39) |
| LAX-MEDIUM | 8 cores / 8 GB | 160 GB (25,000 IOPS) | 20 TB, 10 Gbps | $800/yr (list $960) | [Order LAX-MEDIUM](https://sixtynet.net/aff.php?aff=39) |
| LAX-LARGE | 8 cores / 16 GB | 320 GB (25,000 IOPS) | 40 TB, 10 Gbps | $1,600/yr (list $1,920) | [Order LAX-LARGE](https://sixtynet.net/aff.php?aff=39) |

Two things the table doesn't show. The same page lists a China Unicom Premium group starting at $2,500/year for the entry configuration, and a set of residential-IP configurations at various core counts. Those residential products carry port restrictions (80 and 443 are closed for IP risk-control reasons, and some configurations reject external probes and scans entirely), so check the exact configuration against your game port before ordering one for a public server. The LAX plans above are the straightforward choice for a FiveM box.

The other constraint is location. Everything is in Los Angeles. If your community is in Europe, a roleplay server with 90 ms of baseline ping feels wrong no matter how good the hardware is.

## The 48-player number is where your bill changes

Cfx.re controls the ceiling, and no hosting plan raises it. By default a FiveM server supports up to 48 players using OneSync Infinity. Go past that and you buy an Element Club subscription from Cfx.re directly through their portal, on top of your hosting invoice. Current tiers:

| Subscription | Price | Player ceiling | Extras |
| --- | --- | --- | --- |
| Argentum | $15/mo + VAT | 64 with OneSync and Infinity (up from the default 48) | Element Club access, custom clothing streaming |
| Aurum | $25/mo + VAT | 64 with OneSync, 128 with OneSync Infinity | Same, plus the clothing streaming EUP needs |
| Platinum | $50/mo + VAT | 128 with OneSync, 2048 with OneSync Infinity | Custom animated server icon, magenta highlight in public listings |

Every tier is quoted plus VAT, and Cfx.re notes perks can take up to 6 hours to activate after payment. So the honest maths for a 128-slot city is hosting plus $25 a month to Cfx.re, not hosting alone. A host advertising "up to 2048 players" is quoting the platform ceiling you reach with the $50 Platinum tier, which you buy somewhere else.

If you're sizing a machine for a population you haven't hit yet, the plan below is the one that maps to the 64-to-128 range without overspending on hardware:

👉 [Check the LAX-MICRO configuration and current price](https://sixtynet.net/aff.php?aff=39)

## How much RAM does a FiveM server actually need?

Three tiers cover almost every server, based on the guidance BruceNode publishes in its own FAQ. It's one host's rule of thumb, but it lines up with what the other providers recommend for similar workloads:

| Your server | RAM | Why |
| --- | --- | --- |
| Basic RP or freeroam, around 32 players | 4 GB minimum | Enough for a light framework and a modest resource list |
| Full QBCore or ESX, 64+ players, custom scripts | 8 GB minimum | Frameworks, database and scripts run concurrently |
| Heavy RP with vehicle packs, EUP and 100+ players | 12–16 GB | Streaming assets and peak-hour population |

Cfx.re's own system requirements are broad: an x86-64 machine on Linux or Windows (7/2008 R2 or newer), decent upstream connectivity, and preferably a multi-core processor. That "preferably multi-core" line is why the 8-core LAX-MEDIUM and LAX-LARGE exist. A single-core 2 GB box will boot a FiveM server and then struggle the moment a few players stream custom vehicles into the same street.

Storage matters more than people expect, and not for the reason you'd guess. A vanilla server is small, but a city with MLOs, EUP uniforms, vehicle packs and a full map set will burn through tens of gigabytes, and NVMe keeps asset streaming from becoming the bottleneck. The 40 GB on LAX-STARTER is enough to start; the 160 GB on LAX-MEDIUM is what a year-old roleplay city usually looks like.

## Three things in the fine print that change the decision

**Refund windows vary far more than the marketing pages admit.** Gravel Host offers 72 hours, but only on a new customer's first hosting purchase, once per account for life, minus processing fees, and renewals, add-ons, upgrades and free-trial products are excluded. An initial annual plan can qualify for a prorated refund within 7 days instead. Sparked Host runs 48 hours plus a 24-hour free trial. Shockbyte advertises a 72-hour self-serve refund. All three are real policies, and all three mean something different. SixtyNet's refund terms aren't spelled out in the plan listings I read, so confirm the window at checkout before you pay a year upfront.

**EUP uniforms need the $25 tier, not the $15 one.** BruceNode states plainly that streaming EUP requires a Cfx.re Element Club Aurum subscription at $25/mo to Cfx.re. If your city's police department is the centrepiece of the roleplay, that cost is not optional and it doesn't appear on any hosting invoice.

**Your server key is free.** Register at portal.cfx.re to generate it, with no cost, no expiration and no limits. Element Club subscriptions are optional and only needed for higher player counts or EUP streaming. Nobody should be selling you a key.

👉 [Review SixtyNet's plans before you commit a year](https://sixtynet.net/aff.php?aff=39)

## What the rest of the market charges, for comparison

These are published prices from hosts selling one-click FiveM game servers. No links, just numbers to sanity-check whatever quote you're looking at.

| Host | Entry plan | Largest plan | Refund terms |
| --- | --- | --- | --- |
| Gravel Host | 3.5 GB DDR4, $5.00/mo | 12 GB, $23.00/mo | 72h, first purchase only, once per account, fees deducted |
| Sparked Host | 2 GB / 2 vCPU, $4.78/mo | 16 GB / 4 vCPU, $38.24/mo | 48h refund, 24h free trial |
| BruceNode | 2 GB / 8 players, $8.00/mo | 16 GB / 128+ players, $48.00/mo | Not stated on the plan page |
| Shockbyte | 3 GB / 12 players, price not listed | 6 GB / unlimited players, $24.99/mo | 72h self-serve |

Two warnings when you read tables like this. First, advertised player counts don't override the 48/64/128 ceiling, so a "128 players" label on an 8 GB plan still requires an Aurum subscription to be true. Second, plan names repeat across hosts with completely different contents: Gravel Host's Zentorno is 6 GB at $7.00/mo, Sparked Host's Zentorno is 12 GB at $28.68/mo. Always read the RAM figure, never the name.

Sparked Host's add-on pricing is also worth knowing because it's easy to miss: Game Management runs +$20.00/mo (10 mod installs and 10 map or save uploads per month), a dedicated IP is +$6.00/mo, and a Discord support channel is +$3.00/mo. A $9.56 plan can turn into $38.56 before you've installed anything.

## What you take on with a VPS instead of a game panel

Renting a VPS means you are the panel. You install the FXServer artifacts, set up txAdmin, configure MariaDB, write your server.cfg, open the game port, and handle artifact and resource updates yourself. None of the one-click framework recipes a game host provides come with the box.

What you get in return is root access, dedicated CPU and RAM rather than shared slices, the ability to run a web dashboard or a database on the same machine, and DDoS protection included on the LAX plans. For someone already comfortable on a Linux command line, that's a fair trade. For someone whose first FiveM server this is, it's a weekend of documentation reading before the first player connects.

The cash-flow difference is real too. $400 upfront for LAX-MICRO is roughly $33 a month, more than a 4 GB game-server plan costs monthly elsewhere. You're paying for control, not for savings.

## FAQ

**How many players can join by default?** Up to 48, using OneSync Infinity, with no subscription at all.

**Where does the 2048-player figure come from?** The Platinum Element Club tier at $50/mo + VAT, which raises the OneSync Infinity ceiling to 2048. Perks can take up to 6 hours to activate.

**Is txAdmin an extra purchase?** No. It ships with FiveM, and game hosts preinstall it. On a VPS you install and configure it yourself.

**ESX, QBCore or Qbox?** BruceNode's view, and it's one host's opinion rather than a consensus: ESX is the original roleplay framework with the largest script ecosystem and the most tutorials and resources; QBCore is the more modern alternative with cleaner architecture and easier setup; for new servers they recommend Qbox, the evolution of QBCore, for the best developer experience.

**What are the official system requirements?** x86-64, Linux or Windows 7/2008 R2 or newer, decent upstream connectivity, multi-core processor preferred.

## Which one to order

Match the plan to the population you expect in three months, not the one you have on launch night.

- **Under 48 players, light scripts:** a 4 GB game-server plan, no subscription. LAX-MICRO at $400/year if you'd rather manage the machine yourself.
- **64 to 100 players on QBCore or ESX:** 8 GB of RAM plus Argentum at $15/mo, or Aurum at $25/mo if you're going past 64. LAX-MEDIUM matches this tier on the VPS side.
- **100+ players with EUP:** 12–16 GB, Aurum at $25/mo as the floor, Platinum if you want the 128+ headroom. LAX-LARGE covers the hardware.
- **You want root, or you're running more than the game server:** VPS, and accept the Los Angeles location and annual billing.

Before you pay, confirm four things: whether the price includes VAT, the exact refund window and its conditions, whether txAdmin comes preinstalled or you install it, and the ping your players will actually get from the data centre. On an annual plan that last one is worth more attention than the discount.

👉 [Open SixtyNet's order page and pick the plan that matches your slot count](https://sixtynet.net/aff.php?aff=39)
