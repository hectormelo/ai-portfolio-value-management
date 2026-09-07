# Security Notes

- Never commit Langflow API keys, model-provider keys, passwords, or tokens.
- Never commit real institutional contracts unless they are explicitly approved for public release.
- Remove local machine paths and user identifiers from exported Langflow files.
- Treat browser `localStorage` as convenience storage, not a secure secrets vault.
- Prefer local-only or protected deployments for confidential documents.
- Rotate any credential that has previously been embedded in a file intended for sharing.
