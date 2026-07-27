# PathReview Contribution Journal

## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/27

**Issue title:** Vector store returns stale embeddings after a document is re-ingested

**Tier:** [ ] Tier 1  [x] Tier 2  [ ] Tier 3

**Problem summary:**
The current ingestion pipeline creates new embeddings when a repository or document is updated, but older embeddings are not removed from the vector store. This can cause retrieval results to include outdated information alongside newer content. The fix should ensure that re-ingesting a source replaces or invalidates previous embeddings so retrieval only uses current data. The affected areas are the ingestion pipeline and RAG vector store components.

**Branch name:** fix/27-stale-vector-embeddings

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

### Selection notes:
I chose this issue because it involves both backend data flow and AI/ML retrieval behavior. The scope is manageable because the problem is isolated to ingestion and vector storage, but it demonstrates understanding of RAG systems, embeddings lifecycle, and data consistency.