### Overview: GWS CLI Technical Architecture

The `gws` CLI is a cross-platform tool that communicates with Google Workspace APIs via OAuth 2.0. It requires a Desktop-type OAuth Client ID associated with a GCP project where the relevant APIs (Drive, Gmail, Sheets) are enabled.

### Implementation Details

- **Configuration Storage**: Settings are stored in `$HOME/.config/gws/`.
- **Token Management**: OAuth tokens are encrypted and cached in `token_cache.json`.
- **Scope Requirements**: Core tasks require `https://www.googleapis.com/auth/drive`, `https://www.googleapis.com/auth/gmail.readonly`, and `https://www.googleapis.com/auth/spreadsheets`.

### Edge Cases & Troubleshooting

| Issue | Likely Cause | Resolution |
| :--- | :--- | :--- |
| `403 Forbidden` | API not enabled in GCP | Go to Library and enable the specific API. |
| `insufficientPermissions` | Scopes not checked in browser | Re-run `gws auth login` and check all boxes. |
| `Connection Refused` | CLI listener timeout | Restart the login command and refresh browser. |
| `EPERM` (Windows) | Missing Admin rights | Restart terminal as "Run as Administrator". |

### Q&A

**Q: Can I use the same Client ID for multiple users?**
A: Yes, the Client ID identifies the *application* (the CLI), while the login process identifies the *user*.

**Q: How do I change the project after setup?**
A: Run `gws auth setup --project new-project-id` to overwrite the existing configuration.

### Key Links

* **Official Docs:** [https://googleworkspace-cli.mintlify.app/](https://googleworkspace-cli.mintlify.app/)  
* **GitHub Repository:** [https://github.com/googleworkspace/cli](https://github.com/googleworkspace/cli)  
* **NPM Package:** [https://www.npmjs.com/package/@googleworkspace/cli](https://www.npmjs.com/package/@googleworkspace/cli)  
* **Video Tutorial (Fru Dev):** [https://www.youtube.com/watch?v=aci6mSkFPf8](https://www.youtube.com/watch?v=aci6mSkFPf8)
