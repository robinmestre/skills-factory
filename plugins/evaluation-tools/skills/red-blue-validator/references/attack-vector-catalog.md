# Attack Vector Catalog

> Systematic categories for adversarial stress-testing of propositions.

This catalog provides 10 attack vector categories with 5+ specific attack patterns each. Use this to ensure comprehensive coverage when stress-testing decisions, strategies, architectures, and plans.

---

## Overview

| Category | Focus | Risk Level | Best For |
|----------|-------|------------|----------|
| ASSUMPTIONS | Hidden beliefs and dependencies | HIGH | All propositions |
| DEPENDENCIES | External/internal dependencies | HIGH | Architecture, Plans |
| EDGE_CASES | Boundary conditions | MEDIUM | Technical propositions |
| SCALABILITY | Growth/shrink capacity | HIGH | Architecture, Strategy |
| SECURITY | Vulnerabilities and threats | CRITICAL | Architecture, Security |
| COMPETITIVE | Market and competitor dynamics | HIGH | Strategy, Investment |
| OPERATIONAL | Day-to-day execution | MEDIUM-HIGH | Plans, Architecture |
| ECONOMIC | Financial viability | HIGH | Investment, Strategy |
| ORGANIZATIONAL | People and culture | MEDIUM-HIGH | All propositions |
| TEMPORAL | Timing and duration | HIGH | Plans, Strategy |

---

## 1. ASSUMPTIONS

**Definition:** Attacks targeting hidden, unstated, or fragile assumptions that underpin the proposition.

**Risk Level:** HIGH — Assumption failures often invisible until catastrophic

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 1.1 | **Hidden Assumption Exposure** | Unstated beliefs | "You're assuming customers will pay 20% more for this feature, but no pricing research validates this. Similar features in the market are free." |
| 1.2 | **Load-Bearing Challenge** | Critical assumptions | "Your entire ROI projection depends on 30% adoption rate. Industry benchmarks show 10-15% is realistic. If adoption is 15%, NPV goes negative." |
| 1.3 | **Temporal Decay** | Time-sensitive assumptions | "You're assuming current market conditions persist. Three similar assumptions failed in the 2022 downturn. What's your hedge if conditions change?" |
| 1.4 | **Behavioral Prediction** | Human behavior | "This requires sales team to change their compensation-optimized behavior. Historical change initiatives show 70% failure rate without structural incentive changes." |
| 1.5 | **Counterfactual Reversal** | Any assumption | "What if your core assumption—that users prefer mobile—is exactly wrong for this demographic? Desktop usage in B2B enterprise is 3x mobile." |
| 1.6 | **Assumption Stacking** | Compound assumptions | "Success requires A AND B AND C to all be true. Each has ~70% probability. Combined probability is 34%. Your plan has no fallback if any fails." |
| 1.7 | **Expert Blind Spot** | Domain expertise assumptions | "Your team's deep expertise in B2C may be a liability in B2B. The assumptions that work in consumer don't transfer to enterprise sales cycles." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Assumption is load-bearing AND confidence < 50% | "Market exists" with no validation |
| HIGH | Assumption is load-bearing OR confidence < 50% | Timeline assumption with no buffer |
| MEDIUM | Assumption affects efficiency, not viability | "Team will adopt new tools quickly" |
| LOW | Assumption is recoverable if wrong | "Documentation format preference" |

### Domain-Specific Variations

**Strategy:** Focus on market, competitive, and behavioral assumptions
**Architecture:** Focus on technical capability, team skill, and scaling assumptions
**Investment:** Focus on financial projections, market size, and exit assumptions
**Product:** Focus on user behavior, adoption, and value proposition assumptions

---

## 2. DEPENDENCIES

**Definition:** Attacks targeting external parties, technologies, or resources the proposition relies upon.

