# MyScale (myscale)

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
