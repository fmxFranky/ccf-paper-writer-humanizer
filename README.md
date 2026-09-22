# CCF Paper Writer + Humanizer

This standalone skill combines the CCF paper-writing workflow with the humanization-first preflight. It is packaged for upload as a ChatGPT skill and does not require the separate CCFA skill family or local absolute paths.

The package includes:

- `SKILL.md`: standalone entrypoint
- `references/`: writing, humanization, citation, venue, compression, and MARL guidance
- `scripts/check_prose_quality.py`: optional local prose diagnostic
- `agents/openai.yaml`: UI metadata

Upload the ZIP containing this folder to the ChatGPT skill interface. After upload, invoke it by its displayed name or `$ccf-paper-writer-humanizer-humanizer` if the interface exposes skill names.
