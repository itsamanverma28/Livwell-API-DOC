# Deploy to GitHub Pages

Repo: https://github.com/itsamanverma28/Livwell-API-DOC (branch `master`)

1. Replace `index.html` in the repo root with the `index.html` in this folder.
   - Web: open the repo, click `index.html`, then the pencil or "..." menu, or use Add file > Upload files and commit to `master`.
   - Or with git:
     git clone https://github.com/itsamanverma28/Livwell-API-DOC.git
     cd Livwell-API-DOC
     cp /path/to/this/index.html ./index.html
     git add index.html && git commit -m "Update API docs" && git push origin master
2. In the repo go to Settings > Pages. Under "Build and deployment" choose Source "Deploy from a branch", Branch `master`, folder `/ (root)`, then Save.
3. After about a minute the site is at https://itsamanverma28.github.io/Livwell-API-DOC/

Notes
- A GitHub Pages site is public to anyone with the link, even if the repo is private (private Pages needs Enterprise Cloud).
- This is the public-safe build: no Findings page, no "no auth" markers, no per-module security rules, no environment URLs, no session or MFA internals, and the internal OTP jobs are removed. It still lists every endpoint path, request fields, and the source file and controller names.
- The page has a "noindex" tag so search engines are asked not to list it. That is a request, not protection.
- Old versions of `index.html` stay in the repo history. If an earlier version had anything private, remove it from the history too.
- Diagrams load Mermaid from cdn.jsdelivr.net, so the viewer needs internet access.
