# Decisions

- **2026-11-19 · Keep Codex lightweight.** Use the working offline environment for Studio changes and regression tests. Use a separate GPU notebook for the rendering milestone. Reinstall only when dependencies are missing or have changed.
- **Start with Colab Studio.** It supports opening the existing notebook directly from GitHub, prepares its own Python 3.12 environment and provides a browser interface for clip downloads. Kaggle supports the same notebook if free Colab GPU capacity is unavailable. Keep local vLLM off to avoid a second model installation.
- **Retain user control.** Use only authorised footage. Obtain approval before spending money, destructive actions or publishing content. Leave uploads and social account integrations unused. Never include keys, tokens or private tunnel URLs in Git.
- **Require output evidence.** A passing API test, a working tunnel or even a green renderer probe cannot establish that clips were produced. Review the actual MP4s before marking the milestone complete.
