# Errors and fixes

| Observation | Cause and action |
| --- | --- |
| Codex Studio returns HTTP 503 at `/api/ready` | Expected for the offline profile. On 2026-11-19 the probe could not import NumPy, OpenCV or faster-whisper. The API and FFmpeg checks passed. Keep Codex intact and run the GPU preflight separately. |
| One Python test skipped | The live vLLM test requires explicit opt-in and a configured server. The offline suite ran successfully. |
| A GPU notebook fails its readiness check | Unresolved until a real GPU run provides diagnostics. Capture the failing check, package versions and safe error code. Follow the [Studio troubleshooting guide](../docs/KAGGLE_STUDIO.md#troubleshooting). Keep secrets and private URLs out of logs shared here. |

No rendering fix or successful real-video run has been verified for this milestone.
