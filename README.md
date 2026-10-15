# SingaLiving

**A property-search prototype connecting a data pipeline, model-backed estimates and a web application.**

SingaLiving explores how natural-language search and property models fit into an ordinary product: structured queries, database-backed listings, saved preferences and a browser interface. The repository contains a FastAPI backend, a Next.js frontend and Python collection and analysis tools.

## Follow a request through the code

| Part | Entry point | What to inspect |
| --- | --- | --- |
| Natural-language search | [Search service](backend/app/services/semantic_search.py) | Anthropic-backed intent parsing into listing filters and fallback explanations |
| Listing API | [Routers](backend/app/routers) | Search, listing details and application endpoints |
| Property estimates | [Valuation service](backend/app/services/valuation.py) | Segment-specific model loading, feature construction and SHAP factors |
| Data preparation | [Pipeline](pipeline) | Aggregation, ingestion, training and offline evaluation scripts |
| User interface | [Frontend](frontend) | Next.js application and components |
| Recommendation evaluation | [Evaluation code](eval_recommendation) | Offline ranking experiments and their assumptions |

The application combines PostgreSQL for listings and Redis for caching. Collection tools for several property sites are present; the right to collect or redistribute their content must be established separately.

## Explore locally

Start with the [backend setup](backend/README.md), [pipeline notes](pipeline/README.md) and [frontend scripts](frontend/package.json). The [Compose configuration](backend/docker-compose.yml) defines the backend, PostgreSQL and Redis services. It contains development defaults; review credentials and exposed ports before starting it.

For the frontend, from a configured checkout:

```bash
cd frontend
npm install
npm run dev
```

The complete application also needs a populated database, compatible model artifacts and backend configuration. Natural-language search needs an Anthropic API key in the local environment. A clean clone is not a self-contained data or model demo.

## Reading the experiments

The repository includes valuation, recommendation and chat-evaluation scripts. Recommendation measurements use synthetic preference profiles; they do not establish user satisfaction. Model estimates depend on dataset coverage and split design, and chat checks do not establish general factual reliability. Historical figures in reports or the [Chinese notes](README_CN.md) should be read with those scopes, rather than as product guarantees.

## Project and data provenance

This repository was published as `TempFYPRepo`. Academic ownership, collaborator contributions and source licensing need clearer documentation. External listings, images, reference data and trained artifacts require their own redistribution permissions. Keep credentials and personal listing/contact data out of shared demos.