**Risk Level:** HIGH — External factors often uncontrollable

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 2.1 | **Vendor/Partner Failure** | Third parties | "Your critical path depends on [Vendor]. They've had 3 major outages this year, and their financial filings show $40M quarterly losses. What's your contingency?" |
| 2.2 | **Technology Obsolescence** | Tech dependencies | "This framework's core maintainer just left the project. NPM downloads are down 60% YoY. You're building on potentially abandoned technology." |
| 2.3 | **Team Capability Gap** | Internal skills | "This requires Kubernetes expertise. Your team's only Kubernetes experience is tutorials. Production K8s requires 6-12 months of painful learning." |
| 2.4 | **Resource Availability** | Resources | "Your plan assumes full team allocation, but Finance shows 40% of budget is at-risk pending Q3 results. What happens at 60% funding?" |
| 2.5 | **Single Point of Failure** | Critical dependencies | "[System/Person] is in the critical path for every milestone. If they're unavailable for 2 weeks, the entire project stops." |
| 2.6 | **API/Contract Changes** | External interfaces | "You're building on [Provider]'s API. Their terms allow 30-day deprecation notice. They deprecated a similar API last year with minimal warning." |
| 2.7 | **Supply Chain Risk** | Upstream dependencies | "Your component depends on 147 transitive dependencies. Any one with a security vulnerability or breaking change cascades to you." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | No fallback for critical dependency | Single cloud provider, no multi-cloud |
| HIGH | Fallback exists but is expensive/slow | Vendor replacement takes 6 months |
| MEDIUM | Fallback exists and is viable | Can switch auth providers in 2 sprints |
| LOW | Dependency is non-critical | Logging provider |

### Domain-Specific Variations

**Architecture:** API stability, library maintenance, infrastructure providers
**Strategy:** Partner reliability, distribution channels, market access
**Investment:** Key customer concentration, supplier relationships
**Plan:** Team availability, budget stability, approval dependencies

---

## 3. EDGE_CASES

**Definition:** Attacks targeting boundary conditions, unusual scenarios, and system limits.

**Risk Level:** MEDIUM — Often discoverable through testing, but costly if missed

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 3.1 | **Boundary Conditions** | Limits | "What happens when quantity = 0? When price = $0.001? When name = 10,000 characters? Your validation doesn't cover these and they'll hit production." |
| 3.2 | **Scale Extremes** | Very large/small | "Works with 100 users. What about 1 user (isolation bugs)? What about 1 million (n² algorithms)? Your test suite doesn't cover either extreme." |
| 3.3 | **Timing Edge Cases** | Temporal boundaries | "What if order is placed at 23:59:59 on Dec 31? Timezone handling, year rollover, and batch job timing all collide. This crashed [Company]." |
| 3.4 | **Concurrency/Race Conditions** | Parallel operations | "Two users clicking 'submit' simultaneously on the same inventory item. Your optimistic locking doesn't handle this; you'll oversell." |
| 3.5 | **Data Quality Edge Cases** | Inputs | "What if the input CSV has Unicode BOM? What if dates are DD/MM/YYYY in some rows and MM/DD/YYYY in others? Real-world data is messy." |
| 3.6 | **Partial Failure** | System states | "Service A succeeds but Service B fails mid-transaction. Your system has no compensation mechanism; data will be inconsistent." |
| 3.7 | **Recovery Edge Cases** | Error handling | "What if the system crashes during your crash recovery routine? Your recovery isn't idempotent; you'll double-process transactions." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Data loss or corruption | Non-idempotent recovery |
| HIGH | Financial impact or SLA breach | Race condition causing oversell |
| MEDIUM | User experience degradation | Timeout on large file upload |
| LOW | Cosmetic or minor UX issue | Long name truncation |

### Domain-Specific Variations

**Architecture:** Distributed system failures, state machine edge cases
**Product:** User behavior extremes, accessibility edge cases
**Data:** Schema edge cases, migration edge cases
**Operations:** Deployment edge cases, monitoring blind spots

---

