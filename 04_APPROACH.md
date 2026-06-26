### How I think about engineering

- **Multi-tenancy is a design decision, not a feature flag.**
  Tenant isolation, RBAC scope, and cost-center modeling have to be
  designed into the schema, not bolted on later. I've seen both sides of
  this — first retrofitting multi-tenancy into BTPN Syariah's banking
  platform serving 4.1 million users, then building SaaS products
  from scratch with multi-tenancy as a first-class constraint. The
  difference is night and day. Retrofitting into a single-tenant
  codebase is where most SaaS products quietly die — usually around the
  third enterprise customer, when someone asks &ldquo;can we just add one
  more tenant?&rdquo; and the schema says no. Getting it right early is
  expensive in design time. Getting it wrong is expensive in years.

- **Contracts prevent drift — especially with AI agents.**
  API specs, DB schemas, and service boundaries are the source of truth.
  Everything else is an implementation detail. I learned this the hard
  way building ML infrastructure at BTPN: OJK compliance meant every
  credit-scoring prediction had to be fully reconstructable — who
  requested it, when, with what input, what came out. Then again building
  RAG pipelines where the backend contract matters as much as the model
  itself. LLMs write code fast but respect exactly zero invariants —
  which is why contract-driven workflows matter more now, not less.

- **If it's not observable, it's not shipped.**
  The LGTM stack — Loki, Grafana, Tempo, VictoriaMetrics — is baseline
  on every project I own. But the real lesson came from a fuel anomaly
  detection system I built for mining operations: pure sensor data missed
  the theft patterns. It was the combination of GPS movement telemetry
  with fuel readings that made the anomalies visible. Three theft
  incidents caught in the first month, 8&ndash;12% annual fuel cost
  reduction. The takeaway: observability isn't just dashboards — it's
  knowing which signals actually matter and correlating across layers
  that weren't designed to talk to each other.

- **Build for the worst-case scenario.**
  The hardest engineering lessons I've had all share a pattern: the
  system worked fine in normal conditions. Then the VSAT link to a
  remote mine site dropped to 512kbps — or a self-intersecting polygon
  silently corrupted every downstream spatial query — or field agents in
  dead zones needed offline sync without losing loan disbursement data.
  At BTPN I cut data loss from 23% to zero with offline-first
  architecture. At Petrosea I built geofence breach detection that ran
  under 2 seconds against 50,000 spatial events per second. Happy-path
  engineering is easy. The edge cases are where systems earn their
  existence.

- **AI-assisted, not AI-dependent.**
  Claude Code, MCP servers, and semantic search are force multipliers — I
  use them aggressively. But I still read every diff, own every
  deployment, and stand behind every line that ships. The leverage
  transfers; the accountability doesn't. Tools accelerate execution,
  but they don't replace knowing why a design decision was made. If I
  can't explain the trade-off to another engineer at 11 PM during an
  incident, I shouldn't have shipped it.
