# Directionally Correct topic and episode explorer

Interactive exploration of 150 public Directionally Correct podcast episodes:

**Live application:** https://lstehlik2809.github.io/directionally-correct-topic-map/

## What the application shows

- a network, frequency view, timeline, and searchable episode catalog covering 298 topics
- topic relationships, clusters, occurrence counts, and episode-level co-occurrence
- episode details, structured ideas, source links, and semantically related episodes
- evidence-linked topic syntheses showing convergence, divergence, conflicts, and distinctive ideas
- filters for publication date, guest, topic, and cluster

## What is in this repository

The public repository is deliberately deployment-only:

- `site/` contains the compiled application, its favicon, and the four JSON datasets required in the browser
- `.github/workflows/deploy-pages.yml` publishes `site/` to GitHub Pages
- this README describes the application and its construction

Source corpora, transcripts, development source code, tests, data-generation utilities, model caches,
logs, and credentials are not published here. The deployed application makes no model or API calls and
contains no API key.

## How it was built

The application was authored locally in React and TypeScript and compiled into static HTML, CSS, and
JavaScript with Vite. Its network visualization uses `react-force-graph-2d` and deterministic weighted
Louvain community detection.

The browser datasets were derived locally from controlled topic tags and structured ideas extracted from
the public episode corpus. Semantic episode recommendations were calculated before deployment. The topic
syntheses were generated with GPT-5.6 Sol using medium reasoning effort, validated against the extracted
idea evidence, and stored with episode references. Only the resulting browser-ready datasets are included
in `site/data/`.

Every push to `main` uploads the already-built `site/` directory through GitHub Actions and publishes it
with GitHub Pages.
