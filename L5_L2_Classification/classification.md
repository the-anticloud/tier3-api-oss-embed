# L5 Narrow / L2 General Classification — api-oss-embed
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign embedding service: local vector computation for all Anticloud modules

## L5 Narrow
api-oss-embed specializes in sovereign embedding service: local vector computation for all anticloud modules within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-embed is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B provides the large-context embedding model; api-oss-embed handles batching, caching, and routing between the fast (MiniLM) and accurate (PAX 27B) embedding models.

## AIOSS Audit Relevance
Every embedding request (input hash + model version + embedding vector hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
GDPR Art. 25 (embeddings never leave device), ISO 27001 A.8.2
