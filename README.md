# preview-vs-figma

Password-protected comparison of the member experience preview against the Figma designs, served from GitHub Pages. Same approach as `hra-journey` and `wr-demo`.

| File | What it is |
|---|---|
| `index.html` | The password gate. No content and no secrets. |
| `payload.enc.json` | AES-256-GCM ciphertext of the page (key from PBKDF2-SHA256, 600,000 iterations). |
| `encrypt.mjs` | Builds the payload from `source.html`. |
| `source.html` | The readable page, images included. **Gitignored: keep it local.** |

A wrong password fails to decrypt, so decryption is the password check. The password isn't stored anywhere in the repo.

## Update the page or change the password

```
node encrypt.mjs
git commit -am "Rebuild payload"
git push
```

The script asks for the password twice with hidden input. Pages redeploys on push.
