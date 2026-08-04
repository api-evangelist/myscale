# MyScale (myscale)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MyScale is a SQL vector database built on a ClickHouse fork (MyScaleDB), combining high-performance vector search, full-text search, and analytical SQL in a single engine. Its primary interface is SQL executed over the ClickHouse-compatible HTTP interface (HTTPS on port 8443), where vector similarity search is expressed with SQL functions like distance() against VECTOR INDEX columns. A managed MyScale Cloud console provisions clusters, and the underlying MyScaleDB is open source under Apache-2.0.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/myscale/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/myscale/refs/heads/main/apis.yml)

## Tags

- Vector Database
- SQL
- ClickHouse
- Vector Search
- Full-Text Search
- RAG

## Timestamps

- **Created:** 2026-06-20
- **Modified:** 2026-06-20

## APIs

### MyScale SQL Interface (ClickHouse HTTP)

MyScale's primary interface is SQL executed over the ClickHouse-compatible HTTP interface (HTTPS, port 8443). Clients POST a SQL statement in the request body (SELECT, INSERT, CREATE TABLE, ALTER, DROP) and authenticate with the cluster username and password via HTTP Basic auth or X-ClickHouse-User / X-ClickHouse-Key headers. This is the same transport used by clickhouse-connect, the official Python client, and by Node.js, Go, and Java clients.

- **Human URL:** [https://docs.myscale.com/en/python-client/](https://docs.myscale.com/en/python-client/)
- **Base URL:** `https://{cluster-host}:8443`

#### Tags

- SQL
- ClickHouse
- HTTP
- Query

#### Properties

- [Documentation](https://docs.myscale.com/en/overview/)
- [API Reference](https://docs.myscale.com/en/cluster-management/)
- [OpenAPI](openapi/myscale-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myscale.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myscale.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyScale Vector Search (SQL)

Vector similarity search is expressed in SQL, not a separate REST surface. Tables declare a VECTOR INDEX over an Array(Float32) column (for example TYPE HNSWFLAT with metric_type Cosine, L2, or IP), and queries rank rows with the distance() function ordered by distance. Vector search composes with standard SQL filtering, joins, and full-text search over the same HTTP query endpoint.

- **Human URL:** [https://docs.myscale.com/en/vector-search/](https://docs.myscale.com/en/vector-search/)
- **Base URL:** `https://{cluster-host}:8443`

#### Tags

- Vector Search
- Embeddings
- Similarity
- HNSW

#### Properties

- [Documentation](https://docs.myscale.com/en/vector-search/)
- [OpenAPI](openapi/myscale-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myscale.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myscale.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyScale Python SDK (clickhouse-connect)

The recommended Python access path is the clickhouse-connect client, which wraps the ClickHouse HTTP interface (host, port 8443, username, password). It executes the same SQL over HTTP transport for table creation, inserts, and distance()-based vector queries, and is the path used by the LangChain and LlamaIndex MyScale integrations.

- **Human URL:** [https://docs.myscale.com/en/python-client/](https://docs.myscale.com/en/python-client/)
- **Base URL:** `https://{cluster-host}:8443`

#### Tags

- SDK
- Python
- clickhouse-connect

#### Properties

- [Documentation](https://docs.myscale.com/en/python-client/)
- [GitHub](https://github.com/myscale/MyScaleDB)
- [OpenAPI](openapi/myscale-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myscale.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myscale.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyScale Cloud / Cluster Management

MyScale Cloud provisions and manages clusters (create, modify name / size / replicas / idle period, reset password, view status) through the web console at the MyScale Cloud site. As of this catalog, cluster lifecycle management is documented as console-only; no public programmatic REST management API is documented. The console surfaces per-cluster Connection Details (MYSCALE_CLUSTER_URL, username, password) used by the SQL-over-HTTP interface above.

- **Human URL:** [https://docs.myscale.com/en/cluster-management/](https://docs.myscale.com/en/cluster-management/)
- **Base URL:** `https://myscale.com/`

#### Tags

- Cloud
- Clusters
- Management
- Console

#### Properties

- [Documentation](https://docs.myscale.com/en/cluster-management/)

## Common Properties

- [GitHub Organization](https://github.com/myscale)
- [LinkedIn](https://www.linkedin.com/company/myscale)
- [Website](https://www.myscale.com)
- [Documentation](https://docs.myscale.com/en/overview/)
- [Plans](plans/myscale-plans-pricing.yml)
- [Rate Limits](rate-limits/myscale-rate-limits.yml)
- [Fin Ops](finops/myscale-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
