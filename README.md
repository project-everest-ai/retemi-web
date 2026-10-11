# Retemi public website

This repository contains the public, dependency-free HTML/CSS website for
Retemi. No mobile application, backend, database, participant data, private
Project Everest documentation, or credentials belong here.

## Provenance

- Source repository: `project-everest-ai/project-everest` (private)
- Source website path: `apps/retemi_web`
- Source website checkpoint: `f3879af`
- Standalone public history begins with the website content at that checkpoint;
  unrelated private-repository history was intentionally not copied.

## Local preview

Run `python3 -m http.server 8080` from this directory and open
`http://localhost:8080`.

## Deployment

`.github/workflows/pages.yml` publishes a validated static artifact to GitHub
Pages from `main` or by manual dispatch. It uses only built-in GitHub Pages
permissions and deploys no application or backend infrastructure.

The Pages URL is publicly addressable. Page-level `noindex,nofollow` metadata
and `robots.txt` intentionally discourage indexing during pre-pilot review;
they are not access controls.

Privacy and pilot-participation pages remain pre-pilot drafts for counsel
review until approved. Do not present them as legally approved or effective.
