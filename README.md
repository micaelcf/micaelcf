# Micael Fernandes

**Full-stack engineer — TypeScript · Go · Python.** I build systems where the hard part is state: rounds that must settle exactly once, catalogs that swallow hundreds of thousands of rows, maps that answer *"can I actually get in here?"*

Belém, Pará — Brazil · [micael-dev.vercel.app](https://micael-dev.vercel.app) · [LinkedIn](https://www.linkedin.com/in/micael-fernandes21/)

---

## Selected work

| Project | What it is | Why the code is worth reading |
| --- | --- | --- |
| **[crash-game-cassino](https://github.com/micaelcf/crash-game-cassino)** | Real-time multiplayer Crash casino | Crash points are **provably fair** — a SHA-256 hash chain plus HMAC makes every round auditable after the fact. Two NestJS services settle money across a **RabbitMQ outbox/inbox**, so a lost message can't double-spend a wallet. The server owns the round clock; clients project the multiplier locally from `m(t) = e^(k·Δt)`, so no tick is ever trusted from the browser. Kong + Logto OIDC at the edge, Prometheus + Grafana behind it, Testcontainers in CI. |
| **[roda-belem-service](https://github.com/micaelcf/roda-belem-service)** | API behind a crowdsourced accessibility map | **sqlc**-generated queries instead of an ORM: the SQL is real, the Go is typed. Radius search runs in MySQL via `ST_DISTANCE_SPHERE`, accessibility filtering is pushed down with `FIND_IN_SET`, and a cuckoo filter dedupes Google Places results before they reach the client. Ports and adapters throughout — the database is a detail. |
| **[list-my-product](https://github.com/micaelcf/list-my-product)** | Product catalog that eats very large CSVs | Streamed, batched ingest instead of load-then-parse, so a 200k-row upload doesn't become a heap problem. FX rates are captured **at upload time** and stored per price, which keeps historical prices honest instead of silently re-pricing the past. MikroORM migrations with committed snapshots; separate dev and prod compose files, the latter with Nginx TLS termination, healthchecks and memory limits. |
| **[landing-builder](https://github.com/micaelcf/landing-builder)** — *Pulso* | Landing-page studio with three finished templates | **Svelte 5 runes end to end**, no legacy stores. Three complete design systems live in one codebase as Tailwind v4 `@theme` token sets. anime.js timelines are synced to scroll position, Three.js/Threlte is dynamically imported only when its section intersects, and every animation degrades to static under `prefers-reduced-motion` — motion never costs the first paint. |
| **[soda-ai](https://github.com/micaelcf/soda-ai)** | A vending machine you talk to | Gemini + `instructor` coerce free text into a **typed action union** — purchase, inventory, history — validated by Pydantic with bounded retries. Products are normalized against real inventory, so the model cannot invent a flavour that doesn't exist. Two endpoints on purpose: one parses intent, one executes it, so the UI can confirm before money moves. |
| **[gomeet-clean-arch](https://github.com/micaelcf/gomeet-clean-arch)** | Realtime chat backend in Go | A WebSocket hub built on typed channels with a **per-connection mutex** rather than one global lock, plus an `isClosing` guard that prevents double-close panics on dead sockets. Domain gateways are interfaces; ArangoDB and AQL sit behind them. |

**Also worth a look —** [hexagonal-arch-go](https://github.com/micaelcf/hexagonal-arch-go): one product domain, three interchangeable adapters (HTTP, MySQL, Kafka) · [stash-task](https://github.com/micaelcf/stash-task): Go + Next.js, fifteen use cases behind gateway interfaces · [child-calendar](https://github.com/micaelcf/child-calendar): visual routines, audio cues and timers for autistic children, SvelteKit + Capacitor on PocketBase · [roda-belem](https://github.com/micaelcf/roda-belem): the map itself, scoring venues on twelve concrete accessibility criteria.

---

## How I build

- **Correctness before cleverness.** Money and game rounds get an outbox, idempotent consumers and exact decimal math — not optimism and a retry button.
- **The database is not a dumb bucket.** Geospatial search, feature filtering and pagination belong in SQL. `sqlc` keeps that type-safe without an ORM guessing on my behalf.
- **Boundaries earn their keep.** The domain declares interfaces; infrastructure implements them. That is why swapping a MySQL adapter for a Kafka one touches a single directory.
- **Motion has a budget.** 3D loads lazily, animation degrades to static, reduced-motion is honoured. A hero section should never be the reason a page is slow.
- **Accessibility is a feature, not a footnote.** Roda Belém rates venues on ramps, elevators, adapted bathrooms, tactile paving, Braille, Libras and guide-dog access — because "accessible" means nothing without specifics.
- **Honest READMEs.** Every repo here states what works, what doesn't, and how to run it. Prototypes are labelled as prototypes.

---

## Stack

**Ship with daily** — TypeScript · Go · Svelte 5 / SvelteKit · NestJS · React · Tailwind · PostgreSQL · Docker

**Comfortable in** — Python (FastAPI, Pydantic, SQLModel) · MySQL · RabbitMQ · Kafka · MikroORM · sqlc · gRPC · Socket.IO · Prometheus + Grafana · Vitest · Playwright · Testcontainers

**Also somewhere in these repos** — C# · Java (Spring Boot) · C++ on Arduino · GDScript in Godot · MQL5 · Jupyter, pandas, scikit-learn

---

## Now

Building event-driven backends and interfaces that feel deliberate. The neural-network, computer-graphics and signal-processing repos below are coursework from UFPA — kept public because the fundamentals still show.

**Open to work.** [micael-dev.vercel.app](https://micael-dev.vercel.app) · [LinkedIn](https://www.linkedin.com/in/micael-fernandes21/) · micaelf81@gmail.com
