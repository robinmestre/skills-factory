# Experience Pool Patterns

> Learn from history. Don't reinvent failure.

This document catalogs 50+ common failure patterns across domains. Use these to generate historically-grounded attacks that reflect real-world failure modes.

---

## How to Use This Pool

1. **During Pre-Round Setup:** Load patterns relevant to the subject type
2. **During Red Team Phase:** Reference patterns when generating attacks
3. **Pattern matching:** Ask "Does this proposition have [pattern]'s warning signs?"

---

## Architecture Failures (12 patterns)

### ARCH-01: Distributed Monolith

**Pattern:** Microservices architecture that has all the complexity of distribution with none of the benefits.

**Warning Signs:**
- Services can't deploy independently
- Changes require coordinated releases
- Shared database between services
- Synchronous calls everywhere
- No clear service boundaries

**Historical Examples:**
- Numerous enterprise "microservices" migrations
- eBay's early SOA problems (pre-2010)

**Attack Template:**
"Your microservices migration shows signs of distributed monolith: [specific sign]. This creates all the operational complexity of microservices (N deployment pipelines, distributed debugging, network failures) with none of the benefits (independent scaling, team autonomy, fault isolation)."

---

### ARCH-02: Premature Optimization

**Pattern:** Optimizing for scale/performance before understanding actual requirements.

**Warning Signs:**
- Complex caching before measuring latency
- Sharding before hitting single-node limits
- Async processing before sync is proven slow
- "We'll need this at scale"

**Historical Examples:**
- Many startup over-engineering stories
- Twitter's original Ruby architecture was fine until it wasn't

**Attack Template:**
"You're building [complex optimization] before proving [simpler solution] is inadequate. This adds complexity you'll maintain forever, for problems that may never materialize. What's your evidence that [simple approach] won't work?"

---

### ARCH-03: Wrong Abstraction

**Pattern:** Creating abstractions at the wrong level, making changes harder not easier.

**Warning Signs:**
- DRY taken to extremes
- Changes require touching abstraction layer
- Abstraction doesn't match domain concepts
- "Flexible" code that's inflexible in practice

**Historical Examples:**
- Sandi Metz: "The wrong abstraction is more costly than duplication"
- Enterprise framework sprawl

**Attack Template:**
"Your abstraction [name] doesn't match how [domain concept] actually varies. When requirements change, you'll be fighting the abstraction instead of extending it. Three duplicated implementations are preferable to one wrong abstraction."

---

### ARCH-04: Integration Complexity Explosion

**Pattern:** Linear growth in systems creates exponential growth in integrations.

**Warning Signs:**
- N systems → N² potential integrations
- "We just need to connect X and Y"
- No integration platform/bus strategy
- Point-to-point connections multiplying

**Historical Examples:**
- Pre-ESB enterprise integration challenges
- Multi-cloud sprawl

**Attack Template:**
"You're adding system [N] to an environment of [N-1] systems. This creates [N×(N-1)/2] potential integration points. Without an integration strategy, you're on exponential complexity growth."

---

### ARCH-05: Event Sourcing Overreach

**Pattern:** Using event sourcing where simple CRUD would suffice.

**Warning Signs:**
- No audit requirements
- No time-travel queries needed
- Simple CRUD operations
- Team has no ES experience

**Historical Examples:**
- Many "modern architecture" overreach stories
- Greg Young warns against inappropriate ES use

**Attack Template:**
"Event sourcing adds projection complexity, eventual consistency challenges, and debugging difficulty. Your use case [description] doesn't require audit trail or temporal queries. Simple CRUD with audit logging achieves your goals with 10% of the complexity."

---

### ARCH-06: Single Point of Failure

**Pattern:** Critical path depends on one component with no redundancy.

**Warning Signs:**
- "It never goes down"
- One database, one server, one person
- No failover configuration
- No disaster recovery plan

**Historical Examples:**
- S3 us-east-1 outage (2017)
- Knight Capital ($440M loss from single deployment)

**Attack Template:**
"[Component] is in the critical path with no redundancy. When it fails—not if, when—your [consequence]. What's your RTO? What's your failover mechanism?"

---

