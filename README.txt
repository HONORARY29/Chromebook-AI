CHROMEBOOK AI V1 — DEXTRADESK EMBED TEST BUILD

Files: index.html, manifest.webmanifest, sw.js, README.txt.

Features:
- Local WebLLM chat configured for Qwen2.5-0.5B-Instruct-q4f16_1-MLC.
- Local browser conversation history, export and clear controls.
- PWA manifest and service-worker app-shell caching.
- Replaced the Chrome Remote Desktop section with a DextraDesk browser panel using an iframe to https://app.dextradesk.com/.
- Reload control for the embedded panel and a separate-site fallback link if embedding is refused.

DextraDesk facts from its public website:
- The remote host is a Windows 10/11 PC with DextraDesk installed.
- The controlling device uses a modern browser; no client app is required on the Chromebook.
- DextraDesk describes its stream as encrypted WebRTC.
- The free plan is limited to one hour per day; paid Personal plan removes the time limit.

Important limitations / verification:
- The DextraDesk website advertises browser access, but its public pages do not document support for embedding its app inside third-party iframes.
- The iframe integration is therefore an unverified embed attempt, not a confirmed working embed. DextraDesk may block it using browser security headers or its authentication flow. If so, the browser cannot override that restriction; the provider would need to support embedding or offer an official SDK/API.
- No DextraDesk account was accessed, no PC was paired, and no remote session was tested.
- This Chromebook AI page cannot directly inspect/control the remote session or automatically authorize sensitive actions.
- Never share DextraDesk passwords or two-factor codes with the local AI.
- Full offline startup has not been verified. The WebLLM JavaScript library is fetched from esm.run.

Deployment:
1. Extract this ZIP.
2. Upload the four files inside chromebook_ai_v1 to the root of your GitHub Pages repository, replacing the existing versions.
3. Wait for GitHub Pages to redeploy, then hard-refresh/reopen the PWA.
4. Sign in to DextraDesk inside the embedded panel if it loads.
5. If the panel is blank or says it refused to connect, DextraDesk does not permit embedding in this page; use the fallback link or ask DextraDesk support whether they offer an embeddable client/SDK.