## 4. SCALABILITY

**Definition:** Attacks targeting the proposition's ability to grow or contract.

**Risk Level:** HIGH — Scaling issues often not discovered until growth happens

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 4.1 | **Horizontal Scaling Limits** | Adding capacity | "Your architecture has shared state that prevents horizontal scaling. Adding servers won't help; you'll need a redesign at 10x load." |
| 4.2 | **Vertical Scaling Limits** | Bigger machines | "Your database fits in memory today. At 10x data, you need expensive hardware. At 100x, no single machine exists. Plan for this?" |
| 4.3 | **Cost Scaling Non-Linearity** | Economics | "Your costs scale O(n²) with users due to all-to-all notifications. At 100K users, notification costs alone exceed revenue per user." |
| 4.4 | **Operational Complexity Scaling** | Team capacity | "Each microservice adds on-call burden. At 50 services, you need 10 engineers just for operational support. Your team is 8 people." |
| 4.5 | **Data Volume Scaling** | Storage/processing | "At 10TB, your full-table scan analytics take 4 hours. At 100TB, they don't complete overnight. Your reporting SLAs will break." |
| 4.6 | **Organizational Scaling** | Team growth | "This architecture requires close coordination between teams. At 3 teams, it works. At 10 teams, coordination overhead dominates." |
| 4.7 | **Geographic Scaling** | Multi-region | "Your current latency (200ms) is acceptable in US-East. Expanding to APAC adds 300ms. Users in Singapore will have 500ms latency—unusable." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Scaling blocker with no known solution | Fundamental architecture limit |
| HIGH | Scaling requires major rework | Database redesign needed |
| MEDIUM | Scaling requires moderate investment | Need to add caching layer |
| LOW | Scaling is straightforward | Add more read replicas |

### Domain-Specific Variations

**Architecture:** Compute, storage, network, state management
**Strategy:** Market expansion, team growth, geographic reach
**Product:** Feature complexity, user segmentation, data volume
**Operations:** Monitoring scale, incident management, deployment frequency

---

## 5. SECURITY

**Definition:** Attacks targeting vulnerabilities, threat vectors, and compliance gaps.

**Risk Level:** CRITICAL — Security failures can be existential

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 5.1 | **Attack Surface Exposure** | Entry points | "Your API has 47 public endpoints. Each is an attack vector. Your security review covered 12 of them. The unreviewed 35 include admin functions." |
| 5.2 | **Data Breach Scenarios** | Data protection | "You store SSNs encrypted, but encryption keys are in the same database. A single breach exposes both. This is Security 101 failure." |
| 5.3 | **Authentication Gaps** | Identity | "Password reset sends token via email. Email is not a secure channel. Attacker with email access can hijack any account in minutes." |
| 5.4 | **Authorization Gaps** | Permissions | "IDOR vulnerability: changing user_id in the URL shows other users' data. Your tests don't cover horizontal privilege escalation." |
| 5.5 | **Compliance Violations** | Regulations | "PCI DSS requires network segmentation. Your architecture has the payment service in the same VPC as the logging service. Audit failure." |
| 5.6 | **Insider Threat** | Internal actors | "Database admin can export all customer data. No audit log, no DLP, no access review. One disgruntled employee = data breach." |
| 5.7 | **Supply Chain Attack** | Dependencies | "Your build pipeline pulls dependencies without integrity verification. A compromised npm package injects code into your production build." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Data breach or system compromise possible | Unpatched RCE vulnerability |
| HIGH | Significant security gap | Weak authentication |
| MEDIUM | Defense in depth weakness | Missing WAF |
| LOW | Security best practice gap | Verbose error messages |

### Domain-Specific Variations

**Architecture:** Infrastructure security, application security, data security
**Operations:** Incident response, access management, monitoring
**Compliance:** GDPR, HIPAA, PCI DSS, SOC 2

---

## 6. COMPETITIVE