### ARCH-07: Leaky Abstraction Debt

**Pattern:** Abstractions that leak, requiring knowledge of underlying implementation.

**Warning Signs:**
- Documentation says "but if you need performance..."
- Users routinely bypass the abstraction
- Abstraction has escape hatches everywhere
- "It's simple unless..."

**Historical Examples:**
- Joel Spolsky's "Law of Leaky Abstractions"
- ORM performance problems

**Attack Template:**
"Your abstraction [name] leaks in [ways]. Users must understand [underlying detail] to use it correctly. This negates the abstraction's value while adding a layer of indirection."

---

### ARCH-08: Cargo Cult Architecture

**Pattern:** Copying Netflix/Google/Amazon architecture without their context.

**Warning Signs:**
- "Netflix does it this way"
- Complexity not justified by scale
- Solutions to problems you don't have
- Pattern without understanding why

**Historical Examples:**
- Startups building for Google scale at MVP
- "We need Kubernetes" (for 3 containers)

**Attack Template:**
"You're adopting [pattern] because [BigCo] uses it. They have [10,000x your scale/team/complexity]. Your context: [your reality]. This pattern solves problems you don't have while creating problems you'll definitely have."

---

### ARCH-09: Data Consistency Theater

**Pattern:** Claiming consistency while actually having complex failure modes.

**Warning Signs:**
- "It's eventually consistent" (without defining "eventually")
- Optimistic locking without handling conflicts
- Distributed transactions with timeout gaps
- No compensation mechanisms

**Historical Examples:**
- Banking system consistency failures
- Double-booking in travel systems

**Attack Template:**
"Your consistency model is [stated model], but under [failure scenario], data becomes [inconsistent state]. What's your compensation mechanism? How do users discover inconsistencies? What's your SLA on consistency lag?"

---

### ARCH-10: Observability Debt

**Pattern:** Building complex systems without ability to understand their behavior.

**Warning Signs:**
- "We'll add monitoring later"
- Logs don't include correlation IDs
- No distributed tracing
- Metrics are infrastructure-only (no business metrics)

**Historical Examples:**
- Every "unknown unknown" outage
- MTTR dominated by diagnosis time

**Attack Template:**
"Your [complex system] has [observability gap]. When the first production incident occurs, MTTR will be dominated by 'what's happening?' not 'how do we fix it?'. Industry data shows debugging distributed systems without tracing takes 3-5x longer."

---

### ARCH-11: Coupling Through Shared Data

**Pattern:** Services coupled through shared database tables.

**Warning Signs:**
- Multiple services read/write same tables
- Schema changes require multi-team coordination
- Foreign keys across service boundaries
- "It's simpler to just share the database"

**Historical Examples:**
- Amazon's pre-SOA architecture challenges
- Most legacy monolith decomposition struggles

**Attack Template:**
"Services [A] and [B] share table [X]. Any schema change requires coordinated deployment. This coupling negates service independence—you have a distributed monolith with network overhead."

---

### ARCH-12: Migration Bridge Forever

**Pattern:** Temporary migration scaffolding becomes permanent.

**Warning Signs:**
- "We'll remove this after migration"
- Dual-write systems
- Feature flags for migration
- Translation layers between old and new

**Historical Examples:**
- Every long-running migration project
- Technical debt classics

**Attack Template:**
"Your migration plan includes [temporary bridge]. Migration bridges have a half-life of forever. Your 'temporary' code will still be running in 3 years because removing it is never the priority."

---

## Strategy Failures (10 patterns)

### STRAT-01: Market Timing Misjudgment

**Pattern:** Too early or too late to market window.

**Warning Signs:**
- "We're ahead of the market"
- "The market is ready now"
- No concrete timing evidence
- Ignoring failed predecessors

**Historical Examples:**
- WebVan (too early for grocery delivery)
- Microsoft Zune (too late for MP3 players)

**Attack Template:**
"Your timing assumption is [X]. Evidence: [Y]. Counter-evidence: [predecessors who failed with same timing assumption]. What's different now?"

---

### STRAT-02: Competitive Response Blindness

**Pattern:** Assuming competitors won't or can't respond.

