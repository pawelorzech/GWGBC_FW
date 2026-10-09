# AGENTS.md

## What this repo is

Hosting mirror of **Funnyplaying FPGA Game Boy Color (GWGBC) firmware** releases. No source code, no build system, no tests. All `update.bin` files are pre-compiled and encrypted; the author (makho) does not own, maintain, or support the firmware. Work here is almost always **adding a release directory + updating the relevant README changelog**.

## Hard rules

- **Never edit files in `media/`** or republish those images — several are third-party copyrighted (see `media/README.md`).
- **Never rename/replace an `update.bin`** or move it between hardware trees. The file must ship named exactly `update.bin`.
- **Do not cross-link firmware between `HWv1_0/` and `HWv1_1/`.** Wrong firmware bricks cartridge booting until reflashed.
- Changelogs quote Funnyplaying directly and paraphrase the rest. Preserve the `> quotes` vs `* paraphrases` convention.

## Layout

- `HWv1_0/` — hardware v1.0 only. Release dirs are old build numbers (`0725`, `0928`, `1117`, …) plus one renamed calendar dir (`2024.1.old`).
- `HWv1_1/` — **hardware v1.1 and newer; this is the primary focus.** Release dirs are `YYYY.MM.DD` dated.
- Each release dir holds `update.bin` (+ sometimes a `.txt` with the original bilingual CN/EN notes).
- `patched_*` / `internal_test_version_patched` subdirs = same firmware with an alternate boot logo ("different aesthetic"), for compatibility or taste.
- `media/` — PCB photos and screenshots used by the root README.

## Gotchas an agent will get wrong

- **Directory date name != internal menu version.** e.g. `HWv1_1/2025.02.17/` shows as v1.14; `HWv1_1/2024.12.13/` is also v1.14. Always read the README changelog and the release `.txt` for the real version, don't infer it from the folder name.
- Firmware version numbering is inconsistent across HW trees (v1.02 appears in both, but they are different builds).
- The `.txt` notes inside release dirs are the primary source; the READMEs are the human-facing digest. Keep them consistent when adding a release.
- READMEs are the only "docs" — there is no CI, no linter, no config to satisfy. Verify changes by reading, not by running anything.

## Update procedure (documented, not code)

Copy `update.bin` to the 1 MB `FUNNY_PLAY_` USB mass-storage volume, device with no cart inserted. v1.0 requires Windows; v1.1+ also supports macOS. Full steps and the corrupt-display-OSD reset keypress sequence are in each tree's `README.md`.