**Definition:** Attacks targeting market dynamics and competitor responses.

**Risk Level:** HIGH — Competitive dynamics are unpredictable

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 6.1 | **Competitor Response** | Reactions | "You're launching Feature X. [Competitor] has 10x your engineering. They can clone it in 3 months and bundle it free. What's your moat?" |
| 6.2 | **Market Timing** | Windows | "The market window is 12 months. Your timeline is 15 months. By launch, early movers will have network effects you can't overcome." |
| 6.3 | **Differentiation Erosion** | Uniqueness | "Your differentiator—AI-powered recommendations—was unique 2 years ago. Now it's table stakes. 7 competitors have it. What's your new differentiation?" |
| 6.4 | **Pricing Pressure** | Economics | "[Competitor] is VC-funded and willing to operate at -30% margins to gain share. They can undercut you for 3 years. Can you survive that?" |
| 6.5 | **Strategic Moves** | Disruption | "What if [Big Tech] enters your market? They did this to [Similar Company] in 2021. Your market is interesting enough to attract them." |
| 6.6 | **Acquisition Disruption** | M&A | "Your key partner is in acquisition talks with [Competitor]. Post-acquisition, they'll be contractually obligated to deprioritize you." |
| 6.7 | **Network Effects** | Lock-in | "[Competitor] has 10x your users and 100x data. Their ML models get better; yours stagnate. This gap compounds; you'll never catch up." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Existential competitive threat | Big Tech market entry |
| HIGH | Significant competitive disadvantage | Price war with funded competitor |
| MEDIUM | Competitive pressure requiring response | Feature parity threat |
| LOW | Minor competitive noise | Small competitor launch |

### Domain-Specific Variations

**Strategy:** Market positioning, differentiation, go-to-market
**Product:** Feature competition, user experience, platform dynamics
**Investment:** Competitive moat, market share, exit scenarios

---

## 7. OPERATIONAL

**Definition:** Attacks targeting day-to-day execution and operational sustainability.

**Risk Level:** MEDIUM-HIGH — Operational issues compound over time

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 7.1 | **Complexity Explosion** | Manageability | "Your system has 47 services, 23 data stores, and 156 integration points. Debugging a user complaint touches 12 services. This is unmaintainable." |
| 7.2 | **Incident Scenarios** | Failure recovery | "At 3 AM, your primary database fails. MTTR is 4 hours. Your SLA is 99.9% (8.7 hours/year downtime). One incident uses half your annual budget." |
| 7.3 | **Recovery Time** | Resilience | "Full disaster recovery requires restoring 20TB from backup. At your network speed, that's 16 hours. Your RTO is 4 hours. The math doesn't work." |
| 7.4 | **Monitoring Gaps** | Observability | "Your system failed for 3 hours last month before anyone noticed. No alerting on the failure mode. How many other blind spots exist?" |
| 7.5 | **On-Call Burden** | Team health | "With 47 services, someone is paged 3x per night average. At 6 months, your best engineers will burn out and leave. This is unsustainable." |
| 7.6 | **Knowledge Concentration** | Bus factor | "[Engineer name] is the only person who understands the payment system. They're interviewing at [Company]. What happens when they leave?" |
| 7.7 | **Technical Debt Accumulation** | Maintainability | "You've accumulated 18 months of 'temporary' hacks. Each new feature takes 3x longer due to workarounds. Velocity will approach zero." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Operational viability at risk | SLA mathematically impossible |
| HIGH | Significant operational burden | Unsustainable on-call |
| MEDIUM | Operational inefficiency | Manual processes needed |
| LOW | Operational inconvenience | Documentation gaps |

### Domain-Specific Variations

**Architecture:** System operations, deployment, monitoring
**Plan:** Execution complexity, resource coordination
**Product:** Support burden, feature maintenance

---

## 8. ECONOMIC

**Definition:** Attacks targeting financial viability and sustainability.