**Warning Signs:**
- "They're too slow"
- "They don't understand this space"
- "It'll take them years"
- No competitive intelligence

**Historical Examples:**
- Every startup disruption that got counter-disrupted
- Quibi vs. TikTok

**Attack Template:**
"You assume [competitor] won't respond for [time]. Their resources: [X engineers, $Y funding]. Your differentiator can be copied in [Z months]. What's your moat when they do respond?"

---

### STRAT-03: Total Addressable Market Fantasy

**Pattern:** TAM calculations that include markets you can't realistically serve.

**Warning Signs:**
- "The market is $X billion"
- TAM = entire industry size
- No SAM/SOM breakdown
- No bottoms-up validation

**Historical Examples:**
- Most pitch deck TAM slides
- WeWork's "space as a service" market sizing

**Attack Template:**
"Your TAM is $[X]B. Let's work backwards: your SOM requires [Y%] penetration of [segment]. Your sales capacity can close [Z] deals/year. Time to $[target]: [calculation] years. Does that math work?"

---

### STRAT-04: Channel Dependency

**Pattern:** Strategy depends on channel you don't control.

**Warning Signs:**
- Google/Facebook/Apple as primary channel
- "We rank well in search"
- API-based business on platform you don't control
- Single customer segment

**Historical Examples:**
- Zynga's Facebook dependency
- Apps killed by App Store policy changes
- Google algorithm changes destroying businesses

**Attack Template:**
"Your strategy depends on [platform]. They can change terms, algorithm, or pricing with [notice period]. What's your contingency when—not if—they do?"

---

### STRAT-05: Technology-Push Fallacy

**Pattern:** Building technology looking for a problem.

**Warning Signs:**
- "This technology is amazing"
- No specific customer segment
- Features first, users second
- "We'll figure out the use case"

**Historical Examples:**
- Google Glass
- Many blockchain/AI projects

**Attack Template:**
"You've built [technology]. Who specifically has [problem]? What do they currently pay for inferior solutions? Why haven't you talked to them before building?"

---

### STRAT-06: First Mover Disadvantage

**Pattern:** Assuming first-mover advantage where fast-follower wins.

**Warning Signs:**
- "We'll be first"
- Market requires education
- High customer acquisition cost
- Low switching costs

**Historical Examples:**
- Friendster vs. Facebook
- Myspace vs. Facebook
- AltaVista vs. Google

**Attack Template:**
"You're first to [market]. First-mover advantage requires: high switching costs (you have [low]), network effects (you have [weak]), or patents (you have [few]). History shows fast-followers win in [your market type]."

---

### STRAT-07: Pricing Assumption Failure

**Pattern:** Pricing based on value delivered, not willingness to pay.

**Warning Signs:**
- "It's worth $X to them"
- No pricing experiments
- Single price point
- Anchored on cost-plus or competitor

**Historical Examples:**
- Enterprise software pricing disconnects
- Premium pricing in commodity markets

**Attack Template:**
"Your pricing assumes customers will pay [$X] for [value]. Evidence of willingness to pay: [none]. Competitors charge [$Y]. Your justification for [Z%] premium: [assumption]. Have you tested this?"

---

### STRAT-08: Synergy Illusion

**Pattern:** M&A or partnership synergies that never materialize.

**Warning Signs:**
- "1+1=3"
- Cost synergies that require firing
- Revenue synergies that require selling
- Cultural integration assumed easy

**Historical Examples:**
- AOL-Time Warner
- Most M&A value destruction studies

**Attack Template:**
"Your synergy case assumes [X]. Achievement requires [difficult integration]. Industry M&A synergy realization rate: ~50%. What's your integration plan for [specific challenge]?"

---

### STRAT-09: Unit Economics Denial

**Pattern:** Growth before unit economics proof.

**Warning Signs:**
- "We'll figure out monetization later"
- CAC > LTV with "it'll improve at scale"
- Losses on every transaction
- No clear path to contribution margin

**Historical Examples:**
- Many 2010s growth-at-all-costs startups
- MoviePass, Quibi

