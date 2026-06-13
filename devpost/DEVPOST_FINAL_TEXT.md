Title: FIND EVIL! — Valhuntir Lite (Protocol SIFT demo)

Project URL: https://github.com/Muhammad-Musab0511/Find-evil-hackathon

Short description (for Devpost header):
Valhuntir Lite — a portable demo container that showcases Valhuntir's human-in-the-loop forensic CLI and approval workflow without requiring SIFT or OpenSearch. Judges can build and run a 90s demo in under 2 minutes.

Problem statement:
Investigative platforms like Protocol SIFT are powerful but heavy to deploy for quick demos. Judges and reviewers often cannot run SIFT VMs or OpenSearch during hackathons.

Our solution:
Valhuntir Lite packages the `vhir` CLI into a reproducible Docker demo that installs the CLI from source, runs a scripted case initialization and status flow, and produces evidence-ready outputs that demonstrate the human-in-the-loop approval workflow.

Key features:
- One-command demo container that initializes a case and shows case listing/status.
- CI smoke test that validates the CLI can initialize and list a case.
- GitHub Actions to build and optionally publish the demo image to GHCR or Docker Hub.
- Devpost assets: 90s demo video, screenshots, and step-by-step demo instructions.

Tech stack:
- Python (Valhuntir CLI)
- Docker
- GitHub Actions
- FFmpeg (for demo video generation)

How to run (for judges):
```bash
# build image
cd demo-lite
docker build -t valhuntir-lite:latest -f Dockerfile ..

# run the scripted demo
docker run --rm --entrypoint /app/demo-lite/entrypoint.sh valhuntir-lite:latest

# for interactive exploration
docker run --rm -it valhuntir-lite:latest /bin/bash
```

Screenshots & captions (for Devpost upload):
1. screenshots/demo_output.png — "Demo: `vhir case init` followed by case listing (shows `demo-case`)."
2. (optional) screenshots/01-case-list.png — "Case list: demo-case appears as active."
3. (optional) screenshots/02-case-status.png — "Case status: shows Findings/Timeline/TODOs counts."

Team & contact:
Muhammad Musab — GitHub: @Muhammad-Musab0511 — repo: https://github.com/Muhammad-Musab0511/Find-evil-hackathon

Notes:
- The original Valhuntir project is MIT-licensed; this demo preserves that license and attribution.
- To publish the demo image automatically, add `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` repository secrets.