**Risk Level:** HIGH — Financial failure is existential

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 8.1 | **Unit Economics Failure** | Per-unit costs | "Your CAC is $500, LTV is $400. You lose $100 on every customer. Scaling this just means losing money faster. Where's the fix?" |
| 8.2 | **Cost Structure Vulnerability** | Fixed costs | "Your fixed costs require $10M ARR to break even. You're at $3M with 20% growth. You need 6 more years of runway at current burn." |
| 8.3 | **Revenue Model Fragility** | Income sources | "78% of revenue comes from one customer segment. If that segment contracts (happened in 2022), you have no fallback." |
| 8.4 | **Funding/Cash Flow** | Capital | "Burn rate: $800K/month. Runway: 14 months. Next funding round at current metrics: unlikely. What's your path to sustainability?" |
| 8.5 | **Market Size Overestimation** | TAM/SAM/SOM | "Your TAM says $10B. Your serviceable market is $500M. Your realistic penetration is 5%. That's a $25M market. Enough?" |
| 8.6 | **Margin Compression** | Profitability | "Your gross margin is 70% today. With enterprise discounts, support costs, and infrastructure at scale, mature companies in your space see 40%. Plan for that?" |
| 8.7 | **Investment Return Failure** | ROI | "This initiative requires $5M and promises $8M return in 3 years. NPV at 15% hurdle rate is negative. This destroys shareholder value." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Financial viability at risk | Negative unit economics at scale |
| HIGH | Significant financial pressure | Runway < 12 months |
| MEDIUM | Financial inefficiency | Above-market CAC |
| LOW | Minor financial optimization | Suboptimal pricing |

### Domain-Specific Variations

**Investment:** ROI, NPV, exit scenarios, risk-adjusted returns
**Strategy:** Business model, pricing, cost structure
**Product:** Feature economics, monetization

---

## 9. ORGANIZATIONAL

**Definition:** Attacks targeting people, teams, and organizational dynamics.

**Risk Level:** MEDIUM-HIGH — Organizational issues are complex and slow to resolve

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 9.1 | **Capability Gaps** | Skills | "This requires ML expertise. Your ML team is 2 people with 3 years combined experience. Your competitors have 50 ML PhDs. You're outmatched." |
| 9.2 | **Key Person Dependency** | Individuals | "[Name] owns the customer relationships, technical knowledge, and team trust. If they leave, you lose customers, knowledge, and morale simultaneously." |
| 9.3 | **Cultural Resistance** | Adoption | "This change threatens middle management's power. They'll slow-roll implementation, redirect resources, and declare 'success' while nothing changes." |
| 9.4 | **Political Opposition** | Stakeholders | "[Executive] sees this as threatening their empire. They have board relationships and will torpedo this in executive meetings. Do you have air cover?" |
| 9.5 | **Change Fatigue** | Capacity | "This is the 4th major initiative this year. Teams are exhausted. Half-implemented changes litter the codebase. Another initiative will break the organization." |
| 9.6 | **Misaligned Incentives** | Motivation | "You're asking the sales team to sell differently, but their compensation is unchanged. They'll optimize for compensation, not your strategy." |
| 9.7 | **Communication Failure** | Information flow | "This requires coordination across 6 teams in 4 time zones. Your last cross-functional initiative had 3-week communication delays. Why will this be different?" |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Organizational blocker | Executive opposition with board support |
| HIGH | Significant organizational resistance | Cultural change required |
| MEDIUM | Organizational friction | Coordination challenges |
| LOW | Minor organizational overhead | Meeting scheduling |

### Domain-Specific Variations

**Strategy:** Executive alignment, organizational capability
**Plan:** Team capacity, stakeholder management
**Change:** Adoption, resistance, communication

---

## 10. TEMPORAL

**Definition:** Attacks targeting timing, duration, and temporal dependencies.

**Risk Level:** HIGH — Timing failures are often unrecoverable

### Attack Patterns