**Attack Template:**
"Your CAC is [$X], LTV is [$Y]. You lose [$Z] per customer. Your plan to fix: [scale]. Explain the mechanism by which scale improves CAC/LTV ratio when [specific reason it won't]."

---

### STRAT-10: Execution Complexity Underestimation

**Pattern:** Strategy requires execution capability beyond organizational capacity.

**Warning Signs:**
- "We just need to execute"
- Multi-geography, multi-product, multi-segment
- No similar execution history
- Aggressive timeline

**Historical Examples:**
- Uber's multi-market growth challenges
- Corporate transformation failures

**Attack Template:**
"Your strategy requires simultaneous excellence in [X], [Y], and [Z]. Your team has executed [none/one] of these before. What's your evidence you can do all three simultaneously?"

---

## Product Failures (10 patterns)

### PROD-01: Feature Creep Death

**Pattern:** Product becomes unusable under weight of features.

**Warning Signs:**
- Every customer request becomes a feature
- No feature deprecation
- UI complexity growing
- "We need feature parity with competitor"

**Historical Examples:**
- Microsoft Office ribbon
- Enterprise software bloat

**Attack Template:**
"Your roadmap adds [N] features this year. What features are you removing? Feature creep increases cognitive load, training time, and maintenance burden. What's your feature discipline?"

---

### PROD-02: Wrong Problem Solved

**Pattern:** Building a solution for a problem customers don't actually have.

**Warning Signs:**
- Solution looking for problem
- "Customers don't know they need this"
- No evidence of pain point
- Assumed vs. validated need

**Historical Examples:**
- Juicero
- Many "solution looking for problem" startups

**Attack Template:**
"What evidence do you have that [target customers] have [problem]? How do they solve it today? What do they currently pay? If the answer is 'nothing,' why do you think they'll pay you?"

---

### PROD-03: Adoption Resistance

**Pattern:** Users won't adopt because switching cost exceeds perceived benefit.

**Warning Signs:**
- Requires behavior change
- Competing with "good enough"
- Learning curve
- Network effects favor incumbent

**Historical Examples:**
- Every "better mousetrap" that failed
- QWERTY alternatives

**Attack Template:**
"Adoption requires users to [behavior change]. Their current solution is [good enough]. Your benefit: [X]. Their switching cost: [time + learning + risk]. Net value: [often negative]. How do you overcome adoption inertia?"

---

### PROD-04: Platform Dependency Trap

**Pattern:** Product exists only at platform's sufferance.

**Warning Signs:**
- Fills gap in platform's offering
- Platform could build it in a week
- No defensible differentiation
- Platform has done this before

**Historical Examples:**
- Twitter killing third-party clients
- Apple/Google absorbing app functionality
- Facebook Platform changes

**Attack Template:**
"Your product fills [gap] in [platform]'s offering. [Platform] has [resources]. If you're successful, you've just validated the market for them to enter. What's your defense when they do?"

---

### PROD-05: Metric Gaming

**Pattern:** Optimizing metrics that don't reflect actual value.

**Warning Signs:**
- Engagement metrics without retention
- Vanity metrics (downloads, signups)
- Short-term vs. long-term misalignment
- Goodhart's Law signs

**Historical Examples:**
- Growth hacking that drove churn
- Wells Fargo fake accounts

**Attack Template:**
"You're optimizing [metric]. But [metric] doesn't measure [actual value]. Example: [counter-case where metric is high but value is low]. What happens when you hit metric targets but don't have a business?"

---

### PROD-06: Feature Factory Mode

**Pattern:** Shipping features without measuring impact.

**Warning Signs:**
- Velocity as success metric
- No feature usage tracking
- "We shipped X features this quarter"
- No experiment framework

**Historical Examples:**
- Most enterprise software development
- John Cutler's "feature factory" posts

**Attack Template:**
"You shipped [N] features last quarter. What percentage improved [key metric]? If you don't know, you're building features that might not matter. What's your learning rate?"

---

### PROD-07: Market Segment Mismatch

**Pattern:** Building for one segment while targeting another.

**Warning Signs:**
- Product team uses it (not customers)
- Power users love it, mainstream confused
- "Users just need to be educated"
- SMB product, enterprise sales

