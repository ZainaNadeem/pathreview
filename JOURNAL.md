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

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** 
PASTE_COMMIT_URL_HERE

**Reproduction summary:**
Reproduced the stale embedding behavior by re-ingesting an updated document and observing that previous vector data remained available during retrieval.

**PLAN.md link:**
https://github.com/ZainaNadeem/pathreview/blob/fix/27-stale-vector-embeddings/PLAN.md

**Walkthrough video (recommended):**

**Blockers or open questions:**
Need to confirm whether stale results are caused by duplicate vector insertion, missing deletion, or vector store update behavior.

### Check-in 2 (end of week)

**PR link:** https://github.com/ascherj/pathreview/pull/1020

**Branch:** fix/27-stale-vector-embeddings

**What you built:**
Implemented a fix for stale embeddings during document re-ingestion. The ingestion pipeline now uses a stable document identifier to remove vectors from the previous document revision before storing the updated embeddings.

**Tests added or updated:**
Added `tests/unit/test_pipeline.py` with regression tests covering resume, README, and repository re-ingestion, document ID stability, deletion scoping, delete-before-add behavior, and unchanged ingestion behavior.

**Self-review confirmation:** [x] make check passes  [x] make test-unit passes

**Draft PR feedback received from:** none