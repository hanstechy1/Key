# HANS TECHY V4 — Private Keys Repository

**Make this repository Private in GitHub Settings before adding any real encrypted key material.**

This repository is the companion key store for HANS TECHY V4. It is intended to hold the encrypted shared AI provider file `keys.enc`, not plaintext credentials.

## Safe setup
1. Change this repository visibility to **Private**.
2. Copy `keys.example.json` to `keys.json` on your own computer.
3. Add real provider API keys only to the local `keys.json`.
4. Encrypt it using the HANS TECHY V4 project command:
   ```bash
   KEYS_ENCRYPTION_KEY=YOUR_64_HEX_KEY npm run keys -- encrypt ./keys.json ./keys.enc
   ```
5. Commit only `keys.enc` to this private repository. Never commit `keys.json`, `.env`, encryption keys, or GitHub tokens.
6. Create a fine-grained GitHub token restricted to this repository with Contents: Read-only.
7. Configure `KEYS_REPO=hanstechy1/Key`, `KEYS_REPO_TOKEN`, `KEYS_ENCRYPTION_KEY` and optionally `KEYS_REF=main` in the bot's deployment environment.
8. After replacing `keys.enc`, run `.reloadkeys` as the bot owner.

## Example structure
```json
{
  "allowSharedKeys": true,
  "sharedKeys": {
    "gemini": "YOUR_GEMINI_API_KEY",
    "openai": "YOUR_OPENAI_API_KEY"
  }
}
```

Do not put real credentials in this README or in `keys.example.json`.