**Historical Examples:**
- Developer tools sold to executives
- Enterprise products with consumer UX expectations

**Attack Template:**
"Your product is built for [segment A] but you're selling to [segment B]. [Segment B] needs [different things]. Your roadmap prioritizes [segment A features]. How does this mismatch resolve?"

---

### PROD-08: MVP Never Graduates

**Pattern:** MVP becomes the product, with MVP's limitations.

**Warning Signs:**
- "We'll fix it after launch"
- Technical debt from "temporary" solutions
- Features built on shaky foundation
- No refactoring time allocated

**Historical Examples:**
- Every startup that scaled with MVP architecture
- Facebook's PHP legacy

**Attack Template:**
"Your MVP has [technical compromise]. You've built [N features] on this foundation. Fixing it now requires [significant work]. Every day increases the cost. When does MVP become real product?"

---

### PROD-09: Premature Monetization

**Pattern:** Monetizing before product-market fit.

**Warning Signs:**
- Paywall before retention
- Complex pricing before understanding value
- Revenue pressure before growth
- "We need to prove business model"

**Historical Examples:**
- Startups that monetized too early and lost to free competitors

**Attack Template:**
"You're monetizing at [current retention rate]. At [rate], customers churn before you recover CAC. Premature monetization creates selection bias—you learn from paying users, not potential users."

---

### PROD-10: Design by Committee

**Pattern:** Product decisions made by consensus, resulting in mediocrity.

**Warning Signs:**
- Every stakeholder's feedback incorporated
- Features that satisfy no one fully
- Lack of clear product vision
- "Let's compromise"

**Historical Examples:**
- Corporate software design
- The Homer car (Simpsons episode)

**Attack Template:**
"Your design process involves [N stakeholders] with [competing priorities]. The result satisfies each stakeholder 60% and delights no one. Great products are opinionated. Who owns the vision?"

---

## Operational Failures (10 patterns)

### OPS-01: Alert Fatigue

**Pattern:** Too many alerts leading to ignored alerts.

**Warning Signs:**
- Hundreds of alerts daily
- Alerts ignored routinely
- "We'll tune alerts later"
- Alert on everything

**Historical Examples:**
- Knight Capital: alerts ignored
- Many outage post-mortems

**Attack Template:**
"You generate [N] alerts per day. Humans can meaningfully respond to ~[much smaller number]. Your critical alerts are buried in noise. When the real emergency comes, will anyone notice?"

---

### OPS-02: Knowledge Silo

**Pattern:** Critical knowledge exists only in one person's head.

**Warning Signs:**
- "Ask Sarah, she knows"
- No documentation
- Tribal knowledge
- Bus factor = 1

**Historical Examples:**
- Every organization after key departure
- Succession failures

**Attack Template:**
"[Person] is the only one who understands [critical system]. Their notice period is [X weeks]. Knowledge transfer takes [Y weeks]. If they leave unexpectedly, you have [gap]. What's your documentation strategy?"

---

### OPS-03: Runaway Operational Complexity

**Pattern:** Operational burden grows faster than value.

**Warning Signs:**
- "We're always firefighting"
- Incident rate increasing
- Team capacity consumed by operations
- No time for improvements

**Historical Examples:**
- Many microservices migrations
- Technical debt spirals

**Attack Template:**
"Your operational burden: [X hours/week]. Growth rate of burden: [Y%/month]. Team capacity: [Z hours/week]. At current trajectory, operations consume 100% of capacity in [N months]. What's your plan?"

---

### OPS-04: Configuration Drift

**Pattern:** Production configuration diverges from documented/intended state.

**Warning Signs:**
- Manual changes in production
- "Just SSH in and fix it"
- No infrastructure as code
- Inconsistent environments

**Historical Examples:**
- Many security breaches
- Phantom configuration issues

**Attack Template:**
"Your production configuration is managed [manually/partially]. Configuration drift causes [security risks, debugging confusion, unreproducible issues]. When did you last audit production vs. intended state?"

---

### OPS-05: Capacity Planning Blindness

**Pattern:** No visibility into when capacity will be exhausted.