| # | Attack Pattern | Target | Steel-Manned Example |
|---|---------------|--------|---------------------|
| 10.1 | **Timeline Compression** | Deadlines | "Marketing committed to Q2 launch without consulting engineering. That's 6 weeks away. Your realistic estimate is 16 weeks. What gets cut?" |
| 10.2 | **Timeline Extension Impact** | Delays | "If this takes 2x as long (industry average for novel projects), you miss the market window. Second-mover in this market averages 1/3 the outcome." |
| 10.3 | **Market Window Closure** | Timing | "The regulatory window for this approach closes in 18 months. New regulations make this strategy illegal. You need 24 months. Too late." |
| 10.4 | **Technology Obsolescence** | Tech lifecycle | "You're building on [Technology] which is in maintenance mode. In 3 years, you'll need to migrate. Factor migration cost into your ROI?" |
| 10.5 | **Dependency Timing** | External timelines | "Your launch depends on [Partner] completing integration by Q3. They've missed their last 4 deadlines. Why will Q3 be different?" |
| 10.6 | **Resource Timing Conflict** | Availability | "You need the senior architect for 3 months. They're committed to Project X until Q4. Your timeline assumes they're available in Q2. They're not." |
| 10.7 | **Seasonal/Cyclical Risk** | Calendar | "You're launching e-commerce redesign in November. Holiday freeze starts Nov 15. You have 3 weeks of runway for a 6-week project. Risky timing." |

### Severity Benchmarks

| Severity | Criterion | Example |
|----------|-----------|---------|
| CRITICAL | Timing makes proposition impossible | Regulatory window closes |
| HIGH | Significant timing risk | Market window at risk |
| MEDIUM | Timing pressure but manageable | Tight but achievable deadline |
| LOW | Minor timing inconvenience | Suboptimal launch date |

### Domain-Specific Variations

**Strategy:** Market timing, competitive timing, regulatory timing
**Plan:** Resource timing, dependency timing, milestone timing
**Product:** Launch timing, feature timing, release cycles

---

## Usage Guidelines

### Selecting Attack Categories

1. **Start with subject type defaults** (see SKILL.md §3)
2. **Add categories based on context:**
   - Novel/innovative? Add ASSUMPTIONS
   - External dependencies? Add DEPENDENCIES
   - Scale expected? Add SCALABILITY
   - Sensitive data? Add SECURITY
   - Market-facing? Add COMPETITIVE
   - Complex execution? Add OPERATIONAL
   - Investment decision? Add ECONOMIC
   - Change initiative? Add ORGANIZATIONAL
   - Time-sensitive? Add TEMPORAL

3. **Minimum coverage:** At least 3 categories
4. **Aggressive intensity:** All applicable categories

### Applying Attacks

1. **Generate attacks per category** (minimum 2 per category)
2. **Steel-man each attack** (see steel-manning-protocol.md)
3. **Score severity** using benchmarks above
4. **Prioritize CRITICAL and HIGH** for Blue Team response

### Domain-Specific Emphasis

| Domain | Primary Categories | Secondary Categories |
|--------|-------------------|---------------------|
| Strategy | COMPETITIVE, ASSUMPTIONS, TEMPORAL | ECONOMIC, ORGANIZATIONAL |
| Architecture | SCALABILITY, DEPENDENCIES, EDGE_CASES | SECURITY, OPERATIONAL |
| Investment | ECONOMIC, ASSUMPTIONS, COMPETITIVE | TEMPORAL, ORGANIZATIONAL |
| Product | ASSUMPTIONS, COMPETITIVE, EDGE_CASES | SCALABILITY, OPERATIONAL |
| Plan | DEPENDENCIES, TEMPORAL, ORGANIZATIONAL | ASSUMPTIONS, OPERATIONAL |
| Security | SECURITY, DEPENDENCIES, EDGE_CASES | OPERATIONAL, SCALABILITY |
