# Progress

## 2026-11-19 — Offline Studio verified

Tested the fork at application revision `1f4e5bc` with its existing environment. Python passed 495 tests, skipped the one opt-in live vLLM test, and reported 139 warnings. All 18 Studio JavaScript tests passed. Package consistency passed. The running API returned a job list and reported FFmpeg available and GPU unavailable. The static Studio dashboard served successfully. Renderer readiness returned the expected HTTP 503.

The environment configuration now has a new base version and a fresh revision-1 draft carrying the previously saved installation and startup instructions. The Python environment survived reconnection. No additional configuration edit was needed.

**Outstanding** — GPU startup, provider access, real transcription, highlight quality, subtitles, face tracking and downloadable MP4s remain unverified here. No source video has been processed for the milestone.

**Next** — Follow the GPU preflight in [SETUP.md](SETUP.md). Record the runtime, checkout revision and readiness result. Once authorised to process the chosen video, run one five-clip job, download and inspect each file, and record the outcome here.