**Warning Signs:**
- "We'll scale when we need to"
- No growth projections
- No capacity dashboards
- Reactive scaling only

**Historical Examples:**
- Black Friday crashes
- Viral load surprises

**Attack Template:**
"Your capacity: [current]. Growth rate: [X%/month]. Exhaustion date: [Y]. Lead time to add capacity: [Z]. If Z > time to Y, you'll hit capacity before you can scale. What's your buffer?"

---

### OPS-06: Incident Déjà Vu

**Pattern:** Same incidents repeating because root causes aren't fixed.

**Warning Signs:**
- "This happened before"
- Post-mortems without action items
- Action items not completed
- No incident categorization

**Historical Examples:**
- Recurring outages in many organizations
- Same mistakes repeated

**Attack Template:**
"In the last [period], [N%] of incidents were repeats of previous incidents. Your post-mortem completion rate: [X%]. You're spending more time fighting fires than preventing them."

---

### OPS-07: Deployment Fear

**Pattern:** Deployments are scary, so they happen infrequently, making them scarier.

**Warning Signs:**
- Deploy freezes
- "Don't deploy on Friday"
- Large batch deployments
- Manual deployment steps

**Historical Examples:**
- Waterfall to DevOps transformation struggles
- Big bang releases

**Attack Template:**
"You deploy [frequency]. Each deployment is [large/risky]. Fear of deployment leads to batching, which increases risk, which increases fear. How do you break this cycle?"

---

### OPS-08: Monitoring Theater

**Pattern:** Dashboards exist but don't lead to action.

**Warning Signs:**
- Dashboards no one looks at
- Metrics without owners
- No response procedures
- "We're monitoring it"

**Historical Examples:**
- Security theater equivalents in operations
- Compliance-driven monitoring

**Attack Template:**
"You have [N] dashboards. When [metric X] crossed [threshold Y] last month, what happened? If the answer is 'nothing,' you have monitoring theater, not operations."

---

### OPS-09: Testing in Production (Unintentionally)

**Pattern:** First time code runs in production-like conditions is production.

**Warning Signs:**
- "Works on my machine"
- Staging doesn't match production
- No load testing
- No chaos engineering

**Historical Examples:**
- Every "but it worked in staging" incident
- Performance surprises

**Attack Template:**
"Your staging environment: [description]. Production: [different description]. You're discovering production behaviors in production. What percentage of bugs are found before users do?"

---

### OPS-10: Toil Acceptance

**Pattern:** Manual work accepted as normal instead of automated.

**Warning Signs:**
- Manual deployments
- Manual data fixes
- Manual reporting
- "It's just how we do it"

**Historical Examples:**
- Pre-DevOps operational patterns
- Google SRE's toil concept

**Attack Template:**
"Your team spends [X%] time on manual operations. This doesn't scale. At [growth target], you need [Y more people] just for current toil. What's your automation roadmap?"

---

## Investment Failures (8 patterns)

### INV-01: Growth Fantasy Funding

**Pattern:** Investment based on hockey-stick projections with no basis.

**Warning Signs:**
- Year 3 revenue = 100x Year 1
- "If we just get X% of the market"
- No comparable growth examples
- Missing execution milestones

**Historical Examples:**
- Many failed growth-stage investments
- Overvalued unicorns

**Attack Template:**
"Your Year 3 projection: [$X]. Required growth rate: [Y%]. Comparable companies achieved: [Z%]. What's your evidence you'll grow [Y/Z]x faster than comps?"

---

### INV-02: Exit Assumption Gap

**Pattern:** Investment assumes exit path that doesn't exist.

**Warning Signs:**
- "We'll IPO in 5 years"
- "Strategic acquirer will pay X"
- No comparable exits
- Valuation requires unprecedented multiple

**Historical Examples:**
- Many late-stage markdowns
- Exit-less categories

**Attack Template:**
"Your exit assumption: [X]. Comparable exits in this category: [few/none]. Required multiple: [Y]x. Last similar company exited at: [Z]x. What drives your exit premium?"

---

### INV-03: Team Capability Discount

**Pattern:** Investment thesis requires team capability that isn't there.

