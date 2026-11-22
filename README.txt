CHROMEBOOK AI — CLOUDFLARE PAGES BUILD

This package preserves the existing five-tab dashboard:
- AI Chat: local WebLLM/Qwen 2.5 0.5B interface and browser-local conversation history.
- Remote Desktop: DextraDesk launch card that opens DextraDesk in a separate tab. The dashboard cannot read its live connection state; check connection status inside DextraDesk.
- Linux VM: LinuxOnTab embed with a separate-tab fallback.
- JSFiddle: embedded editor attempt, separate-tab fallback, and local sandboxed JS scratchpad.
- Compatibility: tests SharedArrayBuffer, cross-origin isolation, WebGPU, secure context, Service Worker API availability, and actual Service Worker registration.

IMPORTANT: This package includes a Cloudflare Pages `_headers` file. GitHub Pages will ignore it. Deploy this build to Cloudflare Pages to apply the response headers. Keep the GitHub repository as your source/backup; do not delete your existing GitHub Pages site until the Cloudflare deployment is verified.

CLOUDFLARE PAGES DEPLOYMENT (Git integration)
1. Extract the ZIP.
2. In the `chromebook_ai_v1` folder, select ALL files, including the extensionless `_headers` file.
3. Upload/commit those files to the ROOT of the GitHub repository that contains your Chromebook AI website. Do not put them in a nested folder. This adds `_headers` alongside index.html, manifest.webmanifest, and sw.js.
4. Sign in to Cloudflare and open Workers & Pages -> Create -> Pages -> Connect to Git.
5. Choose the same GitHub repository and authorize access if prompted.
6. For build settings, choose no framework / None. Leave Build command empty. Set Build output directory to `.` (the repository root, where index.html and _headers are located). If Cloudflare asks for a root directory, leave it at `/` or the repository root.
7. Deploy. Cloudflare will provide a `*.pages.dev` URL. Open that URL on the Chromebook.
8. Open Compatibility and tap Run compatibility test. Check whether SharedArrayBuffer and Cross-origin isolated become Supported. Also check whether Service Worker registration succeeds.
9. Test DextraDesk login/connection, LinuxOnTab, JSFiddle, local AI model loading, and chat history on the Cloudflare URL before changing your usual bookmark/PWA shortcut.

HEADERS INCLUDED
- Cross-Origin-Opener-Policy: same-origin
- Cross-Origin-Embedder-Policy: credentialless
- Permissions-Policy: cross-origin-isolated=(self)

The `credentialless` COEP mode is chosen as a less restrictive starting point for cross-origin embeds than `require-corp`, but third-party sign-in/session behavior can still change. DextraDesk and JSFiddle may not work inside the iframe after isolation is enabled. Their separate-tab links remain available. If DextraDesk authentication stops working in the embed, use its separate-tab fallback; do not weaken security headers without testing.

LIMITATIONS / HONEST STATUS
- The headers are configured in this package but have NOT been deployed or tested on Cloudflare from this session.
- Cloudflare Pages applies `_headers` to static asset responses. This static site has no Pages Functions.
- Cross-origin isolation may enable SharedArrayBuffer, but it does not guarantee LinuxOnTab will run. LinuxOnTab has additional browser, WebAssembly, worker, and networking requirements.
- A false Service Worker registration result may indicate a browser policy, scope, or deployment issue; headers alone do not guarantee registration.
- This is not a cloud VM. LinuxOnTab is a browser-hosted environment and is not connected to the local AI.
- On the Acer Chromebook 311 C723 with 8 GB RAM, running the model and VM together may cause memory pressure.
- First model load still imports WebLLM from esm.run and downloads model artifacts; fully offline inference startup is not yet verified.

ROLLBACK
Keep the original GitHub Pages deployment and repository history. If the Cloudflare version breaks an integration, continue using the original GitHub Pages URL while we adjust the headers or embeds.


REMOTE DESKTOP UPDATE
- The Remote Desktop tab no longer tries to embed DextraDesk in an iframe.
- Use the Launch DextraDesk button. It opens https://app.dextradesk.com/ in a separate tab and leaves Chromebook AI open.
- Use the Return to Chromebook AI link or switch back to the original tab.
- The dashboard intentionally does not claim to detect DextraDesk's live connection status, because cross-origin pages do not expose that state to this site.
- The service-worker cache was bumped to v6 so clients request the updated dashboard shell.

DEPLOY THIS UPDATE
1. Extract the ZIP.
2. Upload/commit index.html, sw.js, manifest.webmanifest, and README.txt to the same GitHub repository root used by your Cloudflare Git integration.
3. Do not add a _headers file for this update; it is not included. This package does not change your current Cloudflare response-header configuration.
4. Wait for the latest Git-connected deployment to show Ready/Success.
5. On the Chromebook, open the Cloudflare URL and hard refresh (Ctrl+Shift+R). If the old view remains, close and reopen the tab once so the updated service worker can take control.


Remote Desktop update: Restores the original embedded DextraDesk panel with Reload panel and Open separately fallback. DextraDesk may still refuse iframe embedding through its own security policy.
