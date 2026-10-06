# Harmonis investor materials: release requirements

Conor requires fixes to cover every investor entry point and published format.
Do not close an investor-deck task with a special URL, cache-busting query, or
instructions to find a differently numbered page.

- Canonical build source: `E:/AI/outputs/harmonis-investor-deck-v6/build/`.
- `sequence.py` defines the shared 17-slide sequence. Financial Upside is 11 in
  the website, PDF and PowerPoint; operating economics is 12.
- Change source, then run `build_deck.py`, `build_site.py`, `release_check.py`,
  `check_freshness.py`, and `qa_site.py`. Inspect the changed slides visually.
- Run `stage_release.py` only after those checks. It copies an explicit asset
  list and rejects mismatched PDF/PPTX/web releases. Never use `git add .`:
  this checkout can contain private, untracked browser screenshots.
- Publish index.html, version.json, the stable PDF alias and the generated
  content-hashed PDF together. Keep existing hashed files intact.
- Cloudflare rules for investors.harmonis.io bypass edge caching and send
  `Cache-Control: no-cache, max-age=0, must-revalidate` for HTML/PDF/manifest.
  Preserve that host-specific policy. Do not alter other Harmonis domains.
- Verify ordinary URLs, historical PDF query URLs, headers, PDF bookmarks,
  returned PDF bytes and returning-browser navigation after deployment.
- `/admin/investor` in the main app routes to this canonical public deck.
  Never restore a separately maintained admin presentation.
- Market/revenue scenarios must remain labeled assumptions. Source documents,
  founders, SAFE terms and pricing must not change as a side effect of fixes.
- Shared Harmonis work still requires Conor's task authorization; this document
  does not authorize unsolicited automation, outreach or financial changes.
