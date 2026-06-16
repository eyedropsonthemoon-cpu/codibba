# Codibba — Deployment Checklist

Every push to `main` is automatically scanned by the **Pre-Deploy Safety Check** GitHub Action. If any check fails, the workflow will block and show you exactly what to fix before deploying.

---

## Automated Checks (run on every push)

| Check | What it catches |
|---|---|
| DOCTYPE validation | Missing `<!` at the start of HTML files |
| Hardcoded secrets scan | API keys, passwords, tokens, localhost URLs left in code |
| Extensionless file detection | Duplicate files saved without `.html` or other extensions |
| Missing image check | Images referenced in HTML that are not in the repo |
| HTML structure validation | Missing `<html>`, `<head>`, `<body>`, charset, or viewport tags |

---

## Manual Pre-Deploy Checklist

Before clicking **Deploy** in Emergent AI, confirm the following:

- [ ] GitHub Actions workflow shows a green checkmark on the latest commit
- [ ] All image files referenced in `index.html` are present in the repo
- [ ] Button `href` values point to real pages (not just `#`)
- [ ] The page looks correct when opened locally in a browser
- [ ] No `.env` files or files containing real API keys are committed

---

## How to Deploy (Emergent AI)

1. Go to [app.emergent.sh](https://app.emergent.sh) and open the **Codibba** project
2. Confirm the latest GitHub commit shows a green checkmark in Actions
3. Click **Deployments → Deploy → Deploy Now**
4. Wait 5–15 minutes for the build to complete
5. Go to **Deployments → Custom Domain → Link Domain**
6. Enter `codibba.co` and follow the DNS steps

---

## Adding the App Icon

The page references `codibba-icon-original-512.png`. To add it:

1. Add the image file to the root of this repo
2. Commit and push — the automated check will confirm it is found
3. Redeploy

Until the image is added, the page shows a gold **"C"** placeholder automatically.