**Warning Signs:**
- "They'll figure it out"
- Key hires needed but not made
- Execution track record missing
- Founder-market fit unclear

**Historical Examples:**
- First-time founder failures in complex markets
- Team gaps discovered post-investment

**Attack Template:**
"Your thesis requires excellence in [X]. Team experience in X: [limited/none]. Plan to acquire: [hire/learn]. Timeline: [aggressive]. What if the team can't level up fast enough?"

---

### INV-04: Competitive Moat Illusion

**Pattern:** Assumed moat that doesn't actually exist.

**Warning Signs:**
- "First-mover advantage"
- "Proprietary technology"
- "Brand"
- No quantified switching cost

**Historical Examples:**
- Disrupted incumbents
- Copied innovations

**Attack Template:**
"Your moat: [stated moat]. Competitor's path to replicate: [analysis]. Time to replicate: [estimate]. Your sustainable advantage after replication: [?]. Is this really a moat?"

---

### INV-05: Portfolio Correlation Risk

**Pattern:** Investment thesis correlated with existing portfolio risks.

**Warning Signs:**
- Multiple investments in same trend
- Sector concentration
- Macro sensitivity
- Factor exposure

**Historical Examples:**
- 2000 dot-com portfolio wipeouts
- 2022 growth portfolio drawdowns

**Attack Template:**
"This investment is exposed to [factor]. Your portfolio exposure to same factor: [X%]. If [factor reverses], portfolio impact: [Y%]. Are you diversified or concentrated in a thesis?"

---

### INV-06: Due Diligence Confirmation Bias

**Pattern:** Due diligence confirms existing enthusiasm rather than stress-tests.

**Warning Signs:**
- Bullish customer calls only
- Friendly reference checks
- Competitive analysis that dismisses threats
- "Everything checks out"

**Historical Examples:**
- Theranos investors
- Many fraud cases

**Attack Template:**
"Your due diligence: [approach]. Adversarial checks performed: [few/none]. What would a short-seller find? What did you look for that would kill the deal? Did you find any?"

---

### INV-07: Revenue Quality Blindness

**Pattern:** Revenue treated as revenue regardless of quality.

**Warning Signs:**
- One-time vs. recurring
- Concentration in few customers
- Unsustainable pricing
- Channel-dependent revenue

**Historical Examples:**
- Revenue restatements
- Churned revenue bases

**Attack Template:**
"Revenue composition: [X% from top customer, Y% one-time, Z% channel-dependent]. Revenue quality score: [low]. Sustainable revenue base: [much smaller]. Are you investing in $[headline] or $[sustainable]?"

---

### INV-08: Governance Gap

**Pattern:** Investment without sufficient governance/information rights.

**Warning Signs:**
- No board seat
- Limited information rights
- Minority position without protections
- "We trust the founders"

**Historical Examples:**
- Governance failures at portfolio companies
- Information asymmetry exploitation

**Attack Template:**
"Your governance rights: [limited]. Information flow: [quarterly decks]. If things go wrong, you'll know [too late]. What's your early warning system? What's your intervention capability?"

---

## Using the Experience Pool

### During Pre-Round Setup

1. Identify subject domain (Architecture, Strategy, Product, Operations, Investment)
2. Load relevant patterns (all patterns from domain + cross-cutting)
3. Note warning signs present in proposition

### During Red Team Phase

1. For each relevant pattern:
   - Does the proposition exhibit warning signs?
   - What's the attack based on this pattern?
2. Reference pattern ID in attack (e.g., "Per ARCH-01, this shows distributed monolith signs")

### Attack Generation Template

```
Pattern match: [ID] - [Name]
Warning signs present: [List]
Historical precedent: [Example]

Attack: "Your proposition exhibits [warning signs] characteristic of
[pattern name]. Historical examples ([companies/situations]) show this
leads to [failure mode]. Specifically: [application to this proposition]."
```

### Cross-Domain Pattern Application

Many patterns apply across domains:
- STRAT-10 (Execution Complexity) applies to architecture projects
- OPS-02 (Knowledge Silo) applies to strategy execution
- PROD-03 (Adoption Resistance) applies to internal tools

Don't limit pattern search to the proposition's primary domain.
