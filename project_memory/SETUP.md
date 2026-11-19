# Development and rendering setup

## Existing Codex environment

Use the fork checkout at `/workspace/opensource-clipping`. Python 3.12.14 runs in the ignored `.venv`. Node 24 runs the Studio tests. FFmpeg 7.1.5 and ffprobe are on PATH. The API reports no GPU. No credentials are needed for these checks.

From the checkout, run the two tests below. Only for a fresh environment missing its dependencies, use the saved install script, which creates the venv with `python3.12 -m venv .venv`, installs `requirements-test.txt` with the venv's pip and runs `pip check`.

```sh
.venv/bin/python -m pytest tests -q
node --test tests/studio.test.cjs
```

For local Studio development run each command in its own terminal from the checkout.

```sh
.venv/bin/python -m uvicorn web.api.app:app --host 127.0.0.1 --port 8000
.venv/bin/python -m http.server 5173 --bind 127.0.0.1 --directory docs
```

On port 8000, expect `/api/health` to report ok and `/api/jobs` to return a jobs array. On port 5173, `/studio/` serves the dashboard. Offline renderer readiness is documented in [Errors and fixes](ERRORS_AND_FIXES.md).

## GPU preflight — stop before submitting a video

1. Open the [fork's Studio notebook in Colab](https://colab.research.google.com/github/5kg8fpw74j-cell/opensource-clipping/blob/main/notebooks/kaggle-studio-server.ipynb). For a private fork, download the notebook from GitHub and choose **File → Upload notebook** in Colab.
2. Select **Runtime → Change runtime type → T4 GPU → Save**, then **Connect**. Use a free GPU allocation. If unavailable, try Kaggle **New Notebook → File → Import Notebook**, import the same file and enable **Internet** and a free GPU in notebook settings. Stop if either service asks for payment.
3. In Colab's left sidebar open **Secrets** (key icon). Add `GOOGLE_API_KEY` for Gemini and `NGROK_AUTHTOKEN` for the Studio connection. Enable notebook access for both. On Kaggle use **Add-ons → Secrets** and attach the same labels. Use only accounts with available free quota and billing disabled. Keep credentials in the notebook platform's secret store.
4. In a fresh session, change the clone cell's `REPO_URL` to `https://github.com/5kg8fpw74j-cell/opensource-clipping.git` if the fork is publicly cloneable. The unchanged default clones upstream. If the fork is private, use the upstream checkout for this preflight only and record the revision actually tested (`!git rev-parse HEAD` after cloning). The notebook reuses an existing checkout.
5. Run cells individually in order through **Start Backend Server + Tunnel**. Use the default CUDA Torch profile and keep `START_LOCAL_VLLM=False`. Setup prepares separate Python 3.12, the constrained Studio dependencies, Deno and checks FFmpeg, renderer and Whisper imports. Check reported output disk space. Keep the backend cell running.
6. Wait for **BACKEND SERVER READY**, open the [Studio dashboard](https://naufalrizqullah.github.io/opensource-clipping/studio/), choose **Connect**, paste the notebook's public URL, then **Test & Connect**. Keep the URL private. Stop here for preflight. The notebook's stop cell closes the backend when finished.

## Later, after choosing an authorised video

Use **New Job**, supply the source, set **Number of Clips** to **5** and aspect ratio to **9:16**, choose Gemini and enable the desired subtitles and face framing. Keep optional B-roll, diarization and upload workflows off for this first run. Download each successful MP4 from the job page before ending the notebook session. Outputs are under `outputs/<job_id>/` in the checkout. Verify five separate files play with picture and sound and review them against [the milestone](GOALS.md). Record any partial failures even if some files downloaded.

[Repository GPU setup and troubleshooting](../docs/KAGGLE_STUDIO.md) · [Colab guide](../wiki/12-Google-Colab-Guide.md)
