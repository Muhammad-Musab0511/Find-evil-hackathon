Title: FIND EVIL! — Valhuntir Lite (Protocol SIFT demo)

Project URL: https://github.com/Muhammad-Musab0511/Find-evil-hackathon

Short description:
Valhuntir Lite is a portable demo container that showcases Valhuntir's human-in-the-loop forensic CLI and approval workflow without requiring SIFT or OpenSearch. Judges can build and run the full demo in under two minutes.

Problem:
Protocol SIFT is powerful, but it is heavy to deploy for quick hackathon reviews. Judges and reviewers often cannot run SIFT VMs or OpenSearch during evaluation.

Solution:
Valhuntir Lite packages the `vhir` CLI into a reproducible Docker demo that installs the CLI from source, runs a scripted case initialization and status flow, and produces evidence-ready outputs that demonstrate the human-in-the-loop workflow.

Highlights:
- One-command demo container that initializes a case and shows case listing/status.
- CI smoke test that validates the CLI can initialize and list a case.
- GitHub Actions to build and optionally publish the demo image to GHCR or Docker Hub.
- Devpost assets: 90s demo video, screenshots, and step-by-step demo instructions.

Tech stack:
- Python (Valhuntir CLI)
- Docker
- GitHub Actions
- FFmpeg (for demo video generation)

How to run:
```bash
cd demo-lite
docker build -t valhuntir-lite:latest -f Dockerfile ..
docker run --rm --entrypoint /app/demo-lite/entrypoint.sh valhuntir-lite:latest
docker run --rm -it valhuntir-lite:latest /bin/bash
```

Suggested upload assets:
- `screenshots/demo_output.png` — demo case initialization and case list output.
- `devpost/demo.mp4` — 90-second submission video.
- `devpost/VIDEO_SCRIPT.md` — recording script.
- `devpost/ASSETS.md` — screenshot checklist.

Team & contact:
Muhammad Musab — GitHub: @Muhammad-Musab0511 — repo: https://github.com/Muhammad-Musab0511/Find-evil-hackathon

Notes:
- The original Valhuntir project is MIT-licensed; this demo preserves that license and attribution.
- To publish the demo image automatically, add `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` repository secrets.
