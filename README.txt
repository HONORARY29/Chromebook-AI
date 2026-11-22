CHROMEBOOK AI — LEFT-NAV DASHBOARD BUILD

Files: index.html, manifest.webmanifest, sw.js, README.txt.

Dashboard navigation (left sidebar on desktop; horizontal tabs on small screens):
- AI Chat: local WebLLM chat configured for Qwen2.5-0.5B-Instruct-q4f16_1-MLC; browser-local conversation history, export and clear.
- Remote Desktop: DextraDesk embedded at https://app.dextradesk.com/ with reload and separate-page fallback.
- Linux VM: LinuxOnTab embedded in the page, with reload and separate-page fallback.
- JSFiddle: attempts to embed https://jsfiddle.net/ with a separate-page fallback. JSFiddle may block full-editor iframe embedding; this is controlled by JSFiddle's response/security policy. Includes a small local sandboxed JavaScript scratchpad as a fallback, not a replacement for the JSFiddle service.
- Compatibility: a built-in test runs in the actual Chromebook AI website context and reports SharedArrayBuffer, cross-origin isolation, Service Worker, secure context, and WebGPU.

Important technical notes:
- SharedArrayBuffer commonly requires cross-origin isolation, usually configured by COOP and COEP response headers. Standard GitHub Pages does not provide arbitrary custom response-header configuration. If the test reports false, that is a website-context result; it does not prove the Chromebook hardware lacks the capability.
- JSFiddle's full editor may refuse iframe embedding. Use its separate-page link if the panel is blank or blocked.
- DextraDesk and LinuxOnTab are third-party embedded sites. Their iframe policies, sign-in, and features are controlled by those providers.
- The VM is a browser-side Linux environment, not a cloud compute VM. It is not automatically connected to the local AI.
- On an 8 GB Chromebook, running the VM and local model simultaneously may cause memory pressure. Close or stop one if performance degrades.
- The JS scratchpad runs user-entered code in a sandboxed iframe. Do not use it for secrets or untrusted code.

Deployment:
1. Extract this ZIP.
2. Open chromebook_ai_v1.
3. Upload all four files to the root of the GitHub Pages repository, replacing the existing versions.
4. Wait for GitHub Pages to redeploy.
5. Refresh the website. If an old version persists, close and reopen the installed PWA or clear its site cache.

Verification:
- Files were created and checked locally for expected sections and controls.
- This build has NOT been tested on the Chromebook.
- Confirm each tab, DextraDesk, LinuxOnTab, JSFiddle embedding, local model loading, and compatibility output on the actual device.
