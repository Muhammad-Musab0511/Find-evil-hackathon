Title: FIND EVIL! — Valhuntir Lite (Protocol SIFT demo)

Short blurb
------------
Valhuntir Lite is a portable demo that showcases Valhuntir's human-in-the-loop forensic CLI and approval workflow without requiring a full SIFT workstation or OpenSearch deployment. Build the lightweight demo image and run a scripted flow that initializes a case, shows case listing, and displays status — everything a hackathon judge needs to validate the workflow in under 2 minutes.

What we built
-------------
- `demo-lite/` — Dockerfile and `entrypoint.sh` that installs `vhir` from repository source and runs a short scripted demo.
- CI smoke test (`tests/test_demo_smoke.py`) to validate `vhir` can init and list cases.
- CI workflows: `ci.yml` (tests + build) and `publish-image.yml` (publish to GHCR / Docker Hub).
- Devpost assets in `devpost/`: `DEVPOST.md` (draft), `FINAL_SUBMISSION.md` (this file), `VIDEO_SCRIPT.md`, `ASSETS.md`.

Why this matters for Protocol SIFT
---------------------------------
Valhuntir is designed to augment forensic investigations with AI while enforcing human review. Many reviewers cannot run full SIFT/OpenSearch environments during a hackathon — this demo provides a minimal, reproducible path to demonstrate the core human-in-the-loop functionality and chain-of-custody workflow.

Live demo instructions (for judges)
----------------------------------
1. Build the demo image:

```bash
cd demo-lite
docker build -t valhuntir-lite:latest -f Dockerfile ..
```

2. Run the demo script:

```bash
docker run --rm --entrypoint /app/demo-lite/entrypoint.sh valhuntir-lite:latest
```

3. The entrypoint will initialize a short demo case and show case listing/status. For full exploration, run an interactive container shell:

```bash
docker run --rm -it valhuntir-lite:latest /bin/bash
```

CI / Published image
---------------------
- Tests are executed in the included GitHub Actions workflow (`.github/workflows/ci.yml`).
- The `publish-image.yml` workflow will publish the demo image to GHCR automatically when pushed to the `hackathon/demo-lite` branch. To enable Docker Hub publishing, set `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` repository secrets.

Assets included for Devpost
--------------------------
- `devpost/DEVPOST.md` — editable Devpost draft text.
- `devpost/VIDEO_SCRIPT.md` — 90s video script for the demo.
- `devpost/ASSETS.md` — checklist and screenshot guidance.
- `screenshots/` — captured demo outputs (text + generated PNG screenshots).

Notes and next steps
--------------------
- Capture the suggested screenshots in `devpost/ASSETS.md` and record the 90s screencast following `devpost/VIDEO_SCRIPT.md`.
- Optionally enable GHCR/Docker Hub publishing via repository secrets for fully-automated demo distribution.

License and attribution
-----------------------
This forked demo is derived from Valhuntir (MIT). Preserve license and attribution in any public distribution.
