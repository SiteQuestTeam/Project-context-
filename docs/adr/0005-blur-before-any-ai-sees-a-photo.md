# Photos are blurred on our server before any AI model sees them; originals are deleted

Every uploaded photo goes through automatic face and licence-plate blurring (EgoBlur) on our own server first; only the blurred copy is sent to an AI model and only the blurred copy is stored, while the original is deleted straight away. No face or plate of a bystander ever reaches Google or Anthropic, and we hold no personal data from photos, which answers GDPR (RODO) questions up front. It also matters for the model choice: the Gemini API free tier's terms say its input may be used to improve Google's products, may be read by human reviewers, and must not contain personal information.

## Consequences

- Blurring runs before classification, so a post takes a little longer to appear in the preview.
- EgoBlur officially supports Linux and macOS, not Windows, so the server runs on Linux (or Docker/WSL). If EgoBlur cannot be made to work, the fallback is `deface`, which blurs faces only; plates then move to the pitch as future work.
