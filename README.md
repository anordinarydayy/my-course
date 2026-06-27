# Interview Prep — DSA, System Design, Databases, AI Engineering, Elasticsearch, RabbitMQ & Redis

Seven interactive, self-study courses for software-engineering interview and skills
prep, hosted as static HTML on GitHub Pages.

**Live site:** https://tolamson.github.io/interview-prep/

## Courses

- **[Data Structures & Algorithms](dsa/index.html)** — 42 lessons covering the ~20
  coding-interview patterns (two pointers, sliding window, binary search, trees, graphs,
  dynamic programming, and more). Each lesson runs the brute force → insight → invariant
  chain with schematic play-through diagrams, a fully worked LeetCode problem per technique,
  a graded practice ladder, and a self-test. See the [DSA roadmap](dsa/dsa-roadmap.html).
- **[System Design](system-design/lessons/index.html)** — 43 lessons from back-of-envelope
  estimation through real designs (rate limiter, message queues, consistent hashing, news
  feed, payment system, order-matching engine). See the
  [System Design roadmap](system-design/system-design-roadmap-v2.html).
- **[Databases & SQL](database/index.html)** — relational databases taught through PostgreSQL,
  for interviews and real engineering. A 46-lesson map across nine phases: the relational model
  and schema design, SQL from joins and aggregation through CTEs and window functions, indexing
  and the query planner (EXPLAIN), transactions, isolation and MVCC, Postgres power features
  (JSONB, full-text search, partitioning), operations and scale, and an applied
  design-and-interview capstone. The first lesson — why a database, the relational model, and
  ACID — is live and interactive; the rest are mapped. See the
  [Databases course map](database/index.html).
- **[AI Engineering](ai-engineering/index.html)** — building applications on foundation
  models, the AI layer on top of strong software engineering. A 48-lesson map across nine
  phases (model internals, prompting, evaluation, RAG, agents, fine-tuning, inference, ops,
  safety); the first ten lessons are live and interactive — the AI-engineering landscape,
  how a foundation model works, tokenization & token economics, sampling & decoding,
  embeddings & the vector space, the model landscape & choosing a model, prompting as a
  discipline, structured output & function calling, prompts as assets, and defensive prompting.
- **[Elasticsearch](elasticsearch/index.html)** — the search & analytics engine and the
  Elastic Stack. A 45-lesson map across ten phases: engine internals (the inverted index,
  text analysis, the write path), data modeling & mapping, querying & relevance (BM25 and
  ES|QL), aggregations, sharding & scale, the modern vector / semantic / hybrid-search AI
  layer (kNN, BBQ, ELSER, `semantic_text`, retrievers & RRF, RAG), the ELK pipeline,
  production operations, and an interview & system-design capstone. The full map is laid out;
  lessons open phase by phase.
- **[RabbitMQ](rabbitmq/index.html)** — the message broker, for backend and system-design
  interviews. A 45-lesson map across ten phases: why messaging and the broker model, the AMQP
  entity model (exchange → binding → queue), exchanges & routing, queues & messages (classic /
  quorum / streams), reliability & delivery guarantees (acks, publisher confirms, dead-lettering,
  idempotency), consumers & throughput, clustering & high availability (quorum queues, Raft,
  Khepri), streams & multi-protocol (native AMQP 1.0, MQTT), production operations, and a
  patterns & interview capstone. The first lesson — why RabbitMQ exists — is live and
  interactive; the rest are mapped.
- **[Redis](redis/index.html)** — the in-memory data-structure store, for interviews and real
  engineering. A 45-lesson map across ten phases: why in-memory and the single-threaded model,
  the core and advanced data types, caching patterns & eviction, persistence (RDB/AOF),
  programmability (transactions, Lua, distributed locks, rate limiting), replication & Redis
  Cluster, the modern Redis 8 platform (Search, JSON, vector search for AI/RAG, semantic
  caching), production operations, and a patterns & interview capstone. The first lesson — why
  Redis exists — is live and interactive; the rest are mapped.

## How to use

Open the [live site](https://tolamson.github.io/interview-prep/) on any device and click into
a course. Each lesson is a single self-contained HTML page — many diagrams are interactive
(press **Play** or step through with **Next**). On a phone, use **Add to Home Screen** for
one-tap access.

## Notes

- **Original material.** Problem names (and LeetCode numbers) are referenced only as
  well-known identifiers; every explanation, diagram, and line of code is written from
  scratch. Not affiliated with any paid course.
- **No build step.** Pure HTML/CSS/JS with fonts from Google Fonts; nothing to install.
  Hosted via GitHub Pages from the `main` branch root.
