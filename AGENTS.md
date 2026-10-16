# GAM Skills

This repository distributes the six `gam-*` skills for Game Assets Maker. It may be checked out independently or at the client's `.agents/skills` submodule path.

- Read the affected `SKILL.md` and the references it links before editing. Keep script and asset paths relative to that skill directory so installed copies work across agents and operating systems.
- For CLI behavior, check the installed `gam-agent` help and receipts. Preserve the distinction between editing a draft and submitting a paid generation task.
- `gam-export` runs its own Python script; keep its Godot support scripts and UID files with the skill. Run `python3 gam-export/tests/test_generate.py` after changing export behavior.
- Keep only GAM-owned skills and their supporting files tracked. Other local skills can share this working directory and remain ignored.
- This is a separate Git repository. Inspect its status, preserve unrelated pending changes, and commit/push it separately from the client. Update the client's submodule pointer only after the intended Skills commit is available remotely.
